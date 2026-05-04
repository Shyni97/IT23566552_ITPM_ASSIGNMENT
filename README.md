# Playwright Test Automation Project

This repository contains a Playwright-based Python automation script that reads test cases from an Excel workbook and writes the actual outputs and test statuses back into the workbook.

Contents
- `test_automation/` — contains `test_automation.py` and the Excel test data `Assignment 1 - Test cases.xlsx`.
- Project files: `README.md`, `requirements.txt`, `.gitignore`, `repo_link.txt` (this file contains the remote GitHub URL).

Scripts and configuration
- `test_automation/test_automation.py` — main runner script. It uses Playwright for browser automation and OpenPyXL to read/write Excel files.
- `requirements.txt` — Python dependencies used by this project (`playwright`, `openpyxl`).
- `.gitignore` — recommended ignore rules for Python projects and generated files.

How it works (high level)
- The script locates the header row in the Excel sheet, finds input and expected columns, iterates each test row, types the input into the frontend, captures the translation/actual output, and writes `Actual output` and `Status` back to the sheet.

Install dependencies (Windows)

1. Open PowerShell and create a virtual environment in the repository root:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

2. Upgrade pip and install Python packages:

```powershell
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

3. Install Playwright browser binaries (Chromium):

```powershell
python -m playwright install chromium
```

Running the tests

From the repository root (with the venv activated) run:

```powershell
python test_automation\test_automation.py --excel "test_automation\Assignment 1 - Test cases.xlsx" --url "https://www.pixelssuite.com/chat-translator" --wait-ms 5000 --type-delay-ms 80 --slow-mo-ms 200 --save-every 1
```

Optional flags
- `--headless` — run browser in headless mode.
- `--max-cases N` — stop after processing N test cases (useful for quick runs).
- `--output <path>` — path to save updated workbook; defaults to input Excel path.
- `--save-every N` — save workbook every N processed cases.
- `--wait-ms`, `--retries`, `--retry-wait-ms` — tune timing and retries for slower frontends.

Troubleshooting
- If you see `ModuleNotFoundError: No module named 'playwright'`, ensure you installed requirements inside the activated virtualenv and ran `python -m playwright install chromium`.
- If output appears stale between rows, increase `--wait-ms` and `--retries`, or run without `--headless` to observe the UI.
- If `playwright` command is not found on your PATH, call it with `python -m playwright` from inside the venv.

Preserving results
- The script overwrites the `Actual output` and `Status` columns in the Excel file. To keep a backup, either copy the workbook before running or provide `--output` with a new filename.

Repository link
- See `repo_link.txt` for the Git remote URL.

License
- MIT
