# 🚦 Vehicle Detection & Traffic Light Violation System  

This project detects vehicles in a video stream and automatically flags **red light violations** using a YOLO-based object detection model. It processes traffic footage, identifies vehicles crossing the stop line during a red light, and saves cropped images of violating vehicles. It also provides a visual flash alert in the annotated video output. NOTE: This project is a prototype and only includes a sample video footage, however, real-time video can be sourced and used as the input to the existing project.

## 📌 Features  
- **Real-time Vehicle Detection** using a trained YOLO model (`best.pt`)  
- **Red Light Violation Detection** based on predefined signal timing  
- **Flashing Alert** for vehicles violating the stop line during red light  
- **Automatic Cropping & Saving** of violating vehicles’ images  
- **Annotated Output Video** showing bounding boxes, traffic light status, and violation count  
- **Customizable Parameters** for adapting to real-world conditions  

## 🖼 Demo  
<img width="2508" height="1408" alt="image" src="https://github.com/user-attachments/assets/e2d12011-5059-4b62-a0c7-06b46db4101f" />

---

## 📂 Project Structure  
Vehicle-Detection-Project/
- ├── 📄 main.py                    # Main script (vehicle detection + violation logging)
- ├── 🎯 best.pt                    # YOLO trained weights  
- ├── 🎥 Traffic_video.mp4          # Input video for detection
- ├── 📄 Vehicle_Detection_Training.ipynb # Used for training the Roboflow model (optional)
- └── 📖 README.md                  # Project documentation

## Project Resources
- Model weights (`best.pt`) can be found at this [link](https://drive.google.com/file/d/1SjlH2T2-ndS5bDOFWX0EKwBPKsZ4gQF4/view?usp=sharing)
- `Traffic_video.mp4` can be found at this [link](https://drive.google.com/file/d/1Rd8oyeFyGN_S16AcO2uWVTZDjwnhx-bM/view?usp=sharing)

## 🤖 Model & Training Reference

The YOLO model (`best.pt`) used in this project was trained using a dataset and preprocessing pipeline from **Roboflow**, originally created and shared by another contributor.  

**Original Roboflow Project:** [Vehicle Object Detection Model](https://universe.roboflow.com/vehicle-object-detection-oyglk/vehicle_detection-rdah2-wvwbb)  

All credit for the dataset and preprocessing configuration goes to the original creator. This repository only covers the detection, logging, and visualization implementation.



## ⚙️ Installation and Setup
1. **Clone this repository**
```bash
git clone https://github.com/Apurba-01/Traffic-Light-Violation-Detection.git
```
2. **Install Dependencies**
```bash
pip install ultralytics opencv-python numpy
```
3. Add the YOLO model weights
   Place your trained YOLO weights file (`best.pt`) in the project folder.
4. Add your video
   Replace `Video_final_4.mp4` with your own traffic video or rename accordingly.

---

## 🚀 Usage
Run the detection script:
```bash
python main.py
```
Press **Q** anytime to exit

## 🛠 Customization
**Change red light timing**
In `main.py`, modify the `is_red_light()` function:
```python
def is_red_light():
    current_pos_seconds = cap.get(cv.CAP_PROP_POS_MSEC) / 1000.0
    return current_pos_seconds > 12  # Change threshold for your video
```
Adjust frame skipping,
```python
frame_skip = 5  # Lower = smoother but slower
```
Modify stop line position:
```python
line_y = 310  # Change based on your camera angle
```
## 📊 Output
- `violations/` → Cropped images of violating vehicles
- `Annotated_Video.mp4` → Video with annotations and alerts
- Terminal logs → Shows when violations are detected

## 🖥 Requirements
- Python 3.8+
- Ultralytics YOLO
- OpenCV
- NumPy

## 📜 License
This project is for educational purposes only. For real-world deployment, follow all local traffic monitoring laws.
