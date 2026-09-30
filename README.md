# 🚀 SpaceX Falcon 9 First Stage Landing Prediction

An end-to-end **Data Science and Machine Learning project** that predicts whether the first stage of a SpaceX Falcon 9 rocket will successfully land after launch.

The project combines **data collection, web scraping, data wrangling, SQL analytics, exploratory data analysis, geospatial visualization, interactive dashboards, and machine learning classification** into a complete data science pipeline.

---

## 📌 Executive Summary

SpaceX's ability to recover and reuse Falcon 9 first-stage boosters is a major factor behind the company's comparatively low launch costs. Predicting whether a first stage will land successfully can therefore provide useful insights into launch reliability, recovery feasibility, and mission characteristics.

This project develops a machine learning pipeline to predict the **landing success of a Falcon 9 first stage** based on launch and payload characteristics.

The target variable is a binary classification:

* `1` → First stage landed successfully
* `0` → First stage did not land successfully

The project evaluates four classification algorithms:

* Logistic Regression
* Support Vector Machine (SVM)
* Decision Tree
* K-Nearest Neighbors (KNN)

All four optimized models achieved a **test accuracy of 83.33%** on the held-out test set.

---

# 🎯 Project Objectives

The primary objectives of this project are to:

1. Collect historical Falcon 9 launch data.
2. Combine data from APIs and web scraping.
3. Clean and transform the raw dataset.
4. Engineer a binary landing-success target variable.
5. Perform exploratory data analysis using Python and SQL.
6. Analyze the geographical characteristics of launch sites.
7. Build an interactive data visualization dashboard.
8. Train and optimize multiple classification models.
9. Compare model performance using cross-validation and test accuracy.
10. Identify factors associated with Falcon 9 first-stage landing success.

---

# 🏗️ Project Workflow

```text
┌──────────────────────┐
│   Data Collection    │
│ REST API + Scraping  │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│   Data Wrangling     │
│ Cleaning + Encoding  │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│ Feature Engineering  │
│   Target + Features  │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│        EDA           │
│ Python + SQL + Viz   │
└──────────┬───────────┘
           │
           ├──────────────────────┐
           ▼                      ▼
┌──────────────────┐     ┌───────────────────┐
│ Geospatial       │     │ Interactive       │
│ Analysis         │     │ Dash Dashboard    │
│ Folium           │     │ Plotly Dash       │
└──────────────────┘     └───────────────────┘
           │
           ▼
┌──────────────────────┐
│ Machine Learning     │
│ Classification       │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│ Model Optimization   │
│ GridSearchCV + CV    │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│ Performance Analysis │
│ Accuracy + Confusion │
│ Matrix                │
└──────────────────────┘
```

---

# 📊 1. Data Collection

### SpaceX REST API

Launch data was collected using the **SpaceX REST API** through paginated API requests.

The collected information included:

* Launch specifications
* Booster/core versions
* Payload characteristics
* Launch sites
* Orbit information
* Landing outcomes

### Web Scraping

Additional historical launch information was collected from **Wikipedia** using:

* Python
* `requests`
* `BeautifulSoup`

The scraped information was combined with API data to create a richer dataset for analysis.

---

# 🧹 2. Data Wrangling & Feature Engineering

The raw data was cleaned and transformed before being used for analysis and machine learning.

### Data Cleaning

The preprocessing stage included:

* Handling missing landing-pad values
* Handling missing flight-related variables
* Cleaning categorical variables
* Converting numerical variables to appropriate data types
* Preparing the dataset for machine learning

### Target Variable

A binary target variable named `Class` was created:

| Class | Meaning                               |
| ----: | ------------------------------------- |
|   `1` | First stage landed successfully       |
|   `0` | First stage did not land successfully |

### Categorical Encoding

Categorical features were converted into numerical representations using one-hot encoding with `pandas.get_dummies()`.

Key categorical features included:

* `Orbit`
* `LaunchSite`
* `LandingPad`
* `Serial`

