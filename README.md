# linked list implementation from illumos

This repo is a standalone copy of the [linked list utility code][man_list] used
in the illumos operating system.

The original (and canonical) source for this implementation is at:

    https://github.com/illumos/illumos-gate/tree/master/usr/src/common/list

The illumos linked list implementation is largely baked, and is not expected to
undergo much change.  However, the copy in this repository should be considered
strictly downstream of the one in illumos.  **There should be no local changes
here.**

## Why does this repository exist?

The linked list implementation in illumos is robust and debuggable.  In
particular, the `list` walker available in [mdb(1)][man_mdb], the Modular
Debugger, makes walking lists embedded in various objects trivial.

## How to use this repository

If you wish to use this linked list implementation, you may statically link it
into your application.  This repository includes Makefiles intended for easy
incorporation into other repositories, as via "git submodule".  The easiest way
to do this is to run:

    $ git submodule add https://github.com/joyent/illumos-list deps/illumos-list

You can build the submodule by changing directories to it and typing "make".
The default target builds a static library for the list routines.  It's fully
supported to customize two pieces of the build:

* `CFLAGS`: customize this to configure a 32-bit or 64-bit build
* `BUILD_DIR`: the directory in which to build object files and the static
  library file

You can customize these by setting these environment variables and invoking
`make`.

[man_mdb]: http://illumos.org/man/1/mdb
[man_list]: http://illumos.org/man/9F/list_create
