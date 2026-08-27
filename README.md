# Weather-Forecasting-System
Rainfall Forecasting using SimpleRNN and LSTM Networks in Western Province, Sri Lanka 

This repository contains an end-to-end time-series forecasting pipeline built to predict next-day rainfall in the Western Province, Sri Lanka, using 12.5 years (2014–2026) of historical weather data.

## Project Overview
Rainfall forecasting is challenging due to highly non-linear dynamics and extreme right-skewed distributions. This project evaluates recurrent neural networks against statistical baselines to benchmark performance on both routine days and heavy precipitation events.

## Key Features & Architecture
- **Data Source:** Hourly Open-Meteo archive aggregated to daily resolution.
- **Engineered Features:** 14-day sequences, rolling statistics, lagged variables, and cyclical date encodings (21 features total).
- **Models Evaluated:** SimpleRNN, LSTM, Persistence, Climatology.
- **Loss Function:** Huber Loss ($\delta=1.0$) to handle extreme right-skewed values without sensitive MSE distortion.

## Model Performance

| Model | MAE (mm) | RMSE (mm) | R² |
| :--- | :--- | :--- | :--- |
| **LSTM** | **5.153** | **11.738** | **0.182** |
| SimpleRNN | 5.254 | 12.156 | 0.123 |
| Persistence | 6.161 | 12.883 | 0.015 |
| Climatology | 7.057 | 12.983 | -0.000 |

## Key Takeaways & Limitations
- **LSTM superiority:** Handles 14-day memory sequences better than SimpleRNN.
- **Tail Event Failure:** While LSTM performs well overall, evaluation on the top 10% heaviest rainfall days (>19.71 mm) yields a negative R², highlighting severe under-forecasting during extreme storms.

## Project Structure
```text
├── data/                  # Raw and processed daily datasets
├── notebooks/             # Exploratory Data Analysis & Model Training
├── reports/               # Final project report PDF
├── README.md              # Project documentation
└── requirements.txt       # Python dependencies
