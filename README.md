# C1 Camera ROS2 Package for Jetson AGX Orin

## Overview

This repository is an ROS2 package for the C1 camera designed for Jetson devices. It enables the use of the C1 camera via a GMSL2-USB 3.0 Conversion Kit. Images are acquired via USB, and time synchronization is possible using the [`sensor_trigger`](https://github.com/tucasa/sensor_trigger) package. 

## Environment

- **Jetson AGX Orin** (Verified with JetPack r35.5.0)
- **ROS2 Humble** (Verified in a Docker environment)
- **GMSL2-USB 3.0 Conversion Kit**
- **C1 Camera**

## Dependencies

- [`v4l2_camera`](https://github.com/tier4/ros2_v4l2_camera)
- [`sensor_trigger`](https://github.com/tucasa/sensor_trigger)

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/tucasa/c1_cam_usb_sync
   cd c1_cam_usb_sync
   ```
2. Build:
   ```bash
   colcon build --symlink-install
   ```
3. Set up environment variables:
   ```bash
   source install/setup.bash
   ```

## Usage

### Launch Command

To start the C1 camera, execute the following command (when using time synchronization with a single C1 camera):

```bash
ros2 launch c1_x1_gpio_trigger.launch.xml
```

### Key Parameters

| Parameter      | Description                                          |
| -------------- | ---------------------------------------------------- |
| `camera_name`  | Name of the camera being used                        |
| `video_device` | Video device used (e.g., `/dev/video0`)              |
| `publish_rate` | Frequency of image publishing (in Hz)                |
| `gpio_name`    | Name of the GPIO pin (for sync signal)               |
| `phase`        | Phase setting for GPIO synchronization (0.0 – 360.0) |
