# How to Run Python Code on Windows

This guide will help you run Python data analysis scripts on your Windows computer.

## Option 1: Google Colab (Easiest - No Installation)

Google Colab lets you run Python code in your browser. No installation required.

### Steps:
1. Go to [Google Colab](https://colab.research.google.com/)
2. Sign in with your Google account
3. Click **File → Open notebook** and upload the `.ipynb` file I shared with you
4. To upload your CSV file:
   - Click the folder icon on the left sidebar
   - Click the upload button and select your CSV file
   - Wait for upload to complete
5. Run the code by clicking the play button on each cell (or **Runtime → Run all**)

### Notes:
- Uploaded files are temporary - they disappear when the session ends
- For large files, you may want to upload to Google Drive first, then mount Drive in Colab

---

## Option 2: Install Python on Windows

If you prefer to run scripts locally on your computer.

### Step 1: Download Python

1. Go to [python.org/downloads](https://www.python.org/downloads/)
2. Click the big yellow "Download Python 3.x.x" button

### Step 2: Install Python

1. Run the downloaded installer
2. **IMPORTANT: Check the box that says "Add Python to PATH"** ✓
3. Click "Install Now"
4. Wait for installation to complete
5. Click "Close"

### Step 3: Open Command Prompt

1. Press `Windows key + R`
2. Type `cmd` and press Enter
3. A black window should appear

### Step 4: Verify Python Installation

Type this and press Enter:
```
python --version
```
You should see something like `Python 3.12.0`

### Step 5: Navigate to the Script Folder

If the scripts are in your Downloads folder:
```
cd Downloads
```

Or if they're somewhere else, use the full path:
```
cd C:\Users\YourName\Desktop\DataAnalysis
```

### Step 6: Install Required Packages

If there's a `requirements.txt` file:
```
pip install -r requirements.txt
```

Or install packages individually:
```
pip install pandas
```

### Step 7: Run the Script

```
python script_name.py
```

Replace `script_name.py` with the actual filename.

---

## Troubleshooting

### "python is not recognized"
- Python wasn't added to PATH during installation
- Uninstall Python, reinstall, and make sure to check "Add Python to PATH"

### "pip is not recognized"
- Try using `python -m pip install` instead of `pip install`

### Package installation fails
- Try: `python -m pip install --upgrade pip` first
- Then retry installing the package

---

## Quick Reference

| Task | Command |
|------|---------|
| Check Python version | `python --version` |
| Install a package | `pip install package_name` |
| Run a script | `python script_name.py` |
| Change directory | `cd folder_name` |
| Go up one folder | `cd ..` |
| List files | `dir` |
