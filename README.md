PIUIO input driver for Linux
============================

*Well hello there!*  Terrified of change?  You've come to the right place.
Welcome to the legacy branch of the PIUIO driver.  This branch contains hacks
to get it compile all the way back to Linux 2.6.12, but it is neither actively
tested nor actively maintained.  Patches and pull requests are still welcome,
but they are entirely your responsibiity.

You are, of course, strongly encouraged to upgrade to the latest kernel and the
*real* driver!

This is a driver for the PIUIO arcade I/O board that maps panels and buttons to
a standard Linux event interface, typically appearing as a joystick.  It is
coded assuming the default configuration where four sets of inputs are attached
to a multiplexer.


Module parameters
-----------------

There are currently no parameters for this module.


Compiling and installing
------------------------

To compile the kernel module, run `make` inside the `mod` directory.  This will
build a kernel object file `piuio.ko` which is compatible with your currently
installed kernel.  To build against different kernel headers, you may specify
the path to a source tree using the `KDIR` variable when building, e.g.:

    make KDIR=~/src/linux-3.15.7

To install this module once you have built it, use the `make install` command.
By default this will attempt to install the module directly to your system;
note that doing so will require root privileges.  To specify a path under
which to install (e.g. for packaging), you can specify a `DESTDIR`:

    make DESTDIR="$pkgdir" install


Tools
-----

Since this module uses the input subsystem, you can use standard tools such as
[evemu](http://cgit.freedesktop.org/evemu/) to test it.  Outputs are currently
not implemented in the driver.
