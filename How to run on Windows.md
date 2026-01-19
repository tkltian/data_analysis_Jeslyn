# How to Run the PO Data Analysis Tool

This guide will help you run the Purchase Order analysis tool. **No programming experience required!**

**Features:**
- Interactive charts with **zoom, pan, and save** capabilities (toolbar appears below charts)
- Filter products by category (Category, Line, Type, Class, Construction)
- Export all tables to CSV for use in Excel
- Color-coded results (Green = savings, Red = paid more)

**Choose one option:**
- **Option 1: Google Colab** (Recommended!) - Easiest method, runs in your web browser, nothing to install
- **Option 2: Local Installation** - Install Python on your Windows computer

---

# Option 1: Google Colab (Recommended - No Installation!)

Google Colab is a free service from Google that lets you run Python code in your web browser. You don't need to install anything on your computer!

## What You Need Before Starting

1. A Google account (Gmail)
2. The notebook file: `po_analysis.ipynb`
3. Your data file: `PO Data.csv`

---

## Step 1: Open Google Colab

1. Open your web browser (Chrome works best, but Edge or Firefox also work)
2. Go to this website: **https://colab.research.google.com/**
3. You will see a page asking you to sign in or showing recent notebooks
4. If you're not already signed in to Google:
   - Click **"Sign in"** in the top right corner
   - Enter your Gmail email address and click **Next**
   - Enter your password and click **Next**
   - You should now see the Google Colab main page

---

## Step 2: Upload the Notebook File

The notebook file (`po_analysis.ipynb`) contains all the analysis tools. You need to upload it to Colab.

1. Look at the top menu bar and click **File**
2. A dropdown menu will appear. Click **Upload notebook**
3. A dialog box will appear with tabs at the top
4. Click the **Browse** button (or you might see "Choose file")
5. A file browser window will open on your computer
6. Navigate to where you saved the `po_analysis.ipynb` file:
   - If it's on your Desktop, click "Desktop" on the left side
   - If it's in Downloads, click "Downloads" on the left side
   - If it's in a folder, double-click folders to open them until you find the file
7. Click on `po_analysis.ipynb` to select it (it will be highlighted)
8. Click **Open**
9. Wait a few seconds - the notebook will upload and open automatically
10. You should now see the notebook with multiple sections of code and text

---

## Step 3: Upload Your CSV Data File

**IMPORTANT: You must do this step BEFORE running any code!**

Your CSV file contains all the Purchase Order data that will be analyzed.

1. Look at the **left side** of the screen
2. Find and click the **folder icon** (📁) - it's a small icon that looks like a folder
   - If you don't see it, look for a small arrow or tab on the left edge and click it
3. A panel will slide open showing "Files"
4. At the top of this panel, you'll see some small icons. Click the **upload icon** (it looks like a paper with an up arrow 📤)
5. A file browser window will open
6. Find your CSV file (it should be named `PO Data.csv`)
7. Click on it to select it
8. Click **Open**
9. **Wait for the upload to complete!**
   - You'll see a progress bar
   - For large files, this might take a minute or two
   - Don't proceed until the upload is finished
10. Your file should now appear in the file list on the left

**File naming options:**
- **Option A (Easiest):** Name your file `PO Data.csv` - this is the default and will work automatically
- **Option B:** Keep your own filename - after uploading, you can change the filename in the notebook's "Data File" text box before clicking "Load Data"

---

## Step 4: Run the Notebook

Now you'll run all the code to activate the analysis tools.

1. Look at the top menu bar and click **Runtime**
2. A dropdown menu will appear. Click **Run all**
3. You might see a warning message that says "This notebook was not authored by Google"
   - This is normal! Click **Run anyway**
4. The notebook will start running all the code sections
5. **Watch for the progress:**
   - Each code section (called a "cell") has a small play button ▶️ on the left
   - While running, you'll see a spinning circle ⏳
   - When finished, you'll see a green checkmark ✓ or a number like [1], [2], etc.
6. **Wait for ALL cells to finish running** - this might take 30-60 seconds
7. If you see any red error messages, scroll up to find them - see Troubleshooting section below

---

## Step 5: Understanding the Notebook Interface

Before using the tools, let's understand what you're looking at:

### What is a Jupyter Notebook?

A Jupyter notebook is like a document that contains both text explanations AND working code. Think of it as a smart document where you can click buttons and see results.

### The Notebook Layout

