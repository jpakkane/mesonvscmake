# Compilation speed comparison test

*DO NOT USE THIS FOR ANY SORT OF PRODUCTION*

This is a (historyless) fork of the Mediascanner project. It is only
used for the purposes of comparing build speed between CMake and
Meson. It is broken and handicapped in many ways:

 - disable all things using dbus-cpp because it is not generally available
 - disable Qml stuff
 - tests will not run successfully (in fact don't run them at all)
 - functionality is probably broken

If you wish to use Mediascanner, get it [from its original web
site](https://launchpad.net/mediascanner2). This repo should not be
used for anything else except build speed comparison tests.