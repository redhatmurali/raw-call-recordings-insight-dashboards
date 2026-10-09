# Raw Call Recordings — Insight & Analytics Dashboard

An AI-powered pipeline for analyzing audio call recordings using speech-to-text, speaker diarization, voice emotion recognition, text sentiment analysis, and interactive dashboards.

## Pipeline Overview

```text
Audio Recordings (.wav, .mp3)
           |
           v
1. Speaker Diarization
   WhisperX / pyannote.audio
           |
           v
2. Speech-to-Text Transcription
   WhisperX / faster-whisper
           |
           v
3. Text Sentiment & Interest Analysis
   Hugging Face Transformers
           |
           v
4. Voice Emotion Recognition
   SpeechBrain / Audeering
           |
           v
5. Feature Fusion
   Text Features + Voice Features
           |
           v
6. Dashboard & Analytics
   Streamlit / Apache Superset / Metabase
```

## Recommended Technology Stack

| Component | Recommended tools | Purpose |
|---|---|---|
| Audio transcription | WhisperX, faster-whisper | Convert speech into text with timestamps. |
| Speaker diarization | pyannote.audio | Identify speaker turns and who spoke when. |
| Text sentiment analysis | Hugging Face Transformers | Classify sentiment and conversational intent. |
| Voice emotion recognition | SpeechBrain, Audeering | Estimate emotion-related characteristics from audio. |
| Interest prediction | Fine-tuned DistilBERT or logistic regression | Predict predefined interest or intent categories. |
| Feature fusion | Python, scikit-learn | Combine text and acoustic features into a unified score. |
| Dashboard | Streamlit | Build interactive analytics applications. |
| BI reporting | Apache Superset, Metabase | Create reports and business dashboards. |
| Data storage | SQLite, CSV, SQL database | Store transcripts, timestamps, predictions, and metrics. |

## Processing Workflow

### 1. Audio ingestion

- Accept WAV and MP3 recordings.
- Validate file formats and audio duration.
- Normalize audio where required.
- Associate recordings with unique IDs and metadata.

### 2. Speaker diarization

- Detect speaker changes.
- Assign speaker labels such as `SPEAKER_00` and `SPEAKER_01`.
- Associate timestamps with each speaker segment.

### 3. Speech transcription

- Generate text transcripts with timestamps.
- Associate transcript segments with speaker labels.
- Review transcription confidence and errors where available.

### 4. Text analysis

- Estimate positive, neutral, or negative sentiment.
- Detect predefined customer-interest or intent categories.
- Store model outputs and confidence scores.

### 5. Voice emotion analysis

- Extract acoustic features and estimate emotion-related categories.
- Align audio segments with transcript timestamps.
- Treat emotion predictions as estimates, not definitive statements about a speaker's internal state.

### 6. Feature fusion

Combine text and voice features into a unified analytical model.

Example initial weighting:

- Text features: 60%
- Voice features: 40%

These weights are illustrative starting values. Validate and calibrate them against representative, appropriately labeled data before using the resulting score for business decisions.

### 7. Dashboard and reporting

Display metrics such as:

- Total recordings processed
- Transcription completion rate
- Speaker-turn distribution
- Sentiment and intent trends
- Estimated voice-emotion distributions
- Processing errors and model confidence
- Trends over time

## Suggested Hardware

| Workload | Suggested hardware |
|---|---|
| Small experiments | CPU, 16 GB RAM |
| Regular audio processing | NVIDIA GPU, 16–32 GB RAM |
| Larger workloads | NVIDIA GPU with 16 GB or more VRAM, 32–64 GB RAM |

Actual requirements depend on audio duration, model size, concurrency, and batch processing.

An RTX 3080 or RTX 4070 with CUDA support can be a practical starting point for GPU-based experiments, subject to model memory requirements.

## Installation Preparation

Create a Python virtual environment:

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
```

Install the dependencies appropriate to your selected models and CUDA environment. PyTorch, WhisperX, pyannote.audio, and SpeechBrain may have version and hardware compatibility requirements; verify their official installation instructions before combining versions.

## Data and Privacy

Call recordings may contain sensitive personal information.

- Obtain appropriate authorization to process recordings.
- Restrict access to audio, transcripts, and dashboards.
- Protect stored data and credentials.
- Establish retention and deletion policies.
- Avoid using emotion or interest predictions as the sole basis for consequential decisions.
- Evaluate model accuracy, bias, and reliability before production deployment.

## Project Goals

- Automated transcription and speaker segmentation
- Searchable call transcripts
- Text and audio feature analysis
- Configurable interest and intent classification
- Interactive analytics and reporting
- Scalable processing of recording collections

## License

Add a license file if you intend to distribute or publish this project for reuse.
