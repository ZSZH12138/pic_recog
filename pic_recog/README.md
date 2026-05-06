# YOLOv8 Recognition Pipeline

This repository contains the cleaned inference pipeline for image recognition.

## What It Detects

The main detector supports these labels:

```text
gun
knife
blood
syringe
pill
powder
swastika
nazi_symbol
poker_card
dice
chip
roulette
slot_machine
middle_finger
crowd
flag
banner
signboard
police
```

An optional pretrained face detector adds:

```text
face
```

## Files

```text
scripts/recognize.py
weights/detector_19class.pt
weights/blood_classifier.pt
weights/face_detector.pt
data/yolo_final_19class/data.yaml
requirements.txt
```

## Install

```powershell
pip install -r requirements.txt
```

The original working environment was:

```powershell
D:\MyAnaconda\envs\pic_recog\python.exe
```

## Run

Single image:

```powershell
python scripts/recognize.py path\to\image.jpg --enable-face
```

Save JSON result:

```powershell
python scripts/recognize.py path\to\image.jpg --enable-face --output outputs\result.json
```

Save annotated image:

```powershell
python scripts/recognize.py path\to\image.jpg --enable-face --save-image outputs\annotated.jpg
```

## Output

The output is JSON. For a single image:

```json
{
  "image": "path/to/image.jpg",
  "elapsed_seconds": 0.08,
  "device": "0",
  "categories": ["gun", "face"],
  "category_counts": {
    "gun": 1,
    "face": 2
  },
  "detections": []
}
```

`categories` is the de-duplicated category list for the image. `detections` keeps box coordinates and confidence scores.
