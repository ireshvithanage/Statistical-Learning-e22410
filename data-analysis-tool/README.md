# Data-Analysis-Tool

A powerful Python toolkit built for data preprocessing, exploration, and interactive visualization, especially optimized for Google Colab workflows. It streamlines common data workflows such as cleaning, missing value handling, outlier detection, feature scaling, and statistical relationship analysis.

## Features

* **Smart Data Loading**: Automatically detects and standardizes common missing-value markers (such as `?`, `N/A`, `NULL`) and attempts to infer correct data types for each column.

* **Full Dataset Overview**: Instantly provides dataset shape, data type distribution, and detailed statistical summaries for both numerical and categorical features.

* **Automated Data Cleaning**:

  * Fill missing values using mean, median, mode, or fixed constants.
  * Detect and eliminate duplicate records efficiently.
  * Identify and remove outliers using IQR-based filtering.
  * Supports interactive row and column removal for flexible preprocessing.

* **Advanced Feature Scaling & Encoding**:

  * **Numerical features**: Supports Min-Max scaling, Z-score standardization, and Robust scaling for outlier-heavy data.
  * **Categorical features**: Offers One-Hot encoding, Ordinal encoding, and frequency-based encoding options.

* **Rich Interactive Visualizations** (built with Plotly):

  * Violin plots, scatter plots, histograms, and grouped bar charts.
  * Automatically adapts visualization type based on data structure.

* **Deep Statistical Analysis Tools**:

  * Pearson correlation heatmaps for numerical variables.
  * Cramér’s V for categorical variable relationships.
  * Combined association heatmaps using statistical tests such as point-biserial correlation and ANOVA-based measures.

## Installation

```bash
# Standard installation
pip install "git+https://github.com/ireshvithanage/Statistical-Learning-e22410"

# Optional: install with full visualization support
pip install data-analysis-tool[plotting]
```

## Quick Start (Typical Workflows)

This toolkit is designed primarily for **Google Colab environments**, enabling interactive and fast data processing.

### 1. Data Cleaning & Missing Value Handling

Load and prepare your dataset in a streamlined workflow.

```python
from data_analysis import DataInspector

inspector = DataInspector()

# Upload dataset interactively in Colab
inspector.upload_data()

# Fill missing values using median imputation
inspector.handle_missing_values(strategy='median')

# Remove duplicate rows
inspector.remove_duplicates()
```

### 2. Exploratory Data Analysis (EDA)

Generate quick visual summaries of your data.

```python
# Visualize distributions of numerical columns
inspector.plot_numerical(['Age', 'Salary'])

# Explore relationships between variables
inspector.plot_relationship('Department', 'Salary')
```

### 3. Feature Scaling & Encoding for ML

Prepare your dataset for machine learning models.

```python
# Apply Robust Scaling for better handling of outliers
normalized_numeric = inspector.extract_normalized_numeric_data(method='robust')

# Convert categorical variables using One-Hot Encoding
encoded_cat = inspector.extract_normalized_categorical_data(method='onehot')

# Combine processed features into a final dataset
final_df = inspector.create_normalized_data_df()
```

### 4. Statistical Relationship Mapping

Discover hidden patterns across variables.

```python
# Generate a full association heatmap across numeric and categorical features
inspector.plot_all_associations_heatmap()
```

### 5. Custom Visualization Tools

The `PlottingMethods` class allows fine-grained control over charts. Outputs are returned as Plotly-compatible HTML objects.

#### Bar Charts

```python
result = plotter.plot_bar_chart(
    x='Department',
    y='Salary',
    color='Gender',
    barmode='group',
    data=my_json_data
)
plotter.display_image(result)
```

#### Pie Charts

```python
result = plotter.plot_pie_chart(
    names='Category',
    values='Total',
    hole=0.4,
    title='Revenue Distribution'
)
plotter.display_image(result)
```

#### Histograms

```python
result = plotter.plot_histogram(
    x='Age',
    bins=[0, 18, 35, 60, 100],
    title='Age Distribution'
)
plotter.display_image(result)
```

### 6. Google Colab Rendering Note

To properly display Plotly outputs from `PlottingMethods`, always use the built-in rendering helper:

```python
result = inspector.plot_bar_chart(...)
inspector.display_image(result)
```

## Project Structure

```text
data-analysis-tool/
├── data_analysis/
│   ├── __init__.py
│   └── core.py        # Core implementation: DataInspector & PlottingMethods
├── pyproject.toml     # Build and dependency configuration
└── README.md
```

## Authors

* **Mugalan** – [ireshvithanage2003@gmail.com](mailto:ireshvithanage2003@gmail.com)
