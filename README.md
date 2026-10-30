# Face Recognition Attendance System

An attendance system that marks students present automatically by recognising their faces through a webcam. It includes a **blink-based liveness check**, so a photo shown to the camera cannot mark attendance, and a **Streamlit dashboard** for reports.

Developed by: Bhoomi bansal, RCEW

## Features

- Real-time face detection and recognition using a webcam
- Blink (eye aspect ratio) liveness check to reject photos and screens
- One attendance per student per day, saved to `attendance.csv` (Name, Date, Time)
- Register new students by uploading a photo or taking one with the camera
- Web dashboard with attendance percentage, daily trend, student-wise report, low-attendance list and CSV download

## How it works

1. **Detect** the face in the camera frame
2. **Encode** the face as 128 numbers (dlib deep-learning model)
3. **Match** it with registered students using Euclidean distance (threshold 0.5)
4. **Blink check** using the eye aspect ratio (EAR) to confirm a live person
5. **Save** name, date and time in a CSV file

## Tech stack

Python 3.11, OpenCV, face_recognition (dlib), NumPy, pandas, Altair, Streamlit

## Project files

| File | Purpose |
|------|---------|
| `app.py` | Home page: Take Attendance, Register Student, Dashboard |
| `attendance_live.py` | Camera window: recognition, blink check, saves attendance |
| `dashboard.py` | Dashboard design and charts |
| `run_dashboard.bat` | Double-click launcher for Windows |

## Setup (Windows)

1. Install Python 3.11 and open a terminal in the project folder.
2. Install the libraries:

```
py -3.11 -m pip install opencv-python numpy pandas pillow altair streamlit "setuptools<81"
py -3.11 -m pip install dlib-bin
py -3.11 -m pip install face_recognition --no-deps
py -3.11 -m pip install face_recognition_models Click
```

3. Create a folder named `known_faces` and add one clear photo per student, named like `Rahul.jpg` (one face per photo, do not end a name with a number).
4. Run the app:

```
py -3.11 -m streamlit run app.py
```

Or double-click `run_dashboard.bat`.

## Usage

- **Take Attendance:** click *Start attendance camera*, look at the camera and blink once. Press `q` to close the window.
- **Register Student:** enter the name, add a photo and save.
- **Dashboard:** view reports and download the data.

## Privacy note

Student photos and attendance records are not included in this repository.

## License

MIT License
