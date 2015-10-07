# yue.nicholas@gmail.com

configure_file(eLut.h eLut.h COPYONLY)
configure_file(toFloat.h toFloat.h COPYONLY)

SET_SOURCE_FILES_PROPERTIES(
  half.cpp
  PROPERTIES
  OBJECT_DEPENDS
  ${CMAKE_CURRENT_BINARY_DIR}/eLut.h
  OBJECT_DEPENDS
  ${CMAKE_CURRENT_BINARY_DIR}/toFloat.h
  )

IF(BUILD_SHARED_LIBS)
    ADD_DEFINITIONS(-DHALF_EXPORTS)
ENDIF()

ADD_LIBRARY ( Half ${LIB_TYPE}
  half.cpp
  )

INSTALL ( TARGETS
  Half
  DESTINATION
  lib
)

INSTALL ( FILES 
  half.h
  halfFunction.h
  halfExport.h
  halfLimits.h
  DESTINATION
  include/OpenEXR
)
