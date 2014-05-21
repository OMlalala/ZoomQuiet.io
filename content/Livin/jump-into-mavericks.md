Title: from Lion jump into Mavericks
Date: 2013-12-30
Tags: MAC,Leo,Pyenv,ZQ
Slug: jump-into-mavericks


# 为毛
得承认是被 老池的文章忽悠到了, 
而且, 10.9 免费了, 进一步的通过OS 提高了电池/内存的使用效率,
最关键的,在 [无责任报道~ECUG2013Con](http://techparty.org/events/2013/12/29/et-ecugcon-sz/) 中提及过的,
有好基友,已经折腾过,明确从 10.7 直升没有问题!

于是一个月黑风高的晚上...

# 回顾

## Leo
About X11 and OS X 
    http://support.apple.com/kb/HT5293
XQuartz 
    http://xquartz.macosforge.org/landing/


$ brew install pyqt
==> Downloading http://downloads.sf.net/project/pyqt/PyQt4/PyQt-4.10.3/PyQt-mac-gpl-4.10.3.tar.gz
Already downloaded: /Library/Caches/Homebrew/pyqt-4.10.3.tar.gz
==> Patching
patching file configure.py
==> /usr/local/opt/python/bin/python2 configure.py --confirm-license --bindir=/usr/local/Cellar/pyqt/4.10.3/bin --destdir=/usr/local/Cellar/
Error: Unable to find the qmake configuration file
/usr/local/Cellar/qt/4.8.5/mkspecs/unsupported/macx-clang-libc++/qmake.conf.
Use the QMAKESPEC environment variable to specify the correct platform.
Determining the layout of your Qt installation...

READ THIS: https://github.com/Homebrew/homebrew/wiki/troubleshooting



## Pyenv




==> Upgrading python3
==> Installing python3 dependency: sqlite
==> Downloading https://downloads.sf.net/project/machomebrew/Bottles/sqlite-3.8.2.mavericks.bottle.tar.gz
###################                                                       26.9%
curl: (56) Recv failure: Connection reset by peer
Warning: Bottle installation failed: building from source.
==> Downloading http://www.sqlite.org/2013/sqlite-autoconf-3080200.tar.gz
######################################################################## 100.0%
==> ./configure --prefix=/usr/local/Cellar/sqlite/3.8.2 --enable-dynamic-extensions
==> make install
==> Caveats
This formula is keg-only, so it was not symlinked into /usr/local.

Mac OS X already provides this software and installing another version in
parallel can cause all kinds of trouble.

OS X provides an older sqlite3.

Generally there are no consequences of this for you. If you build your
own software and it requires this formula, you'll need to add to your
build variables:

    LDFLAGS:  -L/usr/local/opt/sqlite/lib
    CPPFLAGS: -I/usr/local/opt/sqlite/include

==> Summary
🍺  /usr/local/Cellar/sqlite/3.8.2: 9 files, 2.0M, built in 48 seconds



==> Installing python3
==> Downloading http://python.org/ftp/python/3.3.3/Python-3.3.3.tar.bz2
######################################################################## 100.0%
==> ./configure --prefix=/usr/local/Cellar/python3/3.3.3 --enable-ipv6 --datarootdir=/usr/local/Cellar/python3/3.3.3/share --datadir=/usr/lo
==> make
==> make install PYTHONAPPSDIR=/usr/local/Cellar/python3/3.3.3
==> make frameworkinstallextras PYTHONAPPSDIR=/usr/local/Cellar/python3/3.3.3/share/python3
Error in sitecustomize; set PYTHONVERBOSE for traceback:
ValueError: list.remove(x): x not in list
Error in sitecustomize; set PYTHONVERBOSE for traceback:
ValueError: list.remove(x): x not in list
Error in sitecustomize; set PYTHONVERBOSE for traceback:
ValueError: list.remove(x): x not in list
Error in sitecustomize; set PYTHONVERBOSE for traceback:
ValueError: list.remove(x): x not in list
Error in sitecustomize; set PYTHONVERBOSE for traceback:
ValueError: list.remove(x): x not in list
Error in sitecustomize; set PYTHONVERBOSE for traceback:
ValueError: list.remove(x): x not in list
Error in sitecustomize; set PYTHONVERBOSE for traceback:
ValueError: list.remove(x): x not in list
Error in sitecustomize; set PYTHONVERBOSE for traceback:
ValueError: list.remove(x): x not in list
Error in sitecustomize; set PYTHONVERBOSE for traceback:
ValueError: list.remove(x): x not in list
Error in sitecustomize; set PYTHONVERBOSE for traceback:
ValueError: list.remove(x): x not in list



## 伟光大的 sshfs


    $ brew link fuse4x
    Linking /usr/local/Cellar/fuse4x/0.9.2... Warning: Could not link fuse4x. Unlinking...

    Error: Could not symlink file: /usr/local/Cellar/fuse4x/0.9.2/lib/pkgconfig/fuse.pc
    Target /usr/local/lib/pkgconfig/fuse.pc already exists. You may need to delete it.
    To force the link and overwrite all other conflicting files, do:
      brew link --overwrite formula_name

    To list all files that would be deleted:
      brew link --overwrite --dry-run formula_name

    zoomq @ MBP111216ZQ in /usr/local/lib
    $ brew link --overwrite fuse4x
    Linking /usr/local/Cellar/fuse4x/0.9.2... 7 symlinks created


    $ brew install osxfuse
    ==> Downloading https://downloads.sf.net/project/machomebrew/Bottles/osxfuse-2.6.2.mavericks.bottle.tar.gz
    ==> Pouring osxfuse-2.6.2.mavericks.bottle.tar.gz
    ==> Caveats
    If upgrading from a previous version of osxfuse, the previous kernel extension
    will need to be unloaded before installing the new version. First, check that
    no FUSE-based file systems are running:

      mount -t osxfusefs

    Unmount all FUSE file systems and then unload the kernel extension:

      sudo kextunload -b com.github.osxfuse.filesystems.osxfusefs

    The new osxfuse file system bundle needs to be installed by the root user:

      sudo /bin/cp -RfX /usr/local/Cellar/osxfuse/2.6.2/Library/Filesystems/osxfusefs.fs /Library/Filesystems
      sudo chmod +s /Library/Filesystems/osxfusefs.fs/Support/load_osxfusefs
    ==> Summary
    🍺  /usr/local/Cellar/osxfuse/2.6.2: 84 files, 5.0M


## DisplayLink

## 140518
zoomq @ MBP111216ZQ in ~
$ brew upgrade
==> Upgrading 32 outdated packages, with result:
autojump 21.7.1, brew-cask 0.35.0, doxygen 1.8.7, ffmpeg 2.2.2, fftw 3.3.4, fribidi 0.19.6, ghc 7.6.3_2, git 1.9.3, glib 2.40.0_1, gmp 6.0.0a, gnupg2 2.0.22_1, go 1.2.2, harfbuzz 0.9.28, imagemagick 6.8.9-1, lftp 4.4.16, libass 0.11.2, libgpg-error 1.13, libtasn1 3.5, little-cms2 2.6, mongodb 2.6.1, mpc 0.25, mpd 0.18.11, nginx 1.6.0_1, node 0.10.28, orc 0.4.19, qt 4.8.6, readline 6.3.5, redis 2.8.9, rtmpdump 2.4+20131018, tree 1.7.0, wavpack 4.70.0, x264 r2412
==> Upgrading autojump

...

==> Downloading https://storage.googleapis.com/golang/go1.2.2.src.tar.gz
######################################################################## 100.0%
==> ./make.bash --no-clean
==> Caveats
As of go 1.2, a valid GOPATH is required to use the `go get` command:
  http://golang.org/doc/code.html#GOPATH

`go vet` and `go doc` are now part of the go.tools sub repo:
  http://golang.org/doc/go1.2#go_tools_godoc

To get `go vet` and `go doc` run:
  go get code.google.com/p/go.tools/cmd/godoc
  go get code.google.com/p/go.tools/cmd/vet

You may wish to add the GOROOT-based install location to your PATH:
  export PATH=$PATH:/usr/local/opt/go/libexec/bin

Bash completion has been installed to:
  /usr/local/etc/bash_completion.d

zsh completion has been installed to:
  /usr/local/share/zsh/site-functions

...

==> Pouring nginx-1.6.0_1.mavericks.bottle.tar.gz
==> Caveats
Docroot is: /usr/local/var/www

The default port has been set in /usr/local/etc/nginx/nginx.conf to 8080 so that
nginx can run without sudo.

To have launchd start nginx at login:
    ln -sfv /usr/local/opt/nginx/*.plist ~/Library/LaunchAgents
Then to load nginx now:
    launchctl load ~/Library/LaunchAgents/homebrew.mxcl.nginx.plist
Or, if you don't want/need launchctl, you can just run:
    nginx

    

# Changelog

- 140505 快速简述完成
- 140110 起意,总结
