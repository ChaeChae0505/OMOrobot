
### OMO 구동
1. Keyboard 설정
- [teleop twist keyboard pkg 다운](github.com/ros-teleop/teleop_twist_keyboard)
- drive_r1.launch 파일 수정
```
<!-- Launch R-1 default -->
before
<node respawn="true" pkg="teleop_twist_keyboard" type="teleop_twist_keyboard.py" name="teleop" output="screen"/>

<node respawn="true" pkg="joy" type="joy_node" name="teleop_joy"/>
<include file="$(find omoros)/launch/includes/r1_description.launch.xml">
</include>
<node pkg="omoros" type="driver_r1.py" name="omoros" output="screen">
<param name="port" value="$(arg set_port)"/>
<param name="baud" value="115200"/>
<param name="modelName" value="r1"/>
<param name="joy_enable" value="$(arg set_joy_en)"/>
</node>

-------------------------------------------------------
after
   <arg name="set_joy_en" default="0"/>
<!-- Launch R-1 default -->
      <node respawn="true" pkg="teleop_twist_keyboard" type="teleop_twist_keyboard.py" name="teleop" output="screen"/>
      <include file="$(find omoros)/launch/includes/r1_description.launch.xml">
      </include>
      <node pkg="omoros" type="driver_r1.py" name="omoros" output="screen">
         <param name="port" value="$(arg set_port)"/>
         <param name="baud" value="115200"/>
         <param name="modelName" value="r1"/>
         <param name="joy_enable" value="$(arg set_joy_en)"/>
      </node>
```
2. rplidar수정
- [링크참조](https://chaechae777.tistory.com/35?category=892631)

```
$ roslaunch omoros drive_r1.launch
$ roslaunch omoros omoros_navigation.launch
```
