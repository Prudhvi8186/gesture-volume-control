# gesture-volume-control
Project Report: Hand Gesture Controlled Volume System
1. Project Title

Hand Gesture Based Volume Control using OpenCV, MediaPipe, and Pycaw

2. Introduction

This project implements a contactless volume controller that allows the user to adjust the system’s audio volume using hand gestures captured through a webcam.
The program uses computer vision (OpenCV), MediaPipe hand tracking, and Pycaw (Python Core Audio Windows Library) to map specific hand movements to system volume levels.

This project is an excellent example of combining AI-based computer vision with real-world system controls.

3. Objectives

To design a gesture recognition system using MediaPipe hand landmarks.

To map the distance between fingers to the system audio volume.

To implement real-time computer vision with OpenCV.

To integrate hardware (webcam) input with software-based volume control.

To make the user interface more intuitive and interactive.

4. System Requirements
Hardware

Webcam (built-in or external)

Processor: Intel i3 or higher

RAM: Minimum 4 GB

Software

OS: Windows 10/11 (PyCaw works with Windows Audio APIs)

Python 3.8+

Required Libraries:

opencv-python

numpy

mediapipe

pycaw

math

comtypes

5. Technologies Used

OpenCV (cv2): Captures video frames and draws hand tracking visuals.

MediaPipe: Detects and tracks hand landmarks (e.g., wrist, thumb, index finger).

NumPy: Used for distance calculations and interpolation mapping.

PyCaw: Provides access to system audio controls through Windows Audio API.

Python: Programming language used to integrate all components.

6. Working of the Project
Step-by-Step Flow

Video Capture:
The webcam captures frames continuously using cv2.VideoCapture(0).

Hand Detection:
The custom handModule (based on MediaPipe) identifies hand landmarks such as wrist, thumb, middle, ring, and pinky fingers.

Landmark Extraction:

Thumb tip (id=4)

Middle finger tip (id=12)

Ring finger tip (id=16)

Pinky finger tip (id=20)

Wrist (id=0)

Gesture Recognition & Distance Calculation:

Distance between thumb and middle finger determines volume level.

Distance between wrist and ring finger or ring and pinky finger is used to set control conditions (flag).

Volume Mapping:

The calculated distance is interpolated (np.interp) between min distance → min volume and max distance → max volume.

The mapped value is passed to volume.SetMasterVolumeLevel() from PyCaw.

Visualization:

A volume bar is displayed on the video frame.

Landmarks and connecting lines are drawn to guide the user.

FPS and current volume percentage are displayed.

Exit Condition:
Pressing the ESC key (key==27) stops the program.

7. Key Features in Code

Real-Time Hand Tracking: Achieved using MediaPipe with OpenCV integration.

Volume Control Logic: Distance → mapped volume using interpolation.

Flag Mechanism: Prevents unwanted volume changes when specific conditions are met.

Visualization: Shows FPS, volume percentage, and a graphical volume bar.

8. Sample Output

When running the program:

A camera feed window appears.

The hand is detected and landmarks are marked.

Moving the thumb closer/farther to the middle finger changes the system volume.

A green rectangle bar updates in real-time to show volume level.

Display includes:

FPS: Frames per second

Volume %

9. Applications

Touchless volume control system for laptops and PCs.

Useful in gesture-based Human-Computer Interaction (HCI).

Can be extended to control brightness, media players, or presentations.

Beneficial for situations where physical contact is undesirable (e.g., during cooking, medical settings).

10. Advantages

Hands-free control of volume.

User-friendly and intuitive interface.

Works in real-time with low latency.

Demonstrates integration of computer vision with system-level APIs.

11. Limitations

Requires a good webcam and proper lighting.

Works only on Windows OS (due to Pycaw).

May not perform well if multiple hands are in the frame.

Gesture recognition limited to specific finger movements.

12. Future Enhancements

Extend to support multi-gesture controls (pause/play music, skip track, mute).

Develop a cross-platform solution for Linux and macOS.

Add machine learning models to classify gestures more robustly.

Create a GUI interface with customizable gesture settings.

Implement support for multiple users/hands.

13. Conclusion

The Hand Gesture Controlled Volume System successfully demonstrates how computer vision and audio control APIs can be combined to build an interactive application. This project provides a practical and innovative solution for contactless media control, opening doors to advanced gesture-based HCI systems.
