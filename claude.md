# PO Data Analysis Project

## Data Source
- **File**: `PO Data.csv`
- **Purpose**: Purchase Order data analysis for product pricing trends

## Getting Started

See **[How to run on Windows.md](How%20to%20run%20on%20Windows.md)** for detailed setup instructions:
- **Option 1**: Google Colab (no installation required)
- **Option 2**: Local Python installation on Windows

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

### Category Columns (for Filtering)
These columns enable filtering products by category in all analysis sections:

| Column | Description |
|--------|-------------|
| `Material Category Description` | Top-level product category |
| `Material Line Description` | Product line within category |
| `Material Product Type Description` | Product type |
| `Material Class Description` | Product class |
| `Construction Type Description` | Construction/manufacturing type |

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
- Optional: Filter by category (Category, Line, Type, Class, Construction)
- Optional: Filter by specific product(s)

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

**Color Coding**:
- **GREEN** = Below average (savings - you paid less!)
- **RED** = Above average (paid more than average)

**Output Tables**:

1. **Monthly Deviation Table (Dollars)** - Excel-format pivot:
   - Rows: Products (Material ID + Short Name)
   - Columns: Months within selected date range
   - Values: `Monthly Weighted Avg - Overall Weighted Avg` (positive = above avg, negative = below)
   - Last column: Overall weighted avg for reference
   - Color coded: Green = below avg (savings), Red = above avg (paid more)

2. **Monthly Deviation Table (Percentage)** - Same format with percentage deviation

3. **Monthly Price Reference Table** - Shows actual monthly weighted avg prices

4. **Individual PO Line Item Table**:
   - Product name, PO Date, Purchase Price
   - Weighted Average (for that product in selected range)
   - Dollar Deviation (+/- $X.XX) - color coded
   - Percentage Deviation (+/- X.XX%) - color coded
   - Threshold filter: show items above/below a dollar amount

---

### 4. Deviation Banding / Distribution Analysis

**Goal**: Categorize items into deviation bands for visual analysis.

**Band Categories** (using short labels for readability):
- $5+ below
- $4-5 below
- $3-4 below
- $2-3 below
- $1-2 below
- $0-1 below
- $0-1 above
- $1-2 above
- $2-3 above
- $3-4 above
- $4-5 above
- $5+ above

**Color Coding**:
- **GREEN** = Below average (savings - you paid less!)
- **RED** = Above average (paid more than average)

**Visualizations**:
1. **Histogram**: Total quantity in each band (not count of items)
2. **Pie Chart**: Distribution of quantity across bands (legend below to avoid label overlap)
3. **Filter capability**: Show items that are e.g., "$1+ above average" or "0.5%+ below average"

---

### 5. Benchmark Comparison

**Goal**: Compare a new date range against a baseline date range.

**Process**:
1. **Select Baseline Range**: Choose PO Date range for baseline analysis (price benchmark)
2. **Calculate Baseline Metrics**: Weighted average per product
3. **Select Comparison Range**: Choose a second PO Date range
4. **Compare**:
   - Price change (dollar and percentage)
   - Gain/Loss calculation

**Gain/Loss Calculation**:
```
Gain/Loss = (Baseline Price - Comparison Price) × Comparison Qty
```
- **POSITIVE = GAIN** (you paid less than baseline, saved money!)
- **NEGATIVE = LOSS** (you paid more than baseline)

**Output Tables**:

1. **Product-by-Product Comparison**:
| Product | Base Price | Comp Price | Price Δ | Price Δ% | Comp Qty | Gain/Loss ($) |
|---------|------------|------------|---------|----------|----------|---------------|
| Product A | $54.80 | $52.00 | -$2.80 | -5.1% | 1,000 | +$2,800.00 |
| Product B | $41.70 | $43.50 | +$1.80 | +4.3% | 500 | -$900.00 |

2. **Monthly Comparison vs Baseline Benchmark**:
   - Price delta vs baseline for each month
   - Gain/Loss vs baseline for each month

3. **Total Gain/Loss Summary**

4. **Deviation Banding Charts** (same style as Section 5):
   - Histogram showing quantity distribution by deviation from baseline
   - Pie chart with legend below
   - Period info displayed: date ranges, PO counts, quantities for both baseline and comparison

