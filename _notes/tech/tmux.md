---
title: Notes on rolling out tmux
layout: notes
---

I have used [screen] for a while, particularly when doing server
admin[^fn-compare].

Recently, I came across a similar tool, [tmux](https://github.com/tmux/tmux/wiki)
that I thought would be worth testing out. There can be a steep learning curve
with some of these things, and tmux was the same. Here are some notes, tips and
resources.

### introductions

* <https://hackernoon.com/a-gentle-introduction-to-tmux-8d784c404340>
* <https://thoughtbot.com/blog/a-tmux-crash-course>
* <https://danielmiessler.com/study/tmux/>
* [More advanced](https://thoughtbot.com/blog/seamlessly-navigate-vim-and-tmux-splits)
  as both ViM and tmux can create split windows.
### tmux configuration

* There are (similar to ViM) a large range of configuration options, files,
  tweaks and even meta configs. [An example](https://github.com/gpakosz/.tmux)
* The config file references a color palette of 16 or 256 colours. You can
  display a list of these colours by [running this shell script](https://superuser.com/questions/285381/how-does-the-tmux-color-palette-work).

[^fn-compare]: A [comparison of keybindings](http://hyperpolyglot.org/multiplexers)
