# Slouch Detector

![License](https://img.shields.io/badge/license-MIT-green)

## Overview

This application monitors user posture in real-time by analyzing body landmarks captured through a webcam. When slouching is detected, the system displays a prominent visual alert to encourage posture correction.

## Features

- **Real-time pose detection** using MediaPipe Pose.
- **Automatic calibration** based on initial sitting position.
- **Visual alert system** with big "STOP SLOUCHING!" text.
- **Loud audio alarms** to grab your attention when slouching.
- **Color-coded status indicators** (green for good posture, red for slouching).
- **Session slouch counter** to track your progress.
- **Live recalibration** capability.

## Versions

### 1. Browser Version (Recommended)
The easiest way to use the slouch detector. No installation required other than a modern browser.
- **File**: `index.html`
- **How to use**: Simply open `index.html` in your browser (Chrome/Edge recommended).
- **Features**: Includes a synthetic alarm sound and a large red overlay.

### Interface Elements

- **Status Banner**: Displays calibration status or current posture state
- **Debug Information**: Shows real-time slouch measurement versus threshold
- **Alert Display**: Red popup indicating slouch detection
- **Session Information**: Slouch counter and available keyboard shortcuts

### Camera Access Issues

**macOS**: System Settings → Privacy & Security → Camera → Enable Terminal

**Windows**: Settings → Privacy → Camera → Allow apps to access camera

**Linux**: Typically no additional permissions required

### Common Problems

**Camera not opening**
- Verify no other application is using the camera
- Check camera permissions for your terminal application

**Pose not detected**
- Ensure adequate lighting
- Position yourself fully within camera frame
- Maintain appropriate distance from camera

## Technical Details

### Dependencies

- **mediapipe** (0.10.14): Pose detection and landmark tracking
- **opencv-python** (4.10.0.84): Video capture and display
- **numpy** (1.26.4): Numerical computations

### Detection Algorithm

The posture detection algorithm operates by:

1. Tracking the vertical position of the nose landmark
2. Calculating the midpoint between left and right shoulder landmarks
3. Measuring the vertical distance from nose to shoulder line (neck distance)
4. Comparing the current neck distance against calibrated baseline
5. Triggering alerts when distance exceeds the defined threshold

The calibration process uses the median of collected frames to minimize the impact of outliers and transient movements.

## License

This project is licensed under the MIT License. See LICENSE file for details.

## Acknowledgments

- [MediaPipe](https://google.github.io/mediapipe/) by Google
- [OpenCV](https://opencv.org/)