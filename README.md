# README

## Face Mesh Detection using MediaPipe

This project utilizes the MediaPipe library to detect and draw face mesh landmarks on real-time video feed from a webcam. It demonstrates the application of machine learning techniques to detect facial landmarks and overlay them on the video.

### Requirements:
- Python 3.6 or higher
- OpenCV library
- MediaPipe library


### Code Overview

The core functionality is implemented in the `face_mesh_detection.py` script:

- **Import Libraries**: The script imports the necessary libraries (`cv2` for OpenCV and `mediapipe` for MediaPipe).
- **Drawing Specifications**: Custom drawing specifications are set for the face mesh contours.
- **Video Capture**: The script captures video from the default webcam.
- **Face Mesh Detection**: The `mp_face_mesh.FaceMesh` object is used to detect face mesh landmarks.
- **Drawing Landmarks**: The detected landmarks are drawn on the video frame using the specified styles.
- **Display Video**: The processed video frame is displayed in a window. Press 'q' to exit.

### Key Components

- **Drawing Specifications**:
  ```python
  my_drawing_specs = mp_drawing.DrawingSpec(color=(0, 255, 0), thickness=1)
  ```
  This sets the drawing color to green and the thickness to 1 pixel.

- **Face Mesh Initialization**:
  ```python
  with mp_face_mesh.FaceMesh(
      max_num_faces=2,
      refine_landmarks=True,
      min_detection_confidence=0.5,
      min_tracking_confidence=0.5
  ) as face_mesh:
  ```
  This initializes the FaceMesh object to detect up to 2 faces with a minimum detection and tracking confidence of 0.5.

- **Drawing Landmarks**:
  ```python
  mp_drawing.draw_landmarks(
      image=image,
      landmark_list=face_landmarks,
      connections=mp_face_mesh.FACEMESH_TESSELATION,
      landmark_drawing_spec=None,
      connection_drawing_spec=mp_drawing_styles.get_default_face_mesh_tesselation_style()
  )
  ```
  This draws the face mesh tesselation landmarks on the image using default styles.
