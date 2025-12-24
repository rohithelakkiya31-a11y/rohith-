Streamlit Chatbot using Groq API

This project is a simple AI Chatbot built using Streamlit and Groq API.
It allows users to enter a prompt and receive AI-generated responses in real time.

📌 Features

Simple and clean chatbot UI

Built using Streamlit

Uses Groq LLM models (LLaMA)

Secure API key handling with .env

Easy to run locally

🛠️ Requirements

Make sure you have the following installed:

Python 3.8 or above

pip (Python package manager)

Internet connection
Create .env file

In the same folder as app.py, create a file named .env and add:

GROQ_API_KEY=your_api_key_here


⚠️ Do not share your API key publicly.

▶️ Run the Chatbot

Run the following command:

streamlit run app.py


After running, Streamlit will open the chatbot in your browser.

🧠 Example app.py Code
import os
from dotenv import load_dotenv
import streamlit as st
from groq import Groq
load_dotenv()

st.title("Groq Chatbot 🤖")

api_key = os.getenv("GROQ_API_KEY")

if not api_key:
    st.error("GROQ_API_KEY not found")
    st.stop()

client = Groq(api_key=api_key)

user_input = st.text_input("Ask a question:")

if user_input:
    response = client.chat.completions.create(
        model="llama3-8b-8192",
        messages=[{"role": "user", "content": user_input}]
    )
    st.write(response.choices[0].message.content)
