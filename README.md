# 🤖 CrewAI Financial Researcher

> An intelligent multi-agent system powered by [CrewAI](https://crewai.com) that researches companies, analyzes market data, and generates comprehensive financial reports using Google's Gemini AI and real-time web search.

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://www.python.org/downloads/)
[![CrewAI](https://img.shields.io/badge/CrewAI-1.7.2-orange.svg)](https://github.com/joaomdmoura/crewai)

## 📋 Overview

This project leverages a multi-agent AI system to conduct deep financial research on any company. Two specialized AI agents collaborate sequentially:

1. **Senior Financial Researcher** - Gathers real-time data using Serper (Google Search API)
2. **Market Analyst & Report Writer** - Analyzes findings and produces a professional markdown report

## ✨ Features

- 🔍 **Real-time Web Search** via Serper API for current financial data, news, and market insights
- 🤖 **Dual-Agent System** with specialized roles for research and analysis
- 📊 **Comprehensive Reports** covering company status, historical performance, challenges, opportunities, and future outlook
- 🧠 **Powered by Google Gemini** (gemini-2.5-flash-lite) for fast, intelligent responses
- 🛠️ **Customizable** agents, tasks, and tools via YAML configuration
- 📁 **Organized Output** with reports saved to `output/report.md`

## 🚀 Quick Start

### Prerequisites

- Python **3.10 - 3.13** installed
- [Gemini API Key](https://aistudio.google.com/app/apikey) (free tier available)
- [Serper API Key](https://serper.dev/) (free tier: 2,500 searches/month)

### Installation

1. **Clone the repository:**
```bash
git clone https://github.com/revant-999/CrewaiFinancialResearcher.git
cd CrewaiFinancialResearcher
```

2. **Install dependencies:**
```bash
pip install crewai[google-genai,tools]==1.7.2 crewai-tools
```

3. **Set up environment variables:**
   
   Copy the example file and add your API keys:
```bash
cp .env.example .env
```

Edit `.env` and add your keys:
```env
GEMINI_API_KEY=your_actual_gemini_api_key
SERPER_API_KEY=your_actual_serper_api_key
```

### Usage

Run the financial researcher crew:

```bash
crewai run
```

When prompted, enter a company name (e.g., `Tesla`, `Apple`, `Microsoft`). The system will:
1. Research the company using web search
2. Analyze all gathered data
3. Generate a comprehensive report in `output/report.md`

**Example:**
```bash
$ crewai run
Enter company name: Tesla
# agents start researching...
```

## 📁 Project Structure

```
financial_researcher/
├── .env                          # API keys (not tracked by git)
├── .env.example                  # Template for environment variables
├── .gitignore                    # Ignores sensitive files
├── pyproject.toml                # Project dependencies
├── README.md                     # This file
├── knowledge/
│   └── user_preference.txt       # Optional context for agents
├── output/
│   ├── .gitkeep                  # Keeps output folder in git
│   └── report.md                 # Generated financial reports
├── src/financial_researcher/
│   ├── __init__.py
│   ├── crew.py                   # Agent and crew definitions
│   ├── main.py                   # Entry point
│   ├── config/
│   │   ├── agents.yaml           # Agent roles, goals, backstories
│   │   └── tasks.yaml            # Task definitions and prompts
│   └── tools/
│       ├── __init__.py
│       └── custom_tool.py        # Template for custom tools
└── tests/
```

## 🛠️ Configuration

### Agents (`src/financial_researcher/config/agents.yaml`)

Two agents are configured:

- **researcher**: Senior Financial Researcher
  - Uses `SerperDevTool` for Google search
  - Gathers company data, news, challenges, opportunities
  
- **analyst**: Market Analyst & Report Writer
  - Consumes research findings
  - Creates structured markdown reports

### Tasks (`src/financial_researcher/config/tasks.yaml`)

- **research_task**: Multi-step research with web searches
- **analysis_task**: Report generation with executive summary, financial analysis, and outlook

### Customization

You can easily customize:

1. **Agents**: Edit `config/agents.yaml` to change roles, goals, or LLM models
2. **Tasks**: Modify `config/tasks.yaml` to adjust prompts and output formats
3. **Tools**: Add custom tools in `tools/` directory (e.g., database connectors, APIs)
4. **Inputs**: Update `main.py` to accept different input parameters

## 🤖 Technologies Used

- **[CrewAI](https://crewai.com)** - Multi-agent orchestration framework
- **[Google Gemini](https://ai.google.dev/)** - LLM (gemini-2.5-flash-lite)
- **[Serper](https://serper.dev/)** - Google Search API for real-time data
- **[Python 3.11+](https://www.python.org/)** - Core language
- **[Pydantic](https://docs.pydantic.dev/)** - Data validation

## 📊 Sample Output

The generated report includes:

- **Executive Summary** - High-level overview and key takeaways
- **Current Company Status** - Financial health, market cap, profitability metrics
- **Historical Performance** - Revenue trends, stock performance, growth trajectory
- **Challenges & Opportunities** - SWOT-style analysis with market dynamics
- **Recent News & Events** - Latest developments, regulatory actions, product launches
- **Future Outlook** - Analyst projections, growth drivers, strategic vision

Reports are saved as markdown in `output/report.md` with proper formatting, sections, and bullet points.

## 🔐 Security

- ✅ API keys stored in `.env` (git-ignored)
- ✅ `.env.example` provided for setup guidance
- ✅ `.gitignore` configured to exclude sensitive files
- ⚠️ **Never commit `.env` to version control**

## 🤝 Contributing

Contributions are welcome! To contribute:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

##  Acknowledgments

- [CrewAI](https://github.com/joaomdmoura/crewai) for the amazing multi-agent framework
- [Google AI Studio](https://aistudio.google.com/) for Gemini API access
- [Serper.dev](https://serper.dev/) for real-time search capabilities

## 📞 Support

For questions or issues:

- **CrewAI Documentation**: [docs.crewai.com](https://docs.crewai.com)
- **GitHub Issues**: [Create an issue](https://github.com/revant-999/CrewaiFinancialResearcher/issues)
- **CrewAI Discord**: [Join here](https://discord.com/invite/X4JWnZnxPb)

---

**Made with ❤️ using CrewAI**
