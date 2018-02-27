# darknet_ros
ROS wrapper for Darknet (Open Source Neural Networks in C) YOLOv2 Detector


# Build Darknet and make it available to the Wrapper

This wrapper requires the Darknet library. 
Follow the instructions at https://pjreddie.com/darknet/install/ to build it.
This process will create the library file `libdarknet.so`.

Add the following line to you `~/.bashrc` file:

```
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:<path_to_libdarknet_so>
```


# Get the Wrapper

Pull this repository in your `catkin_ws/src/` directory.


# Install Darknet Weights

Before you can use this wrapper, you have to download the weights for a pre-trained model or train the model from scratch on your own data.

You can download the pre-trained models from https://pjreddie.com/darknet/yolo/.

Save the file `yolo.weights` and `tiny-yolo.weights` in the `./models` directory.


# Build your catkin_ws

Run

```
catkin_make -C <path_to_your_catkin_ws_dir>
```


# Launch the real-time detector

```
roslaunch darknet_ros darknet_detector.launch image:=<topic_of_Image_msgs>
```

NOTE: 
- `<topic_of_Image_msgs>` has to be a topic of `sensor_msgs/Image` messages.
- The bounding boxes will be published on the topic `/darknet/detections`. Specify the `namespace` argument while launching the launch file to change the namespace of the output.
