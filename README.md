
# 📊 Marketing Campaign Data Optimization

A Python-based data analysis project focused on cleaning, preprocessing, and evaluating messy marketing campaign data to identify the most cost-effective marketing channels across seasonal promotions.

## 📌 Project Overview

The objective of this project is to transform raw, inconsistent marketing campaign data into a clean, structured, and analysis-ready dataset. Using Python, Pandas, and NumPy, the project addresses data quality issues, standardizes campaign metrics, engineers new features, and evaluates marketing performance using key performance indicators (KPIs).

### Key Objectives

- Clean and standardize messy marketing campaign data.
- Handle missing values, duplicate columns, and extreme outliers.
- Normalize categorical values and Boolean fields.
- Correct invalid campaign date ranges.
- Extract seasonal information from campaign names.
- Calculate Cost Per Acquisition (CPA) and conversion rates.
- Identify the most cost-effective marketing channels.
- Analyze campaign tag efficiency to support data-driven marketing decisions.

## 📂 Dataset Overview

**Dataset:** `marketing_campaign_data_messy.csv`

The original dataset contains **2,020 records and 12 initial columns**.

### Key Features

| Column | Description |
|---|---|
| `Campaign_ID` | Unique campaign identifier |
| `Campaign_Name` | Name of the marketing campaign |
| `Start_Date` | Campaign start date |
| `End_Date` | Campaign end date |
| `Channel` | Marketing channel used |
| `Impressions` | Number of times an advertisement was displayed |
| `Clicks` | Number of clicks generated |
| `Spend` | Total campaign expenditure |
| `Conversions` | Number of conversions generated |
| `Active` | Indicates whether a campaign is active |
| `Campaign_Tag` | Campaign classification or messaging tag |

The dataset contains duplicated columns, missing values, extreme outliers, inconsistent categorical formatting, and invalid date ranges that require preprocessing.

## 🧹 Data Cleaning and Preprocessing

### 1. Column Standardization
- Removed leading and trailing whitespace from column names.
- Converted column names to lowercase.
- Replaced spaces with underscores for consistent naming conventions.
- Removed duplicated columns, including redundant click features.

### 2. Currency Formatting
- Removed currency symbols such as `$` from the `spend` column.
- Extracted numeric values using regular expressions.
- Converted spend values into floating-point numbers.

### 3. Categorical Normalization

Corrected inconsistent marketing channel names and typographical errors.

Examples:

- `Insta_gram` → `Instagram`
- `Facebok` → `Facebook`
- `Tik_Tok` → `TikTok`
- `Gogle` → `Google Ads`

### 4. Boolean Standardization

Converted inconsistent values in the `active` column into standardized Boolean values.

- `Y`, `Yes`, and `1` → `True`
- `No` and `0` → `False`

### 5. Datetime Conversion
- Converted `start_date` and `end_date` into native datetime objects.
- Identified invalid campaign date ranges.
- Corrected campaigns whose end dates occurred before their start dates by enforcing a standard 30-day duration.

### 6. Outlier Handling

Applied the **Interquartile Range (IQR)** method to identify extreme spending values.

Spend outliers were capped at the upper IQR boundary to reduce the influence of unusually high values on campaign performance analysis.

### 7. Deduplication and Missing Values
- Removed duplicate records and redundant columns.
- Removed records with missing or invalid marketing channels.
- Improved data consistency for reliable channel-level comparisons.

## ⚙️ Feature Engineering

### 1. Seasonality Extraction

Created a new categorical feature named `season` by extracting seasonal identifiers from the `campaign_name` column using regular expressions.

The seasonal categories include:

- Summer
- Winter
- Launch
- BlackFriday

### 2. Cost Per Acquisition (CPA)

Calculated campaign-level CPA to measure the cost of acquiring a conversion.

**Formula:**

`CPA = Spend / Conversions`

NumPy's `np.where()` was used to handle zero-conversion cases and prevent division-by-zero errors.

A lower CPA generally indicates better acquisition cost efficiency.

### 3. Conversion Rate

Calculated the percentage of clicks that resulted in conversions.

**Formula:**

`Conversion Rate (%) = (Conversions / Clicks) × 100`

This metric helps evaluate how effectively marketing campaigns convert clicks into desired actions.

## 📈 Key Performance Insights

Campaign performance was evaluated by grouping total spend and total conversions by season and marketing channel.

Blended CPA was calculated using aggregated spend and conversions rather than averaging campaign-level CPA values.

**Blended CPA Formula:**

`Blended CPA = Total Spend / Total Conversions`

### Seasonal Channel Performance

| Season | Top Channel | Blended CPA | Total Spend |
|---|---|---:|---:|
| BlackFriday | Instagram | $3.06 | $53,379.15 |
| Launch | Facebook | $2.83 | $48,377.90 |
| Summer | Google Ads | $2.89 | $44,926.65 |
| Winter | Facebook | $3.18 | $61,951.41 |

