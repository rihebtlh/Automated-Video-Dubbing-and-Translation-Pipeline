# Automated Video Dubbing & Translation Pipeline

End-to-end pipeline that automatically transcribes, translates and dubs videos into another language, using open-weight speech recognition, machine translation and text-to-speech models.

![Python](https://img.shields.io/badge/Python-3.x-blue)
![Google Colab](https://img.shields.io/badge/Runtime-Google%20Colab%20GPU-orange)
![Open-weight models](https://img.shields.io/badge/Models-open--weight%20only-green)

---

## Overview

An AI-powered pipeline that turns a video into a multilingual version. It preserves subtitle timestamps and synchronizes the generated speech with the original video.

Everything relies on open-source tools and open-weight models, with **no commercial AI APIs**. Processing is done on a Google Colab GPU runtime.

## Objectives

- Extract audio from YouTube videos
- Transcribe speech and generate accurate, timestamped subtitles
- Translate subtitles into a target language while preserving timestamps
- Generate dubbed speech using Text-to-Speech (TTS)
- Synchronize the translated audio with the original video
- Mix original and generated audio using audio ducking
- Embed translated subtitles into the final video
- Deploy the pipeline as an interactive web application

## Pipeline Architecture

```
YouTube video
     │
     ▼
┌──────────────────────────┐
│ 1. Extraction & ASR      │  yt-dlp → FFmpeg → ASR → forced alignment → .srt / .vtt
└──────────┬───────────────┘
           ▼
┌──────────────────────────┐
│ 2. Subtitle translation  │  lightweight open-weight LLM (< 2B params)
└──────────┬───────────────┘
           ▼
┌──────────────────────────┐
│ 3. Speech generation     │  Hugging Face TTS, per segment, duration/speed adjustment
└──────────┬───────────────┘
           ▼
┌──────────────────────────┐
│ 4. Mixing & integration  │  sync + audio ducking + embedded subtitles → final video
└──────────┬───────────────┘
           ▼
┌──────────────────────────┐
│ 5. Deployment            │  Gradio / Streamlit, Docker, Hugging Face Spaces
└──────────────────────────┘
```

### 1. Audio Extraction & Transcription
- Video downloading with `yt-dlp`
- Audio extraction using `FFmpeg`
- Automatic Speech Recognition (ASR)
- Forced alignment for precise timestamps
- Subtitle generation (`.srt` / `.vtt`)

### 2. Subtitle Translation
- Lightweight open-weight LLM (under 2B parameters)
- Translation with timestamp preservation
- Prompt engineering and output validation

### 3. Speech Generation
- Text-to-Speech using Hugging Face models
- Segment-based speech generation
- Duration and speed adjustment
- Optional voice cloning

### 4. Audio Mixing & Video Integration
- Speech and video synchronization
- Audio ducking (90% dubbed audio / 10% original audio during speech)
- Subtitle embedding
- Final video rendering

### 5. Deployment
- Interactive interface with Gradio or Streamlit
- Docker containerization
- Deployment on Hugging Face Spaces

## Technologies

| Category | Tools |
|---|---|
| Programming | Python |
| Environment | Google Colab (GPU) |
| Speech recognition | Hugging Face ASR |
| Forced alignment | Alignment models |
| Translation | Lightweight open-weight LLMs |
| Speech synthesis | Hugging Face TTS |
| Audio / video | FFmpeg, yt-dlp |
| Interface | Gradio / Streamlit |
| Deployment | Docker, Hugging Face Spaces |
| Version control | Git, GitHub |

## Expected Output

A final dubbed video containing:

- Translated speech synchronized with the original video
- Embedded translated subtitles
- Original background audio preserved through audio ducking

## Getting Started

1. Open `Projet_Traitement_Parole.ipynb` in Google Colab.
2. Select a GPU runtime (**Runtime → Change runtime type → GPU**).
3. Run the cells in order: download, transcription, translation, speech generation, then mixing and rendering.

## Project Structure

**Current:**

```
.
├── Projet_Traitement_Parole.ipynb   # Full pipeline notebook
└── README.md
```

**Planned:**

```
.
├── src/
│   ├── audio_extraction.py
│   ├── transcription.py
│   ├── translation.py
│   ├── speech_generation.py
│   └── video_integration.py
├── outputs/
├── app.py                           # Gradio / Streamlit interface
├── requirements.txt
├── Dockerfile
└── .gitignore
```

## Project Status

- [x] Pipeline prototype in a Colab notebook
- [ ] Refactor notebook into modules (`src/`)
- [ ] Web interface (Gradio / Streamlit)
- [ ] Docker containerization
- [ ] Deployment on Hugging Face Spaces

## Project Constraints

- No commercial or closed-source AI APIs
- Only open-weight models
- Models must be compatible with limited GPU memory
- Processing is performed on the Google Colab GPU runtime

## Academic Context

Developed as part of the *Traitement de la Parole* (TP) coursework, 2026, at USTO-MB.
