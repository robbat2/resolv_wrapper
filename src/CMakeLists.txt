project(libresolv_wrapper C)

include_directories(${CMAKE_BINARY_DIR})
add_library(resolv_wrapper SHARED resolv_wrapper.c)
target_link_libraries(resolv_wrapper ${RWRAP_REQUIRED_LIBRARIES})

set_target_properties(
  resolv_wrapper
    PROPERTIES
      VERSION
        ${LIBRARY_VERSION}
      SOVERSION
        ${LIBRARY_SOVERSION}
)

install(
  TARGETS
    resolv_wrapper
  RUNTIME DESTINATION ${BIN_INSTALL_DIR}
  LIBRARY DESTINATION ${LIB_INSTALL_DIR}
  ARCHIVE DESTINATION ${LIB_INSTALL_DIR}
)

set(RESOLV_WRAPPER_LOCATION "${CMAKE_CURRENT_BINARY_DIR}/${CMAKE_SHARED_LIBRARY_PREFIX}resolv_wrapper${CMAKE_SHARED_LIBRARY_SUFFIX}" PARENT_SCOPE)