The resulting feature matrix was converted to a numerical format suitable for machine learning.

---

# 🔎 3. Exploratory Data Analysis

Exploratory Data Analysis was performed using **Python visualization libraries and SQL**.

### Python Visualization

The relationships between landing success and variables such as:

* Payload mass
* Flight number
* Launch site
* Orbit type
* Booster version
* Mission characteristics

were analyzed using:

* Matplotlib
* Seaborn

### SQL Analysis

SQL queries were used to investigate:

* Landing outcome counts
* Maximum payload missions
* Booster variations
* Customer/mission characteristics
* Launch-site statistics

This provided an additional analytical perspective beyond Python-based EDA.

---

# 🌍 4. Interactive Geospatial Analysis

## Folium Mapping

Folium was used to create an interactive geographical representation of Falcon 9 launch sites.

The analysis included:

* Launch-pad locations
* Distance to coastlines
* Distance to railways
* Distance to highways
* Landing outcome visualization
* Clustered launch-site markers

The geographical analysis helped investigate whether the physical characteristics and surroundings of launch sites could provide useful information for understanding landing outcomes.

---

# 📈 5. Interactive Dashboard

A **Plotly Dash** application was developed to provide interactive visual analytics.

### Dashboard Features

The dashboard allows users to:

* Adjust payload-mass ranges using sliders
* Explore launch-site statistics
* Analyze landing success rates
* Compare launch sites
* View interactive charts

The dashboard provides a more accessible way to explore the dataset compared with static visualizations.

---

# 🤖 6. Machine Learning

The landing prediction problem was formulated as a **binary classification task**.

## Feature Scaling

The feature matrix was standardized using:

```python
StandardScaler
```

This ensured that numerical features were placed on comparable scales before model training.

## Train-Test Split

The dataset was divided into:

* **80% Training Data**
* **20% Test Data**

The experiment used:

```text
random_state = 2
```

The test set contained **18 observations**.

---

# 🧠 7. Classification Models

Four machine learning algorithms were trained and optimized:

### 1. Logistic Regression

Used as a baseline linear classification model.

### 2. Support Vector Machine

Used to identify separating boundaries between successful and unsuccessful landing outcomes.

### 3. Decision Tree

Used to model nonlinear relationships through a sequence of feature-based decisions.

### 4. K-Nearest Neighbors

Used to classify missions based on the characteristics of similar observations.

---

# ⚙️ 8. Hyperparameter Optimization

Each classification algorithm was optimized using:

* `GridSearchCV`
* 10-fold cross-validation

This approach systematically evaluated different hyperparameter combinations and selected the configuration producing the strongest cross-validation performance.

---

# 📊 9. Results

## Model Performance

| Model                  | Cross-Validation Score | Test Accuracy |
| ---------------------- | ---------------------: | ------------: |
| Logistic Regression    |                  84.6% |    **83.33%** |
| Support Vector Machine |                  84.8% |    **83.33%** |
| Decision Tree          |              **87.3%** |    **83.33%** |
| K-Nearest Neighbors    |                  84.8% |    **83.33%** |

All four optimized models achieved the same test accuracy of:

> **83.33%**

This corresponds to **15 correct predictions out of 18 test observations**.

---

## Confusion Matrix

The reported confusion matrix contained:

|                     | Predicted Negative | Predicted Positive |
| ------------------- | -----------------: | -----------------: |
| **Actual Negative** |                  3 |                  3 |
| **Actual Positive** |                  0 |                 12 |

Where:

* **True Negatives (TN):** 3
* **True Positives (TP):** 12
* **False Positives (FP):** 3
* **False Negatives (FN):** 0

The primary classification error was **false-positive predictions**, where the model predicted a successful landing for missions that were actually unsuccessful.

---

# 🚀 10. Key Findings

### 📈 Landing Success Improved Over Time

Falcon 9 landing performance improved substantially over successive generations of the launch system.

Early missions experienced more landing failures, while later missions demonstrated considerably higher recovery success rates.

The improvement became particularly noticeable with the maturation of the **Block 5** configuration.

