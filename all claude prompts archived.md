# Claude Prompts Archive

This file contains all the prompts used during the development session for the PO Data Analysis Tool.

---

## Session Date: January 18, 2026

---

### Prompt 1: Fix Section 5 Histogram Colors and Auto-scale
```
Section 5, the banded histogram drawing, switch the color: above average should be red, below should be green; also do an auto scale after drawing it
```

---

### Prompt 2: Improve Section 2 Chart Readability
```
Section 2: make the chart much taller, to make it readable; the legends are eating too mcuh space into the chart
```

---

### Prompt 3: Commit and Push
```
commit and push
```

---

### Prompt 4: Fix Gain/Loss Calculation Sign
```
Section 6: somehow, some rows are having a price delta of 2.8 dollars, with price delta of -10.1%... the Gain/Loss should be positive, a gain!!! ... It should not be -8050.34, instead it should be 8050.34...
```

---

### Prompt 5: Rename and Rewrite Setup Guide
```
Change the file "How to run python code on Windows.md" name to "How to run on Windows.md". Make it very easy to follow with detailed steps...
```

---

### Prompt 6: Fix Overall Change Comparison and Add Color Coding
```
For the comparison I did... that didn't make sense... the average price of the comparison period, seems to be calculated to be higher than baseline... HOW DOES THAT MAKE SENSE? ALSO, make a change, to color all numbers; if it's 'Saving', show green; if it's 'Loss', show red.
```

---

### Prompt 7: Standardize Decimals, Restructure Section 6, Add Export
```
Set all tables, in the entire notebook, digits after decimal count should be 2... Section 6 should use similar structure of section 4; that is, don't do a product mix... ALSO, add export function for each of the tables...
```

---

### Prompt 8: Add CSV to Gitignore
```
Add any .csv files, to .gitignore; so that sensitive data is not going to be uploaded to github
```

---

### Prompt 9: Update All Documentation
```
Update all documentations, including the "How to run on Windows.md" file, since I will ask my friend, who is not a software engineer, to follow that guide; so make it very detailed, and not assuming people know how to do things.
```

---

### Prompt 10: Commit and Push (after documentation update)
```
commit and push
```

---

### Prompt 11: Commit and Push (verification)
```
Commit / push
```

---

### Prompt 12: Add Product Category Filtering
```
We talked about product catogorizing / grouping, from the few columns we specified. Use these exact columns in the
  CSV files: "Material category description" column; "Material line description" column; "Material Type
  description" column; "Material Class description" column; "Construction type description" column.    And with those grouping / categorizing, in ANY "Filter by products" selector, we display the drop downs, to let the user select "select products of material category", by filtering per the "material category description" column; and let user select "select products of material line", by filtering per the "material line description" column; and let user select "select products of material class", by filtering per the "material class description" column, and select "select prodcts of material line", by filtering per the "material line description" column.
```

---

### Prompt 13: Add Color Coding to Section 4
```
For sections 4, also use the green / red coloring for the tables. For deviations that would cause a gain for the PO process (e.g. purchased a product at lower price than average, deviation that causes savings), mark it green color. Vice versa, for the losses, red color
```

---

### Prompt 14: Fix Section 5 Histogram Chart Rendering
```
Also, I don't get why the Deviation banding histogram chart just don't load well; see the screenshot. It's a VERY simple histogram, but somehow the cahrt always shows up like the screenshot, with no content visible, and the boxes out of shape of format; and if I click the "AutoScale" button, then the chart would show meaningful, normal histogram, which is progress, althought the format is still way off, since the big, pink region under the chart, with no content in there, see the second screenshot: which is after clicking the "Autoscale" button
```

---

### Prompt 15: Update Documentation and Commit
```
Yes, and update the claude.md and other documentations.
```

---

### Prompt 16: Archive All Prompts
```
Also, store another file "all claude prompts archived" to archive all prompts we used in this session, for reference
```

---

### Prompt 17: Add Category Filtering to Section 2
```
The 'filter products' feature, also do it for the 'show pricing trends' products picker, in section 2. Basically, anywhere there is a product picker, use it!!!
```

---

### Prompt 18: Add Show All Rows Toggle
```
For tables like this, what's the best way to be able to see all rows? Do I have to export to .csv, and load in another program to see all rows? What's the best way in Jupyter notebook?
```
(User chose: "Show All Rows" toggle button with scrollable tables)

---

### Prompt 19: Replace Plotly with Matplotlib
```
The histogram chart still doesn't display well, with huge pink region under the chart that is blank; and I still need to click the "AUTOSCALE" button to make the diagram display correctly. This is just plain mindblowing, since it is indeed just a VERY SIMPLE HISTOGRAM!!!!!! Now, let's try something different: ditch plotly. Let's use matplotlib. And just feed the histogram data, to matplotlib as a SIMPLE histogram.... let's see whether this will work well.
```

---

### Prompt 20: Use Matplotlib Everywhere
```
Just use matplotlib everywhere. Remember to update the requirements.txt, and update documentations as needed
```

---

### Prompt 21: Add Interactive Toolbar to Charts
```
Add plotting tools, such as zoom buttons, to the matplotlib plots
```

