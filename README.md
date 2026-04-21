# 🤖 AI Agent with Web Search

A conversational AI agent built with **LangGraph** that can search the web in real-time to answer questions beyond its training data. Powered by **Groq (LLaMA 3.1)** and **Tavily Search**.

---

## 🧠 How It Works

The agent uses a **ReAct (Reasoning + Acting)** loop:
1. User asks a question
2. Agent decides whether to answer directly or search the web
3. If needed, it calls the Tavily search tool
4. It reasons over the results and returns a final answer

---

## 🛠️ Tech Stack

| Component | Tool |
|-----------|------|
| LLM | Groq — `llama-3.1-8b-instant` |
| Search Tool | Tavily Search API |
| Agent Framework | LangGraph + LangChain |
| Runtime | Google Colab |

---

## 📦 Installation

```bash
pip install langchain langgraph langchain-groq langchain-community langchainhub
```

---

## 🔑 API Keys Setup

This project uses **Colab Secrets** to manage API keys securely (never hardcoded).

In Google Colab, go to the 🔑 **Secrets** tab (left sidebar) and add:
- `GROQ_API_KEY` → Get from [console.groq.com](https://console.groq.com)
- `TAVILY_API_KEY` → Get from [tavily.com](https://tavily.com)

```python
from google.colab import userdata
GROQ_KEY = userdata.get('GROQ_API_KEY')
SEARCH_API_KEY = userdata.get('TAVILY_API_KEY')
```

---

## 🚀 Usage

```python
response = agent_executor.invoke({
    "messages": [("user", "Who is the current deputy CM of Andhra Pradesh?")]
})
print(response["messages"][-1].content)
```

**Example Output:**
```
The current deputy chief minister of Andhra Pradesh is Konidala Pawan Kalyan.
```

---

## 📁 Project Structure

```
├── Untitled0.ipynb   # Main notebook with agent implementation
└── README.md
```

---

## 💡 Key Concepts Used

- **ReAct Agent** — LLM reasons and acts in a loop
- **Tool Calling** — Agent decides when to invoke search
- **Real-time Web Search** — Answers questions beyond LLM's training cutoff

---

## 📌 Note

> LangGraph's `create_react_agent` is deprecated in V1.0. Future versions should use `from langchain.agents import create_agent`.

---

## 👩‍💻 Author

**Yashu** — AI Engineer Intern | B.Tech CSE @ Veltech University  
Building in public 🚀
