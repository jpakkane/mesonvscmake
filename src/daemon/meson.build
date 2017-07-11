scanner_lib = static_library('scannerstuff',
  'InvalidationSender.cc',
  'MountWatcher.cc',
  'VolumeManager.cc',
  'SubtreeWatcher.cc',
  'Scanner.cc',
  '../mediascanner/utils.cc',
  link_with : extr_lib,
  include_directories : ms_inc,
  dependencies : [glib_dep, udisks_dep],
)

executable('mediascanner-service-2.0',
  'scannerdaemon.cc',
  link_with : [mslib, scanner_lib],
  dependencies : glib_dep,
)
