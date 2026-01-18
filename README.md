# PO Data Analysis Tool

Interactive Jupyter notebook for analyzing Purchase Order pricing data, including weighted average calculations, deviation analysis, and benchmark comparisons.

See [How to run python code on Windows.md](How%20to%20run%20python%20code%20on%20Windows.md) for general Python setup instructions.

## Quick Start

```bash
# Install dependencies
pip install -r requirements.txt

# Launch the notebook
jupyter notebook po_analysis.ipynb
```

## Files

| File | Description |
|------|-------------|
| `po_analysis.ipynb` | Main analysis notebook with interactive widgets |
| `requirements.txt` | Python dependencies |
| `PO Data.csv` | Source Purchase Order data |
| `CLAUDE.md` | Detailed project documentation and data dictionary |

## Features

### 1. Monthly Price Trend Visualization
- Interactive line chart showing weighted average price over time
- Multi-product selector to compare trends
- Groups by `Material` ID (aggregates all sizes/colors)

### 2. Weighted Average Calculator
- Select date range using date pickers
- Filter by specific products or view all
- Displays: weighted avg price, total quantity, total FOB value
- **Excel-format monthly price trend table**: pivot table showing weighted avg price per product per month
- **Excel-format monthly quantity table**: pivot table showing quantity ordered per product per month
- All tables constrained to the user-selected date range

### 3. Deviation Analysis
- Shows how each PO deviates from the weighted average
- Dollar deviation: `Item Price - Weighted Average`
- Percentage deviation: `(Deviation / Average) * 100%`
- Threshold filters: show items above/below a dollar amount
- **Monthly deviation table (dollars)**: Excel-format pivot showing each month's price deviation from overall weighted avg
- **Monthly deviation table (percentage)**: same as above but in percentage format
- **Monthly price reference table**: shows actual monthly weighted avg prices for context
- All analysis constrained to user-selected date range

### 4. Deviation Banding
- Categorizes purchases into $1 bands (e.g., "$1 to $2 above average")
- **Uses Total Quantity** (not count) - shows how much you bought at each deviation level
- Histogram visualization with color coding (red=below, green=above)
- Pie chart showing quantity distribution

### 5. Benchmark Comparison
- Compare pricing between two date ranges
- **Clear period summaries**: PO count, total quantity, total FOB value, overall weighted avg
- **Overall change**: quantity change and price change with percentages
- **Product-by-product table**: Base POs, Base Price, Base Qty, Comp POs, Comp Price, Comp Qty, Price Δ, Qty Δ
- Summary statistics for price increases/decreases

## Data Processing Notes

### Primary Date Field
**Always use `PO Date`** for time-based analysis. The data contains many other date fields (XFD, ETA, Delivery dates) but these should NOT be used for trend analysis.

### Dollar Sign Parsing Issue

The `Purchase Price` column contains values like ` $41.70 ` (with spaces and `$`).

**Problem**: Simple string replacement doesn't work reliably:
```python
# THIS DOESN'T WORK
df['Price'] = df[' Purchase Price '].str.replace('$', '', regex=False).astype(float)
```

**Solution**: Use regex with escaped dollar sign:
```python
# THIS WORKS
df['Purchase_Price'] = pd.to_numeric(
    df[' Purchase Price '].astype(str).str.replace('\\$', '', regex=True).str.strip(),
    errors='coerce'
)
```

**Why?** The `$` character has special meaning in regex (end of string). When using `regex=False`, pandas string methods don't handle `$` consistently. Using `regex=True` with `\\$` explicitly matches the literal dollar sign.

### PO-Level Aggregation
Multiple rows with the same `PO#` + `Material` represent different **sizes** of the same order. Since all sizes have the same unit price, we aggregate by summing quantities. This reduces ~3,000 raw rows to ~300 PO line items.

### Product Grouping
- Products grouped by `Material` ID (numeric)
- All sizes (SML, MED, LG, XL, etc.) aggregated together
- All colors aggregated together

### Data Summary
- Raw rows: 3,230 → Cleaned: 3,098 → After PO aggregation: 303
- Date range: 2025-01-29 to 2026-01-09
- Unique POs: 278
- Unique products: 74

## Dependencies

- pandas
- matplotlib
- plotly
- ipywidgets
- jupyter
