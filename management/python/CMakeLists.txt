#
# Licensed to the Apache Software Foundation (ASF) under one
# or more contributor license agreements.  See the NOTICE file
# distributed with this work for additional information
# regarding copyright ownership.  The ASF licenses this file
# to you under the Apache License, Version 2.0 (the
# "License"); you may not use this file except in compliance
# with the License.  You may obtain a copy of the License at
#
#   http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing,
# software distributed under the License is distributed on an
# "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
# KIND, either express or implied.  See the License for the
# specific language governing permissions and limitations
# under the License.
#

find_package(PythonInterp 2.7 REQUIRED)

add_custom_target(management_python_build ALL
                  COMMAND
                      ${PYTHON_EXECUTABLE} setup.py build
                      --build-base=${CMAKE_CURRENT_BINARY_DIR}
                      --build-lib=${CMAKE_CURRENT_BINARY_DIR}/lib
                      --build-scripts=${CMAKE_CURRENT_BINARY_DIR}/bin
                  WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR})

install(CODE "execute_process(COMMAND ${PYTHON_EXECUTABLE} setup.py install
        --prefix=${CMAKE_INSTALL_PREFIX} WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR})")
  
                
