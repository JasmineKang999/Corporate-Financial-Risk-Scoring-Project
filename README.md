# Corporate-Financial-Risk-Scoring-Project

## Project Overview
This project aims to assess the financial risk of listed companies based on their financial statements using a multi-dimensional scoring approach. It calculates a risk score for each company by combining balance sheet, income statement, and cash flow data, without requiring prior knowledge of industry classification.
The methodology is unsupervised and interpretable, allowing users to identify companies with high financial risk and the main contributing factors.

## Data Sources
The project uses three financial statements:
* **Balance Sheet**:
Key indicators: Total Assets, Total Liabilities, Cash, Accounts Receivable, Inventory, Accounts Payable, Advance Receipts, Equity, Debt-to-Asset Ratio
* **Income Statement**:
Key indicators: Revenue, Net Profit, Total Expenses, Operating Profit, Total Profit
* **Cash Flow Statement**:
Key indicators: Operating Cash Flow, Operating Cash Flow Ratio, Cash Flow Year-over-Year Growth
The data used in this project is for demonstration purposes (e.g., 2023 fiscal year) and comes from publicly available sources.

## Methodology
The project follows a multi-step pipeline:
* **1.Data Cleaning and Standardization**:
Select relevant columns from the three statements
Rename columns to English for consistency
Handle missing values and infinities
* **2.Feature Engineering**:
Compute financial ratios that reflect solvency, profitability, and cash flow quality:
 * Leverage: total_liabilities / total_assets
 * Cash-to-Debt Ratio: cash / total_liabilities
 * Operating Asset Ratio: (accounts_receivable + inventory) / total_assets
 * Operating Liability Ratio: (accounts_payable + advance_receipts) / total_liabilities
 * Profitability Ratios: gross_margin, net_profit_ratio, operating_profit_ratio, profit_to_total_profit
 * Cash Flow Ratios: cash_profit_ratio, cashflow_to_debt, ocf_ratio, ocf_growth
* **3.Risk Scoring**:
 * Standardize indicators using z-score
 * Adjust the direction: higher values indicate higher risk for some indicators, lower for others
 * Combine all indicators to calculate a final risk_score (0–100)
 * Each individual indicator also produces a zscore for interpretability
* **4.Output**:
CSV table containing:
 * company_name, stock_code, risk_score
 * Individual z-scores for all indicators (leverage_z, cash_to_debt_z, etc.)

## Notes
* The risk score is relative among the companies in the dataset. 
* A high risk_score does not necessarily imply imminent failure but indicates comparatively higher financial risk.

