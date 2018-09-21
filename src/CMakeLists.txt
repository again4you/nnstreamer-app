FIND_PACKAGE(PkgConfig REQUIRED)
SET(PKGAPP_MODULES
  nnstreamer
  gstreamer-1.0
  gstreamer-base-1.0
  gstreamer-controller-1.0
  gstreamer-video-1.0
  gstreamer-app-1.0
)
pkg_check_modules(pkgs REQUIRED ${PKGAPP_MODULES})

ADD_EXECUTABLE(test_app test_app.c)
TARGET_LINK_LIBRARIES(test_app ${pkgs_LIBRARIES})
TARGET_INCLUDE_DIRECTORIES(test_app PUBLIC ${pkgs_INCLUDE_DIRS})
TARGET_COMPILE_OPTIONS(test_app PUBLIC ${pkgs_CFLAGS_OTHER})
INSTALL(TARGETS test_app RUNTIME DESTINATION ${EXEC_PREFIX})

ADD_SUBDIRECTORY(lib)
