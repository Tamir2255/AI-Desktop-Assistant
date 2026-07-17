# AI Desktop Assistant

A floating, always-on-top desktop sidebar assistant for Windows — chat, write, read/analyze, and control your PC, all from one sleek panel. Works fully out of the box with **zero API keys required**, and can optionally be boosted with your own OpenAI or Gemini key.

---

## ✨ Features

- **Chat** — ask questions, get live web-researched answers (no external AI needed by default)
- **Write Assistant** — professional emails, summaries, action plans, and full researched essays saved straight to Word
- **Read & Analyze** — highlight any text on your screen, copy it, and get instant explanations, summaries, or translations
- **Voice mode** — speak your commands and hear responses back (multiple text-to-speech engines with automatic fallback)
- **App & file control** — open apps/browsers, search the web, manage folders (open, rename, move, zip, delete with confirmation)
- **Built-in calculator** — step-by-step math, equation solving, unit conversion, and graphing
- **Activity log** — every command is saved and can be tapped again with one click
- **7 built-in themes** — switch instantly, no restart needed
- **Fully personalizable** — rename the assistant, set your own name, birthday shout-outs, and startup behavior
- **Optional Smart Mode** — bring your own OpenAI or Gemini key for richer conversational answers (never required)

---

## 🖥 Requirements

- Windows 10 or 11 (some features are Windows-only — see [Platform Notes](#platform-notes))
- Python 3.10+ installed
- Internet connection (for web search, weather, and voice features)

### Install dependencies

```bash
pip install pyperclip pyttsx3 edge-tts elevenlabs SpeechRecognition pyaudio yt-dlp sympy matplotlib numpy python-docx openpyxl reportlab pywin32
```

> Every dependency is optional and wrapped in safe fallbacks — if a package isn't installed, that one feature is disabled gracefully and everything else keeps working. Install only what you need, or install everything above for the full experience.

Recommended for OpenAI/Gemini Smart Mode (optional):

```bash
pip install openai google-generativeai
```

---

## 🚀 Getting Started

1. Install Python 3.10+ and the dependencies above.
2. Run the app:
   ```bash
   python vex.py
   ```
3. A floating sidebar appears on the right edge of your screen. Type a command or tap the mic to speak.
4. On first launch, open **⚙ (Settings) → Personalization** to set your name and the assistant's name.

That's it — no setup wizard, no accounts, no required API keys.

---

## ⚙️ Settings Guide

Click the **⚙** icon in the title bar to access:

| Menu | What it does |
|---|---|
| **🎨 Themes** | Instantly switch between 7 color palettes (Aurora, Midnight Ember, Emerald Forest, Solar Gold, Rose Quartz, Ocean Depths, Monochrome) |
| **Personalization** | Set your name, rename the assistant, choose the animated core design, set a birthday shout-out, and toggle silent startup |
| **API Settings** | Optionally add your own OpenAI key, Gemini key, or ElevenLabs voice key, and turn on **Smart Mode** |
| **Clear History** | Wipe the activity log |

### About Smart Mode

The assistant is fully self-contained by default — every answer is generated from live web search and scraping, with no third-party AI involved. If you add your **own** OpenAI or Gemini API key in API Settings and enable Smart Mode, the assistant will try that key first for more natural, conversational answers before falling back to its own web research. This is entirely optional and off by default.

---

## 🗂 Where your data lives

Nothing is written to the install folder or tied to any specific machine or developer account. All personal data is stored per-user in:

- **Windows:** `%APPDATA%\AI Desktop Assistant\`
- **macOS/Linux (dev/testing):** `~/.ai_desktop_assistant/`

This includes `config.json` (settings + optional API keys), `history.json` (activity log), and `learning.json` (custom learned replies, if used).

Generated documents (essays, PDFs, spreadsheets, downloaded videos, graphs) are saved to:

```
Desktop/AI Assistant Output/
```

---

## 🎛 Quick Command Reference

| Say / Type | Result |
|---|---|
| `open chrome` / `open notepad` | Launches an app |
| `open browser` | Opens your default browser |
| `search for [topic]` | Opens a search tab |
| `look up [topic]` | Researches and answers inline |
| `weather in [city]` | Current weather |
| `open folder [name]` | Opens a folder by name |
| `delete folder [name]` | Deletes with confirmation |
| `write an essay on [topic]` | Researches and saves a Word document |
| `write a professional email about [topic]` | Drafts an email |
| `35 * 5` or `solve x + 4 = 10` | Calculator |
| `convert 10 meters to feet` | Unit conversion |
| `graph x^2` | Plots and saves a graph image |
| `voice mode` | Switches to voice input |
| `my name is [name]` | Sets your name |
| `help` | Full command list |
| `bye` | Closes the assistant |

---

## 🧩 Customizing the Brand

Everything user-facing pulls from the **assistant name** set in Personalization — there is no hardcoded product name baked into the logic, so you can fully white-label this for your own product:

- Window title, chat labels, spoken greetings, and shortcuts all use the configured name
- The logo is an original vector mark (an "A" pierced by an "I"), drawn live on a Tkinter canvas — no external image assets, easy to recolor per theme
- Add new palettes by extending the `THEMES` dictionary near the top of `vex.py` — each theme is a simple dictionary of hex colors

---

## 🩺 Troubleshooting

- **Voice input says PyAudio is missing** — install PyAudio for your Python version, or install Microsoft C++ Build Tools first if the wheel fails to build.
- **No sound on speech output** — the assistant tries ElevenLabs → Edge Neural TTS → local `pyttsx3` in that order; it needs at least one working and an internet connection for the first two.
- **Graphing/math commands do nothing** — install `sympy`, `matplotlib`, and `numpy`.
- **Word/Excel/PDF export fails** — install `python-docx`, `openpyxl`, and `reportlab` respectively.
- **App list is empty** — the assistant scans Start Menu shortcuts and common install folders on first run; give it a few seconds after launch.

## Platform Notes

Window transparency, rounded corners, volume/lock/shutdown controls, and shortcut creation rely on Windows-specific APIs (`ctypes.windll`, `pywin32`). The core chat/search/write/read features run cross-platform, but the full experience is designed for Windows 10/11.

---

## 📄 License

Add your own license terms here before distributing to buyers (e.g. single-use commercial license, resale rights, attribution requirements).

---

*Questions or support requests: add your contact/support info here.*
