```md
# Sign Language AI

A Streamlit-based sign language communication dashboard that lets a user interact using hand gestures, voice input, and text-to-speech. The app uses a trained gesture model to recognize hand poses from a webcam and convert them into text or spoken output.

## Features

- Live camera-based gesture recognition using OpenCV and MediaPipe
- Hand gesture classification with a pre-trained pickle model (`gesture_model.pkl`)
- Sentence-building workflow for composing phrases from recognized gestures
- Text-to-speech output with `pyttsx3`
- Speech-to-text mode using the Google Speech Recognition API
- Simple dashboard UI built with Streamlit

## Tech Stack

- Python 3.10
- Streamlit
- OpenCV
- MediaPipe
- NumPy
- SpeechRecognition
- pyttsx3

## Repository Structure

```text
.
├── dashboard.py          # Main Streamlit app
├── gesture_model.pkl    # Trained gesture classification model
├── requirements.txt      # Python package requirements
├── packages.txt          # System packages needed for OpenCV/GL
├── runtime.txt           # Python runtime version
└── README.md            # Project documentation
```

## Setup

1. Clone the repository:

```bash
git clone https://github.com/sunitswain64/sign-language-ai.git
cd sign-language-ai
```

2. Create and activate a virtual environment (recommended):

```bash
python -m venv .venv
source .venv/bin/activate   # Linux/macOS
# or
.venv\Scripts\activate      # Windows
```

3. Install system dependencies (Linux):

```bash
sudo apt-get update
sudo apt-get install -y $(cat packages.txt)
```

4. Install Python dependencies:

```bash
pip install -r requirements.txt
```

## Running the App

Start the dashboard with:

```bash
streamlit run dashboard.py
```

Then open the local URL shown by Streamlit in your browser.

## How It Works

### Gesture Mode
- Enables the webcam
- Detects a hand using MediaPipe
- Extracts landmark coordinates
- Normalizes the feature vector
- Predicts the gesture using the loaded model
- Displays the recognized gesture and lets the user add it to a sentence

### Voice Mode
- Uses the microphone to capture audio
- Converts spoken input to text via Google Speech Recognition

### Text Mode
- Accepts text input and reads it aloud using text-to-speech

## Notes

- A webcam and microphone are required for gesture and voice features.
- The app expects the hand gesture model file `gesture_model.pkl` to be present in the project root.
- Some environments may require additional OS dependencies depending on your platform.
- The runtime is configured for Python 3.10 via `runtime.txt`.

## Example Usage

1. Launch the app.
2. Choose the "Gesture" mode.
3. Start the camera and perform a recognized hand sign.
4. Add the gesture to the sentence.
5. Speak the sentence aloud or build a phrase.

## Disclaimer

This project is intended as a prototype/demo for sign-language communication assistance. Gesture recognition accuracy depends on camera quality, lighting, the trained model, and the user's hand positioning.

## License

This repository does not currently include a license file. If you are planning to distribute or reuse it, add an appropriate open-source license before publishing.
```
