# Autonomous Vehicle Final Project (Lane Detection in CARLA Simulator)

This repository contains the final project implementation for the Autonomous Vehicle course (Perception Projects).
The system utilizes classic Computer Vision techniques to perform real time lane detection and drivable area mapping using recorded camera feeds from the CARLA autonomous driving simulator (`Town03`).

## 🎯 Project Deliverables
As per the project requirements, this pipeline successfully implements:
* **Lane Overlay:** Real-time visual mapping of the drivable area and lane boundaries.
* **Lane Curvature Estimation:** Dynamic calculation of the road's curvature radius and direction using polynomial fitting.
* **Simulation Source:** Evaluated over a pre recorded CARLA dashcam feed, testing the algorithm against dynamic lighting, urban environments, and traffic.

## 🧠 Computer Vision Pipeline

The algorithm is structured to be robust against background noise and lighting variations:

1. **Color Thresholding (HSV):** Converting the raw BGR frame to the HSV color space. We apply specific masks to isolate yellow (left solid lines) and white (right dashed lines) markings.
2. **Region of Interest (ROI):** A dynamic trapezoidal mask is applied to ignore the sky, background buildings, and irrelevant lanes.
3. **Contrast Enhancement:** Using CLAHE (Contrast Limited Adaptive Histogram Equalization) to boost the visibility of lane markings.
4. **Edge Detection:** Applying the **Canny Edge Detector** to find sharp intensity gradients.
5. **Line Extraction (Hough Transform):** Using `cv2.HoughLinesP` to extract mathematical line segments from the detected edges.
6. **Lane Extrapolation:** Filtering noise by slope, categorizing lines into left/right bounds, and calculating the average slope and intercept to draw stable boundaries.
7. **Curvature Estimation:** Fitting a second-degree polynomial (`np.polyfit`) to the edge pixels to calculate the curvature radius in real-time.

## 🚀 How to Run:

### Make sure you have the following Python libraries installed: pip install numpy opencv-python matplotlib
Running the Script:
Clone this repository.
Ensure carla_video.mp4 is located in the root directory.
Execute the script: python lane_detection_video.py
The output will be saved automatically as Final_Project_Submission.avi.

Developed by : Meni Shteinberg 
