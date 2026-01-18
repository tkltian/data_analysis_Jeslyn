# PO Data Analysis Project

## Data Source
- **File**: `PO Data.csv`
- **Purpose**: Purchase Order data analysis for product pricing trends

## Data Structure Overview

### Key Columns
| Column | Description |
|--------|-------------|
| `PO#` | Purchase Order number |
| `Material` | Product ID |
| `Short Name` | Product name/description |
| `Color` | Product color |
| `Size` | Product size (SML, MED, LG, XL, XXL, etc.) |
| `PO Date` | **PRIMARY DATE ANCHOR** - Date when PO was issued |
| `Ordered Q'ty` | Quantity ordered |
| `Purchase Price` | Unit price (formatted as `$XX.XX`) |
| `Vendor Name` | Supplier name |

### Important Date Fields
The data contains MULTIPLE date fields. **Always use `PO Date`** as the primary anchor for analysis:

| Date Column | Description | Use For Analysis? |
|-------------|-------------|-------------------|
| `PO Date` | When PO was issued | **YES - PRIMARY** |
| `Requested XFD` | Requested ship date | No |
| `Confirmed XFD` | Confirmed ship date | No |
| `Original Delivery` | Original delivery date | No |
| `XFD` | Expected ship date | No |
| `ETA` | Estimated arrival | No |
| `IBD ETA` | Inbound delivery ETA | No |
| `Goods Receipt Date` | When goods received | No |

**CRITICAL**: Do NOT mix `PO Date` with other date fields when doing time-based analysis.

---

## Analysis Requirements

### 1. Monthly Price Trend Analysis

**Goal**: Visualize each product's price trend over months based on PO Date.

**Logic**:
- Group data by `PO Date` month (extract YYYY-MM)
- Group by product (`Material` or `Short Name`) - aggregate ALL sizes together
- For each product-month combination, calculate weighted average price:
  ```
  Weighted Avg Price = SUM(Purchase Price * Ordered Qty) / SUM(Ordered Qty)
  ```
- Create line chart showing price trend per product over months

**Output**: Line chart with months on X-axis, price on Y-axis, one line per product.

---

### 2. Weighted Average Price Calculator

**Goal**: Calculate weighted average price for user-selected date range.

**Inputs**:
- Start date (PO Date)
- End date (PO Date)
- Optional: Filter by product(s)

**Calculation**:
```
Weighted Average = SUM(Purchase Price * Ordered Qty) / SUM(Ordered Qty)
```

**Output**:
- Weighted average price per product
- Total ordered quantity per product
- Total FOB value per product
- **Excel-format monthly price trend table**: Pivot table with products as rows, months as columns, weighted avg prices as values
- **Excel-format monthly quantity table**: Same format showing quantities ordered

---

### 3. Deviation from Average Analysis

**Goal**: Show how individual line items deviate from the weighted average.

**Metrics to Calculate**:
| Metric | Formula |
|--------|---------|
| Weighted Average | SUM(Price * Qty) / SUM(Qty) |
| Dollar Deviation | Item Price - Weighted Average |
| Percentage Deviation | (Item Price - Weighted Average) / Weighted Average * 100 |

**Output Tables**:

1. **Monthly Deviation Table (Dollars)** - Excel-format pivot:
   - Rows: Products (Material ID + Short Name)
   - Columns: Months within selected date range
   - Values: `Monthly Weighted Avg - Overall Weighted Avg` (positive = above avg, negative = below)
   - Last column: Overall weighted avg for reference

2. **Monthly Deviation Table (Percentage)** - Same format with percentage deviation

3. **Monthly Price Reference Table** - Shows actual monthly weighted avg prices

4. **Individual PO Line Item Table**:
   - Product name, PO Date, Purchase Price
   - Weighted Average (for that product in selected range)
   - Dollar Deviation (+/- $X.XX)
   - Percentage Deviation (+/- X.XX%)
   - Threshold filter: show items above/below a dollar amount

---

### 4. Deviation Banding / Distribution Analysis

**Goal**: Categorize items into deviation bands for visual analysis.

**Band Categories** (configurable):
- $5+ below average
- $4 to $5 below
- $3 to $4 below
- $2 to $3 below
- $1 to $2 below
- $0 to $1 below
- $0 to $1 above
- $1 to $2 above
- $2 to $3 above
- $3 to $4 above
- $4 to $5 above
- $5+ above average

