# Watt's Next? Predicting EV Trends and Charging Needs

A comprehensive data science project analyzing Electric Vehicle (EV) trends, predicting performance metrics, and identifying optimal charging infrastructure locations using machine learning and geospatial analysis.

---

## 📊 Project Overview

Electric vehicles represent a transformative shift in the transportation industry, addressing critical global challenges including climate change, air pollution, and fossil fuel dependency. This project leverages data science techniques to unlock insights from EV adoption patterns, performance characteristics, and infrastructure requirements.

### Key Objectives

* **Analyze EV Performance:** Explore electric range trends across manufacturers and model years
* **Test Hypotheses:** Validate assumptions about BEV vs PHEV performance and regional adoption patterns
* **Build Predictive Models:** Forecast electric range and classify vehicle eligibility for incentives
* **Market Segmentation:** Categorize EVs using clustering techniques for strategic insights
* **Infrastructure Planning:** Identify regions requiring additional charging infrastructure

---

## 👥 Authors

* **Abhishek Rithik Origanti** (UID: 121305534)
* **Matheswara Annamalai Senthilkumar** (UID: 121281500)

---

## 🚗 Dataset Information

* **Size:** 216,772 rows × 17 columns
* **Time Range:** Electric vehicles manufactured between 1999-2025
* **Geographic Scope:** Primarily Washington State, USA
* **Key Features:** Electric range, model year, manufacturer, vehicle type, location data

### Dataset Columns

| Column                | Description                        | Usage                   |
| --------------------- | ---------------------------------- | ----------------------- |
| Electric Range        | Maximum electric-only range        | Primary target variable |
| Model Year            | Vehicle manufacturing year         | Trend analysis          |
| Make/Model            | Manufacturer and model             | Performance comparison  |
| Electric Vehicle Type | BEV vs PHEV classification         | Classification tasks    |
| CAFV Eligibility      | Clean Air Vehicle incentive status | Prediction target       |
| Geographic Data       | County, City, State, Coordinates   | Infrastructure planning |

---

## 🛠️ Technologies & Libraries

**Core Libraries**

```python
pandas              # Data manipulation and analysis
numpy               # Numerical computing
matplotlib/seaborn  # Data visualization
scikit-learn        # Machine learning algorithms
plotly              # Interactive visualizations
```

**Specialized Tools**

```python
geopandas           # Geospatial data analysis
folium              # Interactive mapping
imblearn            # Handling class imbalance (SMOTE)
statsmodels         # Statistical analysis
```

---

## 📈 Key Findings & Results

### 1. Performance Analysis

* **Electric Range Evolution:** Steady improvement in EV ranges over time, with 91.8% accuracy in range prediction
* **Manufacturer Leadership:** Tesla, Jaguar, and Polestar lead with highest average electric ranges
* **Market Diversity:** Growing variety from budget-friendly to premium long-range vehicles

### 2. Predictive Modeling Results

| Model Type                 | Accuracy   | Key Insights                                        |
| -------------------------- | ---------- | --------------------------------------------------- |
| Electric Range Prediction  | R² = 0.918 | Model year and manufacturer are strong predictors   |
| CAFV Eligibility           | 99.85%     | Electric range and model year determine eligibility |
| BEV vs PHEV Classification | 98.42%     | Clear distinction based on range and year           |

### 3. Statistical Analysis

* **Hypothesis Testing:** Significant difference in electric range between BEVs and PHEVs (p < 0.001)
* **Regional Patterns:** Strong association between geographic location and vehicle type preference
* **CAFV Adoption:** 76% of vehicles eligible for clean air incentives

### 4. Infrastructure Insights

* **Urban Concentration:** High EV density in Seattle, Bellevue, and Tacoma
* **Rural Gaps:** Central and eastern Washington require additional charging infrastructure
* **Strategic Planning:** Heatmap analysis identifies optimal locations for new charging stations

---

## 🗂️ Project Structure

