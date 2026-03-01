# 😴 DrowsyGuard — Real-Time Driver Drowsiness Detection System

> An AI-powered real-time drowsiness detection system that monitors eye and facial movements to alert drivers before fatigue-related accidents occur.

![Python](https://img.shields.io/badge/Python-3.8+-3776AB?logo=python&logoColor=white)
![OpenCV](https://img.shields.io/badge/OpenCV-4.x-5C3EE8?logo=opencv&logoColor=white)
![Dlib](https://img.shields.io/badge/Dlib-Face_Detection-008000)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-FF6F00?logo=tensorflow&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-Scientific_Computing-013243?logo=numpy&logoColor=white)

---

## 📌 About the Project

DrowsyGuard is a real-time computer vision-based drowsiness detection system that uses a webcam to continuously monitor a driver's eye activity and facial landmarks. When signs of drowsiness are detected — such as prolonged eye closure or head nodding — the system immediately triggers an audio-visual alert to wake the driver and prevent potential accidents.

Road accidents caused by driver fatigue are a major global concern. This system provides a low-cost, software-based solution that can be deployed on any device with a camera, making it practical for everyday use.

---

## ✨ Features

- 🎥 **Real-Time Face Detection** — Detects the driver's face using a webcam feed
- 👁️ **Eye Aspect Ratio (EAR) Monitoring** — Measures eye openness to detect blinking and closure
- 😪 **Drowsiness Alert** — Triggers a loud alarm when eyes remain closed beyond a threshold
- 🔔 **Head Pose Detection** — Detects head nodding or tilting as a sign of drowsiness
- 📊 **Live EAR Graph** — Displays real-time eye aspect ratio on screen
- 💾 **Log System** — Records drowsiness events with timestamps
- 🌙 **Low-Light Support** — Works in dim lighting conditions
- ⚡ **Lightweight & Fast** — Optimized for real-time performance on standard hardware

---

## 🧠 How It Works

The system uses the **Eye Aspect Ratio (EAR)** algorithm to determine whether eyes are open or closed:

```
EAR = (||p2 - p6|| + ||p3 - p5||) / (2 * ||p1 - p4||)
```

Where `p1` to `p6` are the six facial landmark points around each eye.

- When the **EAR drops below a threshold** (default: 0.25) for a consecutive number of frames (default: 20), drowsiness is detected and an alarm is triggered.
- **Dlib's 68-point facial landmark detector** is used to map the face and isolate eye regions accurately.

---

## 🛠️ Tech Stack

| Component | Technology |
|-----------|-----------|
| Language | Python 3.8+ |
| Computer Vision | OpenCV |
| Face & Landmark Detection | Dlib |
| Deep Learning (optional) | TensorFlow / Keras |
| Numerical Computing | NumPy, SciPy |
| Alert System | Pygame (audio alarm) |
| Visualization | Matplotlib, Imutils |

---

## 📁 Project Structure

```
drowsy-guard/
├── model/
│   └── shape_predictor_68_face_landmarks.dat  # Dlib pretrained model
├── alarm/
│   └── alert.wav                              # Alarm sound file
├── logs/
│   └── drowsiness_log.txt                     # Event logs
├── screenshots/
│   └── demo.png                               # Demo screenshots
├── detect_drowsiness.py                       # Main detection script
├── eye_aspect_ratio.py                        # EAR calculation module
├── head_pose.py                               # Head pose estimation
├── alert.py                                   # Alarm trigger module
├── requirements.txt                           # Python dependencies
└── README.md
```

---

## ⚙️ Getting Started

### Prerequisites
- Python 3.8 or higher
- Webcam (built-in or external)
- pip

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/drowsy-guard.git
   cd drowsy-guard
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Download the Dlib landmark model**

   Download `shape_predictor_68_face_landmarks.dat` from the [Dlib model repository](http://dlib.net/files/shape_predictor_68_face_landmarks.dat.bz2) and place it inside the `model/` folder.

4. **Run the detection system**
   ```bash
   python detect_drowsiness.py
   ```

---

## 📦 Requirements

```txt
opencv-python
dlib
imutils
numpy
scipy
pygame
matplotlib
tensorflow
keras
```

Install all at once:
```bash
pip install -r requirements.txt
```

---

## 🎛️ Configuration

You can adjust detection sensitivity in `detect_drowsiness.py`:

```python
# Eye Aspect Ratio threshold — lower = more sensitive
EAR_THRESHOLD = 0.25

# Number of consecutive frames eyes must be closed to trigger alarm
EAR_CONSEC_FRAMES = 20

# Alarm sound file path
ALARM_PATH = "alarm/alert.wav"
```

---

## 📸 Screenshots

| Real-Time Detection | Drowsiness Alert |
|---|---|
| ![Detection](screenshots/detection.png) | ![Alert](screenshots/alert.png) |

> Add your screenshots to the `/screenshots` folder.

---

## 📊 Detection Logic Flow

```
Start Webcam
     ↓
Capture Frame
     ↓
Detect Face (Dlib)
     ↓
Extract 68 Facial Landmarks
     ↓
Calculate EAR for Both Eyes
     ↓
EAR < Threshold for N Frames?
     ↓              ↓
    YES             NO
     ↓              ↓
Trigger Alarm   Continue Monitoring
     ↓
Log Drowsiness Event
```

---

## 🔮 Future Enhancements

- [ ] Yawning detection using Mouth Aspect Ratio (MAR)
- [ ] SMS/push notification alerts to emergency contacts
- [ ] Mobile app integration
- [ ] Deep learning CNN model for higher accuracy
- [ ] Dashboard for fleet monitoring (multiple drivers)
- [ ] Night vision / infrared camera support
- [ ] Speed/GPS integration for smart alerting

---

## ⚠️ Limitations

- Requires good frontal face visibility for accurate detection
- Performance may vary with glasses or heavy facial hair
- Needs adequate lighting for best results
- Currently supports single-driver detection only

---

## 📚 References

1. Soukupová & Čech — *Real-Time Eye Blink Detection Using Facial Landmarks*, 2016
2. Dlib C++ Library — [dlib.net](http://dlib.net)
3. OpenCV Documentation — [docs.opencv.org](https://docs.opencv.org)
4. T. Senthilkumar et al. — *Driver Drowsiness Detection Using Eye Blink Monitoring*, IEEE 2022
5. WHO Global Road Safety Report, 2023

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

<p align="center">Made with ❤️ for road safety — Stay Alert, Stay Safe 🚗</p>
