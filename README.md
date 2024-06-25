# Object Detection and Tracking using OpenCV

This repository contains code for object detection and tracking using OpenCV. The project aims to detect objects in real-time from a video feed and track them as they move across the frame.

## Table of Contents
- [Introduction](#introduction)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Results](#results)
- [Contributing](#contributing)
- [License](#license)
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
    git clone https://github.com/yourusername/your-repo-name.git
    cd your-repo-name
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

## Usage

1. To run the object detection and tracking script, execute the following command:
    ```sh
    python main.py
    ```

2. You can modify the parameters in the `config.py` file to change the detection and tracking behavior:
    ```python
    # config.py
    DETECTION_MODEL = 'yolov3'
    TRACKING_ALGORITHM = 'KCF'
    CONFIDENCE_THRESHOLD = 0.5
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
