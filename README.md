
# Multi-Model Cloud Segmentation and Solar Irradiance Attenuation Forecasting over Guwahati using 4-Band Sentinel-2 Imagery

> **Repository Description:** A deep learning capstone project evaluating **U-Net**, **DeepLabV3+ (Xception41)**, and **SegFormer (MiT-B2)** for high-resolution cloud segmentation over Guwahati using 4-band Sentinel-2 imagery. The project integrates cloud segmentation with solar irradiance attenuation estimation, solar power yield forecasting, clearness and variability analysis, and model uncertainty visualization.

---

#  Project Overview

This repository contains the complete implementation of a deep learning framework for **cloud segmentation from Sentinel-2 satellite imagery** and the subsequent estimation of **solar irradiance attenuation** caused by cloud cover.

The study focuses on **Guwahati, Assam, India**, using **4-band Sentinel-2 imagery (Blue, Green, Red, Near-Infrared)** captured over multiple years. The generated cloud masks are further utilized for estimating solar energy availability, enabling applications in photovoltaic planning, weather monitoring, and renewable energy forecasting.

The project evaluates three different semantic segmentation architectures:
## SAVED MODELS CAN BE FOUND IN: https://drive.google.com/file/d/17l3W_xLU2QfTmNh0fh7WzsfJz4FlHh_4/view?usp=sharing
1. **U-Net**
   - Convolutional encoder-decoder architecture
   - Strong baseline for biomedical and satellite image segmentation
   - Excellent localization capability

2. **DeepLabV3+ (Xception41 Backbone)**
   - Encoder-decoder semantic segmentation network
   - Atrous Spatial Pyramid Pooling (ASPP)
   - Multi-scale contextual feature extraction
   - Better boundary refinement

3. **SegFormer (MiT-B2)**
   - Transformer-based semantic segmentation model
   - Hierarchical Transformer encoder
   - Efficient multi-scale representation
   - Strong generalization with fewer parameters

---

#  Key Features

## ☁️ High-Resolution Cloud Segmentation

- Pixel-wise cloud mask prediction
- Multi-model performance comparison
- Binary cloud/non-cloud classification
- 4-band Sentinel-2 image support

---

##  Solar Irradiance Attenuation Estimation

Cloud coverage is converted into ground-level solar irradiance using a parameterized attenuation model:

\[
I = I_{max}(1-\alpha C)
\]

where:

- **I** = Ground irradiance (W/m²)
- **Imax** = Clear sky irradiance
- **α** = Atmospheric attenuation coefficient
- **C** = Cloud coverage ratio

---

##  Solar Power Yield Forecasting

Estimated irradiance is further translated into photovoltaic power generation by incorporating:

- Solar panel efficiency
- System losses
- Urban land utilization
- Module installation density

The complete **5.12 km × 5.12 km (26.2144 km²)** study area is modeled for macro-scale solar energy estimation.

---

##  Historical Climate Analysis

The repository computes long-term atmospheric indicators including:

- Clearness Index (Kt)
- Cloud Coverage Ratio
- Variability Index
- Historical irradiance trends

These metrics provide insight into long-term climatic behavior over Guwahati.

---

##  Statistical Model Evaluation

Performance comparison includes:

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- Pearson Correlation Coefficient
- IoU
- Dice Score
- Precision
- Recall
- F1 Score

---

##  Model Uncertainty Visualization

Soft prediction probabilities are converted into uncertainty maps using:

- Pixel-wise entropy
- Confidence estimation
- Probability variance
- Boundary uncertainty visualization

These heatmaps identify regions where the neural networks exhibit lower prediction confidence.

---

#  System Architecture

```text
                    4-Band Sentinel-2 Images
                (B02, B03, B04, B08)
                           │
                           ▼
              Image Normalization & Preprocessing
                           │
                           ▼
                  Dataset Preparation Pipeline
                           │
                           ▼
                ┌──────────────────────────┐
                │   Model Training Engine   │
                └──────────────────────────┘
                           │
     ┌─────────────────────┼─────────────────────┐
     ▼                     ▼                     ▼
   U-Net         DeepLabV3+ (Xception41)    SegFormer (MiT-B2)
     │                     │                     │
     └─────────────────────┼─────────────────────┘
                           ▼
                  Probability Prediction Maps
                           │
              ┌────────────┴────────────┐
              ▼                         ▼
      Binary Cloud Masks        Uncertainty Heatmaps
                                        │
                           (Entropy / Variance Maps)
              ▼
        Cloud Coverage (%)
              │
              ▼
    Solar Irradiance Attenuation
              │
              ▼
 Solar Power Generation Forecast
              │
              ▼
 Historical Climate Analytics
```

---

# 🛰️ Dataset

### Satellite Platform

- Sentinel-2 Level-2A

### Spectral Bands

| Band | Description | Resolution |
|------|-------------|-----------|
| B02 | Blue | 10 m |
| B03 | Green | 10 m |
| B04 | Red | 10 m |
| B08 | Near Infrared | 10 m |

---

### Image Size

```
512 × 512 pixels
```

Ground coverage:

```
5.12 km × 5.12 km
```

Study area:

```
26.2144 km²
```

---

#  Deep Learning Models

## U-Net

- Encoder-decoder CNN
- Skip connections
- Binary segmentation
- BCE + Dice Loss

---

## DeepLabV3+

Backbone:

```
Xception41
```

Features:

- Atrous Spatial Pyramid Pooling (ASPP)
- Dilated convolutions
- Multi-scale context
- Decoder refinement

---

## SegFormer

Encoder:

```
MiT-B2
```

Features:

- Transformer encoder
- Hierarchical architecture
- Efficient attention
- Scale-invariant features

---

#  Workflow

```text
Satellite Images
        │
        ▼
Preprocessing
        │
        ▼
Training
        │
        ▼
Model Prediction
        │
        ▼
Cloud Segmentation
        │
        ▼
Cloud Coverage Estimation
        │
        ▼
Solar Irradiance Modeling
        │
        ▼
Power Generation Forecast
        │
        ▼
Historical Climate Analysis
        │
        ▼
Visualization & Evaluation
```

---

#  Outputs

The repository generates:

- Prediction vs Ground Truth Curves

- Year-Wise 3-Line Cloud Cover + Irradiance Curves

- Average Solar Irradiance Block Chart (Year-Wise)

- Solar Power Generation Calculation & Graph

- Panel Output for 5.12×5.12 km Area + Spectral Signature of Clouds

- Variability Index & Clearness Index (Kt)

- Uncertainty Heatmap from Model Probability Maps

---

#  Technologies Used

- Python
- PyTorch
- segmentation_models_pytorch
- TensorFlow / Keras
- NumPy
- OpenCV
- Rasterio
- GDAL
- Matplotlib
- Pandas
- Scikit-learn
- Google Earth Engine

---

#  Evaluation Metrics

Segmentation Metrics

- IoU
- Dice Score
- Precision
- Recall
- F1 Score

Regression Metrics

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- Pearson Correlation Coefficient

---

#  Applications

- Solar energy forecasting
- Smart grid planning
- Renewable energy assessment
- Climate monitoring
- Cloud cover estimation
- Environmental analytics
- Satellite image segmentation
- Remote sensing research

---

#  Author

**Abdul Matin**

Electronics & Telecommunication Engineering

Assam Engineering College


---

#  License

This project is intended for academic and research purposes.

Feel free to fork, improve, and cite this repository in future research.
