# Poster_Genration_System

# 🩺 AI Prescription Generator

Generate personalized **"Prescription for Happiness"** cards for doctors using a **locally-hosted Phi-3 model via Ollama**: no paid API keys, no data leaving your machine.

The app takes a doctor's details, generates motivational prescription-style content tailored to their specialty, experience and achievements, adds a QR code to their Google profile, and renders everything onto a prescription template as a shareable PNG.

Perfect for:
- Doctor's Day campaigns
- Medical Representative engagement
- Healthcare marketing
- Personalized appreciation gifts

---

## ✨ Features

- 🤖 AI-generated personalized content using **Ollama + Phi-3** (runs fully locally)
- 🖥️ Web frontend to enter doctor details and preview/download the card
- 🩺 Works with **any medical specialty**
- 🎨 Automatic rendering onto a prescription template
- 📱 QR code linking to the doctor's Google profile
- 🏆 Includes awards and years of experience
- 🖼️ High-quality PNG output
- ⚡ FastAPI backend with interactive Swagger docs

---

## 🛠 Tech Stack

| Technology | Purpose |
|------------|---------|
| Ollama (Phi-3) | Local LLM for content generation |
| FastAPI | Backend REST API |
| HTML / CSS / JavaScript | Frontend interface |
| Pillow (PIL) | Image rendering |
| qrcode | QR code generation |
| Pydantic | Request validation |
| Uvicorn | ASGI server |

---

## 📁 Project Structure

```
ai-prescription-generator/
│
├── assets/
│   ├── fonts/
│   ├── templates/
│   └── icons/
│
├── frontend/
│   ├── index.html
│   ├── style.css
│   └── script.js
│
├── generator.py        # Prompts Ollama Phi-3 and parses the response
├── renderer.py         # Draws content on the prescription template
├── utils.py            # Helpers (QR code, text wrapping, etc.)
├── config.py           # Configuration (model name, paths, etc.)
├── main.py             # FastAPI app and routes
├── requirements.txt
├── .gitignore
└── README.md
```

> Adjust the `frontend/` contents to match your actual files.

---

## ⚙️ Prerequisites

- Python 3.10+
- [Ollama](https://ollama.com/download) installed
- Phi-3 model pulled locally

---

## 🚀 Installation

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/ai-prescription-generator.git
cd ai-prescription-generator
```

### 2. Create a virtual environment

**Windows**
```bash
python -m venv .venv
.venv\Scripts\activate
```

**Linux / macOS**
```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Set up Ollama and Phi-3

```bash
ollama pull phi3
ollama serve
```

Ollama runs at `http://localhost:11434` by default.

---

## ▶️ Run the App

```bash
uvicorn main:app --reload
```

- Backend API: `http://localhost:8000`
- Swagger docs: `http://localhost:8000/docs`
- Frontend: open `frontend/index.html` in your browser (or the URL served by the app, if configured)

---

## 📡 API Endpoint

### `POST /generate`

Generates a personalized prescription PNG.

**Sample request**

```json
{
  "name": "Dr. Dilip Hemnani",
  "specialty": "Dermatologist",
  "google_profile_link": "https://www.google.com/search?q=Dr.+Dilip+Hemnani",
  "years_experience": 12,
  "awards": "Best Dermatologist Award 2023"
}
```

**Response:** PNG image, ready to download or share on WhatsApp.

---

## 🔄 How It Works

1. User enters the doctor's details in the frontend.
2. The frontend sends the data to the FastAPI backend.
3. The request is validated with Pydantic.
4. Ollama (Phi-3) generates personalized prescription content.
5. A QR code is created from the doctor's Google profile link.
6. Pillow renders the text and QR code onto the prescription template.
7. The final PNG is returned and shown in the frontend.

---

## 🎯 Personalization

Each card adapts to:

- Doctor name
- Medical specialty
- Years of experience
- Awards and recognition
- Google profile link

---

## 🔮 Future Improvements

- Multiple prescription templates
- PDF export
- Batch generation for multiple doctors
- WhatsApp / email delivery
- Multi-language support
- Doctor database integration

---

## 📄 License

This project is intended for educational and demonstration purposes.

---

## 👩‍💻 Author

**Shravani Maske**
AI/ML Engineer | [LinkedIn](https://linkedin.com/in/shravanimaske) | [GitHub](https://github.com/shravanimaske)
