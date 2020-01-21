include(FetchContent)

FetchContent_Declare(
  Eigen
  GIT_REPOSITORY       https://github.com/eigenteam/eigen-git-mirror.git
  GIT_TAG              3.3.7
  )

FetchContent_GetProperties(Eigen)
if(NOT eigen_POPULATED)
  FetchContent_Populate(Eigen)
  add_library(Eigen INTERFACE)
  target_compile_definitions (Eigen INTERFACE "")
  target_include_directories(Eigen INTERFACE
    $<BUILD_INTERFACE:${eigen_SOURCE_DIR}>
    $<INSTALL_INTERFACE:${INCLUDE_INSTALL_DIR}>
  )

  set_target_properties (Eigen PROPERTIES EXPORT_NAME Eigen)
  install (TARGETS Eigen EXPORT Eigen3Targets)
  export (TARGETS Eigen NAMESPACE Eigen3:: FILE Eigen3Targets.cmake)
  export (PACKAGE Eigen3)
  install (EXPORT Eigen3Targets NAMESPACE Eigen3:: DESTINATION ${CMAKE_INSTALL_DATADIR}/Eigen3/cmake)

  add_library(Eigen3::Eigen ALIAS Eigen)
endif()

