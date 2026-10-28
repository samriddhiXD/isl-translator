# PLAN

## Goal
Deaf users ke Indian Sign Language (ISL) signs ko webcam se recognize karke Hindi/English text aur voice mein convert karna.

Hospital Emergency Mode mein 15 words support karne hain. Hearing users ke liye speech-to-text feature bhi hoga, taaki two-way communication possible ho.

## Pipeline
Webcam → OpenCV → MediaPipe Holistic landmarks → 30-frame sequence → LSTM model → word + confidence → threshold/smoothing → sentence builder + Hindi mapping → UI text + gTTS voice

## Folder Structure
```text
isl-translator/
├── data/
│   └── Har word ka folder, .npy files
├── models/
│   ├── model.h5
│   └── labels.json
├── src/
│   ├── landmarks.py
│   ├── collect_data.py
│   ├── train.py
│   ├── predict.py
│   ├── sentence.py
│   └── speech.py
├── notebooks/
│   └── Colab training notebooks
├── app.py
├── requirements.txt
├── PROJECT_STATE.md
└── PLAN.md
```

## ISL Vocabulary (15 Words)
1. Hello
2. Thank you
3. Help
4. Doctor
5. Pain
6. Water
7. Medicine
8. Yes
9. No
10. Please
11. Sorry
12. Emergency
13. Food
14. Where
15. Wait

## UI Pages
- Home
- Live Translator
- Two-Way Chat
- Practice/Contribute
- About

## Development Rules
- Har module alag banega aur test hoga; uske baad hi agla module start hoga.
- Har working step ke baad Git commit karna hai.
- `PROJECT_STATE.md` mein current progress update karni hai.
- `PLAN.md` project ka source of truth rahega.
- Webcam, landmark detection, dataset collection, model training aur prediction ko separately test karna hai.

## Tools and Responsibilities
- Claude: Planning and debugging
- Antigravity: Code building
- Google Colab: Model training

## 7-Day Development Outline
- Day 1: Repository setup, environment configuration, dependencies and project documentation.
- Day 2: Webcam setup and landmark detection.
- Day 3: Dataset collection for the 15 ISL words.
- Day 4: Model training using an LSTM.
- Day 5: Real-time prediction and confidence thresholding.
- Day 6: Streamlit UI, Hindi/English text and voice output.
- Day 7: Two-way communication, testing, debugging and documentation.

*Note: This is the planned workflow. Features will be marked complete only after implementation and testing.*
