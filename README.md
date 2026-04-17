# SQL---Sales--Analysis

End-to-end SQL analysis of pizza restaurant sales. Features data normalization, KPI tracking, and trend analysis to optimize staffing and inventory. From raw data to $817K in insights.


# Project Overview

In the competitive food and beverage industry, data-driven decision-making is key to maintaining profitability and operational efficiency. This project transforms raw transactional records into structured business intelligence by performing a full SQL analysis on a year's worth of pizza sales data.
The analysis identifies critical sales trends, customer behavior patterns, and product performance metrics to provide actionable recommendations for inventory optimization, marketing strategy refinement, and revenue maximization.

# Database Schema

Database Schema

The project uses a MySQL database named `pizzaclub` with the following tables:

### `orders`
| Column | Type | Constraint |
|--------|------|------------|
| `order_id` | INT | PRIMARY KEY, NOT NULL |
| `order_date` | DATE | NOT NULL |
| `order_time` | TIME | NOT NULL |

### `orders_details`
| Column | Type | Constraint |
|--------|------|------------|
| `order_details_id` | INT | PRIMARY KEY, NOT NULL |
| `order_id` | INT | NOT NULL |
| `pizza_id` | TEXT | NOT NULL |
| `quantity` | INT | NOT NULL |

> Additional referenced tables: `pizzas` (pizza_id, price, size) and `pizza_types` (pizza_type_id, name, category)

---

## Key Analysis & SQL Queries

### Basic Level

| # | Analysis | Result |
|---|----------|--------|
| 1 | Total number of orders placed | **21,350** |
| 2 | Total revenue from pizza sales | **$817,860.05** |
| 3 | Highest-priced pizza | **The Greek Pizza — $35.95** |
| 4 | Most common pizza size ordered | **Large (L) — 18,526 orders** |
| 5 | Top 5 most ordered pizza types | Classic Deluxe, BBQ Chicken, Hawaiian, Pepperoni, Thai Chicken |

### Intermediate Level
| # | Analysis | Result |
|---|----------|--------|
| 6 | Total quantity per pizza category | Classic: 14,888 · Supreme: 11,987 · Veggie: 11,649 · Chicken: 11,050 |
| 7 | Order distribution by hour of day | Peak hours at **12:00 (2,520)** and **17:00–18:00** |
| 8 | Category-wise pizza distribution | Chicken: 6 · Classic: 8 · Supreme: 9 · Veggie: 9 |
| 9 | Average pizzas ordered per day | **138 pizzas/day** |
| 10 | Top 3 pizzas by total revenue | Thai Chicken ($43,434) · BBQ Chicken ($42,768) · CA Chicken ($41,409) |

### Advanced Level

| # | Analysis | Result |
|---|----------|--------|
| 11 | Revenue contribution % by category | Classic: 26.91% · Supreme: 25.46% · Chicken: 23.96% · Veggie: 23.68% |
| 12 | Cumulative revenue over time | Tracked daily from 2015-01-01 onwards |
| 13 | Top 3 pizzas by revenue per category | Ranked using `RANK() OVER (PARTITION BY category)` window function |

---

## Key Findings

- **Top Revenue Generator:** The Thai Chicken Pizza leads with over $43,400 in total revenue, despite not being the most ordered by volume.
- **Most Popular by Volume:** The Classic Deluxe Pizza (2,453 units) and Barbecue Chicken Pizza (2,432 units) top the order count.
- **Customer Size Preference:** Customers overwhelmingly prefer **Large (L)** size — 18,526 orders vs. 15,385 Medium and 14,137 Small.
- **Category Dominance:** The **Classic category** is the primary driver for both volume and revenue (~26.91% of total sales).
- **Peak Hours:** Lunch rush peaks at **12:00–13:00** (2,520 / 2,455 orders) and dinner rush at **17:00–18:00** (2,336 / 2,399 orders).
- **Revenue is well-distributed** across all four categories (Classic, Supreme, Chicken, Veggie), each contributing roughly 24–27%.

## Business Recommendations

1. **Staff Optimization:** Increase staff at peak hours (12 PM and 5 PM) to handle order volume efficiently and reduce wait times.
2. **Marketing Focus:** Push targeted promotions for the **Thai Chicken Pizza** — it's the top revenue driver and has strong upsell potential.
3. **Inventory Planning:** Prioritize **Large-size** ingredients; demand for XL (544) and XXL (28) is minimal and may not justify full stocking.
4. **Category Strategy:** The **Classic category** dominates — consider expanding menu options within it while also promoting higher-margin Chicken pizzas.

---

## Key Features of This Project

- **Comprehensive Data Cleaning** — Handled data type formatting (dates/times) and filtered records for accurate reporting.
- **Top Performance Ranking** — Created dynamic rankings for top-selling pizzas by revenue and quantity per category.
- **Revenue Distribution** — Calculated percentage contributions of different pizza categories to total sales.
- **Scalable Code** — Modular SQL scripts that can be updated instantly with new data imports.

---

## Tech Stack

- **Database:** MySQL (MySQL Workbench)
- **Language:** SQL
- **Techniques:** JOINs, GROUP BY, Subqueries, Window Functions (`RANK() OVER`), Aggregate Functions, Date/Time Functions

---
## Project Structure

pizza-sales-analysis/
│
├── schema/
│   └── create_tables.sql         # Database and table creation scripts
│
├── queries/
│   ├── basic_analysis.sql         # Total orders, revenue, highest price, size orders
│   ├── intermediate_analysis.sql  # Category totals, hourly distribution, daily avg
│   └── advanced_analysis.sql      # Revenue %, cumulative revenue, category rankings
│
└── README.md

---

## How to Run

1. Clone the repository:
```bash
   git clone https://github.com/mitaksharaaggarwal/pizza-sales-analysis.git
   cd pizza-sales-analysis
```

2. Set up the database:
```sql
   SOURCE schema/create_tables.sql;
```

3. Import your data into the `orders`, `orders_details`, `pizzas`, and `pizza_types` tables.

4. Run the analysis scripts in order:
```sql
   SOURCE queries/basic_analysis.sql;
   SOURCE queries/intermediate_analysis.sql;
   SOURCE queries/advanced_analysis.sql;
```


---

*If you found this project helpful or interesting, consider giving it a ⭐ on GitHub!*
