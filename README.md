# Apache-Kafka Stock Price Prediction System

## Overview
This project implements a real-time stock price prediction system using **Apache Kafka** and a **deep learning model** (LSTM). The system streams stock data, processes it in real time, and generates predictions.

## System Design
The system consists of the following components:

- **Data Producer**: Reads stock price data and streams it to Kafka.
- **Kafka Broker**: Manages real-time data flow.
- **Consumer with Machine Learning Model**: Listens for stock price data, processes it using an **LSTM model**, and generates predictions.
- **Evaluation Metrics**: Tracks accuracy and latency.

## Implementation Details

### Data Processing
- Dataset sourced from Kaggle (historical stock price data).
- Preprocessing includes:
  - Converting date columns to a standardized format.
  - Normalizing stock prices using `MinMaxScaler`.
  - Selecting the top 100 records for optimization.

### Kafka Setup
Kafka topics used:
- **stock-data**: Receives real-time stock prices from the producer.
- **predictions**: Stores model-generated forecasts.

### Machine Learning Model
- **LSTM-based** deep learning model for sequential stock price prediction.
- Architecture:
  - Two **LSTM layers** to capture temporal dependencies.
  - A **dense layer** for final price prediction.
  - **MSE (Mean Squared Error)** as the loss function.

### Prediction Pipeline
1. The **Kafka Consumer** reads stock prices from `stock-data`.
2. The latest prices are buffered to create an input sequence for LSTM.
3. The trained model predicts the next day’s stock price.
4. The prediction is logged and sent to `predictions` in Kafka.

## Evaluation and Performance Analysis

### Performance Metrics
- **Mean Squared Error (MSE)**: Measures accuracy.
- **Latency**: Measures prediction response time.

### Challenges & Solutions
- **Improper data scaling** → Fixed by correctly applying `MinMaxScaler`.
- **Negative predicted prices** → Resolved inverse transformation issues.
- **Windows Kafka issues** → Optimized paths to reduce command-line errors.

## Conclusion & Future Work
The system successfully integrates **Apache Kafka** with an **LSTM-based stock predictor**, enabling **real-time stock price forecasting**.

### Future Enhancements:
- Implement **multi-stock prediction** for broader coverage.
- Use **reinforcement learning** for adaptive improvements.
- Deploy the system in a **cloud environment** for scalability.

---

## Running the Project

### Prerequisites
Ensure the following are installed:
- **Apache Kafka**
- **Python 3.x**
- **TensorFlow / Keras**
- **Kafka-python library**
- **Pandas, NumPy, Sklearn**
