Driver Drowsiness Detector
A real-time system that detects driver drowsiness using a webcam and triggers an alarm.

Computer Vision & AI Concepts Used
Concept	How it's used
Facial Landmark Detection	68-point face mapping to locate eyes
Eye Aspect Ratio (EAR)	Mathematical formula to measure eye openness
Convex Hull	Drawing eye contours on the face
Haar Cascade Classifier	Drawing bounding boxes around faces
Real-time Video Processing	Frame-by-frame webcam analysis
AI Model Used
dlib's 68-point facial landmark predictor - Pre-trained model that detects specific points on the face (eyes, nose, jaw, etc.)

Model file: shape_predictor_68_face_landmarks.dat

How it works
Webcam captures video frames in real-time

dlib model detects 68 landmarks on the face

Eye coordinates are extracted (6 points per eye)

EAR formula calculates how open each eye is: EAR = (||p2-p6|| + ||p3-p5||) / (2 * ||p1-p4||)

If EAR stays below threshold (0.3) for 50+ frames → alarm triggers

Installation
bash
pip install opencv-python dlib imutils scipy numpy pygame
Required Files
shape_predictor_68_face_landmarks.dat - dlib model (download)

haarcascade_frontalface_default.xml - OpenCV face detector

audio/alert.wav - Alarm sound file

Run
bash
python drowsiness_detector.py
Press q to quit.

Adjust Sensitivity
**Note:** 50 frames ≈ 2 seconds at 25-30 FPS (typical webcam speed)
python
EYE_ASPECT_RATIO_THRESHOLD = 0.3    # Lower = needs more closed eyes
EYE_ASPECT_RATIO_CONSEC_FRAMES = 50 # Higher = longer delay