When the notebook opens, you'll see it divided into **cells** (rectangular boxes):

1. **Text cells** (gray/white background) - These contain explanations and instructions. Just read them!

2. **Code cells** (with `[ ]:` or `[1]:` on the left) - These contain the actual program code. You don't need to understand the code - just run it!

3. **Output cells** - These appear below code cells and show results, charts, buttons, and tables.

### How to Scroll Through the Notebook

- Use your **mouse scroll wheel** to move up and down
- Or use the **scrollbar** on the right side of the page
- The notebook is organized into numbered sections (Section 2, 3, 4, 5, 6)
- **Section 1** is the setup code at the top - you don't need to interact with it

### What the Numbers Mean

- `[ ]:` = This cell hasn't run yet
- `[*]:` = This cell is currently running (wait for it!)
- `[1]:`, `[2]:`, etc. = This cell has finished running (the number shows the order)

---

## Step 6: Use the Analysis Tools

Once all cells have run successfully (you see numbers like [1], [2], [3] instead of [*]), scroll down through the notebook to find the interactive analysis sections.

**How to Use Interactive Elements:**

| Element | What It Looks Like | How to Use It |
|---------|-------------------|---------------|
| **Date Picker** | A box with a date | Click on it → A calendar pops up → Click a date |
| **Dropdown** | A box with an arrow ▼ | Click on it → A list appears → Click your choice |
| **Multi-Select List** | A tall box with many items | Click an item to select it. Hold **Ctrl** and click to select multiple items. Click again to deselect. |
| **Checkbox** | A small square ☐ | Click to check ☑ or uncheck ☐ |
| **Button** | A colored rectangle with text | Click it to perform the action |
| **Slider** | A bar with a draggable circle | Click and drag the circle left or right |

---

### Section 2: Monthly Price Trend Chart

**Where to find it:** Scroll down until you see "Section 2: Monthly Price Trend Visualization"

**What it does:** Shows a line chart of how prices changed over time for each product.

**How to use it:**

1. **Filter by category** (optional):
   - Find the dropdown boxes labeled "Category:", "Line:", "Type:", "Class:", "Construction:"
   - Click any dropdown and select a value to filter products
   - Or leave them as "All" to see everything

2. **Select products to display:**
   - Find the tall list box showing product names
   - Products are pre-selected (highlighted in blue)
   - To **remove** a product: Hold **Ctrl** and click on it
   - To **add** a product back: Hold **Ctrl** and click on it
   - Use **"Select All"** or **"Clear All"** buttons for quick selection

3. **View the chart:**
   - The chart updates automatically when you change selections
   - **Legend is below the chart** - shows which color = which product

4. **Use the chart toolbar** (below the chart):
   - 🏠 **Home** - Reset to original view
   - ◀ ▶ **Arrows** - Go back/forward in view history
   - ✛ **Pan** - Click and drag to move around the chart
   - 🔍 **Zoom** - Draw a rectangle to zoom into that area
   - 💾 **Save** - Save chart as an image file

5. **View data tables:**
   - Scroll down below the chart to see data tables
   - Check **"Show All Rows (scrollable)"** to see all data
   - Click **"Export to CSV"** to download for Excel

---

### Section 3: Weighted Average Calculator

**Where to find it:** Scroll down until you see "Section 3: Weighted Average Calculator"

**What it does:** Calculates the true average price you paid for products in a date range.

**How to use it:**

1. **Filter by category** (optional):
   - Use the category dropdowns to narrow down products

2. **Select products:**
   - In the product list, select which products to analyze
   - Default is "All Products" - leave this selected to analyze everything

3. **Select date range:**
   - Click the **Start Date** box → select a date from the calendar
   - Click the **End Date** box → select a date from the calendar

4. **Display options:**
   - Check **"Show All Rows (scrollable)"** if you want to see all rows in tables

5. **Calculate:**
   - Click the **"Calculate Weighted Average"** button
   - Results appear below!

6. **View results:**
   - **Summary table** - Shows weighted average, quantity, and value per product
   - **Monthly Price Pivot** - Shows prices by month (like Excel pivot table)
   - **Monthly Quantity Pivot** - Shows quantities by month
   - Click any **"Export to CSV"** button to download that table

---

### Section 4: Deviation Analysis

**Where to find it:** Scroll down until you see "Section 4: Deviation Analysis"

**What it does:** Shows how each purchase compares to the average price.

**How to use it:**

1. **Set up filters and date range** (same as Section 3)