---

### Prompt 22: Ensure ipympl in Requirements and Guide
```
make sure ipympl is in the requirements.txt, and also in the guide
```

---

### Prompt 23: Add Show All Rows Toggle to ALL Tables
```
Oh I see it now. But the request, is to have it for EVERY table; example is the section 2, === Monthly Weighted Average Price by Product ===
(Rows: 74 products, Columns: 13 months): I need an option to see ALL ROWS for that table too!!! So do an audit, basically make sure for EVERY table, there is a way to see all rows
```

---

### Prompt 24: Improve Pie Chart Labels and Visuals
```
The pie chart, has the labels overlapping with each other; modify it so that with no overlap, and place the labels such that each can have a line linking the label to the pie, if necessary. Also, the pies in the pie chart, should have better boundary; maybe use some more clear boundary with 3D effect or something; do resaerch to see what makes sense
```

---

### Prompt 25: Use Shorter Band Labels
```
Also use "$0-1 above" (instead of "0to1 above" or "$0 to $1 above")
```

---

### Prompt 26: Move Section 2 Legend Below Chart
```
The plot for "Monthly weighted average price trend" in section 2, the legends box is way clipped and difficult to read. Put the legend box under the chart (while keeping the chart the same height as now, so there is plenty of room for displaying hte trend lines)
```

---

### Prompt 27: Add Histogram/Pie Chart to Section 6
```
Section 6: add the same histogram / pie chart, just like section 5, but instead of comparing against the data's own weighted average, it's comparing against the benchmark baseline weighted average; and also put the data range, PO count information of benchmark baseline, and the comparison, along with the charts.
```

---

### Prompt 28: Use Black Text for Pie Chart Percentages
```
For all pie charts, when the pies are light green, or light red, the white characters don't stand out because of lack of contrast. We should just Use deep color characters instead. I think let's just use black characters for the percentages markings on the pie charts
```

---

### Prompt 29: Update All Documentation
```
Update all documentations. Also, for "how to run on Windows" documentation, add detailed steps / guide, assuming the user don't know how to use Jupyter notebook or Google Colab
```

---

### Prompt 30: Collapse Code Sections and Show Data File Path
```
ALso, for the Jupyter notebook, the code sections are getting pretty lengthy. By default, collapse all code sections. Also, for loading data, add a box for the user to see the data file that is being loaded, instead of just having part of the code that says "df_raw = pd.read_csv('PO Data.csv'... "
```

---

### Prompt 31: Allow Custom Data File Name
```
Let's do another improvement: right now, the file name is hard coded: Important: The file must be named exactly PO Data.csv. Let's change that, in the Jupyter notebook, let the user specify the file name. By default, the filename is PO Data.csv, thus the notebook would run just like before. But optionally, the user can put their own custom file name in the file name box to run with different data files.
```

---

## Summary of Changes Made

### Features Implemented
1. **Section 2**: Line chart with matplotlib, category filters + product filter, legend below chart
2. **Section 2**: Added Show All Rows toggle to data tables
3. **Section 5**: Color swap (green=below avg/savings, red=above avg/paid more), matplotlib bar chart and pie chart
4. **Section 5**: Pie chart uses legend below to avoid label overlap, black text for percentages
5. **Section 5**: Shorter band labels ($0-1 instead of $0 to $1)
6. **Section 6**: Fixed Gain/Loss calculation sign convention, per-product comparison, color coding
7. **Section 6**: Added histogram and pie chart showing deviation from baseline
8. **All Sections**: Standardized to 2 decimal places
9. **All Tables**: Added CSV export buttons
10. **Sections 2, 3, 4, 5, 6**: Added category-based filtering (5 dropdowns)
11. **Section 4**: Added green/red color coding for deviations
12. **All Sections with Tables**: Added "Show All Rows (scrollable)" toggle
13. **All Charts**: Replaced Plotly with matplotlib for reliable rendering
14. **All Charts**: Added interactive toolbar (zoom, pan, reset, save) via ipympl
15. **Data Loading**: Interactive file selector - users can specify custom CSV filename
16. **Notebook UX**: Code cells collapse by default for cleaner interface

### Bug Fixes
1. Gain/Loss formula: Changed from `(Comp - Base) × Qty` to `(Base - Comp) × Qty`
2. Removed misleading "Overall Change" comparison in Section 6
3. Fixed Section 5 histogram chart rendering issues by switching to matplotlib
4. Fixed pie chart label overlap by using legend below instead of annotations

### Documentation
1. Renamed "How to run python code on Windows.md" to "How to run on Windows.md"
2. Complete rewrite of setup guide with detailed Google Colab and Windows instructions
3. Added "Understanding the Notebook Interface" section explaining Jupyter concepts
4. Added detailed step-by-step instructions for each analysis section
5. Added table explaining interactive elements (date pickers, dropdowns, etc.)
6. Updated README.md with user-friendly explanations
7. Updated CLAUDE.md with technical details and design decisions

### Other
1. Added `*.csv` and `exports/` to `.gitignore`
2. Updated `requirements.txt` - added `ipympl` for interactive matplotlib
