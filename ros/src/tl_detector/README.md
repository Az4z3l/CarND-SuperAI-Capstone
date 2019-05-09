Traffic Light Detection
---

This node is in charge of detecting the traffic lights from the images fed from the on-board camera, when a red light is detected
a message is published on the `/traffic_waypoint` topic.

The approach taken for this task is to train a neural network for object detection using each light state as a different class, in
this way the classification task is reduced into the same network.

The documentation and code used for training can be found [here](https://github.com/marcomarasca/CarND-Traffic-Light-Detection).

The data for training was collected from both the simulator, recording a bag and then saving the camera images and from a bag provided by udacity that can be downloaded from [here](https://s3-us-west-1.amazonaws.com/udacity-selfdrivingcar/traffic_light_bag_file.zip).

Additional bags are provided by udacity for testing the detector in the real world that were recorded at the [Test Site](https://drive.google.com/file/d/0B2_h37bMVw3iYkdJTlRSUlJIamM/view?usp=sharing).

To record a bag while running in the simulator:

```sh
$ mkdir ~/bagfiles
$ cd ~/bagfiles
$ rosbag record /image_color

```

After the bag was recorded we can play it running roscore in one terminal:

```sh
$ roscore
```

In a separate terminal we play the bag:

```sh
$ rosbag play -l bagfile.bag
```

and finally in yet a separate terminal we can save the images received from the /image_color topic:

```sh
$ rosrun image_view image_saver _sec_per_frame:=0.01 image:=/image_color
```

NOTE: The topic from the the ros bag recorded from the Carla at Udacity is instead */image_raw*

