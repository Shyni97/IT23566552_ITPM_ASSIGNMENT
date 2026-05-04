# Playwright Test Automation

This repository contains a Playwright-based test automation script that reads test cases from an Excel file and writes actual outputs and statuses back to the workbook.

Contents
- `test_automation/` - automation script and test data (Excel workbook)

Requirements
- Python 3.10+ (3.14 tested here)
- Virtual environment recommended

Quick start

1. Create and activate a virtual environment (Windows):

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

2. Install Python dependencies:

```powershell
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

3. Install Playwright browser binaries:

```powershell
python -m playwright install chromium
```

4. Run the tests (example):

```powershell
python test_automation\test_automation.py --excel "test_automation\Assignment 1 - Test cases.xlsx" --url "https://www.pixelssuite.com/chat-translator" --wait-ms 9000 --type-delay-ms 80 --slow-mo-ms 200 --save-every 1 --max-cases 15
```

Notes
- The script overwrites the `Actual output` and `Status` columns in the Excel workbook by default. To keep backups, copy the workbook before running or supply an `--output` path.
- If Playwright is installed globally but not in the virtualenv, run installation inside the venv.
- If outputs look stale between rows, increase `--wait-ms`, `--retries`, and `--retry-wait-ms`.

Repository link
- See `repo_link.txt` for the target remote URL.

License
- MIT (change as needed)
