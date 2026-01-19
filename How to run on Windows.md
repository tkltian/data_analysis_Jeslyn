# How to Run the PO Data Analysis Tool

This guide will help you run the Purchase Order analysis tool and load your own CSV data files.

**Choose one option:**
- **Option 1: Google Colab** - Easiest, no installation, works in your browser
- **Option 2: Local Installation** - Install Python on your Windows computer

---

# Option 1: Google Colab (Recommended - No Installation!)

Google Colab lets you run Python code in your web browser. Nothing to install!

## Step 1: Open Google Colab

1. Open your web browser (Chrome, Edge, Firefox)
2. Go to: **https://colab.research.google.com/**
3. Sign in with your Google account (Gmail)

## Step 2: Upload the Notebook File

1. Click **File** in the top menu
2. Click **Upload notebook**
3. Click **Browse** and find the `po_analysis.ipynb` file
4. Select it and click **Open**
5. Wait for it to upload (you'll see the notebook open)

![Upload notebook](https://i.imgur.com/placeholder1.png)

## Step 3: Upload Your CSV Data File

**IMPORTANT: Do this BEFORE running any code!**

1. Look at the **left side** of the screen
2. Click the **folder icon** (📁) to open the Files panel
3. Click the **upload button** (📤 icon with up arrow)
4. Find your CSV file (e.g., `PO Data.csv`)
5. Select it and click **Open**
6. **Wait for the upload to finish** (you'll see a progress bar)
7. Your file should now appear in the file list

**IMPORTANT:** Your CSV file MUST be named exactly `PO Data.csv` (with the space). If your file has a different name, either:
- Rename your file to `PO Data.csv` before uploading, OR
- After uploading, right-click the file in Colab and rename it to `PO Data.csv`

## Step 4: Run the Notebook

1. Click **Runtime** in the top menu
2. Click **Run all**
3. If you see a warning about "This notebook was not authored by Google", click **Run anyway**
4. Wait for all cells to run (you'll see spinning circles turn to green checkmarks)

## Step 5: Use the Analysis Tools

Scroll down through the notebook to find the interactive sections:
- **Section 2**: Monthly Price Trend Chart
- **Section 3**: Weighted Average Calculator
- **Section 4**: Deviation Analysis
- **Section 5**: Deviation Banding Charts
- **Section 6**: Benchmark Comparison

Each section has buttons and date pickers you can use!

## Important Notes for Colab

- **Files are temporary!** When you close Colab or your session times out, your uploaded CSV file will be deleted. You'll need to upload it again next time.
- **Save your work:** Click **File → Download → Download .ipynb** to save a copy of your notebook with any changes.
- **Session timeout:** If you leave Colab idle for ~30 minutes, it may disconnect. Just reconnect and re-upload your file.

---

# Option 2: Install on Windows (Local Setup)

This option lets you run the tool on your own computer without internet.

## Step 1: Download and Install Python

### 1.1 Download Python

1. Open your web browser
2. Go to: **https://www.python.org/downloads/**
3. Click the big yellow button that says **"Download Python 3.x.x"** (the exact version number doesn't matter)

### 1.2 Install Python

1. Find the downloaded file (usually in your Downloads folder), it's called something like `python-3.12.4-amd64.exe`
2. **Double-click** to run it
3. **VERY IMPORTANT:** Check the box at the bottom that says:

   ☑️ **"Add python.exe to PATH"**

   (If you miss this, Python won't work properly!)

4. Click **"Install Now"**
5. Wait for installation to complete
6. Click **"Close"**

## Step 2: Download the Project Files

1. Download these files from wherever they were shared with you:
   - `po_analysis.ipynb` (the analysis notebook)
   - `requirements.txt` (list of required packages)
2. Create a folder on your computer, for example: `C:\Users\YourName\Documents\POAnalysis`
3. Put both files in that folder
4. Also put your `PO Data.csv` file in the **same folder**

## Step 3: Open Command Prompt

1. Press the **Windows key** on your keyboard
2. Type **cmd**
3. Click on **"Command Prompt"** (the black icon)
4. A black window will appear - this is the Command Prompt

## Step 4: Navigate to Your Project Folder

In the Command Prompt, type this command and press **Enter**:

```
cd C:\Users\YourName\Documents\POAnalysis
```

**Replace `YourName` with your actual Windows username!**

To check if you're in the right folder, type:
```
dir
```

You should see your files listed (`po_analysis.ipynb`, `requirements.txt`, `PO Data.csv`).

## Step 5: Install Required Packages

Type this command and press **Enter**:

```
pip install -r requirements.txt
```

Wait for it to finish. You'll see lots of text scrolling - that's normal!

If you see any errors, try this instead:
```
python -m pip install -r requirements.txt
```

## Step 6: Start Jupyter Notebook

Type this command and press **Enter**:

```
jupyter notebook
```

**What happens:**
- A new browser window will open automatically
- You'll see a list of files in your folder
- If browser doesn't open, look for a URL in the Command Prompt (starts with `http://localhost:8888/`) and copy-paste it into your browser

## Step 7: Open and Run the Notebook

1. In the browser, click on **`po_analysis.ipynb`**
2. The notebook will open in a new tab
3. Click **Cell** in the top menu
4. Click **Run All**
5. Wait for all cells to finish running (you'll see `[*]` turn into `[1]`, `[2]`, etc.)

## Step 8: Use the Analysis Tools

Scroll down to use the interactive sections just like in Colab!

## To Run Again Next Time

1. Open Command Prompt
2. Navigate to your folder: `cd C:\Users\YourName\Documents\POAnalysis`
3. Start Jupyter: `jupyter notebook`
4. Click on the notebook file

---

# How to Use Your Own CSV Files

## CSV File Requirements

Your CSV file must have these columns (with these exact names):

| Required Column | Description |
|-----------------|-------------|
| `PO#` | Purchase Order number |
| `Material` | Product ID number |
| `Short Name` | Product name/description |
| `PO Date` | Date in format M/DD/YY (e.g., 1/29/25) |
| `Ordered Q'ty` | Quantity ordered |
| ` Purchase Price ` | Unit price (can have $ sign and spaces) |

**Optional columns** (used for filtering):
- `Vendor Name`
- `Color`
- `Material Category Description`
- `Material Line Description`
- `Material Product Type Description`
- `Material Class Description`
- `Construction Type Description`

## Steps to Use Your Own Data

1. **Prepare your CSV file:**
   - Make sure it has the required columns listed above
   - Name it exactly: `PO Data.csv`

2. **Replace the data file:**
   - **Colab:** Upload your new `PO Data.csv` (it will replace any existing one)
   - **Local:** Put your `PO Data.csv` in the same folder as the notebook

3. **Re-run the notebook:**
   - **Colab:** Runtime → Run all
   - **Local:** Cell → Run All

4. **Check for errors:**
   - Look at Section 1 output - it should show your data summary
   - If you see errors, check that your column names match exactly

---

# Troubleshooting

## Google Colab Issues

### "File not found" error
- Make sure your CSV file is named exactly `PO Data.csv`
- Make sure you uploaded it to Colab (check the Files panel on the left)
- Re-upload the file and run all cells again

### Charts not showing
- Click Runtime → Run all to run everything again
- Make sure you ran Section 1 first (it loads the data)

### Session disconnected
- Click "Reconnect" at the top
- Re-upload your CSV file
- Run all cells again

## Windows Installation Issues

### "python is not recognized"
**Problem:** You didn't check "Add Python to PATH" during installation.

**Solution:**
1. Uninstall Python (Settings → Apps → Python → Uninstall)
2. Re-install Python
3. This time, CHECK the box "Add python.exe to PATH"

### "pip is not recognized"
**Solution:** Use this command instead:
```
python -m pip install -r requirements.txt
```

### "jupyter is not recognized"
**Solution:**
```
python -m pip install jupyter
python -m jupyter notebook
```

### Can't find my folder
**Solution:**
1. Open File Explorer
2. Navigate to your folder
3. Click in the address bar at the top
4. Copy the full path (e.g., `C:\Users\Jeslyn\Documents\POAnalysis`)
5. In Command Prompt, type: `cd ` then paste the path

### Notebook shows errors when running
- Make sure `PO Data.csv` is in the same folder as the notebook
- Make sure the CSV file has the required columns
- Try running cells one at a time to find where the error occurs

---

# Quick Reference

## Colab Commands

| Action | How to Do It |
|--------|--------------|
| Upload file | Click folder icon → Upload button |
| Run all code | Runtime → Run all |
| Download notebook | File → Download → Download .ipynb |
| Reconnect | Click "Reconnect" button at top |

## Windows Commands

| Action | Command |
|--------|---------|
| Open folder | `cd FolderPath` |
| List files | `dir` |
| Install packages | `pip install -r requirements.txt` |
| Start Jupyter | `jupyter notebook` |
| Check Python | `python --version` |

---

# Need Help?

If you're stuck:
1. Take a screenshot of the error message
2. Note which step you were on
3. Send both to the person who gave you this tool

Common things to check:
- Is your CSV file named exactly `PO Data.csv`?
- Is the CSV file in the same location as the notebook?
- Did you run ALL the cells, starting from the top?
