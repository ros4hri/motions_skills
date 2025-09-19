# Copyright (c) 2025 PAL Robotics S.L. All rights reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

cmake_minimum_required(VERSION 3.8)
project(motion_skills)

find_package(ament_cmake_auto REQUIRED)
if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wno-float-equal)
endif()


ament_auto_find_build_dependencies()

rosidl_generate_interfaces(${PROJECT_NAME}
  "action/ExecuteJointTrajectory.action"
  DEPENDENCIES builtin_interfaces std_skills trajectory_msgs
)

ament_export_dependencies(rosidl_default_runtime)

if(BUILD_TESTING)
    ament_auto_find_test_dependencies()
    ament_lint_auto_find_test_dependencies()
endif()

ament_auto_package()
