# 📈 Stock Market Recommendation System

A machine learning-based stock recommendation system that generates **BUY, HOLD, and SELL** signals by combining technical indicators with financial news sentiment analysis.

The system uses individual XGBoost models for multiple Indian stocks, processes historical stock market data, analyzes recent company-related news, and combines machine learning predictions with sentiment scores to generate recommendations.

## 🚀 Features

- BUY, HOLD, and SELL stock predictions
- Individual XGBoost model for each supported stock
- Technical indicator-based feature engineering
- Financial news sentiment analysis using NLTK VADER
- News headline retrieval using GNews
- Flask-based REST API
- Top 5 stock ranking endpoint
- Interactive web dashboard
- Separate trained models and feature scalers for each stock

## 🛠️ Tech Stack

- **Programming:** Python
- **Machine Learning:** XGBoost, Scikit-learn
- **Data Processing:** Pandas, NumPy
- **NLP:** NLTK VADER
- **News Retrieval:** GNews
- **Backend:** Flask, Flask-CORS
- **Frontend:** HTML, Tailwind CSS, JavaScript
- **Model Serialization:** Pickle, Joblib

## 📂 Project Structure

```text
Stock-Market-Recommendation-System/
│
├── app.py
├── main.py
├── news_sentiment.py
├── frontend.html
├── requirements.txt
├── README.md
├── .gitignore
│
├── models/
│   ├── *_model.pkl
│   └── *_scaler.pkl
│
└── stock_data/
    └── *.csv
```

## ⚙️ Installation and Setup

### 1. Clone the repository

```bash
git clone https://github.com/LohithHS12/Stock-Market-Recommendation-System.git
cd Stock-Market-Recommendation-System
```

### 2. Create a virtual environment

```bash
python -m venv venv
```

Activate it on Windows:

```powershell
venv\Scripts\activate
```

On Linux/macOS:

```bash
source venv/bin/activate
```

### 3. Install dependencies

```bash
python -m pip install -r requirements.txt
```

### 4. Download the NLTK VADER lexicon

```bash
python -c "import nltk; nltk.download('vader_lexicon')"
```

## 🧠 Model Training

To train individual stock prediction models:

```bash
python main.py
```

The training script:

- Loads historical stock datasets.
- Generates technical indicators.
- Creates BUY, HOLD, and SELL labels based on future price movements.
- Trains individual XGBoost classifiers.
- Fits feature scalers.
- Saves trained models and scalers in the `models/` directory.

**Note:** Training again may replace the existing model files.

## ▶️ Running the Application

### 1. Start the Flask backend

```bash
python app.py
```

The backend runs at:

```text
http://127.0.0.1:5000
```

### 2. Open the frontend

Open `frontend.html` in your web browser while the Flask backend is running.

The dashboard communicates with the local Flask API to display stock predictions, sentiment analysis, and rankings.

## 📌 API Endpoints

### 1. Stock Prediction

**Method:** POST

```text
/predict
```

Example request:

```json
{
    "symbol": "RELIANCE",
    "sentiment_method": "vader"
}
```

The API returns the stock symbol, final recommendation, machine learning prediction, news sentiment information, combined score, and explanation.

### 2. Top 5 Stock Recommendations

**Method:** GET

```text
/top5
```

Returns the five highest-ranked stocks based on the combined prediction score.

## 📊 Technical Indicators

The system generates the following features from historical stock data:

- Daily Returns
- 5-Day Returns
- 10-Day Moving Average
- 20-Day Moving Average
- Price vs Moving Average
- Volatility
- Relative Strength Index (RSI)
- Volume Moving Average
- Volume Ratio

## 📰 News Sentiment Analysis

The system retrieves recent company-related news headlines and uses NLTK VADER to calculate sentiment scores.

The sentiment score is combined with the machine learning prediction score.

### Final Score Calculation

```text
Final Score =
0.6 × ML Prediction Score
+
0.4 × News Sentiment Score
```

The combined score is used to determine the final BUY, HOLD, or SELL recommendation.

## 🤖 Machine Learning Approach

- XGBoost Classifier
- StandardScaler
- Technical Feature Engineering
- Multi-class Classification
- Individual models for supported stocks

The model predicts three classes:

- **BUY (2)**
- **HOLD (1)**
- **SELL (0)**

## 🔮 Future Improvements

- Live stock market price integration
- Portfolio tracking and management
- Risk analysis
- Improved model evaluation
- Additional sentiment analysis models
- Real-time market data integration

## 👨‍💻 Author

**Lohith H S**

B.E. Artificial Intelligence and Machine Learning

GitHub: [Lohith H S](https://github.com/LohithHS12)

---

**Disclaimer:** This project is developed for educational and experimental purposes. Its predictions are not financial advice or guaranteed indicators of future stock performance.