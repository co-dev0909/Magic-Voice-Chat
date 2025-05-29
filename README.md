# 🎙️ Magic Voice Chat

**Magic Voice Chat** lets you talk with AI characters in real time using your voice — like chatting with Einstein, a space wizard, or the OS from *Her*. It's fast, expressive, hilarious, and fully customizable. Run locally, use your favorite models (OpenAI, Anthropic, xAI, Ollama), and switch between multiple voices (OpenAI TTS, ElevenLabs, XTTS, or Kokoro TTS) — all from a slick Web UI.

![screenshot](https://github.com/bigsk1/voice-chat-ai/assets/demo_image.jpg)

---

## 🚀 Features

- **Real-Time Conversations** with OpenAI’s WebRTC Realtime API — interrupt mid-sentence!
- **Expressive TTS**: GPT-4o-mini-tts, ElevenLabs, XTTS, or Kokoro TTS with emotional voice prompts.
- **Flexible Transcription**: OpenAI or local Faster Whisper.
- **Web UI + CLI**: Talk, tweak, and test with your voice or keyboard.
- **Huge Cast of Characters**: 50+ AIs with wild personalities — therapists, pirates, vampires, and more.
- **Game & Story Modes**: Escape rooms, trivia games, noir mysteries, space adventures, and more.
- **Docker & Local Support**: Run it your way — Docker or native Python 3.10 on Windows, Linux, or macOS.
- **Sentiment-Based Replies**: AI adjusts its tone based on your mood.
- **Fully Offline Capable**: Use local models like Ollama + XTTS with zero internet.

---

## 🧪 Quick Start

### 🔧 Requirements

- Python 3.10  
- `ffmpeg`  
- A microphone  
- (Optional) CUDA-enabled GPU for faster XTTS/Faster Whisper  
- Docker (if running via container)

### 🖥️ Local Installation

```bash
git clone https://github.com/bigsk1/voice-chat-ai.git
cd voice-chat-ai
python -m venv venv
source venv/bin/activate      # Windows: venv\Scripts\activate
pip install -r requirements_cpu.txt  # or requirements.txt for GPU
````

Then run the app:

```bash
uvicorn app.main:app --host 0.0.0.0 --port 8000
```

Visit: [http://localhost:8000](http://localhost:8000)

### 🐳 Docker Run (CPU)

```bash
docker pull bigsk1/voice-chat-ai:latest
docker run -d --env-file .env -p 8000:8000 --name magic-voice-chat bigsk1/voice-chat-ai:latest
```

> Need CUDA? Use `Dockerfile.cuda` or native install.

---

## 🗣️ Voice, Model, and Transcription Options

| Feature        | Providers                        |
| -------------- | -------------------------------- |
| Language Model | OpenAI, Anthropic, xAI, Ollama   |
| TTS Voices     | OpenAI, ElevenLabs, XTTS, Kokoro |
| Transcription  | OpenAI Whisper, Faster Whisper   |
| UI Control     | Web browser or terminal          |

---

## 🎮 Game & Story Modes

* **Games**: Hangman, Escape Master, Trivia, Word Weavers, Logic Puzzles
* **Stories**: Noir Detective, Oregon Trail, Space Adventure, Haunted Mansion

All driven by in-character AI guides!

---

## 🧙 Create Your Own Characters

1. Create a new folder: `characters/wizard/`
2. Add:

   * `wizard.txt` (character prompt + voice instructions)
   * `prompts.json` (mood responses)
   * Optional: `wizard.wav` (custom XTTS voice)
3. Done! Select in the UI and start talking.

---

## 🔧 Configuration

Copy `.env.sample` → `.env` and adjust settings:

```env
MODEL_PROVIDER=openai
CHARACTER_NAME=einstein
TTS_PROVIDER=elevenlabs
OPENAI_MODEL=gpt-4o
OPENAI_API_KEY=your_api_key
ELEVENLABS_API_KEY=your_api_key
...
```

---

## 🧠 Smart Features

* **"What's on my screen?"** — screen analysis with llava (Ollama/OpenAI)
* **"Quit" / "Exit"** — ends conversation
* **Dynamic mood detection** — TextBlob sentiment scores adjust AI tone
* **ElevenLabs voice sync** — load your voice list via:

```bash
curl -s -X GET https://api.elevenlabs.io/v1/voices \
  -H "xi-api-key: $ELEVENLABS_API_KEY" | jq ...
```

---

## 📺 Demos

| Mode                | Demo Video            |
| ------------------- | --------------------- |
| OpenAI Realtime     | whisperer.mp4         |
| XTTS (local, GPU)   | magic\_xtts\_gpu.mp4  |
| OpenAI Enhanced TTS | expressive\_voice.mp4 |
| Escape Game Demo    | ninja\_assassin.mp4   |

---

## 💡 Tips

* Best combo: `xAI + ElevenLabs + Faster Whisper (GPU)`
* Want fast + local? Use `Ollama + XTTS` (slower on CPU)
* UI is recommended for switching voices/models on the fly

---

## 📜 License

MIT License

---

> ⭐ Like the project? Show some love with a star: [Magic Voice Chat on GitHub](https://github.com/bigsk1/voice-chat-ai)
