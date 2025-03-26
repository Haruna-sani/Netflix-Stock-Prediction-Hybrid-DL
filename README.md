# Predicting Netflix Stock Price using Hybrid Deep Learning Algorithms

## Overview
This project explores the use of deep learning models to predict Netflix's closing stock price from 2002 to 2025. Three different architectures were tested:
- **LSTM (Long Short-Term Memory)**
- **CNN+GRU-LSTM (Convolutional Neural Network + Gated Recurrent Unit + LSTM)**
- **CNN+Bi-LSTM (Convolutional Neural Network + Bidirectional LSTM)**

Each model was trained with **batch size 64** and tested across **four distinct learning rates**: `0.0001, 0.001, 0.01, 0.1`.

## Performance Evaluation
The performance of each model was assessed using the **R-squared (R²) metric**, which indicates how well the model explains the variance in stock prices. Higher values (closer to 1) indicate better performance, while negative values suggest poor predictions.

### Results with Batch Size 64
| Model               | 0.0001 | 0.001 | 0.01  | 0.1   |
|--------------------|--------|--------|--------|--------|
| **LSTM**           | 0.996  | 0.998  | 0.995  | -1.325 |
| **CNN+GRU-LSTM**   | 0.996  | 0.995  | 0.995  | -3.961 |
| **CNN+Bi-LSTM**    | 0.995  | 0.997  | 0.958  | -0.673 |

### Results with Higher Batch Size of 128
To analyze the effect of batch size, the models were trained with a **larger batch size**. The results are as follows:

| Model               | 0.0001 | 0.001 | 0.01  | 0.1   |
|--------------------|--------|--------|--------|--------|
| **LSTM**           | 0.995  | 0.996  | 0.997  | 0.736  |
| **CNN+GRU-LSTM**   | 0.997  | 0.995  | 0.990  | -0.625 |
| **CNN+Bi-LSTM**    | 0.995  | 0.995  | 0.994  | -1.296 |

## Interpretation of Results
1. **Low Learning Rates (0.0001 & 0.001):**
   - All models performed well, achieving R² values close to 1, indicating strong predictive capabilities.
   - CNN-based architectures slightly underperformed compared to standalone LSTM.

2. **Moderate Learning Rate (0.01):**
   - The models maintained strong performance, but CNN+Bi-LSTM showed a drop (0.958), suggesting that it struggled to generalize at this rate.

3. **High Learning Rate (0.1):**
   - Performance deteriorated drastically, with **negative R² values** indicating that the model performed worse than a simple mean predictor.
   - CNN+GRU-LSTM was the most affected (-3.961), showing extreme instability.

4. **Effect of Higher Batch Size:**
   - In most cases, increasing the batch size did not significantly impact performance for well-optimized learning rates (0.0001 & 0.001).
   - However, for high learning rates (0.1), performance improved slightly compared to the smaller batch size but still resulted in poor predictions.

## Conclusion
- **LSTM remains the most stable model**, consistently achieving the highest R² values.
- **CNN+GRU-LSTM and CNN+Bi-LSTM offer competitive performance** but are more sensitive to learning rate changes.
- **Very high learning rates (0.1) lead to model instability** and should be avoided.
- **Higher batch size improves learning stability at high learning rates** but does not drastically change results at optimal learning rates.

This study highlights the importance of tuning **learning rates** and **batch sizes** when designing deep learning models for stock price prediction.



