# train_video_processing

📋 Project Overview
A comprehensive video processing system that automatically analyzes train videos to detect individual coaches, identify door status (open/closed), classify coach types (engines/wagons), and generate detailed reports with annotated videos.

🎯 Key Features
Coach Detection: Automatically detects and segments individual train coaches from video

Door Status Analysis: Identifies whether doors are open or closed for each coach

Coach Classification: Classifies coaches as front engine, rear engine, or wagons

Video Processing: Creates individual video clips for each coach

Comprehensive Reporting: Generates PDF reports, JSON data, and CSV event logs

Annotated Videos: Produces videos with visual annotations showing coach information and door status



Create a virtual environment (recommended):

bash
python -m venv train_analysis
source train_analysis/bin/activate  # Linux/Mac
train_analysis\Scripts\activate    # Windows
Install dependencies:

bash
pip install -r requirements.txt
💻 Usage
Basic Command
bash
python main.py input_videos/your_video.mp4 --output_dir output
Advanced Options
bash
# Disable overall annotated video creation (faster processing)
python main.py input_videos/your_video.mp4 --output_dir output --no_overall

# Custom output directory
python main.py input_videos/your_video.mp4 --output_dir my_results
📊 Output Structure
After processing, the system creates:

1. Coach Detection
Samples frames at regular intervals (0.3 seconds)

Analyzes frame differences to detect coach boundaries

Uses Gaussian smoothing and dynamic thresholding

Falls back to uniform splitting if automatic detection fails

2. Door Status Analysis
Monitors specific regions of each coach for door activity

Uses edge detection and motion analysis

Tracks door open/close events throughout the video

Provides per-frame door status information

3. Coach Classification
Front Engine: First detected coach

Rear Engine: Last detected coach

Wagons: All coaches in between

Simple deterministic assignment based on position

4. Video Processing
Extracts individual coach segments as separate video files

Creates annotated versions with door status overlays

Generates a complete annotated video of the entire train

📈 Output Metrics
The system provides:

Coach Count: Total number of coaches detected

Engine Identification: Front and rear engine designations

Door Statistics: Open/closed status and event counts

Color Consistency: Verification that frames belong to the same coach

Temporal Analysis: Duration and frame ranges for each coach

⚙️ Configuration
Key parameters can be adjusted in respective files:

Coach Detection (coach_detector.py)

🐛 Troubleshooting
Common Issues
"Module not found" errors

Ensure all dependencies are installed: pip install -r requirements.txt

Video processing fails

Check video file path and format

Verify sufficient disk space for output files

Poor coach detection

Adjust sample_seconds in coach_detector.py

Modify min_duration and max_duration parameters

Memory issues with large videos

Use --no_overall flag to skip full annotated video

Process shorter video segments

📋 Requirements
Python 3.7+

OpenCV 4.9+

NumPy, SciPy, scikit-learn

ReportLab for PDF generation

4GB+ RAM recommended for large videos

🎯 Expected Input
Video files showing train from side view

Stable camera position

Clear view of train coaches

Recommended: 1080p resolution, 25-30 fps

📞 Support
For issues or questions:

Check the troubleshooting section above

Verify all dependencies are installed correctly

Ensure input video meets recommended specifications

📄 License
This project is designed for educational and research purposes in video processing and computer vision applications.

