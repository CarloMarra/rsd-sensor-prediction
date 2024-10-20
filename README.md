# RSD Sensor Particle Position Prediction

This project tackles the problem of predicting the position of a particle passing through an RSD (Resistive Silicon Detector) sensor. The goal is to predict the (x, y) coordinates of the particle's passage using machine learning models applied to sensor data.

Full report available [here](https://github.com/CarloMarra/rsd-sensor-prediction/blob/main/Report.pdf)
Code available [here](https://github.com/CarloMarra/rsd-sensor-prediction/blob/main/Regression_Task.ipynb)

Authors

- Francesca Geusa (ToDo)
- Carlo Marra ([marra.carlo@outlook.com](marra.carlo@outlook.com))

## Problem Overview

The objective is to predict the position (x, y) where a particle passes through a sensor based on signals recorded by 12 pads on the RSD sensor surface. Each pad records:

- **pmax**: Positive peak signal magnitude (mV)
- **negpmax**: Negative peak signal magnitude (mV)
- **tmax**: Time delay from a reference point (ns)
- **area**: Area under the signal curve
- **rms**: Root mean square of the signal

The dataset consists of:
- **Development set**: 385,500 events with (x, y) coordinates.
- **Evaluation set**: 128,500 events without target coordinates.

## Approach

### Data Preprocessing
1. **Noise Reduction**: Removed 6 noisy pads using correlation analysis.
2. **Feature Selection**: Discarded irrelevant features (tmax and rms) based on feature importance.
3. **Data Partitioning**: Used the holdout method for splitting the dataset, relying on scikit-learn for preprocessing and model training.

### Model Selection
- **Ensemble Methods**: Compared Random Forest and Histogram Gradient Boosting Trees (HGBT), with Random Forest performing better for multi-output regression.
- **Evaluation Metric**: Average Euclidean distance between predicted and actual coordinates.

### Hyperparameter Tuning
Used Optuna for hyperparameter optimization:
- **Development set**: 4.371 average Euclidean distance
- **Evaluation set**: 4.801 average Euclidean distance

## Results
- Random Forest performed best, balancing accuracy and efficiency.
- Discrepancies between development and evaluation sets indicate possible distribution mismatches.

## Future Work

-	Investigating potential dataset distribution mismatches to enhance model generalization.
- Exploring advanced feature engineering techniques to improve the prediction accuracy further.

## License

This project is licensed under the MIT License.
