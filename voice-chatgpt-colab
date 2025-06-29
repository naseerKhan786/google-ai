import openai
import gradio as gr
from gtts import gTTS
import tempfile
import os
import speech_recognition as sr
import io

# Replace with your OpenAI API key
openai.api_key = "sk-xxxxxxxxxxxxxxxxxxxxxxxxxxxx"

# Function to transcribe audio to text
def transcribe(audio_file):
    recognizer = sr.Recognizer()
    with sr.AudioFile(audio_file) as source:
        audio_data = recognizer.record(source)
        text = recognizer.recognize_google(audio_data)
    return text

# Main function: Speech Recognition + GPT + Text-to-Speech
def chat_with_gpt(audio):
    # Convert bytes to file-like object
    audio_file = tempfile.NamedTemporaryFile(delete=False, suffix=".wav")
    audio_file.write(audio)
    audio_file.close()

    # Speech Recognition
    text = transcribe(audio_file.name)
    os.remove(audio_file.name)

    print(f"You said: {text}")

    # GPT Response
    response = openai.ChatCompletion.create(
        model="gpt-3.5-turbo",
        messages=[{"role": "user", "content": text}]
    )
    reply = response['choices'][0]['message']['content']
    print("GPT says:", reply)

    # Convert GPT reply to speech
    tts = gTTS(reply)
    tts_file = tempfile.NamedTemporaryFile(delete=False, suffix=".mp3")
    tts.save(tts_file.name)

    return reply, tts_file.name

# Gradio Interface
iface = gr.Interface(
    fn=chat_with_gpt,
    inputs=gr.Audio(type="filepath", label="Speak your question"),
    outputs=[gr.Textbox(label="GPT Response"), gr.Audio(label="GPT Audio Reply")]
)

iface.launch(share=True)