---

## Category-Based Filtering

All analysis sections (3, 4, 5, 6) support filtering by product categories using dropdown menus:

1. **Material Category** - Filter by `Material Category Description`
2. **Material Line** - Filter by `Material Line Description`
3. **Material Type** - Filter by `Material Product Type Description`
4. **Material Class** - Filter by `Material Class Description`
5. **Construction Type** - Filter by `Construction Type Description`

**How it works**:
- Select "All" to include all products, or select a specific value to filter
- Multiple category filters can be combined (AND logic)
- The product list automatically updates to show only matching products
- A counter shows how many products match the current filters

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
| `How to run on Windows.md` | Setup guide for Windows/Colab |
| `README.md` | Project overview |

### How to Run
See **[How to run on Windows.md](How%20to%20run%20on%20Windows.md)** for detailed instructions.

Quick start:
```bash
pip install -r requirements.txt
jupyter notebook po_analysis.ipynb
```

### Notebook Sections
1. **Setup & Data Loading** - Data cleaning, PO-level aggregation, category options, scrollable table helper
2. **Monthly Price Trend** - matplotlib line chart, category filters + product filter, data tables with Show All Rows toggle
3. **Weighted Average Calculator** - Date range + category filters + product filter, Excel-format monthly trend tables, Show All Rows toggle
4. **Deviation Analysis** - Monthly deviation tables (dollars & %), individual PO deviations with threshold filtering, color coded, Show All Rows toggle
5. **Deviation Banding** - matplotlib histogram and pie chart by **Total Quantity** (Green=savings, Red=paid more), Show All Rows toggle
6. **Benchmark Comparison** - Compare two date ranges with Gain/Loss calculations, color coded, Show All Rows toggle, histogram and pie chart showing deviation from baseline

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

#### 4. Gain/Loss Convention
- **Positive Gain/Loss = SAVINGS** (you paid less than baseline)
- **Negative Gain/Loss = LOSS** (you paid more than baseline)

#### 5. Per-Product Benchmark Comparison
Section 6 compares products individually using an **inner join** - only products that appear in BOTH the baseline and comparison periods are shown. This prevents misleading comparisons when product mix changes between periods.

#### 6. Number Formatting
All currency values are displayed with exactly 2 decimal places (e.g., $41.70, not $41.7 or $41.698).

#### 7. Color Coding Convention
Throughout the notebook:
- **Green = Good** (savings, below average, positive gain)
- **Red = Bad** (loss, above average, negative gain)

#### 8. Category-Based Filtering
All analysis sections support filtering by 5 category dimensions. Filters use AND logic (all selected filters must match). The product selector dynamically updates based on category selections.

#### 9. Show All Rows Toggle
All sections with tables (2, 3, 4, 5, 6) include a "Show All Rows (scrollable)" checkbox. When enabled:
- All rows of each table are displayed (instead of pandas' default truncation)
- Tables are wrapped in a scrollable container (max-height: 400-500px)
- Users can scroll through all data without exporting to CSV

#### 10. Charting with matplotlib (Interactive)
All charts use matplotlib with interactive toolbar (`%matplotlib widget` / `ipympl`):
- Section 2: Line chart for monthly price trends (legend below chart)
- Section 5: Bar chart (histogram) and pie chart for deviation banding
- Section 6: Bar chart and pie chart for deviation from baseline
- **Interactive toolbar buttons**: Pan, Zoom, Reset view, Save image
- **Pie chart design**: Uses legend below chart to avoid label overlap; black text for percentages inside slices for better contrast
- Benefits: No rendering issues, zoom/pan capabilities, easy image export
- Fallback: If ipympl not installed, charts render in inline mode without toolbar

---

## Export Functionality

All tables can be exported to CSV files:
- Click the green **"Export to CSV"** button below any table
- Files are saved to the `exports/` folder with timestamps
- Filenames include descriptive prefixes (e.g., `summary_20250118_143052.csv`)
- HTML formatting is stripped from exported data for clean spreadsheet import

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

- [ ] Add vendor-level analysis
- [ ] Compare prices across vendors for same product
- [ ] Landed cost analysis (including freight, duty, commission)
- [ ] Seasonal trend detection
