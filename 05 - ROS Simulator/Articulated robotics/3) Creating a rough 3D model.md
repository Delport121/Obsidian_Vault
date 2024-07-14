#ROS
Root link must be called base_link
Oritation of this link must be: 
- x-forward
- y-left
- z-up

Robot has been build (He also provides the code)

Was then saved in Rviz

must also run joint state publisher so the wheels will display:
```bash
ros2 run joint_state_publisher_gui joint_state_publisher_gui
```

Can open the rviz config with
```bash
rviz2 -d Documents/dev_ws/src/my_bot/config/view_bot.rviz
```