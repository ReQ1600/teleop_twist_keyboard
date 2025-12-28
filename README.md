# teleop_twist_keyboard
Generic Keyboard Teleoperation for ROS modified for romur teleop purposes.

Fork of https://github.com/ros2/teleop_twist_keyboard repository.

## Build
To build modified teleop_twist_keyboard first clone this repository into src folder of your workspace and checkout jazzy_romur_control branch
```
git clone 
git checkout jazzy_romur_control
```
Then build it with
```
colcon build
```
If you get a package selection error build with
```
colcon build --allow-overriding teleop_twist_keyboard
```

## Run

```sh
ros2 run teleop_twist_keyboard teleop_twist_keyboard
```

Publishing to a different topic (in this case `my_cmd_vel`).
```sh
ros2 run teleop_twist_keyboard teleop_twist_keyboard --ros-args --remap cmd_vel:=my_cmd_vel
```

## Usage

```
his node takes keypresses from the keyboard and publishes them
as Twist/TwistStamped messages. It works best with a US keyboard layout.
---------------------------
Thrust for Motors 0..3 in order:
   u    i    o    p   | thrust++
   j    k    l    ;   | thrust--

t : up (+z)
b : down (-z)

anything else : stop

q/e : increase/decrease thrust step by 1%

CTRL-C to quit
```

## Parameters
- `stamped (bool, default: false)`
  - If false (the default), publish a `geometry_msgs/msg/Twist` message.  If true, publish a `geometry_msgs/msg/TwistStamped` message.
- `frame_id (string, default: '')`
  - When `stamped` is true, the frame_id to use when publishing the `geometry_msgs/msg/TwistStamped` message.
- `speed (double, default: 0.5)`
  - The speed the node starts with by default.
