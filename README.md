# PO Data Analysis Tool

A Jupyter notebook tool for analyzing Purchase Order pricing data. No programming experience required!

**Features:**
- View price trends over time
- Calculate weighted average prices
- See how individual purchases compare to the average
- Compare prices between two time periods
- Export all tables to CSV files

---

## Getting Started

**New to Python or programming?** No problem! See the detailed setup guide:

**[How to run on Windows.md](How%20to%20run%20on%20Windows.md)**

This guide has step-by-step instructions with:
- Option 1: **Google Colab** (Recommended) - Runs in your web browser, no installation needed
- Option 2: **Local Installation** - Install Python on your Windows computer

---

## Quick Start (for experienced users)

```bash
# Install dependencies
pip install -r requirements.txt

# Launch the notebook
jupyter notebook po_analysis.ipynb
```

---

## Files in This Project

| File | What It's For |
|------|---------------|
| `po_analysis.ipynb` | The main analysis tool (open this in Jupyter) |
| `requirements.txt` | List of software the tool needs |
| `PO Data.csv` | Your data file (you provide this) |
| `How to run on Windows.md` | **Step-by-step setup guide for beginners** |
| `CLAUDE.md` | Technical documentation |

---

## What You Can Do With This Tool

### Section 2: Monthly Price Trend Chart

See how prices have changed over time:
- Interactive chart showing all products
- Click on product names to show/hide them
- Hover over lines to see exact prices and dates

### Section 3: Weighted Average Calculator

Calculate the true average price you paid:
- Select a date range (start date to end date)
- Choose specific products or view all
- See weighted average price (accounts for quantity bought)
- View monthly breakdowns in table format
- **Export to CSV** for use in Excel

**What is "weighted average"?** If you buy 100 units at $10 and 900 units at $20, your weighted average is $19 (not $15). It accounts for how much you actually purchased at each price.

### Section 4: Deviation Analysis

See how each purchase compares to the average:
- **Dollar deviation**: How many dollars above/below average?
- **Percentage deviation**: What percentage above/below average?
- Filter to see only purchases above a certain threshold
- **Export to CSV**

**Color coding:**
- Green = Below average (you paid less than usual - good!)
- Red = Above average (you paid more than usual)

### Section 5: Deviation Banding Charts

Visual breakdown of your purchases:
- Histogram showing how much you bought at each price level
- Pie chart showing distribution
- Grouped into $1 bands (e.g., "$1 to $2 below average")

**Color coding:**
- Green bars = Savings (below average)
- Red bars = Paid more (above average)

### Section 6: Benchmark Comparison

Compare prices between two time periods:
- Set a "Baseline" period (your reference)
- Set a "Comparison" period (what you're comparing)
- See price changes for each product
- Calculate total gain or loss

**Gain/Loss explained:**
- If you paid $50 in baseline but $45 in comparison, that's a GAIN (you saved $5 per unit)
- **Positive Gain/Loss = Savings** (green)
- **Negative Gain/Loss = Loss** (red)

---

## Using Your Own Data

Your CSV file needs these columns (exact names matter!):

| Column | What It Contains | Example |
|--------|------------------|---------|
| `PO#` | Purchase Order number | PO-12345 |
| `Material` | Product ID | 78924 |
| `Short Name` | Product name | "Blue Widget" |
| `PO Date` | Date (M/DD/YY format) | 1/29/25 |
| `Ordered Q'ty` | How many you ordered | 500 |
| ` Purchase Price ` | Price per unit ($ OK) | $41.70 |

**Important:** The file must be named exactly `PO Data.csv`

See **[How to run on Windows.md](How%20to%20run%20on%20Windows.md)** for detailed instructions on preparing your data.

---

## Exporting Data

Every table in the notebook has an **"Export to CSV"** button:
1. Click the green "Export to CSV" button below any table
2. A file will be saved to the `exports` folder
3. The filename includes a timestamp (e.g., `summary_20250118_143052.csv`)
4. Download the file:
   - **Colab:** Right-click the file in the Files panel → Download
   - **Local:** Find the file in your `exports` folder

---

## How the Analysis Works

### Primary Date Field
All analysis uses the `PO Date` column (when the PO was issued). Other date columns in your data (like delivery dates) are ignored.

### Product Grouping
Products are grouped by `Material` ID. Different sizes and colors of the same product are combined.

### Weighted Average Calculation
```
Weighted Average = Total $ Spent / Total Units Bought
                 = SUM(Price × Quantity) / SUM(Quantity)
```

### Gain/Loss Calculation
```
Gain/Loss = (Baseline Price - Comparison Price) × Comparison Quantity
```
- Positive = You saved money (paid less than baseline)
- Negative = You lost money (paid more than baseline)

---

## Dependencies

The tool uses these Python packages:
- pandas (data analysis)
- matplotlib (charts)
- plotly (interactive charts)
- ipywidgets (buttons and date pickers)
- jupyter (the notebook environment)
- nbformat (notebook utilities)

All are installed automatically with `pip install -r requirements.txt`

---

## Troubleshooting

See the **Troubleshooting** section in **[How to run on Windows.md](How%20to%20run%20on%20Windows.md)** for solutions to common problems.

**Quick checks:**
1. Is your CSV file named exactly `PO Data.csv`?
2. Is the CSV file in the same folder as the notebook (or uploaded to Colab)?
3. Did you run ALL cells from the top?
4. Do your column names match exactly (including spaces)?
