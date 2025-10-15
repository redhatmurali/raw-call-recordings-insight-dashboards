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


🏁 Summary — Best Practical Setup (2025)
Component	Recommended Tool
Transcription	🟢 WhisperX (large-v3, GPU)
Speaker Diarization	🟢 pyannote.audio
Voice Emotion	🟢 SpeechBrain / Audeering
Text Sentiment	🟢 CardiffNLP RoBERTa
Interest Prediction	🟢 Custom fine-tuned DistilBERT or Logistic Regression
Visualization	🟢 Streamlit Dashboard
Storage	🟢 SQLite / CSV
Hardware	🟢 RTX 3080+ or 4070 GPU (CUDA 12.x)


✔️ WhisperX transcription
✔️ Voice emotion via SpeechBrain
✔️ Text sentiment + interest detection
✔️ Streamlit dashboard
