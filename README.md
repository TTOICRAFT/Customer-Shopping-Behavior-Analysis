# Customer Shopping Behavior Analysis

An end-to-end retail analytics project exploring customer purchase patterns, product preferences, discounts, shipping, and subscriptions. The goal is to turn transaction data into practical ideas for customer engagement, merchandising, and marketing.

## Project overview

The project analyzes **3,900 purchase records** across 25 products, 4 categories, and 50 locations. It combines Python data preparation, PostgreSQL analysis, and a Power BI dashboard, with a written report and stakeholder presentation.

The analysis explores questions such as:

- How does revenue vary by gender and age group?
- Which products receive the highest ratings or sell most often within each category?
- How do average purchase amounts compare across shipping types?
- Do subscribers spend more than non-subscribers?
- Which products have the highest share of purchases using discounts?
- How are customers distributed across new, returning, and loyal segments?

## Key findings

- The average purchase amount is **$59.76**, and the average review rating is **3.75**.
- The report identifies **37 missing review ratings** and fills them with the median rating for each product category.
- Average spend is nearly the same for subscribers (**$59.49**) and non-subscribers (**$59.87**), suggesting the current subscription offer may need a clearer value proposition.
- **839** customers used a discount and still spent above the overall average purchase amount, showing an opportunity to test targeted offers.
- The presentation highlights Gloves as the top-rated product and recommends strengthening the first-to-second-purchase journey, reviewing discount dependence, and targeting high-revenue age groups.

These are descriptive findings from the included dataset; they show patterns and opportunities to investigate, not proof that a particular factor caused spending behavior.

## Workflow

1. **Prepare data in Python:** Load the CSV with pandas, inspect summary statistics and missing values, impute missing review ratings by category median, standardize column names, create age-group and purchase-frequency features, and check whether the discount and promo-code fields are redundant.
2. **Analyze with PostgreSQL:** Load the cleaned data into a `customer` table and use the SQL queries to answer the business questions.
3. **Visualize in Power BI:** Explore the results in the interactive dashboard.
4. **Communicate recommendations:** Review the PDF analysis report and the growth-moves presentation.

## Repository contents

| File | Description |
|---|---|
| `customer_shopping_behavior.csv` | Source purchase dataset |
| `Customer_Shopping_Behavior_Analysis.ipynb` | Python cleaning, feature engineering, and PostgreSQL loading workflow |
| `customer_behavior_postgresql_queries.sql` | PostgreSQL business analysis queries |
| `customer_behavior_dashboard.pbix` | Power BI dashboard |
| `Customer Shopping Behavior Analysis.pdf` | Project analysis report |
| `Customer-shopping-behavior-translated-into-growth-moves.pptx` | Stakeholder presentation |
| `Business Problem  Document.pdf` | Business problem statement and deliverables |

## Tools

- Python and pandas
- Jupyter Notebook
- PostgreSQL
- SQLAlchemy and psycopg2
- Power BI Desktop

## Getting started

### 1. Prepare the Python environment

Install the notebook dependencies:

```bash
pip install pandas sqlalchemy psycopg2-binary jupyter
```

Open `Customer_Shopping_Behavior_Analysis.ipynb` in Jupyter and run the data preparation cells. The notebook reads `customer_shopping_behavior.csv` from the project directory.

### 2. Load the cleaned data into PostgreSQL

Create a PostgreSQL database (the notebook uses `customer_behavior` as its example database), then configure a local connection before running the loading cell. Keep credentials out of shared notebooks and source control; use environment variables or another local secrets mechanism.

The notebook writes the cleaned DataFrame to a table named `customer`. Run `customer_behavior_postgresql_queries.sql` against that database to reproduce the SQL analyses.

### 3. Open the dashboard and reports

Open `customer_behavior_dashboard.pbix` in Power BI Desktop. The PDF report and PowerPoint presentation provide a static walkthrough of the findings and recommendations.

## Recommendations from the analysis

- Test subscription benefits that offer clear customer value.
- Encourage the second purchase and reward repeat buyers.
- Target discounts where they may increase basket value, and monitor product-level discount reliance.
- Use top-rated and frequently purchased products in merchandising and campaigns.
- Focus campaigns on promising age groups and test express-shipping messaging with relevant customer segments.

## Notes

- The notebook imputes **37** missing values in `Review Rating` using category-level medians.
- The notebook derives `age_group` and `purchase_frequency_days`, and drops `promo_code_used` after checking it against `discount_applied`.
- The notebook contains machine-specific PostgreSQL connection settings. Configure your own local connection before running the database-loading cell.
- The dataset and analyses are observational; business recommendations should be validated with experiments and appropriate performance measures.
