# ⚖️ Debate Crew - Multi-Agent Debate & Judging System

A multi-agent AI debate system built with CrewAI that generates arguments **for** and **against** a motion, then uses a judge agent to decide which side is more convincing.

![CrewAI](https://img.shields.io/badge/CrewAI-000000?style=for-the-badge)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)

## ✨ Features

- **Two-Agent Debate Loop**: Debater agent argues both sides; judge agent evaluates
- **Structured Workflow**: Propose → Oppose → Decide (sequential)
- **Markdown Outputs**: Saves each stage to separate `.md` files
- **Config-Driven**: Agents and tasks defined in YAML for easy customization

## 🏗️ Architecture

The system uses a **CrewAI** framework with two specialized agents:

- **Debater Agent**
  - Generates a convincing argument **for** the motion
  - Generates a convincing argument **against** the motion

- **Judge Agent**
  - Reviews both arguments
  - Decides which side is more convincing and explains why

## 📋 Prerequisites

- Python >=3.10 <3.13
- [UV](https://docs.astral.sh/uv/) package manager
- LLM provider API keys (as configured in `src/debate/config/agents.yaml`)

## 🛠️ Installation

1. Install UV:
```bash
pip install uv
```

2. Install dependencies:
```bash
crewai install
```

3. Set required API keys (example):
```env
OPENAI_API_KEY=your_key_here
ANTHROPIC_API_KEY=your_key_here
```

## 🎯 Usage

Run from project root:
```bash
crewai run
```

The default motion is set in `src/debate/main.py` (e.g., "There needs to be strict laws to regulate LLMs").

## ⚙️ Configuration

- **Agents**: `src/debate/config/agents.yaml`
- **Tasks**: `src/debate/config/tasks.yaml`
- **Motion**: Edit `src/debate/main.py`
- **Crew workflow**: `src/debate/crew.py`

## 📁 Project Structure

```text
debate/
├── src/debate/
│   ├── main.py
│   ├── crew.py
│   ├── config/
│   │   ├── agents.yaml
│   │   └── tasks.yaml
│   └── tools/
├── knowledge/
├── output/
└── pyproject.toml
```

## 📤 Output

Generated debate artifacts are saved to:

- `output/propose.md`
- `output/oppose.md`
- `output/decide.md`

## 🛠️ Technologies

CrewAI, Python, OpenAI GPT-4o-mini, Anthropic Claude 3.5 Sonnet