**Visualizations**:
1. **Histogram**: Count of items in each band
2. **Pie Chart**: Distribution of items across bands
3. **Filter capability**: Show items that are e.g., "$1+ above average" or "0.5%+ below average"

---

### 5. Benchmark Comparison

**Goal**: Compare a new date range against a baseline date range.

**Process**:
1. **Select Baseline Range**: Choose PO Date range for baseline analysis
2. **Calculate Baseline Metrics**: Weighted average, deviation bands, etc.
3. **Select Comparison Range**: Choose a second PO Date range
4. **Compare**:
   - Price change (dollar and percentage)
   - Shift in deviation distribution
   - Products with significant price changes

**Output**:
| Product | Baseline Avg | Comparison Avg | Change ($) | Change (%) |
|---------|--------------|----------------|------------|------------|
| Product A | $54.80 | $56.20 | +$1.40 | +2.55% |
| Product B | $41.70 | $41.70 | $0.00 | 0.00% |

---

## Data Processing Notes

### Cleaning Requirements
- `Purchase Price` column has format ` $XX.XX ` (with spaces and dollar sign) - needs parsing
- Handle missing/empty values in date fields
- Some rows may have `Ordered Q'ty = 0` - decide whether to include/exclude

### Product Grouping
- Products are identified by `Material` (numeric ID) or `Short Name`
- Same product comes in multiple sizes - aggregate across sizes for product-level analysis
- Same product may have different colors - decide grouping strategy

### Date Parsing
- PO Date format: `M/DD/YY` (e.g., `1/29/25` = January 29, 2025)
- Extract month as `YYYY-MM` for monthly grouping

---

## Implementation Details

### Files
| File | Description |
|------|-------------|
| `po_analysis.ipynb` | Main Jupyter notebook with interactive analysis |
| `requirements.txt` | Python dependencies |
| `PO Data.csv` | Source data file |

### How to Run
```bash
pip install -r requirements.txt
jupyter notebook po_analysis.ipynb
```

### Notebook Sections
1. **Setup & Data Loading** - Data cleaning, PO-level aggregation
2. **Monthly Price Trend** - Interactive Plotly line chart with product selector, data tables
3. **Weighted Average Calculator** - Date range + product filter, Excel-format monthly trend tables
4. **Deviation Analysis** - Monthly deviation tables (dollars & %), individual PO deviations with threshold filtering
5. **Deviation Banding** - Histogram and pie chart by **Total Quantity** (not count)
6. **Benchmark Comparison** - Compare two date ranges with full period summaries

### Key Design Decisions

#### 1. PO-Level Aggregation
Multiple rows with the same `PO#` + `Material` represent different **sizes** of the same order. Since sizes have the same unit price, we aggregate by summing quantities:
```python
df = df.groupby(['PO#', 'Material', 'Short Name', 'PO_Date', 'Purchase_Price']).agg({
    'Ordered_Qty': 'sum'
}).reset_index()
```
This reduces ~3,000 rows to ~300 rows, giving one row per PO + Material combination.

#### 2. Deviation Banding Uses Total Quantity
Section 5 shows **how much you bought** at each price deviation level, not just count of POs. A single PO for 10,000 units at a bad price is more significant than 10 POs for 100 units each.

#### 3. Product Grouping
Products are grouped by `Material` ID only, aggregating all sizes and colors together.

---

## Known Issues & Solutions

### Dollar Sign Parsing in Purchase Price Column

**Problem**: The `Purchase Price` column contains values formatted as ` $41.70 ` (with leading/trailing spaces and dollar sign).

**What DOESN'T work**:
```python
# This fails silently or throws errors
df['Price'] = df[' Purchase Price '].str.replace('$', '', regex=False).str.strip().astype(float)
```

**Solution** - Use regex=True with escaped dollar sign:
```python
df['Purchase_Price'] = pd.to_numeric(
    df[' Purchase Price '].astype(str).str.replace('\\$', '', regex=True).str.strip(),
    errors='coerce'
)
```

**Why**: The `$` character has special meaning in regex. When using `regex=False`, pandas string replacement doesn't handle the `$` character consistently across all pandas versions. Using `regex=True` with `\\$` (escaped) works reliably.

---

## Future Enhancements

- [ ] Export analysis results to Excel/CSV
- [ ] Add vendor-level analysis
- [ ] Compare prices across vendors for same product
- [ ] Landed cost analysis (including freight, duty, commission)
- [ ] Seasonal trend detection
