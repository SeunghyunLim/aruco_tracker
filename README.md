# snake_tracker

## Calibration
```console
sudo apt-get install ros-melodic-usb-cam uvcdynctrl
roscore
uvcdynctrl --device=/dev/video0 --clist
uvcdynctrl --device=/dev/video0 --set='Focus, Auto' 0
uvcdynctrl --device=/dev/video0 --get='Focus, Auto'

rosrun usb_cam usb_cam_node
rosrun camera_calibration cameracalibrator.py --size 8x6 --square 0.02517 image:=/usb_cam/image_raw camera:=/usb_cam --no-service-check
```

## Marker detection
``` console
roslaunch snake_tracker usb_cam_stream_publisher.launch
roslaunch snake_tracker aruco_marker_finder.launch markerId:=701 markerSize:=0.05
rosrun rqt_gui rqt_gui
```
