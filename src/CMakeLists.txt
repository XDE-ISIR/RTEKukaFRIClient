include_directories(${PROJECT_SOURCE_DIR}/include)
#
# Components, types and plugins.
#
# The CMake 'target' names are identical to the first argument of the
# macros below, except for orocos_typegen_headers, where the target is fully
# controlled by generated code of 'typegen'.
#

# Creates a component library libkuka_send_joint_positions-<target>.so
# and installs in the directory lib/orocos/kuka_send_joint_positions/
#
orocos_library(movingMean movingMean.cpp)
orocos_component(kuka_send_joint_positions kuka_send_joint_positions-component.cpp) # ...you may add multiple source files
orocos_component(DemoKukaKinectKaramaRTNET demoKukaKinectKarama-rtnetcomponent.cpp) # ...you may add multiple source files
target_link_libraries(kuka_send_joint_positions movingMean)
target_link_libraries(DemoKukaKinectKaramaRTNET movingMean)
#
# You may add multiple orocos_component statements.

#
# Additional headers:
#
# Installs in the include/orocos/kuka_send_joint_positions/ directory
#
orocos_install_headers(kuka_send_joint_positions-component.hpp movingMean.hpp demoKukaKinectKarama-rtnetcomponent.hpp) # ...you may add multiple header files
#
# You may add multiple orocos_install_headers statements.

