# Pathloss Prediction using Synthetic Data and Machine Learning Models

## Project Overview

This project focuses on predicting pathloss in wireless communication using a combination of real-world measurements and synthetic data generation techniques. The measurements were collected using Raspberry Pi as both the antenna and receiver. Due to the scarcity of data, various synthetic data generation methods were employed to augment the dataset.

## Data Collection

- **Hardware Used:** Raspberry Pi as the antenna and receiver.
- **Environment:** Measurements were conducted in a farm environment with trees acting as obstacles, affecting signal strength and pathloss.

## Synthetic Data Generation

Given the limited amount of real-world data, synthetic data was generated using the following methods:

- **Copulas**
- **Gaussian Mixture Models (GMM)**
- **Generative Adversarial Networks (GAN)**

### GAN Architecture

The GAN model used in this project consists of the following layers:

#### Generator Configuration
| Layer Number | Layer Type | Output Shape | Activation Function |
|--------------|------------|--------------|---------------------|
| 1            | Input      | Latent_dim   | -                   |
| 2            | Dense      | 128          | ReLU                |
| 3            | Dense      | 256          | ReLU                |
| 4            | Dense      | 512          | ReLU                |
| 5            | Dense      | Num_features(16) | ReLU            |

#### Discriminator Configuration
| Layer Number | Layer Type | Output Shape | Activation Function |
|--------------|------------|--------------|---------------------|
| 1            | Input      | Num_features(16) | -               |
| 2            | Dense      | 512          | ReLU                |
| 3            | Dense      | 256          | ReLU                |
| 4            | Dense      | 128          | ReLU                |
| 5            | Dense      | 1            | Sigmoid             |

### SDV Metrics for Synthetic Data

The performance of the synthetic data generation methods was evaluated using SDV metrics:

| Method | Column Shapes | Column Pair Trends | Overall |
|--------|---------------|--------------------|---------|
| GAN    | 88.18         | 95.34              | 91.76   |
| CTGAN  | 85.61         | 76.09              | 80.85   |
| GMM    | 85.65         | 98.17              | 91.91   |
| Copula | 90.25         | 95.75              | 93.0    |

## Machine Learning Models

Several machine learning models were used to predict pathloss, including:

- **Linear Regression**
- **Support Vector Regression (SVR)**
- **Decision Tree**
- **Random Forest**
- **Multilayer Perceptron (MLP)**
- **XGBoost**

### Best Performing Model

Among all the models, **XGBoost** was found to be the best-performing model in terms of prediction accuracy.

## Conclusion

This project demonstrates the effectiveness of using synthetic data to enhance predictive modeling, particularly in scenarios where real-world data is scarce. The combination of advanced synthetic data generation techniques and robust machine learning models led to accurate pathloss predictions.


