### Pricing Strategy Analytics  
**Do Discounts Increase Sales, and What Discount Level Maximizes Demand?**

This project digs into a practical question retailers and marketplaces care about every day: **how do discounts actually affect demand, and is there such a thing as “too much discount”?**

Using the **Kaggle Amazon Sales Dataset** (about 1,400+ product listings), the analysis looks at how **discount level**, **price**, and **product ratings** relate to **consumer demand**. Because the dataset doesn’t include actual units sold, the number of **product reviews** is used as a reasonable proxy for demand.


---

## 1. Research Questions

The notebook is organized around three main questions:

- **Do discounts increase demand?**  
  Is there a clear relationship between the size of a discount and the amount of “demand” (measured by review counts)?

- **Is there an “optimal” discount range?**  
  Does demand keep going up as discounts get deeper, or is there a point where the impact flattens out?

- **How do ratings and price interact with discounts?**  
  Are discounts more effective for high-rated products? Do very cheap products behave differently from expensive ones?


---

## 2. Data

- **Source**: Kaggle Amazon Sales Dataset  
  (Amazon product listings with prices, discounts, ratings, review metrics, and product metadata)

- **Key Raw Variables** (selected):
  - `discounted_price`
  - `actual_price`
  - `discount_percentage`
  - `rating`
  - `rating_count` (used as a **proxy for demand**)
  - Product/category text fields and links

- **Sample size**: ~1,465 product observations after loading the raw data.


---

## 3. Methodology (What the Notebook Does)

The notebook follows a clear step‑by‑step workflow:

### Step 1 – Load the dataset
- Reads the Kaggle Amazon dataset into a `pandas` DataFrame.
- Prints basic shape and column information to understand what’s available.

### Step 2 – Clean the data
- Converts prices and discounts from messy string formats (with currency symbols, commas, etc.) into numeric variables.
- Cleans up `rating_count` so it can be used as a numeric demand measure.
- Handles missing values and drops or transforms problematic entries where needed.

### Step 3 – Explore the data
- Looks at **distributions** of discounts, prices, and ratings.
- Produces **summary statistics** and basic visualizations to get a feel for typical products vs. outliers.
- Explores how discount, price, and rating are related to review counts at a descriptive level.

### Step 4 – Construct features
- Builds cleaned, analysis‑ready variables, such as:
  - Numeric **discount percentage**
  - Numeric **actual and discounted prices**
  - Transforms for **rating_count** (e.g., log transformations if needed to handle skew).
- Creates any interaction or non‑linear terms required for the empirical models (for example, squared discount terms to capture diminishing returns).

### Step 5 – Empirical analysis
- Uses **regression models** (via `statsmodels`) to estimate how demand responds to:
  - Discount level
  - Price
  - Rating
- Interprets coefficient signs and magnitudes in an economics/business context: how much does demand move when discount or ratings change, holding other factors constant?

### Step 6 – Heterogeneous analysis
- Splits or filters the data to see whether **discount effects differ**:
  - Across categories or product groups
  - Across rating levels (e.g., low-rated vs. high-rated products)
  - Across price bands (cheaper vs. premium products)
- Compares patterns to understand **where discounts seem to work best**.

### Step 7 – Results interpretation
- Ties the statistical findings back to **managerial insights**:
  - How strongly discounts appear to be associated with higher demand.
  - Whether the relationship looks **non‑linear** (e.g., diminishing returns to very large discounts).
  - The role of ratings and price in strengthening or weakening the effect of discounts.
- Discusses practical implications for **e‑commerce pricing strategies**.


---

## 4. Credits

- **Author**: Muhtasim Fuad Chowdhury  
- **Data**: Kaggle Amazon Sales Dataset

