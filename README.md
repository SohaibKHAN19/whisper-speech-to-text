# whisper-speech-to-text
Convert recorded or uploaded speech into text using OpenAI Whisper.
# Whisper Speech-to-Text

AI-powered speech-to-text application built using OpenAI Whisper, Hugging Face Transformers, and Gradio.

This application allows users to:
- Record audio directly from a microphone
- Upload audio files
- Convert speech into English text
- Generate real-time transcriptions using Whisper AI

---

## Features

- Speech-to-text transcription
- Microphone recording support
- Audio file upload support
- Whisper AI integration
- Gradio web interface
- Continuous transcript state handling
- Fast and lightweight implementation

---

## Technologies Used

- Python
- Gradio
- Hugging Face Transformers
- OpenAI Whisper
- PyTorch

---

## Project Structure

```bash
whisper-speech-to-text/
│
├── app.py
├── requirements.txt
├── README.md
└── .gitignore
```

---

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/whisper-speech-to-text.git
cd whisper-speech-to-text
```

---

### 2. Create Virtual Environment (Optional)

### Windows

```bash
python -m venv venv
venv\Scripts\activate
```

### Linux / Mac

```bash
python3 -m venv venv
source venv/bin/activate
```

---

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

---

## Requirements

Add this to `requirements.txt`

```txt
gradio
transformers
torch
torchaudio
openai-whisper
```

---

## Run the Application

```bash
python app.py
```

After running, Gradio will generate a local URL such as:

```bash
http://127.0.0.1:7860
```

Open it in your browser.

---

## Application Code

```python
import gradio as gr
from transformers import pipeline

# Load Whisper model
p = pipeline(
    "automatic-speech-recognition",
    model="openai/whisper-tiny"
)

# Transcription function
def transcribe(audio, state=""):

    if audio is None:
        return state, state

    try:
        result = p(audio)["text"]

        new_state = state + result + " "

        return new_state, new_state

    except Exception as e:
        return f"Error: {str(e)}", state

# Gradio UI
gr.Interface(
    fn=transcribe,

    inputs=[
        gr.Audio(
            sources=["microphone", "upload"],
            type="filepath"
        ),
        gr.State("")
    ],

    outputs=[
        gr.Textbox(label="Transcript"),
        gr.State()
    ],

    live=False
).launch()
```

---

## Future Improvements

- Multi-language transcription
- Urdu speech recognition
- Real-time streaming transcription
- Subtitle (.srt) generation
- Translation support
- Download transcript as TXT/PDF
- Speaker diarization
- Deployment on Hugging Face Spaces

---

## Example Use Cases

- Meeting transcription
- Voice notes conversion
- Lecture transcription
- Accessibility applications
- AI-powered assistants

---

## Screenshots

Add screenshots of:
- Microphone recording
- Uploaded audio transcription
- Gradio UI

---

## Deployment

You can deploy this project on:

- Hugging Face Spaces
- Render
- Railway

---

## License

This project is open-source and available under the MIT License.

---

## Author

Sohaib Khan

MERN Stack Developer & AI Enthusiast
