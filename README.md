# Object Detection and Tracking using OpenCV

This repository contains code for object detection and tracking using OpenCV. The project aims to detect objects in real-time from a video feed and track them as they move across the frame.

## Table of Contents
- [Introduction](#introduction)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Results](#results)
- [Acknowledgements](#acknowledgements)

## Introduction

This project demonstrates object detection and tracking using OpenCV. The implementation includes both single object tracking and multiple object tracking from a given video. Additionally, the project supports real-time tracking using a webcam.

By leveraging OpenCV's robust computer vision algorithms, this project can detect and track objects, visualizing their movement across frames. This can be useful for a variety of applications, including surveillance, activity recognition, and more.

## Features

- Real-time object detection using pre-trained models.
- Object tracking using various algorithms (e.g., KCF, CSRT, MIL, etc.).
- Visualization of bounding boxes and tracking paths.
- Adjustable parameters for detection and tracking to fine-tune performance.

## Installation

1. Clone the repository:
    ```sh
    git clone https://github.com/maduwanthasl/Object-Detection-using-Opencv.git
    cd Object-Detection-using-Opencv
    ```

2. Create and activate a virtual environment (optional but recommended):
    ```sh
    python -m venv venv
    source venv/bin/activate   # On Windows, use `venv\Scripts\activate`
    ```

3. Install the required dependencies:
    ```sh
    pip install -r requirements.txt
    ```

    
## Code

### Single Object Tracking

Below is the Python code for single object tracking using OpenCV. This code demonstrates how to initialize a tracker, select a region of interest (ROI) for tracking, and update the tracker with each frame of the video.

```python
import cv2

# Dictionary of available trackers
TrDict = {
    'csrt': cv2.TrackerCSRT_create,
    'kcf': cv2.TrackerKCF_create,
    'mil': cv2.TrackerMIL_create,
}

# Initialize tracker
tracker = TrDict['mil']()

# Open the video file
video = cv2.VideoCapture("/home/shevi/Downloads/object_tracker.mp4")

# Read the first frame
ret, frame = video.read()

# Check if the video file is opened successfully
if not ret:
    print("Error: Failed to open video file")
    exit()

# Select a bounding box for tracking
bbox = cv2.selectROI('Frame', frame, fromCenter=False, showCrosshair=True)

# Initialize the tracker with the bounding box and the first frame
tracker.init(frame, bbox)

# Define the codec and create VideoWriter object
fourcc = cv2.VideoWriter_fourcc(*'XVID')
out = cv2.VideoWriter('tracked_output.avi', fourcc, 20.0, (frame.shape[1], frame.shape[0]))

# Loop through the video frames
while True:
    # Read a new frame
    ret, frame = video.read()
    if not ret:
        break

    # Update the tracker
    ret, bbox = tracker.update(frame)

    # Draw bounding box
    if ret:
        # Tracking success
        p1 = (int(bbox[0]), int(bbox[1]))
        p2 = (int(bbox[0] + bbox[2]), int(bbox[1] + bbox[3]))
        cv2.rectangle(frame, p1, p2, (255, 0, 0), 2, 1)
    else:
        # Tracking failure
        cv2.putText(frame, "Tracking failure detected", (100, 80), cv2.FONT_HERSHEY_SIMPLEX, 0.75, (0, 0, 255), 2)

    # Write the frame to the output video
    out.write(frame)

    # Display frame
    cv2.imshow('Frame', frame)

    # Exit if ESC pressed
    k = cv2.waitKey(1) & 0xff
    if k == 27:
        break

# Release the video capture, release the video writer, and close any open windows
video.release()
out.release()
cv2.destroyAllWindows()
```

## Results

Here are some sample results from the project:

![Sample Result 1](images/result1.png)
![Sample Result 2](images/result2.png)

## Contributing

Contributions are welcome! Please fork the repository and submit a pull request with your changes. For major changes, please open an issue first to discuss what you would like to change.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgements

- [OpenCV](https://opencv.org/) - Open Source Computer Vision Library.
- [YOLO](https://pjreddie.com/darknet/yolo/) - You Only Look Once: Unified, Real-Time Object Detection.
- [Contributors](https://github.com/yourusername/your-repo-name/graphs/contributors) who helped to improve this project.
