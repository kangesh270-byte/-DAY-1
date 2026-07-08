# AI-Based Hand Gesture Controlled Smart Home Automation Using Python and Arduino

## Project Title
AI-Based Hand Gesture Controlled Smart Home Automation Using Python and Arduino

## Project Overview
1. Webcam captures the user's hand in real time.
2. Python (OpenCV + MediaPipe) recognizes hand gestures.
3. Commands are sent to Arduino/ESP32 through Serial/Wi-Fi.
4. Arduino controls appliances through a relay module.

## Objective
- Touch-free home automation
- Real-time gesture recognition
- Arduino-based appliance control
- Integration of AI, Computer Vision and IoT

## Components

### Hardware
- Laptop/Desktop with Webcam
- Arduino Uno or ESP32
- Relay Module
- LED/Bulb
- Breadboard
- Jumper Wires
- USB Cable

### Software
- Python 3.x
- VS Code
- Arduino IDE
- OpenCV
- MediaPipe
- NumPy
- PySerial

## Install Libraries
```bash
pip install opencv-python
pip install mediapipe
pip install numpy
pip install pyserial
```

## Architecture
```text
-----------------------------
User
 │
 ▼
Webcam
 │
 ▼
Python
 │
 ▼
OpenCV
 │
 ▼
MediaPipe
 │
 ▼
Gesture Detection
 │
 ▼
Serial Communication
 │
 ▼
Arduino
 │
 ▼
Relay Module
 │
 ▼
Light / Fan
```
---------------------------
## Working Procedure
1. Open webcam.
2. Capture live frames.
3. Convert to RGB.
4. Detect hand using MediaPipe.
5. Extract 21 landmarks.
6. Identify gesture.
7. Send command to Arduino.
8. Arduino controls relay.
9. Appliance turns ON/OFF.

## Flowchart
```text
START
 │
 ▼
Open Webcam
 │
 ▼
Capture Frame
 │
 ▼
Detect Hand
 │
 ▼
Extract Landmarks
 │
 ▼
Identify Gesture
 │
 ▼
Send Command
 │
 ▼
Arduino
 │
 ▼
Relay
 │
 ▼
Device ON/OFF
```

## Hand Landmarks
- Wrist: 0
- Thumb Tip: 4
- Index Tip: 8
- Middle Tip: 12
- Ring Tip: 16
- Little Tip: 20

## Gesture Mapping
- 👍 -> Light ON
- ✋ -> Light OFF
- ☝️ -> Fan ON
- ✌️ -> Fan OFF
- 🖐 -> All OFF

## Sample Python Code
```python
import cv2
import mediapipe as mp

cap = cv2.VideoCapture(0)
hands = mp.solutions.hands.Hands()
draw = mp.solutions.drawing_utils

while True:
    ret, frame = cap.read()
    rgb = cv2.cvtColor(frame, cv2.COLOR_BGR2RGB)
    result = hands.process(rgb)

    if result.multi_hand_landmarks:
        for hand in result.multi_hand_landmarks:
            draw.draw_landmarks(frame, hand, mp.solutions.hands.HAND_CONNECTIONS)

    cv2.imshow("Hand Gesture", frame)

    if cv2.waitKey(1) & 0xFF == ord('q'):
        break

cap.release()
cv2.destroyAllWindows()
```

## Advantages
- Touch-free
- Low cost
- Real-time
- Easy to implement

## Applications
- Smart Home
- Smart Classroom
- Smart Office
- Hospitals
- Robotics

## Future Scope
- ESP32 Wi-Fi
- Voice + Gesture
- Mobile App
- Cloud Dashboard
- Face Recognition
