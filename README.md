<div align="center">

# 🎮 Game Crew Agent

**A multi-agent AI system that writes playable games from a single sentence.**

Describe a game idea in plain English — a team of AI agents designs it, codes it in Pygame, and reviews it before handing you a ready-to-run file.

[![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)](https://www.python.org/)
[![CrewAI](https://img.shields.io/badge/Framework-CrewAI-orange.svg)](https://www.crewai.com/)
[![Streamlit](https://img.shields.io/badge/Demo-Streamlit-FF4B4B.svg)](https://streamlit.io/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

[**🚀 Live Demo**](#) &nbsp;•&nbsp; [**📓 Original Notebook**](Copy_of_game_crew.ipynb) &nbsp;•&nbsp; [**🎥 Video Walkthrough**](#)

</div>

---

## What it does

Most "AI game generator" demos are a single prompt-to-code call. **Game Crew Agent** instead models how a real small studio works: three specialized agents hand work off to each other, each one focused on a single responsibility, with the later agents grounded in the earlier agents' output.

| Agent | Role | Output |
|---|---|---|
| 🎨 **Creative Game Designer** | Expands a rough idea into a real design, with web search for inspiration | Game Design Document |
| 💻 **Senior Python Game Developer** | Implements the design as a working Pygame script | First-draft `.py` game |
| 🔍 **QA Engineer & Reviewer** | Checks the code for bugs, missing features, and playability | Final, polished `.py` game |
"a game where you dodge falling meteors"
                                   │
                                   ▼
                    ┌─────────────────────────────┐
                    │   🎨 Game Designer Agent     │
                    │   (+ web search for ideas)   │
                    └──────────────┬───────────────┘
                                   │  Game Design Document
                                   ▼
                    ┌─────────────────────────────┐
                    │  💻 Python Developer Agent   │
                    └──────────────┬───────────────┘
                                   │  First-draft game.py
                                   ▼
                    ┌─────────────────────────────┐
                    │   🔍 QA / Reviewer Agent     │
                    └──────────────┬───────────────┘
                                   │
                                   ▼
                      ✅ Final, runnable game.py
                      Optionally, the original notebook takes this one step further: it builds the finished game for the **browser** using `pygbag` (Pygame → WASM) and exposes it through an `ngrok` tunnel, so it can be played instantly with no local install.

## ✨ Features

- 🤖 **Sequential multi-agent orchestration** with CrewAI — each agent's output becomes the next agent's grounded context
- 🔍 **Web-search-augmented design** via Serper, so concepts aren't generated in a vacuum
- 💻 **Complete, runnable code generation** — not snippets; a full `python game.py` you can play immediately
- 🧪 **Built-in QA pass** — a dedicated review step catches bugs and missing features before the code ships
- 🌐 **Browser build pipeline** (notebook) — Pygame → WASM via `pygbag`, tunneled live with `ngrok`
- 🖥️ **Streamlit demo UI** — type an idea, watch each agent's output, download the final game

## 🛠️ Tech Stack

- **Orchestration:** [CrewAI](https://www.crewai.com/) (sequential multi-agent process)
- **LLM:** Google Gemini 2.5 Flash
- **Search tool:** Serper (web search grounding for the Designer agent)
- **Game engine:** Pygame
- **Browser build:** pygbag (Pygame-to-WASM) + ngrok (public tunnel)
- **Demo UI:** Streamlit

## 🚀 Getting Started

### 1. Clone and install

```bash
git clone https://github.com/hemapranay/game_crew_agent.git
cd game_crew_agent
pip install -r requirements.txt
```

### 2. Get API keys

- **Gemini** (required, free): [aistudio.google.com/app/apikey](https://aistudio.google.com/app/apikey)
- **Serper** (optional, free tier): [serper.dev](https://serper.dev) — enables web search for the Designer agent

### 3. Run the demo

```bash
streamlit run app.py
```

Enter your API key in the sidebar, describe a game idea, and click **Generate Game**. You'll get a design document, the final reviewed code, and a download button for the `.py` file.

### Alternative: run the original notebook

`Copy_of_game_crew.ipynb` runs the same agent pipeline in Colab and additionally builds the result into a browser-playable game via `pygbag` + `ngrok`.

## 📁 Project Structure
## 🗺️ Roadmap

- [ ] One-click browser build from the Streamlit app (integrate the `pygbag` step)
- [ ] Multi-turn iteration — refine a generated game with follow-up prompts
- [ ] Support additional engines beyond Pygame
- [ ] Dockerized deployment
- [ ] Gallery of example generated games

## 📄 License

MIT — see [LICENSE](LICENSE) for details.

---

<div align="center">
Built by <a href="https://github.com/hemapranay">Hemapranay</a> · feedback and PRs welcome
</div>
