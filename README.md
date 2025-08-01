# 💹 LLM-SMC Trading Assistant

A full-stack, AI-powered trading assistant that integrates **Smart Money Concepts (SMC)**, **real-time market data**, **multimodal large language models (LLMs)**, and **chart image analysis** to automate trading decisions and execution.

Built for traders, data scientists, and AI engineers exploring the intersection of finance, machine learning, and LLMs — all running locally without cloud dependencies.

---

## 🚀 Key Features

- **📊 SMC Strategy Detection**  
  Automatically identifies CHoCH, BOS, FVGs, Order Blocks, Liquidity Sweeps, and Premium/Discount zones.

- **🧠 Multimodal LLM Reasoning**  
  Combines raw OHLC data with candlestick chart images, processed via [LLaVA](https://llava.ai) and [Ollama](https://ollama.com), for human-like trade decision-making.

- **📈 Real-Time Market Integration**  
  Pulls live data and executes orders using [cTrader Open API](https://connect.spotware.com/).

- **⚙️ Trade Execution Engine**  
  Supports market and pending orders with stop-loss/take-profit (SL/TP) logic and error handling.

- **🌐 Interactive Frontend**  
  Lightweight HTML + Plotly chart interface for monitoring, AI analysis, and manual trade submission.

- **🛠️ Dockerized + Offline-Ready**  
  Run everything locally using Docker and Ollama—no OpenAI or cloud accounts required.

---

## 📦 Project Structure

```bash
├── backend/
│   ├── app.py                # FastAPI server
│   ├── llm_analyzer.py       # Chart + SMC + LLaVA analysis logic
│   ├── ctrader_client.py     # cTrader Open API integration
│   ├── smc_features.py       # SMC pattern extraction logic
│   ├── data_fetcher.py       # Candle data from cTrader
│   ├── indicators.py         # Technical indicators logic
│   ├── Dockerfile
│   └── .env.example
├── static/                  # JS/CSS assets (if needed)
├── templates/index.html     # Lightweight frontend with Plotly chart
├── requirements.txt
├── docker-compose.yml
└── images/

```

---

## 🛠️ Setup Instructions

### 1. Requirements

- Python 3.11+
- Docker + Docker Compose
- [Ollama](https://ollama.com/download) installed locally with models like `llava`, `llama3`, or `phi3`
- Chrome is required by Plotly Kaleido (auto-installed in Docker)

### 2. Run with Docker

```bash
git clone https://github.com/yourname/llm-smc-trading-assistant.git
cd llm-smc-trading-assistant

# Build and launch the app
docker compose up --build

# Access it at: http://localhost:4000
```

---

## 🧠 How It Works


1. The user selects a symbol, timeframe, and indicators via the frontend.
2. The backend fetches candles from cTrader and renders a Plotly chart.
3. SMC features are extracted programmatically from OHLC data.
4. The chart image + raw features are sent to a multimodal LLM prompt.
5. The LLM returns a JSON signal: {"signal": "long", "sl": ..., "tp": ..., "confidence": ...}.
6. You can place the trade directly or review the decision reasoning in the UI.
7. Optionally, you can submit the trade via the `/api/execute_trade` endpoint.

---

## 📊 Example LLM Prompt

```text
You are a professional Smart Money Concepts (SMC) trading analyst.

Analyze the chart and OHLC for EURUSD (M15):
- Market structure (CHoCH, BOS)
- Liquidity sweeps or grabs
- Fair Value Gaps (FVG)
- Order Blocks (OBs)
- Premium/Discount zones

Suggest: signal, stop loss (sl), take profit (tp), and confidence.
Return JSON only.
```

---

## 🔮 Future Improvements

- Add multi-symbol scanning and filtering
- HTF/MTF bias integration
- Streamlit/Gradio UI
- Backtesting and performance stats
- Plugin version for ChatGPT or TradingView

---

## 📄 License

MIT License


---

## 🙌 Acknowledgements

- [Ollama](https://ollama.com)
- [LLaVA](https://llava.ai)
- [Plotly](https://plotly.com)
- [cTrader Open API](https://connect.spotware.com)
- [LangChain](https://www.langchain.com) *(optional/future)*

---

## ⚠️ Disclaimer
This project is intended for educational and research purposes only.
It should not be used for live trading with real money.
Always test thoroughly with demo accounts and understand that trading involves significant financial risk.
The authors assume no liability for financial loss or damages.



---

## 📷 Live Example Screenshot

The assistant analyzes both the **candlestick chart** and **recent OHLC data** to generate a trading signal using **Smart Money Concepts (SMC)**. It then returns:

- 📍 Entry signal (`long` or `short`)
- ⛔ Stop Loss (SL)
- 🎯 Take Profit (TP)
- 📈 Confidence Score
- 🧠 Reasoning based on SMC features like CHOCH, OBs, FVG, trend, liquidity sweeps, and premium/discount zones

The frontend dashboard includes:

- 🔽 Dropdowns to select **symbol** and **timeframe**
- 📋 Indicator checklist (e.g., SMA, EMA, VWAP, Bollinger Bands)
- 🧠 AI analysis trigger (`Run AI Analysis`)
- 🟢 Trade executor (`Place Trade`)
- 🪄 Live plot (candlestick chart + indicators)
- 💬 LLM JSON output and human-readable explanation

### 📸 Dashboard Example

![Dashboard Screenshot](images/dashboard-chart-tools1.png)
![Dashboard Screenshot](images/dashboard-chart-tools2.png)


---

