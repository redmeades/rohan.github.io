---
title: Notes on rolling out tmux
layout: tech
---

For anyone that spends a reasonable amount of time in a terminal, uses Vi, or
has adopted a [text based approach], the use of a 'multiplexer' is helpful for
managing the various terminals that one inevitably ends up having open at any
one time.

I have used [screen] for a while, particularly when doing server
admin[^fn-compare]. Recently, I came across a similar tool, [tmux](https://github.com/tmux/tmux/wiki)
that I thought would be worth testing out. There can be a steep learning curve
with some of these things, and tmux was the same. Here are some notes, tips and
resources.

### introductions

* <https://hackernoon.com/a-gentle-introduction-to-tmux-8d784c404340>
* <https://thoughtbot.com/blog/a-tmux-crash-course>
* <https://danielmiessler.com/study/tmux/>
* [A cheatsheet](https://gist.github.com/MohamedAlaa/2961058)
* [A comprehensive guide](https://leanpub.com/the-tao-of-tmux/read)
* [More advanced](https://thoughtbot.com/blog/seamlessly-navigate-vim-and-tmux-splits)
  as both ViM and tmux can create split windows.
* and [4 useful tips](https://fedoramagazine.org/4-tips-better-tmux-sessions/)
* More [ViM and tmux](https://rhnh.net/2011/08/20/vim-and-tmux-on-osx/)
* Software development [with vim and tmux](http://joshuadavey.com/2012/01/10/faster-tdd-feedback-with-tmux-tslime-vim-and-turbux/)

### tmux configuration

* you can [generate a file of the running
  configuration](https://unix.stackexchange.com/questions/294956/how-do-i-get-a-default-tmux-configuration-file)
* There are (similar to ViM) a large range of configuration options, files,
  tweaks and even meta configs. [An example](https://github.com/gpakosz/.tmux)
* A definitive guide to [the status line](https://hackernoon.com/customizing-tmux-b3d2a5050207)
* [another guide](https://www.hamvocke.com/blog/a-guide-to-customizing-your-tmux-conf/) to configuration
* The config file references a color palette of 16 or 256 colours. You can
  display a list of these colours by [running this shell script](https://superuser.com/questions/285381/how-does-the-tmux-color-palette-work).

### reference

You can [move a window between sessions](https://stackoverflow.com/questions/3094946/move-window-between-tmux-clients)

> move-window -t other_session:

And [move a pane between windows and
sessions](https://superuser.com/questions/1105090/move-a-tmux-pane-to-another-session)

<!--
NOTES

* https://hpcc.ucr.edu/manuals_linux-cluster_terminalIDE.html
* http://manuals.bioinformatics.ucr.edu/home/programming-in-r/vim-r
* https://github.com/benmills/vimux
* https://www.hamvocke.com/blog/a-guide-to-customizing-your-tmux-conf/
-->

[^fn-compare]: A [comparison of keybindings](http://hyperpolyglot.org/multiplexers)
