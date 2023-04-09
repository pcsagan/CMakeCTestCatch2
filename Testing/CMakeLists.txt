# Download the Catch2 dependency from github
Include(FetchContent)
FetchContent_Declare(Catch2
    GIT_REPOSITORY https://github.com/catchorg/Catch2.git
    GIT_TAG        v3.3.2
)
FetchContent_MakeAvailable(Catch2)

# Create the test runner
add_executable(Testing bdd_style.cpp classic_style.cpp)

# Link the test runner to the test library
target_link_libraries(Testing PRIVATE Catch2::Catch2WithMain)

# Include the utility to discover tests
list(APPEND CMAKE_MODULE_PATH ${catch2_SOURCE_DIR}/extras)
include(Catch)

# Make our tests visible to CTest
catch_discover_tests(Testing)

# Place the testing-related projects into their own solution-level folder
set(TESTING_FOLDER "Testing")
set_target_properties(Catch2         PROPERTIES FOLDER "${TESTING_FOLDER}")
set_target_properties(Catch2WithMain PROPERTIES FOLDER "${TESTING_FOLDER}")
set_target_properties(Testing        PROPERTIES FOLDER "${TESTING_FOLDER}")
