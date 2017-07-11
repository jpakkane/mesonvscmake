# These build definitions only do the configuration
# and build parts. It does not do install, because
# its only purpose is to compare performance
# between Meson and CMake.

project('mediascanner2', 'cpp', 'c',
  version : '0.112',
  default_options : ['cpp_std=c++11',
    'c_std=c99'])

# This is only run so we do the same work as CMake,
# the result is not used.
result = run_command('get-soversion.sh').stdout().strip()

ms_dep = [dependency('gio-2.0'),
  dependency('gio-unix-2.0'),
  dependency('sqlite3', version: '>=3.8.5')
  ]

gst_dep = [dependency('gstreamer-1.0'), dependency('gstreamer-pbutils-1.0')]
glib_dep = dependency('glib-2.0')
gobject_dep = dependency('gobject-2.0')
pixbuf_dep = dependency('gdk-pixbuf-2.0')
exif_dep = dependency('libexif')
taglib_dep = dependency('taglib')
#pkg_check_modules(DBUSCPP dbus-cpp REQUIRED)
#pkg_check_modules(APPARMOR libapparmor REQUIRED)
udisks_dep = dependency('udisks2')
thread_dep = dependency('threads')
qtcore_dep = dependency('qt5', modules : 'Core')

cdata = configuration_data()


subdir('src/mediascanner')
subdir('src/extractor')
#subdir('src/daemon')
##add_subdirectory(src/ms-dbus)
##add_subdirectory(src/qml/Ubuntu/MediaScanner.0.1)
#subdir('src/utils')
#subdir('test')

# Install pkg-config file
configure_file(input : 'mediascanner-2.0.pc.in',
  output : 'mediascanner-2.0.pc',
  configuration : cdata)

# Install Upstart user session job
configure_file(input : 'mediascanner-2.0.conf.in',
  output : 'mediascanner-2.0.conf',
  configuration : cdata)
