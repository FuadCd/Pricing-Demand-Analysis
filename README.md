### Pricing Strategy Analytics  
**Do Discounts Increase Sales, and What Discount Level Maximizes Demand?**

This project digs into a practical question retailers and marketplaces care about every day: **how do discounts actually affect demand, and is there such a thing as “too much discount”?**

Using the **Kaggle Amazon Sales Dataset** (about 1,400+ product listings), the analysis looks at how **discount level**, **price**, and **product ratings** relate to **consumer demand**. Because the dataset doesn’t include actual units sold, the number of **product reviews** is used as a reasonable proxy for demand.

The work was completed for **BUEC 420 – Data Science and Business Economics** and is implemented in a single notebook: `pricing_demand_analysis.ipynb`.


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

## 4. How to Run the Notebook

### Requirements

You’ll need a fairly standard Python data stack:

- **Python 3.8+** (any modern 3.x version should be fine)
- **Packages**:
  - `pandas`
  - `numpy`
  - `matplotlib`
  - `seaborn`
  - `statsmodels`
  - `jupyter` (or any environment that runs `.ipynb` notebooks)

You can install everything with:

```bash
pip install pandas numpy matplotlib seaborn statsmodels jupyter
```

### Steps to run

1. **Clone or download** this repository into a local folder.
2. Make sure the **Kaggle Amazon Sales dataset** file used in the notebook is present in the expected path (or adjust the file path in the first data‑loading cell).
3. From the repository root, launch Jupyter:

```bash
jupyter notebook
```

4. Open `pricing_demand_analysis.ipynb`.
5. Run the cells in order from top to bottom.  
   The notebook is already structured so that each “Step” builds on the previous one.


---

## 5. Repository Structure

At minimum, the repo includes:

- `pricing_demand_analysis.ipynb` – main analysis notebook
- (Optional, depending on how you organize it) Raw or cleaned data files referenced in the notebook
- `README.md` – this file


---

## 6. Interpretation and Use

This project is best thought of as a **course term paper translated into code**:

- It’s **exploratory and empirical**, not a production system.
- The findings are **conditional on this specific Kaggle dataset**, with its own limitations (e.g., using review counts as a proxy for demand).
- The main value is in **demonstrating how to go from raw e‑commerce data → cleaned features → regression models → business insights**.

If you want to extend the work, some natural next steps are:

- Re‑run the analysis on a dataset that includes **actual sales quantities**.
- Test **alternative demand proxies** (e.g., sales rank or time‑series data if available).
- Try **non‑linear or machine learning models** to capture more complex relationships between discounts, price, ratings, and demand.


---

## 7. Credits

- **Author**: Muhtasim Fuad Chowdhury  
- **Course**: BUEC 420 – Data Science and Business Economics  
- **Data**: Kaggle Amazon Sales Dataset

If you’re reading this as a reviewer or instructor, the best place to start is simply opening the notebook and stepping through the seven labeled sections—each one is written to be readable without needing to dig into the raw code too much.

