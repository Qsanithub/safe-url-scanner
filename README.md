# safe-url-scanne
python scan_urls.py
name: URL Scanner
name: URL Scanner
on:
  push:
    paths:
      - "urls.txt"

jobs:
  scan:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Repo
        uses: actions/checkout@v3

      - name: Setup Python
        uses: actions/setup-python@v4
        with:
          python-version: "3.x"

      - name: Install Dependencies
        run: pip install -r requirements.txt

      - name: Run URL Scan
        env:
          API_KEY: ${{ secrets.VT_API_KEY }}
        run: python scan_urls.py
