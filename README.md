Global Food Prices Analysis & Predictive Modeling (2026)
An end-to-end data analysis and machine learning pipeline investigating global food market dynamics across 59 countries using 84,920 cleaned records from the 2026 World Food Programme (WFP) dataset. Developed as a collaborative capstone project under the NTI Advanced Data Analysis Training, this repository bridges descriptive data exploration, relational data modeling, interactive business intelligence, and leakage-controlled predictive regression.

👥 Project Team
Shahd Fawzy

Youssef Nasser Omar

Ahmed Abbas Ebedy

Menna Mahmoud

Marina Hany

🛠️ Multi-Tool Workflow & Architecture
To ensure robust validation and comprehensive data coverage, the project spans five distinct analytical layers, each addressing a specialized stage of the workflow:

Tool / Technology	Core Responsibility in Pipeline
Microsoft Excel	Rapid exploratory data validation, Power Query data cleaning, and foundational PivotTable aggregations.
Power BI	Relational data modeling (Star Schema), custom DAX measures, a dynamic Dim_Date table, and an executive BI dashboard.
Tableau Public	Advanced visual data exploration, geographic market mapping, and multi-parameter interactive filtering.
Python (Colab / Jupyter)	Exploratory Data Analysis (EDA), automated data quality audits, correlation analysis, and custom visualizations (pandas, numpy, matplotlib, seaborn, plotly).
Machine Learning	Leakage-controlled regression modeling (GroupShuffleSplit), preprocessing pipelines, target transformation testing, and hyperparameter optimization (Scikit-Learn, XGBoost).
📊 Key Analytical Insights
Category Cost Disparities: Meat, fish, and eggs represent by far the most expensive food category globally, averaging $402.24 USD, whereas basic staples like cereals, tubers, and vegetables average under $20 USD.

Crisis-Driven Price Peaks: Countries experiencing severe conflict or economic vulnerability—such as Syria ($397 USD), South Sudan ($342 USD), and Somalia ($261 USD)—exhibit the highest average food costs.

Temporal Volatility: Global food prices experienced a sharp inflationary surge during early spring 2026, peaking in April before stabilizing toward lower levels by year-end.

Market Structure: Retail listings dominate the dataset (~81.04% of observations) with higher average valuations, while wholesale listings account for ~18.96%.

🤖 Machine Learning Predictive Modeling
Moving beyond descriptive diagnostics, a rigorous regression pipeline was built to predict food prices (usdprice per KG) based on geographic, market, commodity, and temporal attributes.

Modeling Population & Filtering: Restricted to Retail prices, actual price flags, and KG units to maintain a consistent physical measurement basis, resulting in 41,944 records.

Leakage Control: A compound group key (countryiso3_market_commodity) was applied within GroupShuffleSplit (80/20 train-test split) to ensure zero overlapping groups between training and testing subsets, preventing spatial-group data leakage.

Model Performance Comparison
All evaluation metrics were calculated on the same held-out test set and reported on the original USD/kg scale:

Model Configuration	Target Scale	MAE (USD/kg)	RMSE (USD/kg)	
R 
2
 
 Score	Status
Linear Regression	Log-Target	3.0694	15.6676	0.9492	Baseline
Basic XGBoost	Raw-Target	2.3594	11.3357	0.9734	Iteration 2
Tuned XGBoost	Raw-Target	2.2316	11.2245	0.9739	Final Model 🏆
Note: The machine learning implementation functions as a spatial-categorical prediction framework rather than a chronological time-series forecasting model, as the filtered snapshot spans five observation dates within 2026.

🗂️ Repository Structure
Plaintext
wfp-global-food-prices-2026/
│
├── data/                         # Cleaned and raw dataset files (.csv, .xlsx)
├── notebooks/                    # Python Jupyter notebooks (EDA, Cleaning, ML Pipeline)
├── dashboards/                   # Power BI (.pbix) and Tableau workbook files
├── reports/                      # Final project documentation and presentation slides
└── README.md                     # Project documentation (this file)
🚀 Getting Started & Installation
1. Clone the Repository
Bash
git clone https://github.com/your-username/wfp-global-food-prices-2026.git
cd wfp-global-food-prices-2026
2. Install Dependencies
Ensure you have Python installed, then install the required libraries:

Bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost openpyxl
3. Execution
Open the Jupyter notebooks located in the notebooks/ directory or execute the Python scripts to replicate data preprocessing, exploratory visualization plots, and the optimized XGBoost regression pipeline.
