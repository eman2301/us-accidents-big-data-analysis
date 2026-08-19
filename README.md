# US Accidents Big Data Analysis

A big data analytics project that explores **500,000 US traffic accident records** to identify patterns related to accident severity, time, weather conditions, visibility, and geographic distribution.

The project uses **Polars** for data preprocessing and feature engineering, **PySpark** for scalable machine learning, and **Plotly + Dash** for interactive data visualization.

A **Random Forest classifier** is used to predict accident severity based on environmental, temporal, and accident-related features.

## Dataset

This project uses a sampled version of the **US Accidents dataset** containing **500,000 traffic accident records** from **49 US states** between **2016 and 2023**.

The original sampled dataset contains **46 attributes**, including information related to:

- Accident severity
- Location and state
- Temperature and humidity
- Visibility
- Wind speed
- Precipitation
- Weather conditions
- Accident start and end times
- Day and night conditions

The dataset was cleaned and transformed before analysis to improve data quality and processing efficiency.

## Data Preparation and Feature Engineering

The dataset was processed using **Polars** to improve data quality and reduce unnecessary complexity.

The preprocessing steps included:

- Removing irrelevant and redundant columns
- Handling missing values
- Replacing missing wind speed values with the median
- Replacing missing precipitation values with zero
- Converting date and time columns into datetime format
- Creating new features such as `Year`, `Month`, `Hour`, and `Duration_Minutes`
- Filtering unrealistic values and outliers
- Saving the cleaned dataset in **Parquet** format for more efficient storage and faster loading

These steps produced a cleaner and more reliable dataset for analysis, machine learning, and visualization.

## Exploratory Data Analysis

The cleaned data was analyzed to identify patterns related to:

- Accident severity
- Hour of day
- Month
- State
- Day and night conditions
- Weather conditions
- Temperature
- Visibility
- Wind speed
- Accident duration

Aggregations and visualizations were used to explore relationships between these factors and accident frequency or severity.

## Accident Severity Prediction

A **Random Forest classifier** was developed using **PySpark MLlib** to predict accident severity.

The model used environmental, temporal, and accident-related features, including:

- Temperature
- Humidity
- Visibility
- Wind speed
- Precipitation
- Distance
- Hour
- Month
- Accident duration

The dataset was split into **80% training data** and **20% testing data**.

### Model Performance

| Metric | Score |
|---|---:|
| Accuracy | **79.33%** |
| Precision | 62.94% |
| Recall | 79.33% |
| F1-Score | **70.19%** |

The results demonstrate that historical accident characteristics contain useful information for predicting accident severity. However, class imbalance remains an important limitation because Severity 2 accidents represent the majority of records.

## Visualization and Interactive Dashboards

The project uses **Plotly** and **Dash** to transform the cleaned accident data into interactive visualizations that support data-driven decision making.

Two dashboards were developed.

### Dashboard 1 – Trends and Geographic Analysis

This dashboard focuses on:

- Accident severity distribution
- Accident frequency by hour
- Accident frequency by month
- States with the highest accident counts
- Day versus night accident distribution

### Dashboard 2 – Weather and Risk Analysis

This dashboard focuses on:

- Accident counts by weather condition
- Average accident severity by weather condition
- Average severity by hour
- Visibility across severity levels
- Accident duration across severity levels

Interactive filters allow users to explore accident patterns by state, severity, hour, and weather-related conditions.

## Key Findings

The analysis revealed several important patterns:

- Accident frequency showed clear peaks during the **morning and evening rush hours**.
- Approximately **69.6% of accidents occurred during daytime**, while nighttime accidents showed slightly higher average severity.
- **Fair weather** recorded the highest number of accidents, showing that accident frequency is not limited to poor weather conditions.
- Some less common adverse weather conditions were associated with higher average accident severity.
- More severe accidents generally remained active for longer periods.
- Weather, visibility, time, and accident duration provided useful information for understanding accident severity.
- The findings can support transportation authorities and emergency services in road safety planning, resource allocation, and emergency response.

## Repository Structure

```text
us-accidents-big-data-analysis/
├── data/
│   └── cleaned_data.parquet
├── notebooks/
│   └── us_accidents_big_data_analysis.ipynb
├── .gitignore
├── README.md
└── requirements.txt
```

The original sampled CSV is not included in the repository because its file size exceeds GitHub's normal per-file upload limit.

## Installation and Usage

Clone the repository:

```bash
git clone https://github.com/eman2301/us-accidents-big-data-analysis.git
cd us-accidents-big-data-analysis
```

Install the required Python packages:

```bash
pip install -r requirements.txt
```

The cleaned dataset is available at:

```text
data/cleaned_data.parquet
```

To run the complete preprocessing workflow from the beginning, place the original sampled dataset inside the `data/` directory with the filename:

```text
US_Accidents_March23_sampled_500k.csv
```

Then open:

```text
notebooks/us_accidents_big_data_analysis.ipynb
```

and run the notebook cells in order.

## Technologies Used

- Python
- Polars
- PySpark
- PySpark MLlib
- Random Forest
- Plotly
- Dash
- Pandas
- Parquet
- Jupyter Notebook
