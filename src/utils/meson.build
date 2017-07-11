executable('watcher', 'watchertest.cc')
executable('query', 'query.cc',
  link_with : mslib,
  include_directories : ms_inc
  )
executable('mountwatcher', 'mountwatcher.cc',
  link_with : scanner_lib,
  dependencies : [glib_dep],
  )
