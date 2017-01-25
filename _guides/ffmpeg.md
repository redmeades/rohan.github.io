---
layout: guide
title: "A guide to using ffmpeg for video manipulation"
permalink: /guides/ffmpeg/
date: 2016-08-24
---
Updated: {{ page.date | date: "%b, %Y" }}

If you need to do anything to digital video, it is well worth your while
getting a copy of [ffmpeg](https://ffmpeg.org/).

The project describes itself as

> A complete, cross-platform solution to record, convert and stream audio and video.

I think of it as a video swiss-army knife that enables you to manipulate video,
primarily in terms of converting between formats and reducing big files down.

Importantly, it is a commandline tool, so you will have to know how to launch a Terminal
window.

## Installation ##

I use [brew](https://brew.sh), so installing is as simple as:

{% highlight bash %}
brew install ffmpeg --with-libvpx --with-libvorbis --with-x265 --with-faac --with-fdk-aac
{% endhighlight %}

Check the ffmpeg site for alternate ways.

## Basics ##

To convert formats, one simply has to specify the input file (with -i) and the output
file. The format is determined from the file extension and ffmpeg goes about its
conversion process to achieve the requested output format:

{% highlight bash %}
ffmpeg -i input.mp4 output.avi
{% endhighlight %}

In the case of converting a mov file to a mp4, the internal audio and video streams
actually do not need converting, just the container does. So you can ask ffmpeg to 
copy the streams while converting the container:

{% highlight bash %}
ffmpeg -i input.mov -vcodec copy -acodec copy output.mp4
{% endhighlight %}

### Extracting Audio

Sometimes you come across a lecture video and you want to extract the audio so that
you or others can listen to it on a phone or in the car. ffmpeg can do that:

{% highlight bash %}
ffmpeg -i lecture.mp4 -vcodec none audio.mp3
{% endhighlight %}

## More Advanced Options

At the office we have need to convert our videos to a consistent output format and quality

{% highlight bash %}
ffmpeg -i input.mov -c:v libx264 -preset slow -pix_fmt yuv420p -profile:v main -movflags +faststart -crf 26 -filter:v scale=-1:720 -c:a libfdk_aac -ac 1 -ar 44100 -vbr 3 output.mp4
{% endhighlight %}

Breaking this down:

* -c:v libx264 -- use the x264 encoder, which enables certain other options below
* -preset slow -- presets tell the encoder how hard to work to reduce the file size, here we’re willing to spend more time converting
* -pix_fmt yuv420p -- this ensures that the video format is widely compatible
* -profile:v main -- this again ensures compatibility with a variety of devices
* -movflags +faststart -- this helps for files that are served via a web-browser
* -crf 26 -- a quality factor between 0 (lossless) to 51 (very lossy), 26-8 is a sweet-spot between file size and quality
* -filter:v scale=-1:720 -- resize any input to be 720 high and figure out the width (-1)
* -c:a libfdk_aac -- use this aac encoder
* -ac 1 -- go mono as we mostly have talking, not stereo music
* -ar 44100 -- keep the voice quality high as that is important for listeners
* -vbr 3 -- like crf, but 1 (low) to 6 (high) for audio compression

### GIF file creation

If you are wanting to create a small animated gif, you can look at the instruction
on [this site](http://blog.pkh.me/p/21-high-quality-gif-with-ffmpeg.html)
