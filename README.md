# Sign Language AI

A Streamlit-based sign language communication dashboard that lets a user interact using hand gestures, voice input, and text-to-speech. The app uses a trained gesture model to recognize hand poses from a webcam and convert them into text or spoken output.

## Features

* Live camera-based gesture recognition using OpenCV and MediaPipe
* Hand gesture classification with a pre-trained pickle model (`gesture_model.pkl`)
* Sentence-building workflow for composing phrases from recognized gestures
* Text-to-speech output with `pyttsx3`
* Speech-to-text using the SpeechRecognition library and Google Speech Recognition
* Simple dashboard UI built with Streamlit
* Gesture stability filtering to reduce unstable predictions
* Add, delete, and clear gestures while building a sentence

## Tech Stack

* Python 3.10
* Streamlit
* OpenCV
* MediaPipe
* NumPy
* SpeechRecognition
* pyttsx3
* Pickle

## Repository Structure

```text
.
├── dashboard.py          # Main Streamlit app
├── gesture_model.pkl     # Trained gesture classification model
├── requirements.txt      # Python package requirements
├── packages.txt          # System packages needed for deployment
├── runtime.txt           # Python runtime version
└── README.md             # Project documentation
```

## Setup

### 1. Clone the repository

```bash
git clone https://github.com/sunitswain64/sign-language-ai.git
cd sign-language-ai
```

### 2. Create and activate a virtual environment

```bash
python -m venv .venv
source .venv/bin/activate
```

For Windows:

```bash
.venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Run the application

```bash
streamlit run dashboard.py
```

Then open the local URL shown by Streamlit in your browser.

## How It Works

### Gesture Mode

* Enables the webcam
* Detects the hand using MediaPipe
* Extracts hand landmark coordinates
* Normalizes the feature vector
* Predicts the gesture using the trained model
* Applies stability filtering to reduce unstable predictions
* Displays the recognized gesture
* Allows gestures to be added to a sentence
* Converts the completed sentence into speech

### Voice Mode

* Uses the microphone to capture audio
* Converts spoken input into text using Google Speech Recognition

### Text Mode

* Accepts text input
* Converts the entered text into speech using `pyttsx3`

## Sentence Building

The Gesture Mode provides controls for building and editing sentences:

* **Add Gesture** — adds the current recognized gesture to the sentence
* **Space** — adds a space between gestures
* **Delete Last** — removes the last added gesture
* **Clear Sentence** — clears the complete sentence
* **Speak Sentence** — reads the completed sentence aloud

## Gesture Stability Filtering

The system stores recent gesture predictions in a buffer and selects the most frequently detected gesture as the stable prediction.

```text
Recent Predictions
        ↓
Prediction Buffer
        ↓
Frequency Analysis
        ↓
Stable Gesture
        ↓
Sentence / Speech Output
```

## Notes

* A webcam is required for Gesture Mode.
* A microphone is required for Voice Mode.
* The application expects `gesture_model.pkl` to be present in the project root.
* Gesture recognition accuracy depends on the trained model, lighting, camera quality, and hand positioning.
* Additional system dependencies may be required depending on the operating system and deployment environment.

## Example Usage

1. Launch the application.
2. Select **Gesture** mode.
3. Start the camera.
4. Perform a recognized hand gesture.
5. Add the gesture to the sentence.
6. Use **Space** to separate words.
7. Continue adding gestures.
8. Select **Speak Sentence** to hear the completed sentence.

## Future Improvements

* Support for additional sign gestures
* Two-hand gesture recognition
* Improved gesture recognition accuracy
* Multilingual speech output
* Reverse text/voice-to-sign conversion
* Mobile application deployment
* Improved sentence-level recognition

## Disclaimer

This project is a prototype/demo for sign-language communication assistance. Recognition accuracy depends on the training data, camera quality, lighting conditions, and hand positioning.

## License

This repository currently does not include a license file. Add an appropriate open-source license if you plan to distribute or reuse the project.
