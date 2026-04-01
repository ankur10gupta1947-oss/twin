# Digital Twin · Neural Ops v6

**Your AI thinking partner — loaded with mental models, synced to Google Drive, zero dependencies.**

[![License: MIT](https://img.shields.io/badge/License-MIT-orange.svg)](https://opensource.org/licenses/MIT)
[![Single File](https://img.shields.io/badge/Architecture-Single%20HTML-blue.svg)](.)
[![Zero Dependencies](https://img.shields.io/badge/Dependencies-0-green.svg)](.)
[![Made with Groq](https://img.shields.io/badge/Powered%20by-Groq-purple.svg)](https://groq.com)

> **2,400 lines of vanilla JavaScript. One HTML file. No framework. No build step.**

---

## 🎯 What is This?

**Digital Twin** is an AI-powered thinking companion that mirrors your decision-making style. It's not a generic chatbot — it learns your mental models, remembers your preferences, and applies frameworks from books you analyze.

**The twist?** Everything lives in **one HTML file** and syncs to **your Google Drive**. No backend, no database, no npm install.

---

## ✨ Features

### 🧠 **5 Thinking Modes**
- **Think** — Big picture analysis with brutal clarity
- **Brainstorm** — Divergent ideation, surprising angles
- **Debate** — Argues against you relentlessly
- **Delegate** — Makes decisions as you would
- **Critique** — Stress-tests ideas with zero mercy

### 📚 **Book Intel**
Analyze any book and extract:
- Core ideas & mental models
- Critical thinking tools
- Key insights & application steps
- Thinking prompts to deepen understanding

Mental models automatically feed into the Decision Engine.

### 🎲 **Decision Engine**
- Get a **verdict**, not a list of pros/cons
- Automatically applies loaded mental models
- Considers stakes, context, and your thinking style
- Outputs: verdict, reasoning, risks, next move

### 💡 **Idea Board**
- Pin ideas from chat or ⚡ Spark
- Move through pipeline: Raw → Validated → Shelved
- Visual kanban synced to Drive

### 📅 **Project Planner**
- Extracts roadmaps from conversations
- Phases, tasks, priorities, blockers
- Export to Markdown

### 🧬 **Learning System**
- Learns skills, preferences, projects, insights
- Categories: `SKILL | PREFERENCE | PROJECT | INSIGHT`
- Compounds across all sessions
- Export your knowledge base

### ☁️ **Google Drive Sync**
- All data in `digitaltwin_data.json`
- Exponential backoff retry on failures
- Nothing stored locally — portable across devices

---

## 🚀 Quick Start

### **1. Get API Keys** (5 minutes)

#### Groq API Key (Free)
1. Go to [console.groq.com](https://console.groq.com)
2. Sign up and create an API key
3. Starts with `gsk_...`

#### Google OAuth Client ID
1. Go to [console.cloud.google.com](https://console.cloud.google.com)
2. Create a new project (or use existing)
3. Enable **Google Drive API**
4. Go to **APIs & Services → Credentials**
5. Create **OAuth 2.0 Client ID** (Web application)
6. Add authorized origin: `http://localhost` or your domain
7. Copy the Client ID (ends with `.apps.googleusercontent.com`)

### **2. Run the App**
```bash
# Option A: Open directly
open index.html

# Option B: Simple HTTP server
python3 -m http.server 8000
# Then visit: http://localhost:8000

# Option C: Deploy instantly
# Drag index.html to Netlify/Vercel/GitHub Pages
```

### **3. First Launch**
1. Paste your **Groq API Key** and **Google OAuth Client ID**
2. Click "Connect Google Drive"
3. Authorize Drive access
4. Start talking to your twin

---

## 🏗️ Architecture

### **Why One HTML File?**
```
✅ Zero friction — copy/paste and run
✅ No build step — no webpack, no npm
✅ Fully inspectable — educational value
✅ Deploy anywhere — drag to any host
✅ Fork-friendly — easy to remix
```

**2,400 lines** of vanilla JavaScript, organized into clear sections:
- Gate & Auth (Groq + Google OAuth)
- State Management (Drive sync with retry)
- Chat Engine (5 thinking modes)
- Book Intel (LLM-powered analysis)
- Decision Engine (Framework application)
- Idea Board (Kanban + persistence)
- Planner (Roadmap extraction)
- Learning System (Knowledge accumulation)

### **Tech Stack**
- **No framework** — Pure HTML/CSS/JS
- **No dependencies** — Browser APIs only
- **LLM**: Groq (Llama 3.3 70B)
- **Storage**: Google Drive API
- **Auth**: Google OAuth 2.0
- **Fonts**: Playfair Display, Inter, JetBrains Mono
- **Design**: Custom geometric UI with CSS variables

---

## 🔐 Security

### **API Key Safety**
```javascript
// Keys stored ONLY in sessionStorage
// Wiped when you close the tab
const AK = {
  groqKey:    { key: 'dt_groq_key_v6',    store: sessionStorage },
  driveToken: { key: 'dt_drive_token_v6', store: sessionStorage }
};
```

- ✅ **Never** written to Drive or localStorage
- ✅ XSS protection with HTML escaping
- ✅ No server-side storage
- ✅ OAuth flow best practices

**Recommended**: Save your Groq key in a password manager and paste it each session.

---

## 📖 Usage Example

### **Book → Decision Workflow**

1. **Analyze a book**
   - Go to "Book Intel"
   - Enter: *"Thinking in Systems"*
   - Click "Analyse →"

2. **Feed mental models to twin**
   - Click "⟶ Feed to Twin"
   - Models now loaded in Decision Engine

3. **Make a decision**
   - Go to "Decision Engine"
   - Decision: *"Should I pivot my startup to infrastructure tooling?"*
   - Add context and stakes

4. **Get verdict**
   - Twin applies loaded frameworks
   - Clear verdict + reasoning + risks + next move

### **Keyboard Shortcuts**

| Key | Action |
|-----|--------|
| `Alt + 1-5` | Switch thinking modes |
| `/` | Focus input |
| `↑` | Recall last message |
| `Enter` | Send message |
| `Shift + Enter` | New line |

---

## 🎯 Use Cases

- **Startup founders**: Decision-making with mental models from business books
- **Researchers**: Synthesize ideas from multiple sources
- **Writers**: Brainstorm angles and critique drafts
- **Students**: Apply frameworks to study material
- **Product managers**: Roadmap planning from conversations
- **Anyone**: Building a personal knowledge base that compounds

---

## 🛠️ Customization

### **Change Default Domains**
```javascript
// Line ~78
const DEFAULT_DOMAINS = [
  'Your Domain 1',
  'Your Domain 2',
  'Your Domain 3'
];
```

### **Add a New Thinking Mode**
```javascript
// Line ~95
const MODES = {
  yourmode: {
    desc: 'Description for UI',
    tag: 'TAG',
    cls: 'css-class'
  }
};
```

### **Customize Persona**
```javascript
// buildPersona() function (~line 475)
// Modify traits, communication style, domain expertise
```

---

## 🤝 Contributing

Contributions welcome! Here's how:

1. Fork the repo
2. Make your changes to `index.html`
3. Test thoroughly (one file = changes affect everything)
4. Submit a PR with clear description

### **Ideas for Contributors**
- [ ] Export/import persona profiles
- [ ] Dark/light mode toggle
- [ ] Voice input/output
- [ ] Collaborative sessions
- [ ] Mobile app wrapper
- [ ] Browser extension
- [ ] Claude/GPT support
- [ ] Local LLM option

---

## 🐛 Troubleshooting

| Issue | Solution |
|-------|----------|
| **"Drive session expired"** | Refresh page and reconnect (tokens expire after ~1 hour) |
| **"Rate limited"** | Groq free tier: 30 req/min. App retries automatically. |
| **OAuth errors** | Check authorized origins in Google Console match your domain |
| **Drive sync failed** | App retries 3x with exponential backoff. Check internet/quota. |

---

## 📊 Performance

- **Load time**: < 1s (single file)
- **First interaction**: Instant (no framework overhead)
- **Drive sync**: < 2s (with retry)
- **LLM latency**: 0.5-2s (Groq is fast)

---

## 📜 License

MIT License - do whatever you want with this.

---

## 🌟 Acknowledgments

- **Groq**: Blazing fast LLM inference
- **Google Drive API**: Dead-simple cloud storage
- **Llama 3.3**: Incredible reasoning at 70B
- **Open source community**: For inspiring single-file apps

---

<div align="center">

**Built with 🧠 by a solo developer**

⭐ Star this repo if you find it useful!

</div>
```

---

## Quick Setup Checklist

After pasting the README, also add these files:

### **LICENSE** (MIT)
```
MIT License

Copyright (c) 2025 [Your Name]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

### **.gitignore**
```
# Nothing needed - it's a single HTML file!
# But if you add dev files:
.DS_Store
*.log
node_modules/
.env
