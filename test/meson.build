gtest_inc = include_directories('/usr/src/googletest/googletest')

gtest_lib = static_library('gtest',
  '/usr/src/googletest/googletest/src/gtest-all.cc',
  dependencies : thread_dep,
  include_directories : gtest_inc,
)



# -DQT_NO_KEYWORDS)



configure_file(input : 'test_config.h.in',
  output : 'test_config.h',
  configuration : cdata)

configure_file(
  input : 'services/com.canonical.MediaScanner2.service.in',
  output : 'com.canonical.MediaScanner2.service',
  configuration : cdata)

configure_file(
  input : 'services/com.canonical.MediaScanner2.Extractor.service.in',
  output : 'com.canonical.MediaScanner2.Extractor.service)',
  configuration : cdata)

b = executable('basic', 'basic.cc',
  link_with : [mslib, scanner_lib, gtest_lib],
  include_directories : ms_inc,
  dependencies : [ms_dep, thread_dep],
  )

test('basic', b)
## The gvfs modules interfere with the private D-Bus test fixtures
#set_tests_properties(basic PROPERTIES
#  ENVIRONMENT "GIO_MODULE_DIR=${CMAKE_CURRENT_BINARY_DIR}/modules")
#
mstest = executable('test_mediastore',
  'test_mediastore.cc', '../src/mediascanner/utils.cc',
  include_directories : ms_inc,
  link_with : [mslib, gtest_lib],
  dependencies : [ms_dep, thread_dep],
  )
test('test_mediastore', mstest)

ebe = executable('test_extractorbackend', 'test_extractorbackend.cc',
  link_with : [ext_be_lib, mslib, gtest_lib],
  include_directories : [ms_inc],
  dependencies : [gst_dep, ms_dep, thread_dep],
  )
test('test_extractorbackend', ebe)

#add_executable(test_metadataextractor test_metadataextractor.cc)
#target_link_libraries(test_metadataextractor extractor-client gtest)
#add_test(test_metadataextractor test_metadataextractor)
## The gvfs modules interfere with the private D-Bus test fixtures
#set_tests_properties(test_metadataextractor PROPERTIES
#  ENVIRONMENT "GIO_MODULE_DIR=${CMAKE_CURRENT_BINARY_DIR}/modules")
#
#add_executable(test_subtreewatcher test_subtreewatcher.cc)
#target_link_libraries(test_subtreewatcher mediascanner scannerstuff gtest)
#add_test(test_subtreewatcher test_subtreewatcher)
## The gvfs modules interfere with the private D-Bus test fixtures
#set_tests_properties(test_subtreewatcher PROPERTIES
#  ENVIRONMENT "GIO_MODULE_DIR=${CMAKE_CURRENT_BINARY_DIR}/modules")
#
#add_executable(test_volumemanager test_volumemanager.cc)
#target_link_libraries(test_volumemanager mediascanner scannerstuff gtest)
#add_test(test_volumemanager test_volumemanager)
## The gvfs modules interfere with the private D-Bus test fixtures
#set_tests_properties(test_volumemanager PROPERTIES
#  ENVIRONMENT "GIO_MODULE_DIR=${CMAKE_CURRENT_BINARY_DIR}/modules")
#
#add_executable(test_sqliteutils test_sqliteutils.cc)
#target_link_libraries(test_sqliteutils gtest ${MEDIASCANNER_DEPS_LDFLAGS})
#add_test(test_sqliteutils test_sqliteutils)
#
#add_executable(test_mfbuilder test_mfbuilder.cc)
#target_link_libraries(test_mfbuilder gtest mediascanner)
#add_test(test_mfbuilder test_mfbuilder)
#
##add_executable(test_dbus test_dbus.cc)
##target_link_libraries(test_dbus gtest mediascanner ms-dbus)
##add_test(test_dbus test_dbus)
#
#add_executable(test_qml test_qml.cc)
#qt5_use_modules(test_qml QuickTest)
#target_link_libraries(test_qml mediascanner)
#add_test(test_qml test_qml -import ${CMAKE_BINARY_DIR}/src/qml)
#set_tests_properties(test_qml PROPERTIES
#  ENVIRONMENT "QT_QPA_PLATFORM=minimal"
#  TIMEOUT 600)
#
#add_test(test_qml_dbus test_qml -import ${CMAKE_BINARY_DIR}/src/qml)
#set_tests_properties(test_qml_dbus PROPERTIES
#  ENVIRONMENT "QT_QPA_PLATFORM=minimal;MEDIASCANNER_USE_DBUS=1"
#  TIMEOUT 600)
#
#add_test(test_qml_nodb qmltestrunner -import ${CMAKE_BINARY_DIR}/src/qml -input ${CMAKE_CURRENT_SOURCE_DIR}/test_qml_nodb.qml)
#set_tests_properties(test_qml_nodb PROPERTIES
#  ENVIRONMENT "QT_QPA_PLATFORM=minimal;MEDIASCANNER_CACHEDIR=${CMAKE_CURRENT_BINARY_DIR}/qml-nodb-cachedir;DBUS_SESSION_BUS_ADDRESS="
#  TIMEOUT 600)
#
#
#add_executable(test_util test_util.cc ../src/mediascanner/utils.cc)
#target_link_libraries(test_util gtest ${GLIB_LDFLAGS})
#add_test(test_util test_util)
