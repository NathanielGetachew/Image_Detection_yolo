# YOLO Wind Farm Detection

## Overview

This project uses **YOLOv8** for object detection on images of wind farms. The model detects and identifies wind turbines in aerial or landscape images.

## Dataset

The dataset is structured as follows:

```
datasets/
  wind_farms/
    train/
      images/
      labels/
    valid/
      images/
      labels/
    test/
      images/
      labels/
```

The dataset was preprocessed and converted to **YOLO format** for training.

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/YOLO_WindFarm_Detection.git
cd YOLO_WindFarm_Detection
```

### 2. Install Dependencies

Create a virtual environment and install the required libraries:

```bash
python -m venv venv
source venv/bin/activate  # On Windows use: venv\Scripts\activate
pip install ultralytics opencv-python matplotlib
```

## Training the YOLO Model

To train YOLO on the dataset:

```bash
yolo task=detect mode=train model=yolov8s.pt data=path/to/dataset.yaml epochs=50 imgsz=640
```

This trains a YOLOv8 model for **50 epochs** with an image size of **640x640**.

## Running Inference

To run object detection on images from the validation dataset:

```bash
yolo task=detect mode=predict model=runs/detect/train4/weights/best.pt source="datasets/wind_farms/valid/images"
```

To test on a single image:

```bash
yolo task=detect mode=predict model=runs/detect/train4/weights/best.pt source="datasets/wind_farms/valid/images/windmill9_jpg.rf.a5c71316068bd0b4a0cd3ed5d90ff4a3.jpg"
```

## Results

After inference, results are saved in:

```
runs/detect/predict/
```

You can visualize the detections using:

```python
import cv2
import matplotlib.pyplot as plt

img = cv2.imread("runs/detect/predict/windmill9_jpg.rf.a5c71316068bd0b4a0cd3ed5d90ff4a3.jpg")
img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
plt.imshow(img)
plt.axis("off")
plt.show()
```

## Future Improvements

- Fine-tuning YOLO with more images
- Improving detection accuracy
- Deploying as a web app using Flask or FastAPI

## License

This project is open-source and available under the MIT License.

---

### 🚀 **Contributions Welcome!**

Feel free to open issues or pull requests to improve the model or add new features.

