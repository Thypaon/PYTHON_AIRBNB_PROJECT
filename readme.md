# Airbnb Listings Data Analysis

This project analyzes Airbnb listings in New York for 2024. The dataset is explored, cleaned, and visualized to uncover insights about pricing, availability, and neighborhood trends.

## Table of Contents

1. [Introduction](#introduction)
2. [Dataset Overview](#dataset-overview)
3. [Steps Performed](#steps-performed)
4. [Key Insights](#key-insights)
5. [Installation](#installation)
6. [Usage](#usage)

---

### Introduction

This project aims to analyze Airbnb listings to:
- Understand pricing patterns.
- Identify geographical trends.
- Explore correlations between variables like reviews, availability, and neighborhood.

### Dataset Overview

- **Filename**: `new_york_listings_2024.csv`
- **Attributes**:
  - Listing ID, Host ID, Neighborhood Group, Room Type, Price, Beds, etc.
- **Source**: Airbnb platform

### Steps Performed

1. **Loading Libraries**
   - Used libraries: `pandas`, `numpy`, `matplotlib`, `seaborn`.

2. **Data Import and Overview**
   - Loaded dataset and previewed using `.head()`, `.tail()`.
   - Checked dataset dimensions using `.shape` and data types using `.info()`.

3. **Data Cleaning**
   - Removed duplicate rows:
     ```python
     data.drop_duplicates(inplace=True)
     ```
   - Converted data types for `id` and `host_id` to `object`.
   - Dropped rows with missing values:
     ```python
     data.dropna(inplace=True)
     ```

4. **Exploratory Data Analysis (EDA)**
   - Identified outliers in the `price` column:
     ```python
     sns.boxplot(data=df, x='price')
     ```
   - Created new feature `price per bed`:
     ```python
     df['price per bed'] = df['price'] / df['beds']
     ```
   - Examined geographical distribution using longitude and latitude.

5. **Visualizations**
   - **Price Distribution**:
     ```python
     sns.histplot(data=df, x='price', bins=100)
     ```
   - **Geographical Distribution**:
     ```python
     sns.scatterplot(data=df, x='longitude', y='latitude', hue='room_type')
     ```
   - **Heatmap of Correlations**:
     ```python
     sns.heatmap(data=corr, annot=True)
     ```

### Key Insights

- **Outliers**:
  - Listings with prices above $1500 were excluded from analysis.
- **Neighborhood Trends**:
  - Pricing patterns vary significantly by neighborhood group and room type.
- **Geographical Distribution**:
  - Most listings are clustered around key locations.
- **Correlation Analysis**:
  - Availability and reviews show moderate correlation with price.

### Installation

Ensure the following libraries are installed:

```bash
pip install pandas numpy matplotlib seaborn
```

### Usage

1. Place the dataset `new_york_listings_2024.csv` in your working directory.
2. Run the Python script to perform analysis:

```python
python airbnb_analysis.py
```

3. Explore the visualizations and insights generated.