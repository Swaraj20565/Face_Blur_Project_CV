# 🎭 OpenCV Face Blur Detection

A beginner-friendly **Computer Vision** project built with **Python** and **OpenCV** that detects human faces in real time using a webcam and automatically blurs each detected face.

---

## 📌 Features

* 📷 Real-time webcam capture
* 😀 Face detection using Haar Cascade Classifier
* 🌫️ Automatic face blurring with Gaussian Blur
* 🟩 Draws a bounding box around detected faces
* ⚡ Runs in real time
* ❌ Press **Q** to exit

---

## 🛠️ Technologies Used

* Python 3.x
* OpenCV (`cv2`)
* Haar Cascade Classifier

---

## 📂 Project Structure

```text
Face_Blur_OpenCV/
│
├── main.py
├── README.md
└── requirements.txt
```

---

## 🚀 Installation

### 1. Clone the repository

```bash
git clone https://github.com/your-username/Face_Blur_OpenCV.git
```

### 2. Move into the project folder

```bash
cd Face_Blur_OpenCV
```

### 3. Create a virtual environment (Optional)

```bash
python -m venv venv
```

Activate it:

**Windows**

```bash
venv\Scripts\activate
```

**Mac/Linux**

```bash
source venv/bin/activate
```

### 4. Install dependencies

```bash
pip install -r requirements.txt
```

---

## ▶️ Run the Project

```bash
python main.py
```

The webcam will open automatically.

Press **Q** to close the application.

---

## 📷 How It Works

```text
Webcam
   │
   ▼
Capture Frame
   │
   ▼
Convert BGR → Grayscale
   │
   ▼
Haar Cascade Face Detection
   │
   ▼
Detect Face Coordinates
   │
   ▼
Extract Face ROI
   │
   ▼
Apply Gaussian Blur
   │
   ▼
Replace Original Face
   │
   ▼
Draw Bounding Box
   │
   ▼
Display Live Video
```

---

## 🧠 Face Detection Pipeline

```text
Webcam
   │
   ▼
Read Frame
   │
   ▼
Convert to Grayscale
   │
   ▼
Haar Cascade Classifier
   │
   ▼
Detect Faces
   │
   ▼
For Each Face
   │
   ├── Crop Face Region
   │
   ├── Apply Gaussian Blur
   │
   ├── Replace Original Face
   │
   └── Draw Rectangle
   │
   ▼
Display Result
```

---

## 📖 Code Explanation

### 1. Open Webcam

```python
cap = cv2.VideoCapture(0)
```

Opens the default webcam connected to the computer.

---

### 2. Read Frame

```python
ret, frame = cap.read()
```

Captures one frame from the webcam.

* **ret** → `True` if the frame is captured successfully.
* **frame** → The captured image.

---

### 3. Convert to Grayscale

```python
gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)
```

The Haar Cascade algorithm works on grayscale images because color information is unnecessary for face detection.

Benefits:

* Faster processing
* Lower memory usage
* Better detection performance

---

### 4. Load Haar Cascade

```python
face_cascade = cv2.CascadeClassifier(
    cv2.data.haarcascades +
    "haarcascade_frontalface_default.xml"
)
```

Loads OpenCV's pre-trained face detection model.

---

### 5. Detect Faces

```python
faces = face_cascade.detectMultiScale(
    gray,
    scaleFactor=1.1,
    minNeighbors=5,
    minSize=(30,30)
)
```

**Parameters**

| Parameter      | Description                            |
| -------------- | -------------------------------------- |
| `scaleFactor`  | Image scaling between detection passes |
| `minNeighbors` | Removes false detections               |
| `minSize`      | Minimum detectable face size           |

---

### 6. Blur Face

```python
blurred_face = cv2.GaussianBlur(face, (99,99), 30)
```

Applies Gaussian Blur to hide facial details.

---

### 7. Replace Original Face

```python
frame[y:y+h, x:x+w] = blurred_face
```

Copies the blurred face back into the original frame.

---

### 8. Draw Rectangle

```python
cv2.rectangle(
    frame,
    (x,y),
    (x+w,y+h),
    (0,255,0),
    2
)
```

Draws a green bounding box around each detected face.

---

### 9. Display Video

```python
cv2.imshow("Face Blur", frame)
```

Shows the processed video in real time.

---

### 10. Exit Program

```python
if cv2.waitKey(1) & 0xFF == ord('q'):
    break
```

Press **Q** to quit.

---

## 📦 Requirements

Create a file named **requirements.txt**

```text
opencv-python
```

Install:

```bash
pip install -r requirements.txt
```

---

## 🎯 Applications

* Privacy protection
* Live video anonymization
* CCTV systems
* Video conferencing
* Public surveillance
* Educational Computer Vision projects

---

## 📚 Concepts Covered

* OpenCV
* Computer Vision
* Webcam Capture
* Image Processing
* Grayscale Conversion
* Haar Cascade Classifier
* Face Detection
* Gaussian Blur
* Region of Interest (ROI)
* Bounding Box Detection

---

## 📜 License

This project is open-source and available under the MIT License.

---

## 👨‍💻 Author

**Swaraj Bhumare**

If you found this project helpful, consider giving the repository a ⭐ on GitHub.
