# Automated-Video-Dubbing-and-Translation-Pipeline
🎬 Automated Video Dubbing & Translation Pipeline


📌 Overview

An AI-powered pipeline that automates video transcription, translation, and dubbing using open-weight models. The project transforms a video into a multilingual version while preserving subtitle timestamps and synchronizing generated speech with the original video.

The entire pipeline is designed to run locally using open-source tools and models, without relying on commercial AI APIs.

🎯 Objectives

Extract audio from YouTube videos.

Transcribe speech and generate accurate, timestamped subtitles.

Translate subtitles into a target language while preserving timestamps.

Generate dubbed speech using Text-to-Speech (TTS).

Synchronize translated audio with the original video.

Mix original and generated audio using audio ducking.

Embed translated subtitles into the final video.

Deploy the pipeline as an interactive web application.

⚙️ Pipeline Architecture

Audio Extraction & Transcription

Video downloading with yt-dlp.

Audio extraction using FFmpeg.

Automatic Speech Recognition (ASR).

Forced alignment for precise timestamps.

Subtitle generation (.srt / .vtt).

Subtitle Translation

Lightweight open-weight LLM (under 2B parameters).

Translation with timestamp preservation.

Prompt engineering and output validation.

Speech Generation

Text-to-Speech using Hugging Face models.

Segment-based speech generation.

Duration and speed adjustment.

Optional voice cloning.

Audio Mixing & Video Integration

Speech and video synchronization.

Audio ducking (90% dubbed audio / 10% original audio during speech).

Subtitle embedding.

Final video rendering.

Deployment

Interactive interface with Gradio or Streamlit.

Docker containerization.

Deployment on Hugging Face Spaces.

🛠️ Technologies

Category

Tools

Programming

Python

Environment

Google Colab (GPU)

Speech Recognition

Hugging Face ASR

Forced Alignment

Alignment models

Translation

Lightweight LLMs

Speech Synthesis

Hugging Face TTS

Audio/Video

FFmpeg, yt-dlp

Interface

Gradio / Streamlit

Deployment

Docker, Hugging Face Spaces

Version Control

Git, GitHub

📂 Project Structure

automated-video-dubbing/
│
├── notebooks/
│   └── video_dubbing_pipeline.ipynb
│
├── src/
│   ├── audio_extraction.py
│   ├── transcription.py
│   ├── translation.py
│   ├── speech_generation.py
│   └── video_integration.py
│
├── outputs/
├── app.py
├── requirements.txt
├── Dockerfile
├── README.md
└── .gitignore

🚀 Expected Output

A final dubbed video containing:

Translated speech synchronized with the original video.

Embedded translated subtitles.

Original background audio preserved through audio ducking.

📌 Project Constraints

No commercial or closed-source AI APIs.

Only open-weight models.

Models must be compatible with limited GPU memory.

Processing is performed using Google Colab GPU runtime.

👩‍💻 Academic Context

Developed as part of the Traitement de la Parole (TP) – 2026 coursework.
