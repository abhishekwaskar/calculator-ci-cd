cmake_minimum_required(VERSION 3.10)
project(CalculatorProject)

set(CMAKE_CXX_STANDARD 17)

# Add source files
add_library(calculator src/calculator.cpp)

# Google Test Setup
enable_testing()
find_package(GTest REQUIRED)
include_directories(${GTEST_INCLUDE_DIRS} include/)

# Unit Tests
add_executable(calculator_test tests/calculator_test.cpp)
target_link_libraries(calculator_test calculator GTest::GTest GTest::Main)

add_test(NAME CalculatorTests COMMAND calculator_test)
