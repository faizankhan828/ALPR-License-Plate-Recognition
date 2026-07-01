# ALPR — Automatic License Plate Recognition

Automatic License Plate Recognition system that detects, reads, and logs vehicle license plates from traffic footage using **YOLOv8** for detection and **EasyOCR** for text recognition.

Built by fine-tuning YOLOv8 on a self-built dataset collected from real traffic footage, so it holds up across varied lighting conditions and camera angles — not just clean, front-facing plate images.

## Overview

The pipeline takes a video (or image) of traffic, detects vehicles and their license plates, runs OCR to extract the plate number, and logs every detection with a timestamp. It also produces a frequency report summarizing how often each plate appears, which is useful for things like parking analytics, toll systems, or gate access logs.

## Features

- 🚗 **License plate detection** with a YOLOv8 model fine-tuned on real traffic footage
- 🔤 **OCR text extraction** using EasyOCR to read plate numbers from detected regions
- 🎥 **Video processing pipeline** that handles varied lighting, angles, and motion blur
- 🗒️ **Timestamped detection logs** (`detections_log.csv`) recording every plate read and when it occurred
- 📊 **Summary/frequency reports** (`summary_report.csv`) aggregating detections per plate
- 🗂️ **Reference database matching** (`car_database.csv`) to cross-check detected plates against known records
- ▶️ **Annotated output video** (`license_plate_final_output.mp4`) with bounding boxes and recognized plate text overlaid

## Tech Stack

| Component | Tool |
|---|---|
| Object Detection | YOLOv8 (Ultralytics) |
| OCR | EasyOCR |
| Image/Video Processing | OpenCV |
| Data Handling & Reporting | Pandas |
| Development Environment | Jupyter Notebook |

## Project Structure

```
ALPR-License-Plate-Recognition/
├── License_Plate_Detection_using_YOLO.ipynb   # Main notebook — training/inference pipeline
├── car_database.csv                            # Reference vehicle/plate records
├── detections_log.csv                          # Timestamped log of every detected plate
├── summary_report.csv                          # Aggregated detection frequency per plate
├── license_plate_final_output.mp4              # Sample annotated output video
├── Test.png                                    # Sample test image
└── README.md
```

## How It Works

1. **Input** — A traffic video or image is fed into the pipeline.
2. **Detection** — The fine-tuned YOLOv8 model locates vehicles and their license plates in each frame.
3. **OCR** — EasyOCR reads the text from each detected plate region.
4. **Logging** — Every successful read is timestamped and appended to `detections_log.csv`.
5. **Matching** — Detected plates are optionally cross-referenced against `car_database.csv`.
6. **Reporting** — `summary_report.csv` aggregates how frequently each plate was seen across the footage.
7. **Output** — An annotated video (`license_plate_final_output.mp4`) is generated with bounding boxes and recognized text drawn on each frame.

## Getting Started

### Prerequisites

```bash
pip install ultralytics easyocr opencv-python pandas
```

### Running the notebook

1. Clone the repository:
   ```bash
   git clone https://github.com/faizankhan828/ALPR-License-Plate-Recognition.git
   cd ALPR-License-Plate-Recognition
   ```
2. Open `License_Plate_Detection_using_YOLO.ipynb` in Jupyter Notebook or JupyterLab.
3. Run the cells in order to load the model, process a video/image, and generate the logs and annotated output.

## Sample Output

- `Test.png` — example of a single-frame plate detection
- `license_plate_final_output.mp4` — full video with detection boxes and OCR text overlaid
- `detections_log.csv` / `summary_report.csv` — structured outputs ready for further analysis

## Future Improvements

- Real-time inference from a live camera stream
- Support for multiple plate formats/regions
- Web dashboard for browsing detection logs and reports
- Improved OCR accuracy for low-light and motion-blurred frames

## Author

**Faizan Khan**
AI-Focused Full-Stack Developer | Python, Django & MERN Stack
- GitHub: [@faizankhan828](https://github.com/faizankhan828)
- LinkedIn: [Faizan Khan](https://www.linkedin.com/in/faizan-khan-a40566263/)
- Portfolio: [faizankhan-zeta.vercel.app](https://faizankhan-zeta.vercel.app/)