2. **Click "Analyze Deviations"** button

3. **View deviation tables:**
   - **Monthly Deviation (Dollars)** - How much above/below average each month
   - **Monthly Deviation (Percent)** - Same as above, but in percentages
   - **Individual PO Deviations** - Every single purchase order's deviation

4. **Filter by threshold:**
   - Use the slider to show only large deviations
   - Example: Set to "$2" to see only items that are $2+ above or below average

5. **Understand the colors:**
   - **GREEN** = Below average (you paid LESS - savings!)
   - **RED** = Above average (you paid MORE)

---

### Section 5: Deviation Banding Charts

**Where to find it:** Scroll down until you see "Section 5: Deviation Banding"

**What it does:** Groups purchases into price bands and shows visual charts.

**How to use it:**

1. **Set up filters and date range**

2. **Click "Generate Banding Charts"** button

3. **View the histogram:**
   - Shows how much quantity you bought at each price level
   - X-axis: Deviation bands (e.g., "$0-1 below", "$1-2 above")
   - Y-axis: Total quantity purchased
   - **GREEN bars** = Below average (savings)
   - **RED bars** = Above average (paid more)

4. **View the pie chart:**
   - Shows percentage distribution
   - **Legend below the chart** explains each color
   - Percentages shown inside large slices

5. **Use chart toolbar** to zoom, pan, or save images

---

### Section 6: Benchmark Comparison

**Where to find it:** Scroll down until you see "Section 6: Benchmark Comparison"

**What it does:** Compares prices between two time periods to calculate savings or losses.

**How to use it:**

1. **Set up category filters** (optional)

