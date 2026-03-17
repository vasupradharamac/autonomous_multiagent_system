# Autonomous Multi-Agent System 🤖

An end-to-end autonomous AI pipeline that uses multiple specialized LLM agents to scan, process, and price products in real time — built as part of the [LLM Engineering course](https://github.com/ed-donner/llm_engineering) by Ed Donner.

---

## What It Does

This system orchestrates a team of AI agents that collaboratively:
- Scan the web and RSS feeds for product deals
- Preprocess and clean raw product data
- Predict fair market prices using frontier LLMs
- Improve accuracy with RAG (Retrieval-Augmented Generation)
- Combine predictions via an ensemble approach

---

## Architecture

Web / RSS Feeds
↓
ScanningAgent ← Discovers deals from the web
↓
PreprocessorAgent ← Cleans and structures product data
↓
┌─────────────────────────────┐
│ FrontierAgent │ ← GPT-4 / Claude price estimation
│ RAG Agent │ ← Vector DB similarity retrieval
│ EnsembleAgent │ ← Combines all predictions
└─────────────────────────────┘
↓
Final Price Prediction + Deal Alert

## Project Structure

autonomous_multiagent_system/
├── agents/
│ ├── preprocessor.py # Cleans raw product data via LiteLLM
│ ├── frontier_agent.py # Calls GPT-4/Claude for price prediction
│ ├── rag_agent.py # Vector store retrieval agent
│ ├── ensemble_agent.py # Combines agent outputs
│ └── scanning_agent.py # RSS/web deal scanner
├── day1.ipynb # Modal setup + first agent
├── day2.ipynb # RAG + Frontier + Ensemble agents
├── day3.ipynb # ScanningAgent (live deal discovery)
├── day4.ipynb # Full pipeline — "The Price is Right"
├── day5.ipynb # Deployment + productionized UI
├── .env.example # API key template
├── .gitignore
└── README.md


---

## ⚙️ Setup & Installation

### Prerequisites
- Python 3.11+
- [uv](https://github.com/astral-sh/uv) package manager
- [Modal](https://modal.com) account
- API keys for OpenAI, Anthropic, HuggingFace

### 1. Clone the repo
```bash
git clone https://github.com/vasupradharamac/autonomous_multiagent_system.git
cd autonomous_multiagent_system
```
### 2. Create and activate virtual environment
```bash
uv venv
source .venv/bin/activate
```

### 3. Install dependencies
```bash
uv pip install -r requirements.txt
```

### Edit .env and fill in your keys:
OPENAI_API_KEY=your_openai_key
ANTHROPIC_API_KEY=your_anthropic_key
HF_TOKEN=your_huggingface_token
MODAL_TOKEN_ID=your_modal_token

| Tool             | Purpose                                   |
| ---------------- | ----------------------------------------- |
| Modal            | Serverless cloud execution of agents      |
| LiteLLM          | Unified interface for GPT-4, Claude, etc. |
| OpenAI GPT-4     | Frontier LLM for price prediction         |
| Anthropic Claude | Alternative frontier LLM                  |
| Vector DB        | Product embeddings for RAG retrieval      |
| Jupyter          | Interactive notebook environment          |

📌 Credits
Based on the Week 8 project from the LLM Engineering course by Ed Donner.
