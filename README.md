Upstream: [kord-api](https://gitlab.com/kassowrobots/kord-api)
# Example usage:

`package.xml`
```
<?xml version="1.0"?>
<?xml-model href="http://download.ros.org/schema/package_format3.xsd" schematypens="http://www.w3.org/2001/XMLSchema"?>
<package format="3">
  <name>kassow_test</name>
  <version>0.0.0</version>
...

  <depend>kassow_kord_vendor</depend> <!-- ADD THIS --> 
...

  <export>
    <build_type>ament_cmake</build_type>
  </export>
</package>
```

`CmakeLists.txt`
```
# find dependencies
...
find_package(kassow_kord_vendor REQUIRED)

add_executable(test_node src/test_node.cpp)

ament_target_dependencies(test_node rclcpp)

target_link_libraries(test_node kord-api::kord-api) # link against kord-api

install(TARGETS test_node
  DESTINATION lib/${PROJECT_NAME})

ament_package()
```

`.hpp` includes
```
#include <kord/api/kord.h> 
#include <kord/version.h>
```
