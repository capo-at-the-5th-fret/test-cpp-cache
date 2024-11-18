cmake_minimum_required(VERSION 3.28.0)

project(test_cpp_cache
    VERSION 0.1.0
    LANGUAGES CXX
)

# https://stackoverflow.com/questions/48026483/setting-cmake-cxx-standard-to-various-values
set(CMAKE_CXX_STANDARD 23 CACHE STRING "C++ standard to be used")

add_subdirectory(include)

if (CMAKE_CURRENT_SOURCE_DIR STREQUAL CMAKE_SOURCE_DIR)

    option(TEST_CPP_CACHE_BUILD_TESTS "Enable or disable the building of tests" ON)
    option(TEST_CPP_CACHE_ENABLE_INSTALL "Enable or disable the install rule" ON)

    if (TEST_CPP_CACHE_BUILD_TESTS)
        enable_testing()
        add_subdirectory(tests)
    endif()

    # if (TEST_CPP_CACHE_ENABLE_INSTALL)

    #     include(GNUInstallDirs)
    #     include(CMakePackageConfigHelpers)

    #     # NOTE 1: The XXX_PACKAGE_TARGETS variable is referenced inside of the
    #     # xxxConfig.cmake.in file, so if the name of this variable changes, it
    #     # must be updated inside of the xxxConfig.cmake.in file.
    #     #
    #     # NOTE 2: If value of this variable changes, the xxxConfig.cmake.in file
    #     # name must be renamed to match the new value.
    #     set(TEST_CPP_CACHE_PACKAGE_NAME ${PROJECT_NAME})
    #     set(TEST_CPP_CACHE_PACKAGE_TARGETS ${TEST_CPP_CACHE_PACKAGE_NAME}Targets)

    #     set(TEST_CPP_CACHE_INSTALL_INCLUDE_DIR ${CMAKE_INSTALL_INCLUDEDIR})
    #     set(TEST_CPP_CACHE_INSTALL_CMAKE_DIR ${CMAKE_INSTALL_LIBDIR}/cmake/${TEST_CPP_CACHE_PACKAGE_NAME})

    #     set(TEST_CPP_CACHE_CONFIG_DIR ${PROJECT_BINARY_DIR}/cmake)
    #     set(TEST_CPP_CACHE_CONFIG_IN cmake/${TEST_CPP_CACHE_PACKAGE_NAME}Config.cmake.in)
    #     set(TEST_CPP_CACHE_CONFIG ${TEST_CPP_CACHE_CONFIG_DIR}/${TEST_CPP_CACHE_PACKAGE_NAME}Config.cmake)
    #     set(TEST_CPP_CACHE_CONFIG_VERSION ${TEST_CPP_CACHE_CONFIG_DIR}/${TEST_CPP_CACHE_PACKAGE_NAME}ConfigVersion.cmake)

    #     configure_package_config_file(
    #         ${TEST_CPP_CACHE_CONFIG_IN}
    #         ${TEST_CPP_CACHE_CONFIG}
    #         INSTALL_DESTINATION ${TEST_CPP_CACHE_INSTALL_CMAKE_DIR}
    #     )

    #     # major.minor.patch1 is compatible with major.minor.patch2..n
    #     # if no VERSION is specified, the ${PROJECT_VERSION} variable will be
    #     # used. if the ${PROJECT_VERSION} is not set, CMake will output an
    #     # error
    #     write_basic_package_version_file(
    #         ${TEST_CPP_CACHE_CONFIG_VERSION}
    #         COMPATIBILITY SameMinorVersion
    #     )

    #     install(
    #         FILES
    #             ${TEST_CPP_CACHE_CONFIG}
    #             ${TEST_CPP_CACHE_CONFIG_VERSION}
    #         DESTINATION ${TEST_CPP_CACHE_INSTALL_CMAKE_DIR}
    #     )

    #     install(TARGETS ${TEST_CPP_CACHE_PACKAGE_NAME}
    #         EXPORT ${TEST_CPP_CACHE_PACKAGE_TARGETS}
    #         FILE_SET HEADERS
    #     )

    #     install(EXPORT ${TEST_CPP_CACHE_PACKAGE_TARGETS}
    #         NAMESPACE ${TEST_CPP_CACHE_PACKAGE_NAME}::
    #         DESTINATION ${TEST_CPP_CACHE_INSTALL_CMAKE_DIR}
    #     )

    # endif()

endif()