```
├── data/
│   ├── raw/                    # Original dataset
│   └── processed/              # Cleaned and preprocessed data
├── notebooks/
│   ├── 01_data_preparation.ipynb
│   ├── 02_exploratory_analysis.ipynb
│   ├── 03_hypothesis_testing.ipynb
│   ├── 04_predictive_modeling.ipynb
│   ├── 05_classification.ipynb
│   ├── 06_clustering.ipynb
│   └── 07_infrastructure_planning.ipynb
├── src/
│   ├── data_processing.py
│   ├── modeling.py
│   ├── visualization.py
│   └── utils.py
├── results/
│   ├── models/                 # Trained model files
│   ├── figures/                 # Generated plots and maps
│   └── reports/                 # Analysis summaries
├── requirements.txt
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites

* Python 3.8 or higher
* Jupyter Notebook or JupyterLab
* Git

### Installation

```bash
git clone https://github.com/your-username/ev-trends-prediction.git
cd ev-trends-prediction
python -m venv ev_env
source ev_env/bin/activate  # On Windows: ev_env\Scripts\activate
pip install -r requirements.txt
```

### Dataset

Place your EV dataset in the `data/raw/` directory.

```
Electric_Vehicle_Population_Data-2.csv
```

### Quick Start

```python
import pandas as pd
from src.data_processing import clean_data
from src.modeling import predict_electric_range, classify_vehicle_type
from src.visualization import create_heatmap, plot_trends

# Load dataset
df = pd.read_csv('data/raw/Electric_Vehicle_Population_Data-2.csv')

# Clean and preprocess
df_clean = clean_data(df)

# Predictions
range_predictions = predict_electric_range(df_clean)
vehicle_classifications = classify_vehicle_type(df_clean)

# Visualizations
plot_trends(df_clean)
create_heatmap(df_clean)
```

---

## 📊 Analysis Workflow

1. **Data Preparation**

   * Handle missing values and outliers
   * Feature engineering
   * Data validation
2. **EDA**

   * Trend analysis
   * Manufacturer comparisons
   * Geographic adoption
3. **Hypothesis Testing**

   * t-tests, Chi-square, ANOVA
4. **Predictive Modeling**

   * Linear & Random Forest regression
   * Cross-validation
5. **Classification**

   * Logistic regression + SMOTE
   * Precision, recall, F1-score
6. **Infrastructure Planning**

   * Geospatial mapping
   * Heatmaps & recommendations

---

## 📸 Key Visualizations

* **Electric Range Trends:** Box plots, line charts, bar charts
* **Geographic Analysis:** Interactive maps, heatmaps, cluster maps
* **Model Performance:** Confusion matrices, learning curves, feature importance

---

## 🎯 Business Applications

**For Manufacturers**

* Product strategy
* Performance benchmarking
* R\&D focus

**For Policymakers**

* Optimize incentive programs
* Charging infrastructure planning
* EV growth forecasting

**For Consumers**

* Purchase decision support
* Real-world range understanding
* Charging access mapping

---

## 📊 Model Performance Summary

| Analysis Type          | Method                      | Key Metric    | Result    |
| ---------------------- | --------------------------- | ------------- | --------- |
| Range Prediction       | Random Forest               | R² Score      | 0.918     |
| CAFV Eligibility       | Logistic Regression         | Accuracy      | 99.85%    |
| Vehicle Classification | Logistic Regression + SMOTE | Accuracy      | 98.42%    |
| Hypothesis Testing     | t-test                      | Significance  | p < 0.001 |
| Cross Validation       | 5-Fold CV                   | Mean Accuracy | 98.7%     |

---

## ⚠️ Limitations & Future Work

**Current Limitations**

* Limited geographic scope
* Some feature limitations
* Temporal constraints
* Static infrastructure analysis

**Future Enhancements**

* Expand dataset coverage
* Real-time data integration
* Deep learning models
* Economic & environmental impact analysis

---

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Open Pull Request

**Contribution Areas**

* Data preprocessing
* Additional ML models
* Enhanced visualizations
* Documentation updates

---

## 📚 References & Resources

* **National Renewable Energy Laboratory (NREL)**
* **U.S. Department of Energy**
* **International Energy Agency (IEA)**
* **Scikit-learn Documentation**
* **Geopandas User Guide**
* **Folium Documentation**

---

* ⭐ Star this repository if you find it useful

---

*This project demonstrates the power of data science in accelerating the transition to sustainable transportation. Together, we can build a cleaner, more efficient future.*
