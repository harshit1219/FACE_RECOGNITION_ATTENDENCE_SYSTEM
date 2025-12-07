# FACE RECOGNITION ATTENDANCE SYSTEM

Short description
A simple facial-recognition based attendance system that detects faces from a camera or video, recognizes known people using precomputed face encodings, and logs attendance to a CSV file. Built with OpenCV, dlib/face_recognition and Python.

Features
- Train/encode faces from a structured dataset.
- Real-time recognition using webcam or video file.
- Attendance logging (CSV) with timestamp.
- Easy dataset structure and scripts to add new users.

Demo / Screenshot
(Replace with your screenshots or GIFs)
![demo](path/to/screenshot.png)

Requirements
- Python 3.8+
- Libraries: opencv-python, face_recognition, dlib, numpy, pandas, pillow
- On Linux/macOS you may need: cmake, build-essential, libboost, etc., for dlib compilation.

Example requirements.txt (include in repo)
```
opencv-python
face_recognition
dlib
numpy
pandas
Pillow
```

Dataset structure
Organize images like:
```
dataset/
  Alice/
    img1.jpg
    img2.jpg
  Bob/
    img1.jpg
    img2.jpg
```

Quick setup (Linux / macOS)
1. Create virtualenv and install dependencies:
```
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```
2. If dlib fails to install, ensure cmake and build tools are present:
- Ubuntu: `sudo apt-get install build-essential cmake libopenblas-dev liblapack-dev`
- macOS: `brew install cmake`

How it works (typical scripts)
- encode_faces.py
  - Scans `dataset/` and computes face encodings -> saves `encodings.pickle`
  - Usage:
    ```
    python encode_faces.py --dataset dataset --encodings encodings.pickle
    ```
- recognize.py
  - Loads `encodings.pickle`, opens webcam/video, recognizes faces and writes attendance.
  - Usage:
    ```
    python recognize.py --encodings encodings.pickle --output attendance.csv
    ```
  - Optional args: `--source webcam|video.mp4`, `--display True|False`

Attendance format
CSV columns example:
```
name,date,time,source
Alice,2025-12-07,09:12:33,webcam
Bob,2025-12-07,09:14:01,webcam
```

Tips & best practices
- Use multiple images per person with different angles/lighting for robust encodings.
- Store encodings securely and re-generate after adding new users.
- For deployment on low-power devices, consider using a smaller model or processing at lower FPS.

Troubleshooting
- False negatives: add more varied images per person.
- dlib install errors: install cmake and system build tools first.
- Camera not found: try different device index (0,1,...) or test with OpenCV sample.

Extending the project
- Integrate with a database (MySQL/Postgres) instead of CSV.
- Add a web dashboard to review and edit attendance.
- Use a face detector model optimized for speed (e.g., MobileNet-SSD) for edge devices.

Contributing
- Fork the repo, make changes, and open a PR.
- Add tests for encoding and recognition pipelines if possible.

License
Specify your license here (e.g., MIT). Example:
MIT License — see LICENSE file.

Acknowledgements
- face_recognition (by Adam Geitgey)
- OpenCV
- dlib

Contact
For questions or help, open an issue or contact: sonkarharshit19@gmail.com
