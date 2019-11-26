---
title: git notes
layout: tech
---

[Git](https://gitscm.com) is a source code management tool. It has become one of
the most common tools for source code management and offers many features that
make it suitable for development on large, distributed software projects such as
the Linux kernel, for which it was developed.

### Remote branches and tracking

* <https://git-scm.com/book/en/v2/Git-Branching-Remote-Branches>
* <https://felipec.wordpress.com/2013/09/01/advanced-git-concepts-the-upstream-tracking-branch/>
* <https://www.git-tower.com/learn/git/faq/track-remote-upstream-branch>
* gitlab allows for mirroring a remote repo <https://gitlab.com/help/workflow/repository_mirroring.md>
* Moodle and git <https://docs.moodle.org/33/en/Git_for_Administrators>
* more Moodle and git <https://moodle.org/mod/forum/discuss.php?d=124570>
* and <https://www.nathankowald.com/blog/2012/06/using-git-with-moodle/>
* <https://mmikowski.github.io/git-cross-origin/>

### When you commit something you shouldn't

When you start out using git, you occasionally commit whole directories and this
sometimes picks up files that you didn't want included. Or maybe you add
a feature and include a bunch of files and the configuration has a password in
it. In these instances you would like to go through the repository and remove
the file or directory from all of the commits. The following helped.

* <https://dalibornasevic.com/posts/2-permanently-remove-files-and-folders-from-a-git-repository>
* <https://stackoverflow.com/questions/10067848/remove-folder-and-its-contents-from-git-githubs-history>
