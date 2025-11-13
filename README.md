
# 🚀 AutoQA.AI
### AI-Powered Autonomous Testing Framework  
**Playwright + Google ADK + RAG + DOM Diff + Real-Time Chat UI**  
Created by **Pramod Dutta (The Testing Academy)**

---

## 📌 What This Project Is

This is a **fully autonomous AI QA testing agent** that converts **plain English instructions** into **real browser automation**, using:

- **Python**
- **Playwright**
- **Google ADK (Agent Developer Kit)**
- **Retrieval-Augmented Generation (RAG)**
- **DOM Comparison Engine**
- **Vector DB (Chroma)**
- **Real-time Chat UI (React + TailwindCSS)**
- **WebSocket Streaming**

### 🧠 Example  
You type:

> “Open app.vwo.com → attempt invalid login → verify error message.”

The agent:

1. Understands your text  
2. Plans each browser action  
3. Runs steps in Playwright  
4. Captures DOM after each step  
5. Uses RAG + DOM diff + pattern matching to verify  
6. Streams everything in a chat-like interface  

No scripts.  
No locators.  
No coding.  

This is the **future of automation testing**.

---

## 🎯 Why This Project Exists

Traditional test automation is:

❌ Slow  
❌ Fragile  
❌ Code-heavy  
❌ Hard to maintain  

This framework brings:

✔ **Scriptless testing**  
✔ **Self-verifying steps**  
✔ **AI-driven test planning**  
✔ **DOM-intelligent validation**  
✔ **Fully conversational automation**  

---

# 🖼 Architecture Diagram

```

```
            ┌──────────────────────────────┐
            │          Chat UI             │
            │  (React + Tailwind + WS)     │
            └──────────────┬───────────────┘
                           │ instruction
                           ▼
            ┌──────────────────────────────┐
            │        FastAPI Backend        │
            │      WebSocket Streaming      │
            └──────────────┬───────────────┘
                           │ passes request
                           ▼
            ┌──────────────────────────────┐
            │        ADK Agent Core         │
            │  - LLM Reasoning (Gemini)     │
            │  - Step Planner               │
            │  - Tool Orchestration         │
            └──────────────┬───────────────┘
                           │ generated steps
                           ▼
    ┌──────────────────────────────┐      ┌──────────────────────────────┐
    │      Playwright Executor     │ ---> │         DOM Capture          │
    │  - Real browser automation   │      │  - DOM HTML                  │
    │  - Click, Type, Navigate     │      │  - Element snapshot          │
    └──────────────┬──────────────┘      └──────────────┬───────────────┘
                   │ DOM                       │
                   ▼                           ▼
    ┌──────────────────────────────┐      ┌──────────────────────────────┐
    │         RAG Verifier         │      │         DOM Diff Engine      │
    │  - Chroma Vector DB          │      │  - Pattern matching          │
    │  - Embedding comparison      │      │  - Error detection           │
    └──────────────┬──────────────┘      └──────────────┬───────────────┘
                   │ results                    │ diff
                   ▼                           ▼
            ┌──────────────────────────────┐
            │        Report Engine         │
            │   (JSON / Allure-ready)      │
            └──────────────────────────────┘
```

```

---

# 📁 Project Structure

```

adk-playwright-agent/
├── README.md
├── requirements.txt
├── Dockerfile
├── .env.example
│
├── app/
│   ├── main.py                      # FastAPI + WebSocket server
│   │
│   ├── agent/
│   │   ├── agent_core.py            # ADK-style orchestrator
│   │   ├── planner.py               # Natural language → Steps
│   │   ├── tools.py                 # Tool bindings (click, type, etc.)
│   │   └── **init**.py
│   │
│   ├── executor/
│   │   ├── playwright_executor.py   # Real browser automation
│   │   ├── dom_capture.py           # DOM snapshot utilities
│   │   └── **init**.py
│   │
│   ├── verifier/
│   │   ├── dom_compare.py           # DOM diff + embeddings verify
│   │   ├── rag_store.py             # Chroma vector DB
│   │   └── **init**.py
│   │
│   ├── reporting/
│   │   ├── report.py                # JSON test report
│   │   └── **init**.py
│   │
│   └── utils/
│       ├── helpers.py               # Shared helpers
│       └── **init**.py
│
├── frontend/
│   ├── index.html
│   ├── vite.config.js
│   ├── package.json
│   ├── tailwind.config.js
│   └── src/
│       ├── App.jsx
│       ├── main.jsx
│       ├── components/
│       │   ├── ChatMessage.jsx
│       │   └── InputBox.jsx
│
└── examples/
└── invalid_login.json

```

---

# 🛠 How It Works

### **1️⃣ User sends a command**  
Example:
```

"Open app.vwo.com and verify invalid login."

```

### **2️⃣ LLM plans steps**  
✓ navigate  
✓ type username  
✓ type password  
✓ click login  
✓ assert error message  

### **3️⃣ Playwright executes steps**  
- Opens browser  
- Performs actions  
- Captures DOM  

### **4️⃣ DOM Verifier checks**  
- Error text  
- Similarity to past error pages  
- DOM structural differences  
- Embedding comparison  

### **5️⃣ Chat UI shows real-time updates**  
Every step streams live:
```

▶ Step started: navigate
✓ Step completed
▶ Verifying DOM...

````

### **6️⃣ Report is generated**

---

# ▶️ How to Run Locally (Complete Guide)

### **1. Clone repo**
```bash
git clone https://github.com/yourname/adk-playwright-agent
cd adk-playwright-agent
````

---

### **2. Install backend**

```bash
pip install -r requirements.txt
```

---

### **3. Install Playwright browsers**

```bash
playwright install
```

---

### **4. Create `.env`**

```env
LLM_PROVIDER=ollama
OLLAMA_HOST=http://localhost:11434
CHROMA_PERSIST_DIR=./chroma
PLAYWRIGHT_HEADLESS=false
```

---

### **5. Run backend**

```bash
uvicorn app.main:app --reload --port 8080
```

---

### **6. Start frontend**

```bash
cd frontend
npm install
npm run dev
```

Open browser:
👉 [http://localhost:5173](http://localhost:5173)

---

# 📸 Screenshots (Add later)

```
/assets/chat-ui.png
/assets/test-run.png
/assets/dom-verify.png
```

---

# 🚧 Future Roadmap

### **Phase 1 — Advanced Verifications**

* Screenshot pixel diff
* Automatic locator healing
* XHR/Network validation

### **Phase 2 — Multi-Agent Architecture**

* Planner agent
* Locator agent
* Execution agent
* Verification agent

### **Phase 3 — Test Recording → NL Test Generation**

* Auto-generate test cases
* Self-healing flows

### **Phase 4 — Visual Test Reports**

* Allure integration
* Visual diffs
* Failure heatmaps

### **Phase 5 — SaaS Platform**

* Cloud dashboard
* Test run history
* Team collaboration
* Webhooks + API keys

---

# 🤝 Contributing

Pull Requests are welcome!

* Add more agents
* Improve DOM verification
* Add new UI features
* Extend RAG pipeline
* Improve planner

---

# 📜 License

MIT License.

---

# ⭐ Credits

Built with ❤️ by **Pramod Dutta – The Testing Academy**
