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

## Summary of Changes Made

### Features Implemented
1. **Section 2**: Line chart with matplotlib, category filters + product filter
2. **Section 5**: Color swap (green=below avg/savings, red=above avg/paid more), matplotlib bar chart and pie chart
3. **Section 6**: Fixed Gain/Loss calculation sign convention, per-product comparison, color coding
4. **All Sections**: Standardized to 2 decimal places
5. **All Tables**: Added CSV export buttons
6. **Sections 2, 3, 4, 5, 6**: Added category-based filtering (5 dropdowns)
7. **Section 4**: Added green/red color coding for deviations
8. **Sections 3, 4, 5, 6**: Added "Show All Rows (scrollable)" toggle
9. **All Charts**: Replaced Plotly with matplotlib for reliable rendering

### Bug Fixes
1. Gain/Loss formula: Changed from `(Comp - Base) × Qty` to `(Base - Comp) × Qty`
2. Removed misleading "Overall Change" comparison in Section 6
3. Fixed Section 5 histogram chart rendering issues by switching to matplotlib

### Documentation
1. Renamed "How to run python code on Windows.md" to "How to run on Windows.md"
2. Complete rewrite of setup guide with detailed Google Colab and Windows instructions
3. Updated README.md with user-friendly explanations
4. Updated CLAUDE.md with technical details and design decisions

### Other
1. Added `*.csv` and `exports/` to `.gitignore`
2. Updated `requirements.txt` - replaced `plotly` with `numpy`
