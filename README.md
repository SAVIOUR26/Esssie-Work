# Sales Data Analysis 2024

## Overview

This project performs exploratory and descriptive data analysis on **400 sales transactions** recorded by a Uganda-based business across January–September 2024. The dataset covers three product categories (Electronics, Furniture, Stationery), seven regions, six sales representatives, and five sales channels, with all monetary values denominated in **Ugandan Shillings (UGX)**.

---

## Dataset: `sales_data_2024.csv`

| Property | Value |
|---|---|
| Records | 400 transactions |
| Columns | 21 fields |
| Period | January 10 – September 9, 2024 |
| Currency | UGX (Ugandan Shillings) |

### Column Reference

| Column | Type | Description |
|---|---|---|
| `order_id` | String | Unique order identifier (format: ORD-####) |
| `date` | Date | Transaction date (M/D/YYYY) |
| `month` | String | Month name |
| `quarter` | String | Quarter (Q1–Q4) |
| `product` | String | Product name |
| `category` | String | Product category |
| `unit_price_ugx` | Numeric | Price per unit in UGX |
| `quantity` | Numeric | Units sold per order |
| `gross_revenue_ugx` | Numeric | Revenue before discount |
| `discount_pct` | Numeric | Discount percentage (0–15%) |
| `discount_amount_ugx` | Numeric | Discount value in UGX |
| `net_revenue_ugx` | Numeric | Revenue after discount |
| `cost_ugx` | Numeric | Cost of goods sold |
| `profit_ugx` | Numeric | Net profit |
| `profit_margin_pct` | Numeric | Profit margin (%) |
| `region` | String | Geographic region in Uganda |
| `sales_rep` | String | Sales representative name |
| `payment_method` | String | Payment method used |
| `channel` | String | Sales channel |
| `status` | String | Order status |
| `customer_type` | String | New or Returning customer |

### Categorical Breakdowns

| Dimension | Values |
|---|---|
| **Categories** | Electronics, Furniture, Stationery |
| **Regions** | Kampala Central, Wakiso, Mukono, Jinja, Entebbe, Mbarara, Gulu |
| **Sales Reps** | Brian Okello, Grace Nalwoga, James Ssempa, Lydia Atim, Peter Mugisha, Sarah Nakato |
| **Payment Methods** | Bank Transfer, MTN MoMo, Airtel Money, Flutterwave, Cash |
| **Channels** | Walk-in, Online, Agent, Phone Order, WhatsApp |
| **Order Status** | Completed, Pending, Refunded |
| **Customer Type** | New, Returning |

---

## Analysis Objectives

The analysis addresses the following business questions:

### Revenue & Profitability
- What is the total net revenue and profit for the period?
- Which months and quarters show the strongest / weakest performance?
- Which product category generates the highest profit margin?
- How much revenue is lost to discounts, and which products are discounted most?

### Product Performance
- Which products are top sellers by quantity and by revenue?
- Which products have the highest and lowest profit margins?
- How does category mix shift across quarters?

### Regional Performance
- Which regions contribute the most revenue and profit?
- Are there regional differences in product preference or payment method?

### Sales Rep Performance
- How does net revenue and profit compare across the six sales reps?
- Which rep handles the most orders, and which achieves the highest average order value?

### Channel & Payment Analysis
- Which sales channel drives the most orders and revenue?
- What share of transactions use mobile money (MTN MoMo / Airtel Money) vs. other methods?

### Customer Analysis
- What is the split between new and returning customers?
- Do returning customers have higher average order values?

### Order Quality
- What percentage of orders are Completed vs. Pending vs. Refunded?
- Which products or channels have the highest refund rates?

---

## Repository Structure

```
Esssie-Work/
├── README.md               # This file
└── sales_data_2024.csv     # Raw transaction data
```

---

## Getting Started

### Prerequisites

```bash
pip install pandas matplotlib seaborn plotly openpyxl jupyter
```

### Quick Load (Python)

```python
import pandas as pd

df = pd.read_csv("sales_data_2024.csv")
df["date"] = pd.to_datetime(df["date"])
print(df.shape)         # (400, 21)
print(df.dtypes)
print(df.describe())
```

### Key Aggregations to Start With

```python
# Total revenue and profit
print(df[df["status"] == "Completed"][["net_revenue_ugx", "profit_ugx"]].sum())

# Revenue by category
df.groupby("category")["net_revenue_ugx"].sum().sort_values(ascending=False)

# Profit margin by product
df.groupby("product")["profit_margin_pct"].mean().sort_values(ascending=False)

# Monthly trend
df.groupby("month")["net_revenue_ugx"].sum()

# Top sales rep by net revenue
df.groupby("sales_rep")["net_revenue_ugx"].sum().sort_values(ascending=False)
```

---

## Data Notes

- Filter to `status == "Completed"` for clean revenue/profit aggregations; exclude Refunded orders from totals.
- `profit_ugx = net_revenue_ugx - cost_ugx` — verify this holds before analysis.
- Dates are in M/D/YYYY format; parse with `pd.to_datetime()`.
- All monetary values are in UGX. As of mid-2024, ~1 USD ≈ 3,700 UGX.
