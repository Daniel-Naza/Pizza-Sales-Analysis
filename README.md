# 🍕 Pizza Place Sales Analysis

A comprehensive exploratory data analysis (EDA) of a full year of sales data
from a fictitious pizza restaurant, carried out using Python in a Jupyter Notebook.

---

## 📁 Dataset

The dataset contains four CSV files covering the year 2015:

| File | Description |
|------|-------------|
| `orders.csv` | Order ID, date, and time of each order |
| `order_details.csv` | Pizza ID and quantity per order |
| `pizzas.csv` | Pizza size and price per pizza SKU |
| `pizza_types.csv` | Pizza name, category, and ingredients |

---

## 🛠️ Tools & Libraries Used

- **Python 3** — core programming language
- **Pandas** — data loading, merging, and analysis
- **Matplotlib** — base plotting library
- **Seaborn** — advanced chart styling and visualisation

---

## 🔄 Analysis Workflow

### Step 1 — Load the Data
All four CSV files were loaded into separate Pandas DataFrames.
The `encoding='latin-1'` parameter was used to handle special
characters found in the ingredients column of the pizza types file.

### Step 2 — Merge Into One DataFrame
The four tables were joined into a single combined DataFrame using
Pandas `.merge()` on their shared key columns:

- `order_details` + `orders` → joined on `order_id`
- Result + `pizzas` → joined on `pizza_id`
- Result + `pizza_types` → joined on `pizza_type_id`

This produced a single DataFrame of **48,620 rows × 12 columns**,
containing every order with its full pizza details, price, date, and time.

### Step 3 — Feature Engineering
New columns were created from existing data to enable deeper analysis:

- **`revenue`** — calculated as `quantity × price` per row
- **`hour`** — extracted from the time column for peak hours analysis
- **`day_of_week`** — extracted from the date column for weekly trends
- **`month`** — extracted from the date column for monthly trends
- **`month_num`** — numeric month (1–12) for correct chronological sorting

### Step 4 — Key Business Metrics
Five headline figures were calculated to provide an overall business snapshot:

- Total revenue
- Total quantity of pizzas sold
- Total number of unique orders
- Number of unique pizza types on the menu
- Average price across all pizza SKUs

### Step 5 — Peak Hours Analysis
Orders were grouped by hour of the day using `.groupby("hour")`.
`nunique()` on the order ID column was used to count distinct orders
per hour rather than just row counts. A seaborn bar chart was plotted
to reveal the busiest and quietest hours of operation.

### Step 6 — Sales by Day of the Week
Revenue was grouped by day of the week and reindexed in Monday–Sunday
order to maintain a logical sequence on the chart. A seaborn bar chart
with a `coolwarm` palette was used to visually contrast high and low days.

### Step 7 — Top 5 Best-Selling Pizzas
Total quantity sold was aggregated per pizza name, sorted in descending
order, and the top 5 were extracted using `.head(5)`. A horizontal
seaborn bar chart was used to clearly display and compare the leaders.

### Step 8 — Monthly Sales Trend
Revenue was grouped by numeric month to ensure chronological sorting,
then mapped to short month name labels (Jan–Dec) for the x-axis.
A seaborn line chart with a filled area underneath was used to show
the revenue trend across the full year.

### Step 9 — Underperforming Pizzas
Total quantity sold was sorted in ascending order and the bottom 5
pizzas were identified. A seaborn horizontal bar chart with a red
palette was used to signal poor performance visually.

### Step 10 — Revenue by Pizza Category
Revenue was grouped across the four menu categories: Classic, Supreme,
Chicken, and Veggie. A seaborn bar chart with the `Set2` palette was
used to compare category performance side by side.

### Step 11 — Sales by Pizza Size
Quantity sold was grouped by pizza size and reindexed in logical
order from S to XXL. A seaborn bar chart with a `Blues_d` palette
was used to compare size popularity across the menu.

---

## 📊 Key Findings

| Metric | Value |
|--------|-------|
| Total Revenue | \$817,860 |
| Total Orders | 21,350 |
| Total Pizzas Sold | 49,574 |
| Unique Pizza Types | 32 |
| Average Pizza Price | \$16.44 |
| Busiest Hour | 12pm |
| Best Sales Day | Friday |
| Best Sales Month | July |
| Top Selling Pizza | Classic Deluxe |
| Worst Selling Pizza | Brie Carre |

---

## 💡 Business Insights

- **Peak hours are 12pm and 1pm** — the lunch rush drives the highest
  order volumes of the day, followed by a second peak at 6pm for dinner.

- **Friday is the strongest day** generating \$136,074 in revenue —
  nearly 37% more than Sunday, the weakest day at \$99,204.

- **July is the best month** with \$72,558 in revenue, while October
  is the slowest at \$64,028. Revenue is relatively stable year-round
  with a mild summer peak.

- **The top 5 bestsellers are very close in sales volume**, suggesting
  the menu is well-balanced with no single pizza dominating.

- **The Brie Carre Pizza is severely underperforming** with only 490
  units sold — nearly 5× fewer than the top seller. It is a strong
  candidate for removal or reformulation.

- **All four pizza categories contribute almost equally to revenue**,
  showing a well-diversified menu without over-reliance on any one type.

- **Large pizzas are the most popular size** while XL and XXL sizes
  have very low uptake, suggesting pricing or awareness may be barriers.

---
---

## 👤 Author

**Daniel Chinaza Anyirionye**  
Medical Laboratory Scientist | Data Science Student  
TechCrush Data Science Cohort 2026
