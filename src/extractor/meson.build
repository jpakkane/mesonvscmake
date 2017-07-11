# Build stubs/skeletons for D-Bus interface
gnome = import('gnome')

ms_inc = include_directories('..')

gdb_src = gnome.gdbus_codegen('dbus-generated', 'dbus-interface.xml',
  interface_prefix : 'com.canonical.MediaScanner2',
  namespace : 'MS',
)

# The client code for the extractor daemon
extr_lib = static_library('extractor-client',
  'MetadataExtractor.cc',
  'dbus-marshal.cc',
  '../mediascanner/utils.cc',
  gdb_src,
  dependencies : [gst_dep, ms_dep, exif_dep, pixbuf_dep, taglib_dep],
  include_directories : ms_inc,
)
# The backend code for the extractor daemon, as a library for use by tests
ext_be_lib = static_library('extractor-backend',
  'ExtractorBackend.cc',
  'GStreamerExtractor.cc',
  'ImageExtractor.cc',
  'TaglibExtractor.cc',
  dependencies : [gst_dep, pixbuf_dep, exif_dep, taglib_dep],
)

executable('mediascanner-extractor',
  'main.cc',
  link_with :[extr_lib, ext_be_lib, mslib],
  include_directories : ms_inc,
  dependencies : [gst_dep, glib_dep, ms_dep],
  )

configure_file(input : 'com.canonical.MediaScanner2.Extractor.service.in',
  output : 'com.canonical.MediaScanner2.Extractor.service',
  configuration : cdata)
