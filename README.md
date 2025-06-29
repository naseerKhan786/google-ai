# 🎤 Voice Chat with GPT (Google Colab + Gradio)

This project allows you to talk to ChatGPT using your voice! It uses:

- 🧠 OpenAI's GPT-3.5 model for smart replies  
- 🎙️ Gradio for microphone-based input/output  
- 🗣️ Google Text-to-Speech (gTTS) for voice replies  
- 🧪 Google Colab to run everything in the cloud (no install needed)

---

## 🚀 Features

- 🎤 Record your question by voice
- 🧠 GPT understands and responds
- 🔊 GPT's reply is spoken back to you
- 🌐 Works in any browser using a public Gradio link

---

## 🔧 Setup Instructions (Google Colab)

1. Open the Google Colab notebook.
2. Run the first cell to install dependencies:

```bash
pip install openai gradio gtts SpeechRecognition pydub
