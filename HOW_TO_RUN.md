# How to run the CanLII Section 11(b) scanner

Yes — you're likely right. If the code is only on GitHub and not cloned locally, your Mac won't have `tools/canlii_section11b_scan.py` yet.

## 0) First, clone from GitHub to your Mac
```bash
cd ~
git clone <YOUR_GITHUB_REPO_URL>
cd <YOUR_REPO_FOLDER>
```

You can verify the file exists with:
```bash
ls tools/canlii_section11b_scan.py
```

## 1) Create and activate a virtual environment
```bash
python3 -m venv .venv
source .venv/bin/activate
```

## 2) Install dependencies
```bash
python -m pip install --upgrade pip
python -m pip install playwright
python -m playwright install chromium
```

## 3) Run the scanner
### Option A: direct
```bash
python tools/canlii_section11b_scan.py
```

### Option B: wrapper (safer for path issues)
```bash
./run_canlii_scan.sh
```

The wrapper resolves paths relative to the repo, which avoids `can't open file .../tools/canlii_section11b_scan.py` when your current directory is wrong.

## Quick troubleshooting
- `python: can't open file '/Users/.../tools/canlii_section11b_scan.py'`
  - You're not in the repo folder. Run `cd <YOUR_REPO_FOLDER>` first.
- `ModuleNotFoundError: No module named 'playwright'`
  - Ensure venv is active and re-run install commands.
- Browser binary missing
  - Re-run: `python -m playwright install chromium`.
- Anti-bot block on CanLII
  - Use an approved environment/network or authorized API access.