### 🛰️ Orbit and Payload Characteristics

Landing success varied across different orbit categories and mission types.

Missions targeting **LEO and ISS-related orbits** showed relatively strong recovery performance, including missions carrying substantial payloads.

### 📦 Payload Mass

Payload mass showed a relationship with landing outcomes, although payload mass alone does not determine whether a booster will successfully land.

Mission profile, orbit, launch site, booster configuration, and other operational factors also contribute to the landing outcome.

### 📍 Launch Site

Different launch sites exhibited different landing-success patterns.

Geospatial analysis provided additional context by examining the relationship between launch infrastructure and geographical features such as:

* Coastlines
* Highways
* Railways

---

# 🛠️ Technologies Used

| Category                  | Technologies            |
| ------------------------- | ----------------------- |
| Programming               | Python                  |
| Data Collection           | SpaceX REST API         |
| Web Scraping              | BeautifulSoup, Requests |
| Data Processing           | Pandas, NumPy           |
| Data Visualization        | Matplotlib, Seaborn     |
| SQL Analytics             | SQL                     |
| Geospatial Analysis       | Folium                  |
| Interactive Visualization | Plotly                  |
| Dashboard                 | Plotly Dash             |
| Machine Learning          | Scikit-learn            |
| Feature Scaling           | StandardScaler          |
| Model Optimization        | GridSearchCV            |
| Development               | Jupyter Notebook        |

---

# 📁 Repository Structure

```text
SpaceX-Falcon-9-Landing-Prediction/
│
├── 📓 SpaceX_Data_Collection_API.ipynb
├── 📓 SpaceX_Web_Scraping.ipynb
├── 📓 SpaceX_Data_Wrangling.ipynb
├── 📓 jupyter-labs-eda-dataviz-v2.ipynb
├── 📓 SpaceX_EDA_SQL.ipynb
├── 📓 SpaceX_Interactive_Folium_Map.ipynb
│
├── 🐍 SpaceX_Plotly_Dash_App.py
│
├── 📓 SpaceX_Machine_Learning_Prediction_Part_5.ipynb
│
├── 📄 Data Science Capstone Project Report.pdf
│
└── 📄 README.md
```

---

# 🔄 End-to-End Pipeline

The complete project follows this sequence:

```text
API + Web Scraping
        ↓
Data Collection
        ↓
Data Cleaning
        ↓
Feature Engineering
        ↓
SQL Analysis
        ↓
Exploratory Data Analysis
        ↓
Geospatial Analysis
        ↓
Interactive Dashboard
        ↓
Feature Scaling
        ↓
Train-Test Split
        ↓
GridSearchCV
        ↓
Classification Models
        ↓
Performance Evaluation
        ↓
Landing Prediction
```

---

# 💡 Project Takeaways

This project demonstrates an end-to-end application of data science concepts rather than focusing only on model training.

Key skills demonstrated include:

* API-based data collection
* Web scraping
* Data cleaning
* Feature engineering
* SQL analytics
* Exploratory data analysis
* Data visualization
* Geospatial analytics
* Interactive dashboard development
* Classification modeling
* Feature scaling
* Cross-validation
* Hyperparameter tuning
* Model evaluation

The project shows how raw aerospace launch data can be transformed into **actionable analytical insights and a machine learning prediction system**.

---

# 📌 Conclusion

The project successfully developed a machine learning pipeline for predicting Falcon 9 first-stage landing outcomes.

Four classification algorithms were optimized using 10-fold cross-validation, with all four achieving **83.33% test accuracy** on the held-out test set.

Beyond machine learning, the project integrates **data engineering, SQL, visualization, geospatial analysis, and interactive analytics**, providing a complete data science workflow from raw data collection to predictive modeling.

---

## 📚 References

* SpaceX REST API
* Wikipedia — Falcon 9 launch history
* IBM Data Science Professional Certificate Capstone Project
* Scikit-learn Documentation
* Plotly Dash Documentation
* Folium Documentation