### Key Findings

**1. Facebook Demonstrates Versatility**

Facebook was the most cost-efficient channel during both the Launch and Winter seasons, demonstrating strong performance across different promotional periods.

**2. Launch Campaigns Achieve the Lowest Blended CPA**

Facebook recorded a blended CPA of **$2.83** during the Launch season, the lowest among the reported seasonal channel combinations.

**3. Google Ads Performs Well During Summer**

Google Ads achieved a blended CPA of **$2.89** for Summer campaigns, indicating strong acquisition efficiency.

**4. Instagram Performs Best During BlackFriday**

Instagram recorded a blended CPA of **$3.06** during BlackFriday campaigns, making it the most cost-efficient channel for that season.

**5. Campaign Tags Reveal Optimization Opportunities**

The BlackFriday campaign tag analysis identified `INVALID`, `IN`, and `TI` as the most cost-efficient messaging segments based on reported tag-level CPA.

These tags should be validated before being used to guide future marketing decisions, particularly the `INVALID` category.

## 💡 Marketing Recommendations

Based on the reported analysis:

- **Prioritize Facebook for Launch campaigns:** Its $2.83 blended CPA makes it a strong candidate for future launch promotions.
- **Optimize Winter campaigns:** Investigate opportunities to reduce Facebook's $3.18 blended CPA.
- **Leverage Google Ads during Summer:** Evaluate opportunities to scale campaigns while monitoring marginal acquisition costs.
- **Improve BlackFriday performance:** Analyze Instagram's successful targeting, creative formats, and audience segments.
- **Validate campaign tags:** Review `INVALID`, `IN`, and `TI` to ensure meaningful and reliable segmentation.
- **Monitor KPIs continuously:** Track spend, conversions, CPA, and conversion rates to measure campaign efficiency over time.

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| Pandas | Data cleaning, transformation, and aggregation |
| NumPy | Numerical calculations and conditional logic |
| Matplotlib | Data visualization |
| Seaborn | Statistical visualization and exploratory data analysis |

## 📁 Project Structure

```text
marketing-campaign-data-optimization/
│
├── data/
│   └── marketing_campaign_data_messy.csv
│
├── notebooks/
│   └── marketing_campaign_analysis.ipynb
│
├── README.md
└── requirements.txt
```

*Adjust the folder structure to match your actual repository.*

## 🚀 Getting Started

### Prerequisites

- Python 3.x
- pip

### 1. Clone the Repository

```bash
git clone <your-repository-url>
cd marketing-campaign-data-optimization
```

### 2. Install Dependencies

```bash
pip install pandas numpy matplotlib seaborn
```

Alternatively, add the following to `requirements.txt`:

```text
pandas
numpy
matplotlib
seaborn
```

Install the dependencies:

```bash
pip install -r requirements.txt
```

### 3. Prepare the Dataset

Place `marketing_campaign_data_messy.csv` in the appropriate project directory and update the file path in your Python script or notebook if necessary.

### 4. Run the Analysis

If using Jupyter Notebook:

```bash
jupyter notebook
```

Open `marketing_campaign_analysis.ipynb` and execute the cells sequentially.

If using a Python script:

```bash
python marketing_campaign_analysis.py
```

## 📊 Expected Outcomes

The project produces a cleaned and analysis-ready dataset with standardized campaign information and additional performance metrics.

Expected outcomes include:

- Improved data quality and consistency.
- Standardized campaign dates, channels, and Boolean values.
- Reduced influence of extreme spending outliers.
- Seasonal campaign segmentation.
- Campaign-level CPA and conversion rate calculations.
- Blended CPA comparisons across seasons and channels.
- Campaign tag efficiency analysis.
- Data-driven recommendations for marketing budget optimization.

## 🔮 Future Improvements

- Develop interactive dashboards using Power BI, Tableau, or Plotly.
- Add automated data quality validation checks.
- Calculate Return on Ad Spend (ROAS).
- Evaluate statistical significance across marketing channels.
- Analyze campaign performance trends over time.
- Automate marketing KPI reporting.
- Build predictive models for campaign conversions and spending efficiency.
- Improve campaign tag validation and categorization.

## 🏁 Conclusion

The **Marketing Campaign Data Optimization** project demonstrates how data cleaning, feature engineering, and KPI analysis can transform messy marketing data into actionable business insights.

By standardizing campaign metrics and evaluating blended CPA across seasonal promotions, the analysis identifies cost-efficient marketing channels and highlights opportunities for improving campaign performance.

The findings provide a foundation for data-driven marketing decisions, improved budget allocation, and continuous campaign optimization.
