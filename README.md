
fx-carry-strategy

Systematic G10 FX Carry Strategy

Long high-yielding currencies, short low-yielding ones — the classic FX carry
trade — built as a research backtest on real data.

Data
- FX spot: Yahoo Finance.
- 3-month interbank rates: FRED, pulled directly as CSV (no extra package,
  no API key).

Method
- Each month, rank six G10 currencies by their short rate; go long the top two,
  short the bottom two.
- Total return of holding a currency = spot move vs USD + interest earned; the
  USD funding leg cancels in a dollar-neutral long-short book.
- Signals lagged one month (no look-ahead), volatility-targeted positions,
  transaction costs on turnover, in-sample / out-of-sample split.

Running it
```bash
pip install yfinance pandas numpy matplotlib
```
Run the notebook top to bottom. Saves `fx_carry_results.png`.

Results
*Paste the performance tables + chart here after running.*

Limitations
- Monthly rebalancing on monthly rate data; intraday execution not modelled.
- Flat transaction-cost assumption.
- If a FRED series stops updating, its rate is carried forward; swap the series
  ID for an equivalent 3-month rate if needed.