2. **Select BASELINE date range:**
   - This is your reference period (what you're comparing against)
   - Example: Last year's prices

3. **Select COMPARISON date range:**
   - This is the period you want to analyze
   - Example: This year's prices

4. **Click "Compare Ranges"** button

5. **View results:**
   - **Baseline Prices** - Average price per product in baseline period
   - **Comparison Table** - Side-by-side comparison with gain/loss
   - **Histogram & Pie Chart** - Visual distribution of deviations from baseline
   - **Monthly Breakdown** - Month-by-month comparison

6. **Understand Gain/Loss:**
   - **GREEN (Positive)** = You SAVED money (paid less than baseline)
   - **RED (Negative)** = You LOST money (paid more than baseline)
   - Example: Baseline $50, Comparison $45 → Gain of $5 per unit (GREEN)

---

## Important Notes for Google Colab

### Your files are temporary!
- When you close Colab or if your session times out (after ~30-90 minutes of inactivity), your uploaded CSV file will be **deleted**
- You'll need to upload it again next time you use the tool
- This is actually a security feature - your sensitive data isn't stored permanently

### Saving your work
- The notebook itself (with your code) can be saved
- Click **File** → **Save a copy in Drive** to save to your Google Drive
- Or click **File** → **Download** → **Download .ipynb** to save to your computer

### Session timeout
- If you leave Colab idle for too long, it will disconnect
- You'll see a message saying "Runtime disconnected"
- Just click **"Reconnect"** at the top, re-upload your CSV file, and run all cells again

### Exported CSV files
- When you click "Export to CSV" buttons, files are saved to an "exports" folder in Colab
- To download them to your computer:
  - Look in the Files panel on the left
  - Click the arrow next to "exports" folder to expand it
  - Right-click on the CSV file you want
  - Click **"Download"**

---

---

# Option 2: Install on Windows (Local Setup)

This option lets you run the tool on your own computer. It requires installing some software but works without internet once set up.

## What You Need Before Starting

1. A Windows computer
2. The project files:
   - `po_analysis.ipynb` (the analysis notebook)
   - `requirements.txt` (list of required software)
3. Your data file: `PO Data.csv`

---

## Step 1: Download Python

Python is a programming language that the analysis tool runs on. Don't worry - you don't need to know programming to use it!

### 1.1 Go to the Python Website

1. Open your web browser (Chrome, Edge, Firefox)
2. Go to: **https://www.python.org/downloads/**
3. The website will automatically detect you're on Windows

### 1.2 Download Python

1. You'll see a big yellow button that says **"Download Python 3.x.x"** (the exact numbers don't matter, like 3.12.4 or 3.13.0)
2. Click that yellow button
3. A file will start downloading - you'll see it at the bottom of your browser or in your Downloads folder
4. Wait for the download to complete (it's about 25-30 MB)

---

## Step 2: Install Python

### 2.1 Find the Downloaded File

1. Open **File Explorer** (the yellow folder icon in your taskbar, or press Windows key + E)
2. Click **Downloads** on the left side
3. Look for a file named something like `python-3.12.4-amd64.exe`

### 2.2 Run the Installer

1. **Double-click** the Python installer file
2. A window will appear asking "Do you want to allow this app to make changes?" - click **Yes**

### 2.3 CRITICAL: Check the PATH Option

3. **VERY IMPORTANT - READ THIS CAREFULLY!**

   At the bottom of the installer window, you'll see a checkbox that says:

   ☐ **Add python.exe to PATH**

   **YOU MUST CHECK THIS BOX!** Click on it so it shows a checkmark:

   ☑️ **Add python.exe to PATH**

   If you skip this step, Python won't work properly and you'll need to uninstall and reinstall it.

### 2.4 Complete the Installation

4. Click **"Install Now"** (the option at the top)
5. Wait for the installation to complete (you'll see a progress bar)
6. When you see "Setup was successful", click **Close**

---

## Step 3: Create a Project Folder

You need a folder to keep all the project files together.

### 3.1 Create the Folder

1. Open **File Explorer** (press Windows key + E)
2. Click **Documents** on the left side
3. Right-click in the empty white space
4. Click **New** → **Folder**
5. Type a name for your folder, like `POAnalysis` (no spaces!)
6. Press **Enter**

### 3.2 Put Your Files in the Folder

1. Find these files (wherever you saved them):
   - `po_analysis.ipynb`
   - `requirements.txt`
   - `PO Data.csv` (your data file)
2. Copy or move all of them into your new `POAnalysis` folder
3. To verify: double-click the `POAnalysis` folder - you should see all three files inside

---

## Step 4: Open Command Prompt

Command Prompt is a tool that lets you type commands to your computer. It looks like a black window with white text.

### 4.1 Open Command Prompt

1. Press the **Windows key** on your keyboard (it's between Ctrl and Alt, has the Windows logo)
2. Type: **cmd**
3. You'll see **"Command Prompt"** appear in the search results
4. Click on it (or press Enter)
5. A black window will appear - this is the Command Prompt

### 4.2 Navigate to Your Project Folder

You need to tell Command Prompt where your files are.

1. In the Command Prompt, type this command:

```
cd C:\Users\YourUserName\Documents\POAnalysis
```

2. **IMPORTANT:** Replace `YourUserName` with your actual Windows username!
   - Not sure what your username is? Look at the Command Prompt - it shows something like `C:\Users\John>` - in this case, your username is `John`

3. Press **Enter**

4. The prompt should now show your folder path, like:
   ```
   C:\Users\John\Documents\POAnalysis>
   ```

### 4.3 Verify You're in the Right Folder

1. Type this command and press Enter:
```
dir
```

2. You should see your files listed:
   - `po_analysis.ipynb`
   - `requirements.txt`
   - `PO Data.csv`

3. If you don't see these files, you're in the wrong folder. See troubleshooting below.

---

## Step 5: Install Required Packages

Python needs some additional tools (called packages) to run the analysis. This step downloads and installs them automatically.

1. In the Command Prompt, type this command:

```
pip install -r requirements.txt
```

2. Press **Enter**

3. **Wait for it to finish.** You'll see lots of text scrolling - this is normal! It's downloading and installing the required packages.

4. This might take 2-5 minutes depending on your internet speed.

5. When it's done, you'll see your prompt again (like `C:\Users\John\Documents\POAnalysis>`)

### If You See an Error

If you see an error message like "'pip' is not recognized", try this command instead:

```
python -m pip install -r requirements.txt
```

---

## Step 6: Start Jupyter Notebook

Jupyter Notebook is the program that runs the analysis tool.

1. In the Command Prompt, type:

```
jupyter notebook
```

2. Press **Enter**

3. **What happens next:**
   - You'll see some text appear in the Command Prompt
   - A new browser window (or tab) will open automatically
   - You'll see a page listing the files in your folder

4. **If the browser doesn't open automatically:**
   - Look in the Command Prompt for a line that looks like:
     ```
     http://localhost:8888/?token=abc123...
     ```
   - Copy that entire URL (select it, right-click, choose Copy)
   - Open your web browser
   - Paste the URL in the address bar and press Enter

5. **Keep the Command Prompt window open!** If you close it, Jupyter will stop working.

---

## Step 7: Open the Analysis Notebook

1. In the browser, you'll see a list of files
2. Click on **`po_analysis.ipynb`**
3. The notebook will open in a new tab
4. You'll see sections with code and text

---

## Step 8: Run the Notebook

1. Click **Cell** in the top menu
2. Click **Run All**
3. Wait for all cells to finish running (you'll see numbers appear next to each code block, like [1], [2], [3])
4. If you see `[*]` next to a cell, it means it's still running - wait for it to finish

---

## Step 9: Use the Analysis Tools

Scroll down through the notebook to use the interactive tools. See the descriptions in "Step 5: Use the Analysis Tools" in the Colab section above - the tools work exactly the same way!

---

## Running the Tool Next Time

Once you've done the initial setup, running the tool again is much simpler:

1. Open Command Prompt (Windows key → type "cmd" → Enter)
2. Navigate to your folder:
   ```
   cd C:\Users\YourUserName\Documents\POAnalysis
   ```
3. Start Jupyter:
   ```
   jupyter notebook
   ```
4. Click on `po_analysis.ipynb` in your browser
5. Click **Cell** → **Run All**

---

---

# Using Your Own Data Files

## Required Format

Your CSV file must have these columns with these **exact** names (including spaces):

| Column Name | What It Contains | Example |
|-------------|------------------|---------|
| `PO#` | Purchase Order number | PO-12345 |
| `Material` | Product ID number | 78924 |
| `Short Name` | Product name | "Widget Blue" |
| `PO Date` | Date of the PO | 1/29/25 |
| `Ordered Q'ty` | Quantity ordered | 500 |
| ` Purchase Price ` | Price per unit ($ is OK) | $41.70 |

**Note:** The `Purchase Price` column has spaces before and after the name. This is intentional and must match exactly.

## Optional Columns (for Category Filtering)

These columns enable the category filter dropdowns. If you don't have them, the filters will be empty but the tool will still work:

| Column Name | What It's For |
|-------------|---------------|
| `Material Category Description` | Filter by product category |
| `Material Line Description` | Filter by product line |
| `Material Product Type Description` | Filter by product type |
| `Material Class Description` | Filter by product class |
| `Construction Type Description` | Filter by construction type |

## Other Optional Columns

These columns are helpful but not required:

- `Vendor Name` - Supplier name
- `Color` - Product color
- `Size` - Product size (SML, MED, LG, etc.)

## How to Prepare Your CSV File

### If Your Data is in Excel:

1. Open your Excel file
2. Make sure the column names match exactly (see table above)
3. Click **File** → **Save As**
4. Choose where to save it
5. In "Save as type", select **CSV (Comma delimited) (*.csv)**
6. Name it `PO Data.csv` (or any name - you can specify it in the notebook)
7. Click **Save**
8. If you see a warning about features not compatible with CSV, click **Yes** to continue

### If Your Column Names Don't Match:

1. Open your CSV or Excel file
2. Rename the columns to match exactly:
   - Your "Purchase Order" column → rename to `PO#`
   - Your "Product ID" column → rename to `Material`
   - Your "Product Name" column → rename to `Short Name`
   - Your "Order Date" column → rename to `PO Date`
   - Your "Quantity" column → rename to `Ordered Q'ty`
   - Your "Unit Price" column → rename to ` Purchase Price ` (with spaces!)
3. Save as CSV

---

---

# Troubleshooting

## Google Colab Problems

### "File not found" error when running the notebook

**Problem:** The notebook can't find your CSV file.

**Solutions:**
1. Check that you uploaded the file (look in the Files panel on the left)
2. Make sure the filename in the "Data File" text box matches your actual file name
3. If your file has a different name than `PO Data.csv`:
   - Type your actual filename in the "Data File" text box
   - Click the "Load Data" button
4. Try re-uploading the file
5. After uploading, click "Load Data" again (or run all cells: **Runtime** → **Run all**)

### Charts or widgets not showing

**Problem:** You see empty spaces where charts should be, or buttons don't appear.

**Solutions:**
1. Make sure you ran ALL cells: **Runtime** → **Run all**
2. Wait for all cells to finish (no spinning circles)
3. Try refreshing the page (press F5) and run all cells again
4. If using an older browser, try Chrome instead

### Interactive toolbar not showing on charts

**Problem:** Charts display but there's no zoom/pan toolbar below them.

**Solution:** This is normal if `ipympl` is not installed. The charts will still work, you just won't have the zoom/pan buttons. To enable the toolbar:
1. In a code cell, run: `!pip install ipympl`
2. Restart the runtime: **Runtime** → **Restart runtime**
3. Run all cells again: **Runtime** → **Run all**

### Session disconnected

**Problem:** You see "Runtime disconnected" or similar message.

**Solutions:**
1. Click the **"Reconnect"** button at the top of the page
2. Re-upload your CSV file (it was deleted when disconnected)
3. Run all cells again: **Runtime** → **Run all**

---

## Windows Installation Problems

### "python is not recognized as an internal or external command"

**Problem:** You didn't check "Add Python to PATH" during installation.

**Solution:**
1. Open **Settings** (Windows key → type "settings" → Enter)
2. Click **Apps**
3. Find **Python** in the list
4. Click on it and click **Uninstall**
5. Wait for uninstall to complete
6. Go back to Step 1 and reinstall Python
7. **This time, make sure to check "Add python.exe to PATH"!**

### "pip is not recognized as an internal or external command"

**Solution:** Use this command instead:
```
python -m pip install -r requirements.txt
```

### "jupyter is not recognized"

**Solution:**
1. First, install Jupyter directly:
```
python -m pip install jupyter
```
2. Then start it with:
```
python -m jupyter notebook
```

### "No such file or directory" or "cannot find the path specified"

**Problem:** You're not in the right folder.

**Solution:**
1. Open File Explorer
2. Navigate to your POAnalysis folder
3. Click in the address bar at the top (where it shows the folder path)
4. Select all the text and copy it (Ctrl+C)
5. In Command Prompt, type: `cd ` (with a space after cd)
6. Right-click to paste the path
7. Press Enter

### The browser shows "Unable to connect" or similar

**Problem:** Jupyter server isn't running or wrong URL.

**Solutions:**
1. Make sure the Command Prompt window is still open and running
2. Look in the Command Prompt for a line starting with `http://localhost:8888`
3. Copy that entire URL and paste it in your browser

### Notebook shows errors when running

**Problem:** There's an issue with your data file.

**Solutions:**
1. Make sure `PO Data.csv` is in the same folder as the notebook
2. Check that your CSV file has all the required columns (see "Using Your Own Data Files" section)
3. Try running cells one at a time by clicking the play button ▶️ on each cell to find which one has the error
4. Look at the error message - it often tells you what's wrong

### Interactive toolbar not showing on charts (Windows)

**Problem:** Charts display but there's no zoom/pan toolbar below them.

**Solution:** This happens if `ipympl` is not properly installed. The charts will still work without the toolbar. To enable it:
1. Open Command Prompt
2. Navigate to your project folder
3. Run: `pip install ipympl`
4. Restart Jupyter: close the browser tab, press Ctrl+C in Command Prompt, then start Jupyter again with `jupyter notebook`
5. Run all cells again

---

---

# Quick Reference Cards

## Google Colab Quick Reference

| What You Want to Do | How to Do It |
|---------------------|--------------|
| Upload a file | Click folder icon (📁) on left → Click upload icon (📤) |
| Run all code | **Runtime** menu → **Run all** |
| Save notebook to Drive | **File** menu → **Save a copy in Drive** |
| Download notebook | **File** menu → **Download** → **Download .ipynb** |
| Download exported CSV | Files panel → Right-click file → **Download** |
| Reconnect after timeout | Click **Reconnect** button at top |
| Restart and clear outputs | **Runtime** menu → **Restart and run all** |

## Windows Commands Quick Reference

| What You Want to Do | Command to Type |
|---------------------|-----------------|
| Open your project folder | `cd C:\Users\YourName\Documents\POAnalysis` |
| List files in folder | `dir` |
| Install required packages | `pip install -r requirements.txt` |
| Start Jupyter Notebook | `jupyter notebook` |
| Check if Python is installed | `python --version` |
| Stop Jupyter (in Command Prompt) | Press Ctrl+C twice |

---

# Need Help?

If you're stuck:

1. **Take a screenshot** of the error message or problem
2. **Note which step** you were on
3. **Write down what you tried**
4. Send this information to the person who gave you this tool

**Common things to double-check:**
- Is your CSV file named exactly `PO Data.csv`?
- Is the CSV file in the same location as the notebook?
- Did you run ALL the cells, starting from the top?
- For Windows: Did you keep the Command Prompt window open?
