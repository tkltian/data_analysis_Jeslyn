# PO Data Analysis Tool

Interactive Jupyter notebook for analyzing Purchase Order pricing data, including weighted average calculations, deviation analysis, and benchmark comparisons.

## Getting Started

**New to Python?** See the detailed setup guide: **[How to run on Windows.md](How%20to%20run%20on%20Windows.md)**

Two options:
1. **Google Colab** (recommended) - No installation, runs in your browser
2. **Local Installation** - Install Python on your Windows computer

## Quick Start (for experienced users)

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
| `PO Data.csv` | Source Purchase Order data (replace with your own) |
| `How to run on Windows.md` | **Step-by-step setup guide** for beginners |
| `CLAUDE.md` | Detailed project documentation and data dictionary |

## Using Your Own Data

Your CSV file must:
1. Be named exactly `PO Data.csv`
2. Be placed in the same folder as the notebook (or uploaded to Colab)
3. Have these required columns:

| Column | Description |
|--------|-------------|
| `PO#` | Purchase Order number |
| `Material` | Product ID number |
| `Short Name` | Product name |
| `PO Date` | Date (M/DD/YY format) |
| `Ordered Q'ty` | Quantity ordered |
| ` Purchase Price ` | Unit price ($ signs OK) |

See [How to run on Windows.md](How%20to%20run%20on%20Windows.md) for detailed instructions.

## Features

### Section 1: Data Loading
- Loads and cleans CSV data
- Parses dollar amounts and dates
- Aggregates sizes within same PO

### Section 2: Monthly Price Trend Visualization
- Interactive line chart showing weighted average price over time
- Multi-product selector to compare trends
- Tall chart (900px) with legend below for readability
- Click legend items to show/hide products

### Section 3: Weighted Average Calculator
- Select date range using date pickers
- Filter by specific products or view all
- Displays: weighted avg price, total quantity, total FOB value
- **Excel-format monthly price trend table**: pivot showing weighted avg price per product per month
- **Excel-format monthly quantity table**: pivot showing quantity ordered per product per month

### Section 4: Deviation Analysis
- Shows how each PO deviates from the weighted average
- Dollar deviation: `Item Price - Weighted Average`
- Percentage deviation: `(Deviation / Average) * 100%`
- Threshold filters: show items above/below a dollar amount
- **Monthly deviation tables**: Excel-format pivots showing each month's deviation from overall weighted avg (in dollars and percentages)

### Section 5: Deviation Banding
- Categorizes purchases into $1 bands (e.g., "$1 to $2 above average")
- **Uses Total Quantity** (not count) - shows how much you bought at each deviation level
- Color coding: **Green = Below average (savings)**, **Red = Above average (paid more)**
- Histogram and pie chart visualizations

### Section 6: Benchmark Comparison
- Compare pricing between two date ranges (baseline vs comparison)
- **Gain/Loss calculation**: `(Baseline Price - Comparison Price) × Comparison Qty`
  - **Positive = GAIN** (you paid less, saved money!)
  - **Negative = LOSS** (you paid more)
- Product-by-product comparison table
- Monthly breakdown vs baseline benchmark
- Total gain/loss summary

## Data Processing Notes

### Primary Date Field
**Always use `PO Date`** for time-based analysis. Other date fields (XFD, ETA, etc.) are NOT used.

### Dollar Sign Parsing
The `Purchase Price` column has `$` signs. The notebook handles this automatically using:
```python
df['Purchase_Price'] = pd.to_numeric(
    df[' Purchase Price '].astype(str).str.replace('\\$', '', regex=True).str.strip(),
    errors='coerce'
)
```

### PO-Level Aggregation
Multiple rows with same `PO#` + `Material` (different sizes) are aggregated by summing quantities.

## Dependencies

- pandas
- matplotlib
- plotly
- ipywidgets
- jupyter
- nbformat
