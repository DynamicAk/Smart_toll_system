# Smart Toll Management System

## Problem I wanted to solve

Even with FASTag, toll plazas can face long queues, payment verification issues and limited visibility into traffic congestion. I wanted to explore how GPS-based tolling, computer vision and machine learning could help automate vehicle identification and improve toll management.

## About the project

I started working on this problem during my research internship at NIT Kurukshetra. The initial prototype combines a GPS distance calculator, a web-based toll interface and automatic number plate recognition using YOLOv8.

I have also included our later academic research on AI-based smart toll management, combining license plate detection, OCR, simulated FASTag transactions and lane-wise congestion prediction. The later research is documented in the paper and is separate from the original executable prototype.

## Key features

- GPS distance calculation using the Haversine formula and a Google Maps embed.
- Number plate detection from video using YOLOv8.
- Plate text extraction using Tesseract OCR, duplicate filtering and timestamp logging.
- Web pages for toll services, rates and GPS distance calculation.
- PHP and SQL components for the original toll-system prototype.

## Research extension

In our later work, we evaluated YOLOv8n and YOLOv8s, explored EasyOCR for plate recognition, simulated FASTag wallet transactions using SQLite, and studied lane-wise congestion prediction using Random Forest and synthetic ANPR logs. The paper describes a unified Streamlit dashboard.

The paper reports a YOLOv8n mAP@50 of 0.9757 and congestion classification accuracy of 86.45% on synthetic data. These are reported research results, not verified production performance.

## Technology stack

| Component | Technology |
| --- | --- |
| Computer vision | Python, YOLOv8, OpenCV, cvzone |
| Original OCR | Tesseract, pytesseract |
| Web prototype | HTML, CSS, JavaScript, PHP, SQL |
| GPS | Google Maps embed, Haversine formula |
| Later research | EasyOCR, SQLite, Random Forest, Streamlit |

## Project structure

- `carnumberplate-main/` — detection scripts, trained weights, sample videos, logs and training notebook.
- `carnumberplate-main/main1.py` — video-based plate detection and OCR.
- `ts/` — toll web interface and PHP/SQL components.
- `ts/GPS_Distance.html` — GPS distance calculator.
- `ts/tollsystem.sql` — database script.
- `images/` — project images.
- `paper_latex.tex` — later research paper source.
- [Internship report](internship%20report.pdf) — internship documentation.
- [Major project paper](major_project_paper.pdf) — later research documentation.

## How to run locally

```bash
git clone https://github.com/DynamicAk/Smart_toll_system.git
cd Smart_toll_system
```

### Number plate detection

The original notes recommend Python 3.8. Use an isolated environment with compatible dependency versions.

```bash
cd carnumberplate-main
pip install opencv-python ultralytics cvzone pandas numpy pytesseract
python main1.py
```

Install Tesseract separately and update its executable path in `main1.py` for your system. Run from the detection directory so the script can find the included model and video. Press Esc to close the video window.

### Web prototype

Open `ts/GPS_Distance.html` in a browser to explore the distance calculator. For the PHP pages, configure a local PHP and MySQL environment, import `ts/tollsystem.sql`, and review the database configuration before running the application.

## Current scope

This is an academic and research prototype, not a live toll payment system. The GPS calculation estimates distance between points rather than actual road distance. The later research uses simulated transactions and synthetic congestion data. I have kept the original implementation and research documents together for reference.
