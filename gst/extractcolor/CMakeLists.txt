set (SOURCES
  gstextractcolor.c
  gstextractcolororc-dist.c)
    
set (HEADERS
  gstextractcolor.h)
    
include_directories (AFTER
  ${ORC_INCLUDE_DIR})

set (libname gstextractcolor)

add_library (${libname} MODULE
  ${SOURCES}
  ${HEADERS})
  
target_link_libraries (${libname}
  ${ORC_LIBRARIES}
  ${GLIB2_LIBRARIES}
  ${GOBJECT_LIBRARIES}
  ${GSTREAMER_LIBRARY}
  ${GSTREAMER_BASE_LIBRARY}
  ${GSTREAMER_VIDEO_LIBRARY})
  
if (WIN32)
  install (FILES $<TARGET_PDB_FILE:${libname}> DESTINATION ${PDB_INSTALL_DIR} COMPONENT pdb OPTIONAL)
endif ()
install(TARGETS ${libname} LIBRARY DESTINATION ${PLUGIN_INSTALL_DIR})
