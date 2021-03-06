# Copyright 2016 Husky Team
# 
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
# 
# http://www.apache.org/licenses/LICENSE-2.0
# 
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.


cmake_minimum_required (VERSION 3.0.2)

project (LoSHa)
# include_directories(${PROJECT_SOURCE_DIR} ${Boost_INCLUDE_DIRS})
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_BINARY_DIR})
if(CMAKE_COMPILER_IS_GNUCXX)
    set(CMAKE_CXX_FLAGS_DEBUG "-g")
    set(CMAKE_CXX_FLAGS_RELEASE "-O3 -w")
endif()

# dependencies on husky
add_subdirectory(husky)
add_definitions(${HUSKY_EXTERNAL_DEFINITION})

add_subdirectory(lshcore)
add_subdirectory(l2h)
add_subdirectory(apps)
add_subdirectory(test)

add_library(losha-lib STATIC
    $<TARGET_OBJECTS:lshcore-obj>)
SET_TARGET_PROPERTIES(losha-lib PROPERTIES LINKER_LANGUAGE CXX)
