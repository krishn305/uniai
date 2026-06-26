# uniai
# UniAi 🎓
### AI-Powered International University Recommendation Platform

UniAi is a full-stack web application that helps students discover universities abroad. Users enter their preferred course, degree level, budget, and target country — and the app returns 10 AI-curated university recommendations complete with tuition estimates and official website links.

**Live Demo:** [uniai-pubz.onrender.com](https://uniai-pubz.onrender.com)

---

## Features

- 🔍 **Smart University Search** — Filter by course, degree type, annual fees, target country, and home country
- 🤖 **AI-Powered Recommendations** — Uses Google Gemini 1.5 Flash to generate 10 tailored university matches
- 🌐 **Global Coverage** — Supports target countries including USA, UK, Germany, Canada, Australia, Japan, and more
- 📋 **Structured Results** — Each result card shows university name, city, estimated tuition, and a direct link to the official admissions page
- ⚠️ **Built-in Disclaimer** — Clearly communicates that results are AI-generated and should be verified

---

## Tech Stack

| Layer | Technology |
|---|---|
| **Backend** | Python, Flask, Flask-CORS |
| **AI / LLM** | Google Gemini 1.5 Flash (`google-generativeai`) |
| **Frontend** | HTML5, CSS3, Vanilla JavaScript |
| **Deployment** | Render (Gunicorn WSGI server) |
| **Environment** | Python-dotenv for API key management |

---

## Project Structure

```
uniai-main/
├── app1.py                  # Flask backend — routes, Gemini API call, response parser
├── requirements.txt         # Python dependencies
├── templates/
│   ├── Home.html            # Landing page with feature navigation
│   ├── Programs.html        # University search form (5-filter input UI)
│   └── results.html         # Dynamic results page (university cards)
└── static/
    ├── programs.js          # Handles form submission and API call
    ├── results.js           # Renders university result cards from localStorage
    ├── style.css / style2.css
    └── [images]
```

---

## How It Works

1. User fills the search form on `/Programs.html` — course, degree, fees range, target country, home country
2. On submit, `programs.js` sends a `POST` request to `/find-universities`
3. Flask backend builds a structured prompt and calls **Google Gemini 1.5 Flash**
4. Gemini returns 10 universities in a semicolon-delimited format
5. Backend parses the response using regex into structured JSON (name, city, tuition, website)
6. Results are stored in `localStorage` and rendered as cards on the results page

---

## Getting Started

### Prerequisites
- Python 3.9+
- A [Google Gemini API key](https://aistudio.google.com/app/apikey)

### Installation

```bash
# Clone the repository
git clone https://github.com/krishn305/uniai.git
cd uniai-main

# Install dependencies
pip install -r requirements.txt

# Create a .env file with your API key
echo "GEMINI_API_KEY=your_api_key_here" > .env

# Run the app locally
python app1.py
```

Visit `http://localhost:5000` in your browser.

### Deployment (Render)
Set `GEMINI_API_KEY` as an environment variable in your Render dashboard and use `gunicorn app1:app` as the start command.

---

## Dependencies

```
flask
flask-cors
google-generativeai
python-dotenv
gunicorn
langchain
langchain-google-genai
langchain-core
langgraph
```

---

## Future Enhancements

- [ ] Add scholarship search alongside university results
- [ ] Integrate university ranking data (QS, THE) into recommendations
- [ ] Support more target countries and degree types
- [ ] Add user authentication to save searches
- [ ] Replace localStorage with a proper session/database layer

---

## Author

**Krishnapriya** — [GitHub: krishn305](https://github.com/krishn305)

---

*Disclaimer: University data is AI-generated for guidance purposes only. Please verify all information on official university websites before making any decisions.*
