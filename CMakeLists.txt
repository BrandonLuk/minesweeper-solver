cmake_minimum_required(VERSION 3.10)

project(MinesweeperSolver)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)
set(CMAKE_BUILD_TYPE Debug)
set(CMAKE_CXX_FLAGS "-ggdb -pedantic -Wall -Wextra")

set(LIB Solver/solver.cpp Solver/matrix.cpp Solver/frontier.cpp)

add_executable(MinesweeperSolver Minesweeper/minesweeper.cpp ${LIB})