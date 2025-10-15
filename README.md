🎧 Audio Recordings (.wav, .mp3)
        │
        ▼
1️⃣ Speaker Diarization (who spoke when)
   → WhisperX / pyannote
        │
        ▼
2️⃣ Speech-to-Text (Transcription)
   → OpenAI WhisperX / faster-whisper
        │
        ▼
3️⃣ Text-level Sentiment + Interest
   → Hugging Face Transformers (RoBERTa, DistilBERT)
        │
        ▼
4️⃣ Voice-level Emotion
   → SpeechBrain / Audeering Wav2Vec2 models
        │
        ▼
5️⃣ Combine Text + Voice features
   → Weighted fusion (0.6 text + 0.4 voice)
        │
        ▼
6️⃣ Dashboard & Analytics
   → Streamlit / Apache Superset / Metabase
