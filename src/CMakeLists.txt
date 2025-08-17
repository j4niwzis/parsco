if(BUILD_EXAMPLES)
  add_subdirectory( example )
endif()

file( GLOB sources "[a-zA-Z]*.cpp" )

add_library(
  parsco
  STATIC
  ${sources}
)

target_compile_features(
  parsco
  PUBLIC
  cxx_std_20
)

set_target_properties(
  parsco
  PROPERTIES
  CXX_EXTENSIONS OFF
)

target_compile_options(
  parsco
  PRIVATE
  -Wall
  -Wextra
)

target_include_directories(
  parsco PUBLIC $<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}/src/include>
                $<INSTALL_INTERFACE:include/${PROJECT_NAME}>
)
