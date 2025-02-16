# 📊 SentimentStream: Real-Time Stock Market Sentiment Analysis

## 🔍 Project Overview
SentimentStream is a **real-time stock market sentiment analysis pipeline** using **Kafka and Python**.  
It fetches live stock-related sentiment data, processes it, and dynamically **visualizes** trends using Matplotlib.

## 🚀 Features
- **Kafka Producer** → Streams real-time stock sentiment data (JSON format)
- **Kafka Consumer** → Reads, processes, and stores sentiment data in SQLite
- **Dynamic Visualizations**:
  - 📉 **Smoothed Sentiment Trend Chart** (Moving Average)
  - 📊 **Sentiment Distribution Bar Chart**
- **Live Streaming & Analytics**
- **Modular & Scalable Design**

---

## 📂 Project Structure
SentimentStream/ │── 📂 consumers/ # Kafka Consumer Folder │ ├── consumer_monsuru.py # Reads, processes, and visualizes sentiment data │── 📂 producers/ # Kafka Producer Folder │ ├── producer_monsuru.py # Fetches and streams stock sentiment data │── 📂 utils/ # Utility Functions │ ├── db_utils.py # (Optional) Handles database operations │── 📂 images/ # Stores project images │ ├── sentiment_chart.png # Screenshot of visualization │── 📂 data/ # Stores raw or processed data (optional) │── .gitignore # Specifies files to ignore in Git tracking │── .env # Stores Kafka and DB settings (DO NOT commit) │── .env.example # Example environment variables │── requirements.txt # List of dependencies │── README.md # Project documentation │── sentiment_stream.sqlite # SQLite database file

## 🔍 About the Consumer

The **custom consumer (`consumer_monsuru.py`)** reads stock sentiment data from the **Kafka topic (`sentiment_stream`)**, processes it, and visualizes the insights dynamically.  

### ✅ Features:
- **Stores Sentiment Data in SQLite** → Keeps a record of sentiment trends.
- **Sentiment Trend Chart** → Uses a **Moving Average** to track stock sentiment over time.
- **Sentiment Distribution Bar Chart** → Shows real-time sentiment scores for stocks (**Green = Positive, Red = Negative**).
- **Live Updates** → Automatically updates as new messages arrive from Kafka.

This allows for **real-time stock sentiment monitoring and analysis**. 🚀


---

## ⚙️ Setup Instructions

### 1️⃣ **Clone the Repository**
```sh
git clone https://github.com/don4ye/SentimentStream.git
cd SentimentStream

## Set Up Virtual Environment
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate
pip install -r requirements.txt

## Start Kafka & Zookeeper
zookeeper-server-start.sh config/zookeeper.properties  
kafka-server-start.sh config/server.properties  

## Run the Producer
python -m producers.producer_monsuru

## Run the Consumer
python -m consumers.consumer_monsuru
