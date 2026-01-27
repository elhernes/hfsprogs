hfsprogs
========

Apple's HFS utils, ported and patched for Linux. Now with debian patches applied!

Originally [diskdev-cmds](https://opensource.apple.com/tarballs/diskdev_cmds/).<br />
* Change `tarballs` to `source` if you want to browse the source.

INSTALL
----
Missing right now.

Try referring to the debian/ folder or reading something from the AUR.

COPYING
----
[APPLE PUBLIC SOURCE LICENSE, Version 2.0](www.opensource.apple.com/license/apsl/).

TODOs
----
- [ ] Delete useless things to minimize tarball size.
- [ ] Create build scripts for ArchLinux, AOSC OSes and Generic Systems.
- [ ] Rebase to a newer version, apply patches, distribute minimized&patched tarballs. (Use diff to create patches for those who already downloaded Apple's version.)
- [ ] Test if it compiles on other *nix systems. I hope there is no GCC(gcc can't compile).
