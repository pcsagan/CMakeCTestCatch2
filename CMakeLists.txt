cmake_minimum_required(VERSION 3.14)

# The name of our solution will be Example
project(Example)

# Turning on USE_FOLDERS will cause ALL_BUILD, RUN_TESTS, and ZERO_CHECK to
# be placed into a solution-level folder named CMakePredefinedTargets. It
# also enables the use of set_target_properties(... PROPERTIES FOLDER ...).
set_property(GLOBAL PROPERTY USE_FOLDERS ON)

# See https://cmake.org/cmake/help/latest/prop_tgt/CXX_STANDARD.html
set(CMAKE_CXX_STANDARD 17)

# Enable multi-processor compilation
add_compile_options(/MP)

# Add the example application
add_subdirectory(Application)

# This command should be in the source directory root because Ctest expects to
# find a test file in the build directory root.
# See https://cmake.org/cmake/help/latest/command/enable_testing.html
enable_testing()

# Add the test runner
add_subdirectory(Testing)
