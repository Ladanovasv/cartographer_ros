# Copyright 2016 The Cartographer Authors
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

google_binary(cartographer_node
  SRCS
    node_main.cc
)

install(TARGETS cartographer_node
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

google_binary(cartographer_offline_node
  SRCS
    offline_node_main.cc
)

install(TARGETS cartographer_offline_node
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

google_binary(cartographer_occupancy_grid_node
  SRCS
    occupancy_grid_node_main.cc
)

install(TARGETS cartographer_occupancy_grid_node
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

google_binary(cartographer_rosbag_validate
  SRCS
    rosbag_validate_main.cc
)

install(TARGETS cartographer_rosbag_validate
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

google_binary(pbstream_map_to_pcd
  SRCS
  pbstream_map_to_pcd_main.cc
)

google_binary(pbstream_trajectories_to_rosbag
  SRCS
  pbstream_trajectories_to_rosbag_main.cc
)

# google_binary(pbstream_combine
#   SRCS
#   pbstream_combine_main.cc
# )

google_binary(cartographer_dev_pbstream_trajectories_to_rosbag
  SRCS
  dev/pbstream_trajectories_to_rosbag_main.cc
)

install(TARGETS cartographer_dev_pbstream_trajectories_to_rosbag
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

google_binary(cartographer_dev_rosbag_publisher
  SRCS
  dev/rosbag_publisher_main.cc
)

install(TARGETS cartographer_dev_rosbag_publisher
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

google_binary(cartographer_dev_trajectory_comparison
  SRCS
  dev/trajectory_comparison_main.cc
)

install(TARGETS cartographer_dev_trajectory_comparison
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

# TODO(cschuet): Add support for shared library case.
if (${BUILD_GRPC})
  google_binary(cartographer_grpc_node
    SRCS
      cartographer_grpc/node_grpc_main.cc
  )

  install(TARGETS cartographer_grpc_node
    ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
    LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
    RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
  )

  google_binary(cartographer_grpc_offline_node
    SRCS
      cartographer_grpc/offline_node_grpc_main.cc
  )

  install(TARGETS cartographer_grpc_offline_node
    ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
    LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
    RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
  )

  install(PROGRAMS
    ../scripts/cartographer_grpc_server.sh
    DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
  )
endif()
