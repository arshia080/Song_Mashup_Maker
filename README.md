# Song_Mashup_Maker

**Song_Mashup_Maker** is a Python-based application that automatically generates a music mashup using YouTube videos of a selected singer.

The project can be used in two different ways:

- **Part 1 – Command Line Version (CLI)**
- **Part 2 – Web Application (Streamlit Interface)**

The system fetches videos from YouTube, extracts audio, trims clips to a specified duration, combines them into a single mashup track, and (in the web version) compresses and emails the final output.


## Project Structure
Song-Mashup-Maker/
│
├── part1-cli/
│ └── 102303918.py # Command Line Mashup Script
│
├── part2-webservice/
│ └── app.py # Streamlit-Based Web Application
│
├── requirements.txt # Required Python Packages
├── test.mp3 # Sample Output File
└── README.md

## Main Features

- Download YouTube videos in MP4 format  
- Convert video files into MP3 audio  
- Extract the first *N* seconds from each track  
- Merge multiple trimmed audio clips into one mashup  
- Compress mashup into a ZIP file (Web Version)  
- Send mashup via email (Web Version)  
- Automatically remove temporary files after completion  


# Part 1 – Command Line Interface (CLI)

This version runs directly from the terminal using command-line arguments.

### Command Format

```bash
python part1-cli/102303918.py "Singer Name" <NumberOfVideos> <ClipDurationSeconds> <OutputFileName>
```

### Example
```bash
python part1-cli/102303918.py "Arijit Singh" 12 30 mashup.mp3
```

# Part 2 – Web Application (Streamlit)

The web version provides a simple graphical interface to generate mashups easily.

```bash
pip install -r requirements.txt
streamlit run part2-webservice/app.py
```

# Installation Guide

Install all required libraries using:
```bash
pip install -r requirements.txt
```

# System Requirement

FFmpeg must be installed and properly configured in your system PATH.

To verify:
```bash
ffmpeg -version
```

# Temporary File Cleanup

To ensure the project directory remains clean, a cleanup() function removes all intermediate folders and generated files.
```bash
def cleanup():
    folders = ["downloads", "mp3", "trimmed"]
    files = ["mashup.zip", "mashup.mp3"]

    for f in folders:
        if os.path.exists(f):
            shutil.rmtree(f)

    for file in files:
        if os.path.exists(file):
            os.remove(file)
```

# What It Does
- Deletes downloaded video files
- Removes converted and trimmed audio folders
- Deletes the generated mashup and ZIP file
- Prevents storage clutter after every run
