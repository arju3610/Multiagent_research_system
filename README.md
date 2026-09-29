# ResearchMind: Multi-Agent Research System

ResearchMind is a Streamlit app that turns a topic into a structured research report. Its LangChain-based workflow uses a Groq-hosted language model and Tavily web search.

## How It Works

1. **Search agent:** finds recent web information about the topic.
2. **Reader agent:** selects a relevant result and extracts additional content from its page.
3. **Writer:** creates a report with an introduction, findings, conclusion, and source URLs.
4. **Critic:** reviews the report and returns a score, strengths, and areas to improve.

The app displays the search results, extracted content, final report, and critique. The report can be downloaded as a Markdown file.

## Requirements

- Python 3.10 or newer
- A [Groq API key](https://console.groq.com/keys)
- A [Tavily API key](https://app.tavily.com/home)

API usage may incur charges or be subject to provider rate limits.

## Run Locally

From the project directory, create and activate a virtual environment, then install the dependencies:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
```

Create a `.env` file in the project directory with your API keys:

```text
GROQ_API_KEY=your_groq_api_key
TAVILY_API_KEY=your_tavily_api_key
```

The `.env` file is excluded from Git. Start the app with:

```powershell
streamlit run app.py
```

## Deploy on Streamlit Community Cloud

1. Push this repository to GitHub.
2. Sign in to [Streamlit Community Cloud](https://share.streamlit.io/) with GitHub and select **Create app**.
3. Select this repository, the `main` branch, and `app.py` as the main file.
4. Open the app's **Advanced settings** and add these secrets:

	```toml
	GROQ_API_KEY = "your_groq_api_key"
	TAVILY_API_KEY = "your_tavily_api_key"
	```

5. Select **Deploy**. Streamlit installs packages from `requirements.txt`; the app uses these top-level secrets as environment variables.

Never commit API keys or put them in source code. If you change the app or dependencies later, push the changes to GitHub and Streamlit Community Cloud will redeploy the app.
