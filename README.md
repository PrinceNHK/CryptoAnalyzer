# 🚀 CryptoAnalyzer - Bitcoin Price Forecasting Platform

A comprehensive machine learning application for analyzing historical Bitcoin data and predicting future cryptocurrency prices using Facebook's Prophet time series model. Features an interactive Flask web dashboard for real-time forecasting and performance metrics visualization.

**🔗 Live Repository**: [GitHub - kanishka3125/Crypto_Analyzer](https://github.com/kanishka3125/Crypto_Analyzer)

---

## 🎯 Quick Links
- 📖 [Installation Guide](#-installation--setup)
- 🚀 [Quick Start](#quick-start)
- 📊 [Features](#-features)
- 📈 [Performance Metrics](#-performance-metrics-explained)
- ⚠️ [Important Disclaimer](#️-important-disclaimer)

---

## 📋 About This Project

CryptoAnalyzer is a production-ready cryptocurrency forecasting platform that leverages advanced time series analysis techniques to predict Bitcoin price movements. The application processes 14+ years of historical Bitcoin data (2010-2024) and provides accurate short-term and long-term price forecasts with confidence intervals.

**Key Highlights:**
- ✅ **Prophet ML Model**: Facebook's proven time series forecasting algorithm
- ✅ **Interactive Dashboard**: Real-time web interface for price analysis
- ✅ **Multiple Horizons**: 7, 30, 60, and 90-day prediction windows
- ✅ **Performance Metrics**: MAE, RMSE, MAPE, and Directional Accuracy
- ✅ **Data Visualization**: Historical trends, forecasts, and evaluation plots
- ✅ **Production Ready**: Flask-based scalable architecture

---

## 🗂️ Project Structure

```
CryptoAnalyzer/
│
├── 📄 Core Application Files
│   ├── app.py                      # Flask web server & routing
│   ├── data_loader.py              # Data loading & preprocessing pipeline
│   ├── prophet_model.py            # Prophet model training & forecasting
│   ├── model_evaluation.py         # Metrics calculation & evaluation
│   ├── eda.py                      # Exploratory data analysis
│   └── train_model.py              # Model training script
│
├── 📊 Data & Models
│   ├── bitcoin_2010-07-17_2024-05-23.csv  # Historical OHLCV data (5,059 days)
│   ├── model/
│   │   └── prophet_model.pkl       # Trained Prophet model (serialized)
│   └── data/                       # Data directory
│
├── 🌐 Web Interface
│   ├── templates/
│   │   ├── index.html              # Main dashboard page
│   │   └── about.html              # Project information page
│   └── static/
│       ├── historical.png          # Historical price chart
│       ├── forecast.png            # Future price forecast
│       └── evaluation.png          # Model performance chart
│
├── 📝 Configuration & Documentation
│   ├── requirements.txt            # Python package dependencies
│   ├── README.md                   # This file
│   ├── ARCHITECTURE.md             # System design documentation
│   ├── PROJECT_GUIDE.md            # Detailed project guide
│   ├── QUICKSTART.md               # Quick setup instructions
│   └── SETUP.md                    # Installation guide
│
└── 🎯 Utilities
    ├── START_HERE.py               # Entry point script
    └── 00_START_HERE.txt           # Quick reference guide
```

---

## 🎯 Features

### 📈 Interactive Dashboard
- **Real-time Forecasting**: Generate predictions for 7, 30, 60, or 90 days ahead
- **Historical Analysis**: Visualize 14+ years of Bitcoin price history
- **Performance Metrics**: View MAE, RMSE, MAPE, and directional accuracy
- **Confidence Intervals**: 95% confidence bands on forecast predictions
- **Responsive Design**: Mobile-friendly web interface
- **Auto-refresh**: Dynamic forecast updates based on selected horizon

### 🔬 Advanced Data Processing
- Automatic OHLCV data parsing from CSV files
- Missing value handling using forward/backward fill
- Date parsing and timezone handling
- Train/test split for unbiased model evaluation (5,020 training samples, 90 test samples)
- Data validation and cleaning pipeline

### 🧠 Prophet Time Series Model
- **Automatic Trend Detection**: Identifies price movement patterns
- **Seasonality Analysis**: Captures yearly and weekly patterns
- **Changepoint Detection**: Detects structural breaks in the data
- **Uncertainty Quantification**: Probabilistic forecasts with confidence intervals
- **Robust to Missing Data**: Handles gaps in cryptocurrency data
- **Scalable**: Trained on 5,000+ historical data points

### 📊 Comprehensive Evaluation Metrics
- **Mean Absolute Error (MAE)**: $40,150.59
- **Root Mean Squared Error (RMSE)**: $40,425.44
- **Mean Absolute Percentage Error (MAPE)**: 61.31%
- **Directional Accuracy**: 43.82% (predicting price movement direction)
- **Visualization**: Actual vs predicted comparison plots
- **RMSE**: Root Mean Squared Error - Penalizes large errors
- **MAPE**: Mean Absolute Percentage Error - Percentage-based accuracy
- **Directional Accuracy**: Percentage of correct up/down predictions

## 📁 File Descriptions

### `app.py`
Main Flask application with routes:
- `/` - Home page with dashboard
- `/api/forecast` - JSON API for forecast data
- `/api/metrics` - JSON API for model metrics
- `/about` - Information about the project

### `data_loader.py`
Functions for loading and preprocessing data:
- `load_data()` - Load CSV file
- `preprocess_data()` - Clean and format for Prophet
- `get_train_test_split()` - Split data for evaluation

### `prophet_model.py`
Prophet model training and forecasting:
- `train_prophet_model()` - Train the model
- `create_future_dataframe()` - Create forecast dataframe
- `generate_forecast()` - Generate predictions
- `plot_forecast()` - Visualize forecasts
- `save_model()` / `load_model()` - Model persistence

### `model_evaluation.py`
Model evaluation functions:
- `evaluate_model()` - Calculate evaluation metrics
- `print_evaluation_metrics()` - Display metrics
- `plot_evaluation()` - Plot actual vs predicted

### `eda.py`
Exploratory data analysis:
- `plot_historical_price()` - Historical price chart
- `plot_price_statistics()` - Multi-panel statistics
- `print_data_summary()` - Print summary statistics

## 🔧 Configuration

You can modify Prophet model parameters in `prophet_model.py`:

```python
model = Prophet(
    yearly_seasonality=True,        # Include yearly patterns
    weekly_seasonality=True,        # Include weekly patterns
    daily_seasonality=False,        # No daily patterns
    interval_width=0.95,            # 95% confidence interval
    changepoint_prior_scale=0.05    # Changepoint sensitivity
)
```

## 📈 Model Parameters

### Train/Test Split
- **Training data**: All historical data except last 90 days
- **Test data**: Last 90 days of available data
- **Evaluation period**: Full test set

### Seasonality
- **Yearly seasonality**: Captures patterns that repeat annually
- **Weekly seasonality**: Captures patterns that repeat weekly
- **Changepoint detection**: Identifies sudden trend shifts

## ⚙️ Dependencies

- **Flask** (2.3.3) - Web framework
- **Pandas** (2.0.3) - Data manipulation
- **NumPy** (1.24.3) - Numerical computing
- **Prophet** (1.1.4) - Time series forecasting
- **Matplotlib** (3.7.2) - Data visualization
- **Scikit-learn** (1.3.0) - Machine learning metrics
- **CmdStanPy** (1.1.0) - Prophet backend

## 🎯 Usage Examples

### Change Forecast Horizon
Click the buttons on the dashboard to select:
- 7 days ahead
- 30 days ahead
- 60 days ahead
- 90 days ahead

### View Model Metrics
The dashboard displays:
- Current Bitcoin price
- Forecasted price at selected horizon
- Predicted percentage change
- Model accuracy metrics
- Confidence interval bounds

### Interpret Plots
1. **Historical Price**: Shows all past price data
2. **Forecast**: Shows predicted prices with uncertainty bands
3. **Evaluation**: Compares actual vs predicted on test data

## 📊 Example Output

```
============================================================
DATA SUMMARY
============================================================
Date range: 2010-07-17 00:00:00 to 2024-05-23 00:00:00
Total trading days: 5109

Close Price Statistics:
  Min: $0.05
  Max: $73,750.00
  Mean: $15,423.45
  Median: $8,234.67
  Std Dev: $19,234.56

Volume Statistics:
  Mean: 1234567890
  Max: 9876543210
============================================================

==================================================
MODEL EVALUATION METRICS (TEST SET)
==================================================
Mean Absolute Error (MAE):     $1,234.56
Root Mean Squared Error (RMSE): $1,567.89
Mean Absolute Percentage Error (MAPE): 3.45%
Directional Accuracy:          65.43%
==================================================
```

## ⚠️ Important Disclaimer

**This project is for EDUCATIONAL PURPOSES ONLY.**

- Cryptocurrency markets are highly volatile and unpredictable
- Past performance does not guarantee future results
- This model should NOT be used for real financial decisions
- Predictions can be significantly wrong
- Always consult a qualified financial advisor before investing
- Use at your own risk

## 🚀 Future Enhancements

- [ ] Support for multiple cryptocurrencies
- [ ] ARIMA and LSTM model comparison
- [ ] Real-time data streaming
- [ ] Sentiment analysis integration
- [ ] User authentication and forecast history
- [ ] REST API for programmatic access
- [ ] Cloud deployment (AWS, Azure, Heroku)
- [ ] Advanced visualization with Plotly
- [ ] Database for historical forecasts
- [ ] Mobile app version

## 📚 Resources

- [Facebook Prophet Documentation](https://facebook.github.io/prophet/)
- [Time Series Forecasting](https://en.wikipedia.org/wiki/Time_series)
- [Flask Documentation](https://flask.palletsprojects.com/)
- [Pandas Documentation](https://pandas.pydata.org/)

## 📝 License

This project is open source and available for educational use.

## 👨‍💻 Author

Created as a comprehensive learning project for time series analysis and forecasting.

---

**Last Updated**: January 2026

For questions or improvements, feel free to enhance and customize this project!
#   C r y p t o _ A n a l y z e r 
 
 #   C r y p t o A n a l y z e r 
 
 