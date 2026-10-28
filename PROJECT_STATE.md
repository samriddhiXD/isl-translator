# PROJECT STATE: SignBridge (ISL Translator, Hospital Emergency Mode)

## Overview
- Goal: Deaf user ke ISL signs ko webcam se pehchan kar Hindi/English text + voice mein convert karna
- Extra: Two-way mode (hearing person bole -> speech-to-text screen par)
- Scope: 15 words, Hospital Emergency Mode (chhota scope = better accuracy)
- Why this project: High impact + unique (ISL tools bahut kam hain), software-only, ChatGPT se solve nahi hota
- Duration: 7 days, roz 3-4 hrs
- User: Hinglish mein baat karti hai. Pehle concept samjhao, phir code. Step-by-step chahiye.

## Words (15)
hello, thank you, help, doctor, pain, water, medicine, yes, no, please, sorry, emergency, food, where, wait
(Rule: jis word ka sign ISLRTC se confirm na ho, usse hata do/badlo)

## Tech Stack
- Python 3.10/3.11, venv
- OpenCV, MediaPipe Holistic (landmarks)
- TensorFlow/Keras LSTM/GRU, 30-frame sequences
- gTTS (voice out), SpeechRecognition (voice in)
- Streamlit UI (+ streamlit-webrtc for webcam)
- Training: Google Colab | Backup: Google Drive | Code: GitHub

## Pipeline
Webcam -> OpenCV -> MediaPipe Holistic -> preprocessing (30-frame seq)
-> LSTM -> word + confidence -> threshold/smoothing
-> sentence builder + Hindi map -> UI text + gTTS voice
Hearing user -> Mic -> Speech-to-Text -> Chat UI

## Folder Structure
isl-translator/
- PLAN.md, PROJECT_STATE.md, requirements.txt
- data/ (har word ka folder, .npy files)
- models/ (model.h5, labels.json)
- src/ (landmarks.py, collect_data.py, train.py, predict.py, sentence.py, speech.py)
- app.py (Streamlit)
- notebooks/ (Colab)

## UI Pages
1. Home/Landing  2. Live Translator (webcam + detected word + sentence + Hindi + speak button + history)
3. Two-Way Chat (mic + chat bubbles + quick replies)  4. Practice/Contribute  5. About/Impact
(UI pehle dummy data ke saath banegi, model baad mein jodenge)

## 7-Day Plan
- Day 1: Setup + planning  [DONE]
- Day 2: collect_data.py banana (30-frame sequences .npy save)
- Day 3: Data collection (15 words x 50-60 samples, 2-3 log, alag lighting/background)
- Day 4: Colab par LSTM training, target 85%+ test accuracy, confusion matrix
- Day 5: Real-time prediction + threshold (80%) + TTS
- Day 6: Streamlit UI, two-way mode, Hindi output, sentence formation
- Day 7: Testing, deploy (bonus), backup demo video, pitch deck, Q&A prep

## Done so far
- Day 1 COMPLETE: Python version checked, repo cloned, venv + libraries installed,
  PROJECT_STATE.md/PLAN.md/requirements.txt added, MediaPipe test passed,
  ISL signs practice shuru, Drive folder (isl-data) + Colab login done

## Current status
- Current day: 2 (starting)
- Pending: collect_data.py banana aur test karna
- UI: (not started / dummy UI status yahan likho)

## Problems / Notes
- (koi error ya issue yahan likho)

## Rules / Warnings
- Har working step par git commit
- Ek module banao, test karo, phir agla
- Data quality > model complexity. Accuracy kam ho to pehle data badhao
- streamlit-webrtc deploy tricky hai, demo local laptop par karo, deploy bonus hai
- Newer MediaPipe mein mp.solutions error de sakta hai (fix mujhse pucho)
- Hamesha backup demo video rakho
- Sirf ek insan ka data mat record karo

## Tool Roles
- Claude: planning, concepts, debugging, accuracy analysis, pitch/Q&A
- Antigravity: files/code build, multi-file edits (PLAN.md ko source of truth do)
- ChatGPT: second opinion
- Colab: training | GitHub: version control | Canva: pitch deck
