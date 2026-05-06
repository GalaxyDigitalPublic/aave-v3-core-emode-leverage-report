# aave-v3-core-emode-leverage-report
Analysis of Aave V3 Core E-Mode Loans

- **Ethereum Snapshot Block:** 24932111
- **Snapshot Time:** Apr-22-2026 01:14:23 AM +UTC

---

## Aave market overview (full book: min debt ≥ $100, HF ≤ 50)

```
Positions split by loan_details.e_mode_active. Totals use loan-level debt and collateral from the snapshot; each position needs min debt ≥ $100 and snapshot HF ≤ 50 (strictly greater HF omitted).

Debt-weighted LTV uses loans with collateral > 0; debt-weighted HF uses loans with 1 ≤ HF ≤ 50 among this cohort (underwater HF < 1 and HF ≤ 0 omitted from that average); debt-weighted D/E where equity > 0.

All values shown are net of above filters.
```


| Cohort     | Positions | Debt USD        | Collateral USD  | Debt/collateral | % of book debt | % of book collateral |
| ---------- | --------- | --------------- | --------------- | --------------- | -------------- | -------------------- |
| All        | 19,060    | $10,711,448,252 | $17,373,283,954 | 61.65%          | 100.00%        | 100.00%              |
| E-mode     | 1,372     | $6,303,004,899  | $7,050,166,043  | 89.40%          | 58.84%         | 40.58%               |
| Non-e-mode | 17,688    | $4,408,443,353  | $10,323,117,911 | 42.70%          | 41.16%         | 59.42%               |


```
D_i = position i total debt USD.
C_i = position i total collateral USD.
m_i = position i's value for the metric in that debt-weighted row (current LTV%, liquidation-threshold LTV%, HF, or (D/E)_i, whichever that row averages), among positions eligible for that row.

Debt-weighted metrics (next table). Each entry is a cohort summary Σ(D_i × m_i) / Σ D_i: debt USD D_i weights each position's metric m_i. Only positions eligible for that metric enter the average (HF: 1 ≤ HF ≤ cap as above; LTV: collateral > 0; D/E: equity > 0). Headline position counts and debt/collateral totals still include underwater loans (HF < 1).

Debt-wtd LTV % = debt-weighted average of current LTV% (borrowed notional vs. collateral, as a percent). Positions with zero collateral are excluded.

Debt-wtd liq. threshold LTV % = debt-weighted average of each position's liquidation threshold expressed as LTV% (the LTV% at which the protocol may liquidate). Positions with zero collateral are excluded.

Debt-wtd HF = Σ(D_i × HF_i) / Σ D_i over loans with 1 ≤ HF_i ≤ 50. Underwater loans (HF < 1) and HF ≤ 0 do not contribute; loans above the HF bound are already excluded from this cohort (same eligibility as HF percentiles).

Debt-wtd D/E = Σ(D_i × (D/E)_i) / Σ D_i over positions with equity E_i = C_i − D_i > 0, where (D/E)_i = D_i / E_i.
```


| Cohort     | Debt-wtd LTV % | Debt-wtd liq. threshold LTV % | Debt-wtd HF | Debt-wtd D/E |
| ---------- | -------------- | ----------------------------- | ----------- | ------------ |
| All        | 72.49          | 88.68                         | 1.396       | 6.545        |
| E-mode     | 90.32          | 94.51                         | 1.055       | 10.420       |
| Non-e-mode | 47.01          | 80.35                         | 1.883       | 1.006        |


## Book composition (from snapshot line notionals)


| Metric                         | Value                              |
| ------------------------------ | ---------------------------------- |
| Same cohort as market overview | min debt ≥ $100, snapshot HF ≤ 50. |


**Top collateral symbols — enabled lines (all)**


| Symbol / line     | USD           | Share |
| ----------------- | ------------- | ----- |
| WETH              | 4,272,216,571 | 24.6% |
| WEETH             | 3,585,668,124 | 20.6% |
| WSTETH            | 2,350,521,832 | 13.5% |
| WBTC              | 2,210,851,596 | 12.7% |
| RSETH             | 1,305,899,519 | 7.5%  |
| CBBTC             | 967,608,969   | 5.6%  |
| SUSDE             | 373,955,405   | 2.2%  |
| USDC              | 355,497,955   | 2.0%  |
| USDE              | 338,876,185   | 2.0%  |
| OSETH             | 333,314,172   | 1.9%  |
| USDT              | 327,454,415   | 1.9%  |
| PT-SUSDE-7MAY2026 | 172,804,574   | 1.0%  |


**Top collateral symbols — enabled lines (E-MODE)**


| Symbol / line       | USD           | Share of Collateral Lines        |
| ------------------- | ------------- | -------------------------------- |
| WEETH               | 3,390,969,316 | 48.1% of e-mode collateral lines |
| RSETH               | 1,304,928,638 | 18.5% of e-mode collateral lines |
| WSTETH              | 906,654,981   | 12.9% of e-mode collateral lines |
| SUSDE               | 369,136,497   | 5.2% of e-mode collateral lines  |
| OSETH               | 332,396,965   | 4.7% of e-mode collateral lines  |
| USDE                | 330,631,664   | 4.7% of e-mode collateral lines  |
| PT-SUSDE-7MAY2026   | 172,804,574   | 2.5% of e-mode collateral lines  |
| PT-SRUSDE-25JUN2026 | 74,858,444    | 1.1% of e-mode collateral lines  |
| WETH                | 28,035,387    | 0.4% of e-mode collateral lines  |
| WBTC                | 24,409,245    | 0.3% of e-mode collateral lines  |
| EZETH               | 21,119,881    | 0.3% of e-mode collateral lines  |
| LBTC                | 14,273,813    | 0.2% of e-mode collateral lines  |


**Top collateral symbols — enabled lines (NON E-MODE)**


| Symbol / line | USD           | Share of Collateral Lines       |
| ------------- | ------------- | ------------------------------- |
| WETH          | 4,244,181,183 | 41.1% of non-e collateral lines |
| WBTC          | 2,186,442,351 | 21.2% of non-e collateral lines |
| WSTETH        | 1,443,866,851 | 14.0% of non-e collateral lines |
| CBBTC         | 959,696,000   | 9.3% of non-e collateral lines  |
| USDC          | 348,043,404   | 3.4% of non-e collateral lines  |
| USDT          | 313,723,958   | 3.0% of non-e collateral lines  |
| WEETH         | 194,698,808   | 1.9% of non-e collateral lines  |
| TBTC          | 153,759,157   | 1.5% of non-e collateral lines  |
| LBTC          | 136,720,673   | 1.3% of non-e collateral lines  |
| RETH          | 82,852,860    | 0.8% of non-e collateral lines  |
| LINK          | 76,426,758    | 0.7% of non-e collateral lines  |
| XAUT          | 65,853,198    | 0.6% of non-e collateral lines  |


**Top borrow symbols (all)**


| Symbol / line | USD           | Share |
| ------------- | ------------- | ----- |
| WETH          | 5,475,221,180 | 51.1% |
| USDT          | 2,245,815,476 | 21.0% |
| USDC          | 1,912,962,096 | 17.9% |
| USDE          | 373,081,617   | 3.5%  |
| WBTC          | 137,298,386   | 1.3%  |
| DAI           | 112,311,068   | 1.0%  |
| USDTB         | 103,792,826   | 1.0%  |
| GHO           | 99,995,812    | 0.9%  |
| WSTETH        | 70,087,937    | 0.7%  |
| USDG          | 42,220,227    | 0.4%  |
| EURC          | 37,235,097    | 0.3%  |
| CBBTC         | 31,025,500    | 0.3%  |
| PYUSD         | 26,477,819    | 0.2%  |
| RLUSD         | 19,861,160    | 0.2%  |


**Top borrow symbols — E-MODE**


| Symbol / line | USD           | Share of E-Mode Debt |
| ------------- | ------------- | -------------------- |
| WETH          | 5,363,009,695 | 85.1% of e-mode debt |
| USDT          | 461,930,282   | 7.3% of e-mode debt  |
| USDE          | 201,112,049   | 3.2% of e-mode debt  |
| USDC          | 183,986,766   | 2.9% of e-mode debt  |
| WSTETH        | 51,722,670    | 0.8% of e-mode debt  |
| USDTB         | 30,282,592    | 0.5% of e-mode debt  |
| WBTC          | 4,202,477     | 0.1% of e-mode debt  |
| GHO           | 3,612,110     | 0.1% of e-mode debt  |


**Top borrow symbols — NON E-MODE**


| Symbol / line | USD           | Share               |
| ------------- | ------------- | ------------------- |
| USDT          | 1,783,885,195 | 40.5% of non-e debt |
| USDC          | 1,728,975,330 | 39.2% of non-e debt |
| USDE          | 171,969,567   | 3.9% of non-e debt  |
| WBTC          | 133,095,909   | 3.0% of non-e debt  |
| DAI           | 112,311,068   | 2.5% of non-e debt  |
| WETH          | 112,211,486   | 2.5% of non-e debt  |
| GHO           | 96,383,702    | 2.2% of non-e debt  |
| USDTB         | 73,510,234    | 1.7% of non-e debt  |


**Primary collateral → top borrow symbols (debt ≥ min; top 5 primaries by routed borrow, top 5 borrows each)**

**Primary WEETH  (total borrow routed $3,637,552,506):**


| Borrow symbol | USD           | Share |
| ------------- | ------------- | ----- |
| WETH          | 3,577,976,065 | 98%   |
| USDC          | 40,471,511    | 1%    |
| USDT          | 10,765,350    | 0%    |
| USDE          | 4,162,296     | 0%    |
| GHO           | 1,403,306     | 0%    |


**Primary WETH  (total borrow routed $1,768,419,858):**


| Borrow symbol | USD         | Share |
| ------------- | ----------- | ----- |
| USDT          | 839,465,922 | 47%   |
| USDC          | 693,241,394 | 39%   |
| USDE          | 35,947,089  | 2%    |
| DAI           | 32,164,232  | 2%    |
| WBTC          | 30,253,815  | 2%    |


**Primary RSETH  (total borrow routed $1,189,557,886):**


| Borrow symbol | USD           | Share |
| ------------- | ------------- | ----- |
| WETH          | 1,155,776,200 | 97%   |
| WSTETH        | 28,984,647    | 2%    |
| USDT          | 4,737,292     | 0%    |
| USDC          | 59,183        | 0%    |
| EURC          | 462           | 0%    |


**Primary WBTC  (total borrow routed $956,518,562):**


| Borrow symbol | USD         | Share |
| ------------- | ----------- | ----- |
| USDT          | 508,215,931 | 53%   |
| USDC          | 303,801,261 | 32%   |
| DAI           | 42,308,631  | 4%    |
| USDTB         | 26,165,272  | 3%    |
| GHO           | 21,567,414  | 2%    |


**Primary WSTETH  (total borrow routed $867,056,540):**


| Borrow symbol | USD         | Share |
| ------------- | ----------- | ----- |
| WETH          | 324,078,397 | 37%   |
| USDT          | 283,012,280 | 33%   |
| USDC          | 143,395,692 | 17%   |
| USDE          | 52,967,061  | 6%    |
| GHO           | 21,043,318  | 2%    |


## Aave V3 leverage snapshot (e-mode cohort)

E-mode borrowers in snapshot: 1,998 | after min debt $100 & HF ≤ 50: 1,372

### E MODE


| Metric                                    | Value          |
| ----------------------------------------- | -------------- |
| Borrowers                                 | 1,372          |
| Total collateral (sum of position totals) | $7,050,166,043 |
| Total debt                                | $6,303,004,899 |
| Implied aggregate debt/collateral         | 89.40%         |


```
Definition: index i runs over positions in this cohort after the min-debt filter and excluding snapshot HF strictly above 50. D_i and C_i refer to loan-level totals for each remaining position (fields below). Borrowers, collateral, debt, and implied aggregate debt/collateral above match that cohort.

Debt-weighted average HF and HF percentiles below use only positions with 1 ≤ snapshot HF ≤ 50 (underwater HF < 1 omitted).

D_i = position i total debt USD (`loan_details.approx_total_debt_usdc` or `total_debt_value_base_display`).
C_i = position i total collateral USD (`loan_details.approx_total_collateral_usdc` or `total_collateral_value_base_display`).
```


| Metric                                 | Value  |
| -------------------------------------- | ------ |
| Debt-weighted avg LTV%                 | 90.32  |
| Debt-weighted avg liq. threshold LTV%  | 94.51  |
| Debt-weighted avg HF (1 ≤ HF ≤ 50)     | 1.055  |
| Debt-weighted avg D/E (where equity>0) | 10.420 |


```
Definition: same D_i and C_i as above — loan-level totals from `loan_details`, same cohort (min debt & HF ≤ 50). Equity for position i is E_i = C_i − D_i. Only positions with E_i > 0 are included (equivalently C_i > D_i; positions with C_i ≤ D_i are dropped). (D/E)_i = D_i / E_i. Debt-weighted cohort D/E = (Σ_i D_i · (D/E)_i) / (Σ_i D_i) over that set — same weighting as other debt-weighted lines here. D/E percentiles below are unweighted order statistics of those (D/E)_i values (no debt weights). HF percentiles: same 1 ≤ HF ≤ 50 filter (underwater omitted).
```


| Metric                             | Value                                                            |
| ---------------------------------- | ---------------------------------------------------------------- |
| LTV% percentiles (p50/p75/p90/p95) | p50 **82.7** · p75 **92.0** · p90 **93.1** · p95 **93.1**        |
| Liq. threshold LTV% percentiles    | p50 **93.0** · p75 **95.0** · p90 **95.0** · p95 **95.0**        |
| HF percentiles                     | p50 **1.117** · p75 **1.578** · p90 **2.400** · p95 **3.307**    |
| D/E percentiles                    | p50 **4.767** · p75 **11.563** · p90 **13.469** · p95 **13.560** |


**Top collateral symbols by enabled line value (showing 15):**


| Symbol              | Collateral USD (enabled lines) | Primary accounts |
| ------------------- | ------------------------------ | ---------------- |
| WEETH               | 3,390,968,685                  | 233              |
| RSETH               | 1,304,928,525                  | 28               |
| WSTETH              | 906,653,728                    | 119              |
| SUSDE               | 369,135,350                    | 154              |
| OSETH               | 332,395,196                    | 158              |
| USDE                | 330,630,897                    | 45               |
| PT-SUSDE-7MAY2026   | 172,804,457                    | 30               |
| PT-SRUSDE-25JUN2026 | 74,858,441                     | 7                |
| WETH                | 28,033,921                     | 204              |
| WBTC                | 24,409,186                     | 71               |
| EZETH               | 21,119,881                     | 3                |
| LBTC                | 14,273,797                     | 12               |
| USDT                | 13,730,352                     | 14               |
| SYRUPUSDT           | 10,451,352                     | 8                |
| CBBTC               | 7,912,965                      | 13               |


## E-MODE: per-collateral-symbol depeg analysis


| Metric                                 | Value                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| -------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Population                             | e-mode loans only — loan_details.e_mode_active, debt ≥ $100, snapshot HF ≤ 50. Non-e-mode borrowers excluded (1,372 positions).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| HF_stress uses protocol-style HF       | (Σ collateral_value_base × LT_i) / total_debt_base, where LT_i is each line’s effective liquidation_threshold_bps (e-mode / position-aware). Optional reserve_liquidation_threshold_bps is not used for HF.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Grid debt & collateral aggregates      | **Per-symbol grids:** debt USD = full loan debt; **full collateral USD** = all enabled collateral at snapshot; **shock leg USD** = enabled USD in the shocked ticker only; **post shock USD** = that full collateral minus **(depeg × shock leg)** (value wiped only on shocked lines; matches HF_stress). **Sleeve grids:** same column meanings with **shock leg** = USD in the shocked sleeve bucket(s); **post shock** = full collateral minus **(depeg × shock leg)**.                                                                                                                                                                                                                                                                                                                                                           |
| Implied # of loops — math              | Per-symbol table, **loops row only** (see next row for who is in that subcohort). Let L = debt-weighted average **current LTV** as a decimal (LTV% ÷ 100) and (D/E) = debt-weighted average **debt/equity** where equity > 0, both from the **≥99% concentration subcohort** described in the next row (same debt weights as elsewhere). Then implied loops N = ln((1 − (D/E)(1 − L)) / L) / ln(L) (natural logs); equivalently, under a single-asset constant-L heuristic, N satisfies L^(N+1) = 1 − (D/E)(1 − L). The **Implied # of loops** table row is **omitted** if L ∉ (0, 1), the log argument is non-positive, the value is not finite, that concentration subcohort is empty, or inputs are missing. Other snapshot rows (LTV, liq. LTV, HF, D/E) use all positions with ≥$1 in the ticker — not that concentration slice. |
| Implied # of loops — filters & tickers | The **Implied # of loops** row is printed only for symbols in **liquid staking ETH**, **liquid restaking ETH**, **yield-bearing stable**, or **Pendle PT** (`PT-…` prefix) e-mode depeg buckets. For that row only, L and (D/E) are computed on loans where the named symbol is ≥ 99% of **enabled** collateral (exact ticker match for spot tickers; PT lines match the full `PT-…` symbol), plus ≥ $1 in that symbol, debt ≥ $100, snapshot HF ≤ 50, snapshot HF ≥ 1, then **build_report** (HF cap). If no loan passes the **99%** filter or the formula has no finite solution, the loops row is **omitted**; the rest of the per-symbol snapshot table is unchanged and still uses the broader ≥$1 cohort.                                                                                                                       |


> Borrow notionals held flat in base units. Each scenario scales only the listed sleeve’s collateral line values by (1 − depeg); other lines unchanged.

> Mixed collateral — isolated-sleeve grids shock only the enabled lines in that symbol bucket on each loan (e.g. yield-bearing vs fiat-pegged stable lines are independent). The combined stables+Pendle PT block applies the same haircut to yield stables, fiat stables, and PT lines together.

#### Per symbol — WEETH

> Aggregate enabled e-mode collateral in this ticker: $3,390,968,685    positions with ≥$1 in this ticker: 259

**Debt-weighted snapshot — positions with ≥$1 enabled collateral in this ticker (same cohort as stress grid: min debt, HF ≤ 50, HF ≥ 1)**


| Metric                                                                                 | Value                   |
| -------------------------------------------------------------------------------------- | ----------------------- |
| Debt-weighted avg LTV%                                                                 | 90.82                   |
| Debt-weighted avg liq. threshold LTV%                                                  | 94.97                   |
| Debt-weighted avg HF (1 ≤ HF ≤ 50)                                                     | 1.048                   |
| Debt-weighted avg D/E (where equity>0)                                                 | 10.582                  |
| Implied # of loops (where per-symbol asset ≥ 99% of enabled collateral)                | 41.763                  |
| Σ enabled USD in this ticker (≥99% concentration subcohort; % of ≥$1-in-ticker cohort) | $2,668,662,621 / 78.70% |


> Implied loss on shocked symbol only (%) → HF_stress≈1; p50/p75/p90/p95:  3.13/6.05/39.92/145.98   (positions with symbol ≥ 5% of collateral)

> Readout >100%: symbol-only haircut cannot reach HF≈1 without moves elsewhere.

> HF_stress < 1 (Aave numerator ÷ debt on line values × LT).

> Aggregates: debt USD = full loan debt; full collateral USD = all enabled collateral in loans with symbol at snapshot; shock leg USD = shocked symbol only; post shock USD = full enabled collateral minus (depeg × shock leg USD) — i.e. value wiped only on the shocked ticker.


| depeg  | accounts | debt USD      | full collateral USD | shock leg USD | post shock USD |
| ------ | -------- | ------------- | ------------------- | ------------- | -------------- |
| 0.25%  | 1        | 2,860,579     | 3,014,479           | 3,014,479     | 3,006,942      |
| 0.50%  | 3        | 15,769,286    | 16,640,236          | 16,640,236    | 16,557,035     |
| 1.00%  | 12       | 52,103,450    | 55,225,124          | 55,225,124    | 54,672,872     |
| 2.00%  | 25       | 133,767,407   | 142,520,318         | 142,518,780   | 139,669,943    |
| 3.00%  | 76       | 1,611,383,667 | 1,735,390,518       | 1,733,374,607 | 1,683,389,279  |
| 5.00%  | 179      | 2,104,937,553 | 2,278,306,396       | 2,274,505,769 | 2,164,581,107  |
| 7.00%  | 196      | 2,341,548,338 | 2,541,216,140       | 2,527,373,340 | 2,364,300,006  |
| 10.00% | 205      | 2,468,601,042 | 2,687,444,333       | 2,669,297,541 | 2,420,514,579  |
| 15.00% | 212      | 3,563,372,859 | 3,915,038,717       | 3,342,934,782 | 3,413,598,500  |


#### Per symbol — RSETH

> Aggregate enabled e-mode collateral in this ticker: $1,304,928,525    positions with ≥$1 in this ticker: 31

**Debt-weighted snapshot — positions with ≥$1 enabled collateral in this ticker (same cohort as stress grid: min debt, HF ≤ 50, HF ≥ 1)**


| Metric                                                                                 | Value                   |
| -------------------------------------------------------------------------------------- | ----------------------- |
| Debt-weighted avg LTV%                                                                 | 91.24                   |
| Debt-weighted avg liq. threshold LTV%                                                  | 94.93                   |
| Debt-weighted avg HF (1 ≤ HF ≤ 50)                                                     | 1.041                   |
| Debt-weighted avg D/E (where equity>0)                                                 | 10.975                  |
| Implied # of loops (where per-symbol asset ≥ 99% of enabled collateral)                | 32.938                  |
| Σ enabled USD in this ticker (≥99% concentration subcohort; % of ≥$1-in-ticker cohort) | $1,281,683,576 / 98.22% |


> Implied loss on shocked symbol only (%) → HF_stress≈1; p50/p75/p90/p95:  3.57/11.38/16.83/78.98   (positions with symbol ≥ 5% of collateral)

> Readout >100%: symbol-only haircut cannot reach HF≈1 without moves elsewhere.

> HF_stress < 1 (Aave numerator ÷ debt on line values × LT).

> Aggregates: debt USD = full loan debt; full collateral USD = all enabled collateral in loans with symbol at snapshot; shock leg USD = shocked symbol only; post shock USD = full enabled collateral minus (depeg × shock leg USD) — i.e. value wiped only on the shocked ticker.


| depeg  | accounts | debt USD      | full collateral USD | shock leg USD | post shock USD |
| ------ | -------- | ------------- | ------------------- | ------------- | -------------- |
| 0.25%  | 0        | 0             | 0                   | 0             | 0              |
| 0.50%  | 0        | 0             | 0                   | 0             | 0              |
| 1.00%  | 3        | 81,364,999    | 86,465,663          | 86,465,663    | 85,601,007     |
| 2.00%  | 3        | 81,364,999    | 86,465,663          | 86,465,663    | 84,736,350     |
| 3.00%  | 13       | 322,810,183   | 346,906,483         | 346,906,482   | 336,499,289    |
| 5.00%  | 21       | 1,019,664,018 | 1,110,652,331       | 1,110,652,331 | 1,055,119,715  |
| 7.00%  | 22       | 1,157,984,425 | 1,263,993,598       | 1,263,993,597 | 1,175,514,046  |
| 10.00% | 22       | 1,157,984,425 | 1,263,993,598       | 1,263,993,597 | 1,137,594,238  |
| 15.00% | 25       | 1,177,627,774 | 1,288,289,822       | 1,287,748,024 | 1,095,127,619  |


#### Per symbol — WSTETH

> Aggregate enabled e-mode collateral in this ticker: $906,653,728    positions with ≥$1 in this ticker: 155

**Debt-weighted snapshot — positions with ≥$1 enabled collateral in this ticker (same cohort as stress grid: min debt, HF ≤ 50, HF ≥ 1)**


| Metric                                                                                 | Value                 |
| -------------------------------------------------------------------------------------- | --------------------- |
| Debt-weighted avg LTV%                                                                 | 89.42                 |
| Debt-weighted avg liq. threshold LTV%                                                  | 94.92                 |
| Debt-weighted avg HF (1 ≤ HF ≤ 50)                                                     | 1.064                 |
| Debt-weighted avg D/E (where equity>0)                                                 | 8.761                 |
| Implied # of loops (where per-symbol asset ≥ 99% of enabled collateral)                | 28.603                |
| Σ enabled USD in this ticker (≥99% concentration subcohort; % of ≥$1-in-ticker cohort) | $326,119,802 / 35.97% |


> Implied loss on shocked symbol only (%) → HF_stress≈1; p50/p75/p90/p95:  17.02/60.60/154.41/291.31   (positions with symbol ≥ 5% of collateral)

> Readout >100%: symbol-only haircut cannot reach HF≈1 without moves elsewhere.

> HF_stress < 1 (Aave numerator ÷ debt on line values × LT).

> Aggregates: debt USD = full loan debt; full collateral USD = all enabled collateral in loans with symbol at snapshot; shock leg USD = shocked symbol only; post shock USD = full enabled collateral minus (depeg × shock leg USD) — i.e. value wiped only on the shocked ticker.


| depeg  | accounts | debt USD      | full collateral USD | shock leg USD | post shock USD |
| ------ | -------- | ------------- | ------------------- | ------------- | -------------- |
| 0.25%  | 0        | 0             | 0                   | 0             | 0              |
| 0.50%  | 0        | 0             | 0                   | 0             | 0              |
| 1.00%  | 0        | 0             | 0                   | 0             | 0              |
| 2.00%  | 0        | 0             | 0                   | 0             | 0              |
| 3.00%  | 5        | 12,589,983    | 13,588,352          | 13,587,978    | 13,180,712     |
| 5.00%  | 21       | 236,500,494   | 258,240,152         | 256,106,887   | 245,434,807    |
| 7.00%  | 38       | 300,947,949   | 329,676,720         | 320,160,976   | 307,265,452    |
| 10.00% | 48       | 312,512,640   | 342,969,479         | 333,453,735   | 309,624,106    |
| 15.00% | 67       | 1,401,568,128 | 1,563,896,647       | 889,225,349   | 1,430,512,845  |


#### Per symbol — SUSDE

> Aggregate enabled e-mode collateral in this ticker: $369,135,350    positions with ≥$1 in this ticker: 195

**Debt-weighted snapshot — positions with ≥$1 enabled collateral in this ticker (same cohort as stress grid: min debt, HF ≤ 50, HF ≥ 1)**


| Metric                                                                                 | Value                 |
| -------------------------------------------------------------------------------------- | --------------------- |
| Debt-weighted avg LTV%                                                                 | 87.04                 |
| Debt-weighted avg liq. threshold LTV%                                                  | 91.82                 |
| Debt-weighted avg HF (1 ≤ HF ≤ 50)                                                     | 1.062                 |
| Debt-weighted avg D/E (where equity>0)                                                 | 7.694                 |
| Implied # of loops (where per-symbol asset ≥ 99% of enabled collateral)                | 32.976                |
| Σ enabled USD in this ticker (≥99% concentration subcohort; % of ≥$1-in-ticker cohort) | $195,030,690 / 52.83% |


> Implied loss on shocked symbol only (%) → HF_stress≈1; p50/p75/p90/p95:  13.57/29.10/90.15/155.45   (positions with symbol ≥ 5% of collateral)

> Readout >100%: symbol-only haircut cannot reach HF≈1 without moves elsewhere.

> HF_stress < 1 (Aave numerator ÷ debt on line values × LT).

> Aggregates: debt USD = full loan debt; full collateral USD = all enabled collateral in loans with symbol at snapshot; shock leg USD = shocked symbol only; post shock USD = full enabled collateral minus (depeg × shock leg USD) — i.e. value wiped only on the shocked ticker.


| depeg  | accounts | debt USD    | full collateral USD | shock leg USD | post shock USD |
| ------ | -------- | ----------- | ------------------- | ------------- | -------------- |
| 0.25%  | 0        | 0           | 0                   | 0             | 0              |
| 0.50%  | 0        | 0           | 0                   | 0             | 0              |
| 1.00%  | 3        | 9,445,355   | 10,353,673          | 10,353,673    | 10,250,136     |
| 2.00%  | 9        | 101,161,973 | 111,342,530         | 107,964,980   | 109,183,231    |
| 3.00%  | 21       | 140,023,136 | 154,608,559         | 149,884,756   | 150,112,016    |
| 5.00%  | 44       | 288,573,974 | 320,378,705         | 258,386,199   | 307,459,395    |
| 7.00%  | 60       | 293,962,141 | 326,424,115         | 261,430,127   | 308,124,006    |
| 10.00% | 77       | 302,396,299 | 336,199,854         | 268,419,008   | 309,357,953    |
| 15.00% | 99       | 348,024,619 | 390,745,867         | 307,662,909   | 344,596,431    |


#### Per symbol — OSETH

> Aggregate enabled e-mode collateral in this ticker: $332,395,196    positions with ≥$1 in this ticker: 158

**Debt-weighted snapshot — positions with ≥$1 enabled collateral in this ticker (same cohort as stress grid: min debt, HF ≤ 50, HF ≥ 1)**


| Metric                                                                                 | Value                 |
| -------------------------------------------------------------------------------------- | --------------------- |
| Debt-weighted avg LTV%                                                                 | 92.04                 |
| Debt-weighted avg liq. threshold LTV%                                                  | 95.00                 |
| Debt-weighted avg HF (1 ≤ HF ≤ 50)                                                     | 1.033                 |
| Debt-weighted avg D/E (where equity>0)                                                 | 12.620                |
| Implied # of loops (where per-symbol asset ≥ 99% of enabled collateral)                | 68.016                |
| Σ enabled USD in this ticker (≥99% concentration subcohort; % of ≥$1-in-ticker cohort) | $327,671,575 / 98.58% |


> Implied loss on shocked symbol only (%) → HF_stress≈1; p50/p75/p90/p95:  2.01/2.05/2.10/2.10   (positions with symbol ≥ 5% of collateral)

> Readout >100%: symbol-only haircut cannot reach HF≈1 without moves elsewhere.

> HF_stress < 1 (Aave numerator ÷ debt on line values × LT).

> Aggregates: debt USD = full loan debt; full collateral USD = all enabled collateral in loans with symbol at snapshot; shock leg USD = shocked symbol only; post shock USD = full enabled collateral minus (depeg × shock leg USD) — i.e. value wiped only on the shocked ticker.


| depeg  | accounts | debt USD    | full collateral USD | shock leg USD | post shock USD |
| ------ | -------- | ----------- | ------------------- | ------------- | -------------- |
| 0.25%  | 0        | 0           | 0                   | 0             | 0              |
| 0.50%  | 0        | 0           | 0                   | 0             | 0              |
| 1.00%  | 0        | 0           | 0                   | 0             | 0              |
| 2.00%  | 68       | 111,453,010 | 119,688,668         | 119,688,668   | 117,294,895    |
| 3.00%  | 155      | 277,233,518 | 297,846,423         | 297,846,423   | 288,911,030    |
| 5.00%  | 155      | 277,233,518 | 297,846,423         | 297,846,423   | 282,954,102    |
| 7.00%  | 155      | 277,233,518 | 297,846,423         | 297,846,423   | 276,997,173    |
| 10.00% | 155      | 277,233,518 | 297,846,423         | 297,846,423   | 268,061,781    |
| 15.00% | 157      | 305,775,870 | 332,647,877         | 332,393,891   | 282,788,793    |


#### Per symbol — USDE

> Aggregate enabled e-mode collateral in this ticker: $330,630,897    positions with ≥$1 in this ticker: 154

**Debt-weighted snapshot — positions with ≥$1 enabled collateral in this ticker (same cohort as stress grid: min debt, HF ≤ 50, HF ≥ 1)**


| Metric                                 | Value |
| -------------------------------------- | ----- |
| Debt-weighted avg LTV%                 | 87.31 |
| Debt-weighted avg liq. threshold LTV%  | 92.19 |
| Debt-weighted avg HF (1 ≤ HF ≤ 50)     | 1.111 |
| Debt-weighted avg D/E (where equity>0) | 8.292 |


> Implied loss on shocked symbol only (%) → HF_stress≈1; p50/p75/p90/p95:  19.32/40.55/115.70/172.81   (positions with symbol ≥ 5% of collateral)

> Readout >100%: symbol-only haircut cannot reach HF≈1 without moves elsewhere.

> HF_stress < 1 (Aave numerator ÷ debt on line values × LT).

> Aggregates: debt USD = full loan debt; full collateral USD = all enabled collateral in loans with symbol at snapshot; shock leg USD = shocked symbol only; post shock USD = full enabled collateral minus (depeg × shock leg USD) — i.e. value wiped only on the shocked ticker.


| depeg  | accounts | debt USD    | full collateral USD | shock leg USD | post shock USD |
| ------ | -------- | ----------- | ------------------- | ------------- | -------------- |
| 0.25%  | 1        | 1,331       | 1,450               | 1,450         | 1,447          |
| 0.50%  | 1        | 1,331       | 1,450               | 1,450         | 1,443          |
| 1.00%  | 1        | 1,331       | 1,450               | 1,450         | 1,436          |
| 2.00%  | 3        | 152,299,832 | 166,246,681         | 165,939,282   | 162,927,896    |
| 3.00%  | 4        | 152,696,269 | 166,684,115         | 166,157,782   | 161,699,382    |
| 5.00%  | 13       | 260,542,796 | 286,672,477         | 222,405,634   | 275,552,195    |
| 7.00%  | 27       | 265,921,497 | 292,706,963         | 225,401,526   | 276,928,856    |
| 10.00% | 45       | 281,708,609 | 310,577,509         | 233,548,671   | 287,222,642    |
| 15.00% | 64       | 332,420,090 | 367,524,287         | 247,819,447   | 330,351,370    |


#### Per symbol — PT-SUSDE-7MAY2026

> Aggregate enabled e-mode collateral in this ticker: $172,804,457    positions with ≥$1 in this ticker: 34

**Debt-weighted snapshot — positions with ≥$1 enabled collateral in this ticker (same cohort as stress grid: min debt, HF ≤ 50, HF ≥ 1)**


| Metric                                                                                 | Value                 |
| -------------------------------------------------------------------------------------- | --------------------- |
| Debt-weighted avg LTV%                                                                 | 90.20                 |
| Debt-weighted avg liq. threshold LTV%                                                  | 93.40                 |
| Debt-weighted avg HF (1 ≤ HF ≤ 50)                                                     | 1.036                 |
| Debt-weighted avg D/E (where equity>0)                                                 | 9.851                 |
| Implied # of loops (where per-symbol asset ≥ 99% of enabled collateral)                | 30.123                |
| Σ enabled USD in this ticker (≥99% concentration subcohort; % of ≥$1-in-ticker cohort) | $171,891,195 / 99.47% |


> Implied loss on shocked symbol only (%) → HF_stress≈1; p50/p75/p90/p95:  4.75/9.86/25.12/82.64   (positions with symbol ≥ 5% of collateral)

> Readout >100%: symbol-only haircut cannot reach HF≈1 without moves elsewhere.

> HF_stress < 1 (Aave numerator ÷ debt on line values × LT).

> Aggregates: debt USD = full loan debt; full collateral USD = all enabled collateral in loans with symbol at snapshot; shock leg USD = shocked symbol only; post shock USD = full enabled collateral minus (depeg × shock leg USD) — i.e. value wiped only on the shocked ticker.


| depeg  | accounts | debt USD    | full collateral USD | shock leg USD | post shock USD |
| ------ | -------- | ----------- | ------------------- | ------------- | -------------- |
| 0.25%  | 0        | 0           | 0                   | 0             | 0              |
| 0.50%  | 0        | 0           | 0                   | 0             | 0              |
| 1.00%  | 1        | 35,474,399  | 38,114,730          | 38,114,730    | 37,733,583     |
| 2.00%  | 2        | 50,488,880  | 54,274,025          | 54,274,025    | 53,188,545     |
| 3.00%  | 10       | 97,864,248  | 106,875,763         | 106,875,763   | 103,669,491    |
| 5.00%  | 18       | 100,965,822 | 110,312,119         | 110,307,102   | 104,796,764    |
| 7.00%  | 23       | 153,243,319 | 169,502,471         | 169,220,736   | 157,657,020    |
| 10.00% | 25       | 153,768,985 | 170,105,848         | 169,824,112   | 153,123,436    |
| 15.00% | 29       | 155,960,670 | 172,771,459         | 172,489,722   | 146,898,000    |


#### Per symbol — PT-SRUSDE-25JUN2026

> Aggregate enabled e-mode collateral in this ticker: $74,858,441    positions with ≥$1 in this ticker: 8

**Debt-weighted snapshot — positions with ≥$1 enabled collateral in this ticker (same cohort as stress grid: min debt, HF ≤ 50, HF ≥ 1)**


| Metric                                                                                 | Value                |
| -------------------------------------------------------------------------------------- | -------------------- |
| Debt-weighted avg LTV%                                                                 | 88.50                |
| Debt-weighted avg liq. threshold LTV%                                                  | 93.20                |
| Debt-weighted avg HF (1 ≤ HF ≤ 50)                                                     | 1.056                |
| Debt-weighted avg D/E (where equity>0)                                                 | 8.746                |
| Σ enabled USD in this ticker (≥99% concentration subcohort; % of ≥$1-in-ticker cohort) | $74,851,175 / 99.99% |


> Implied loss on shocked symbol only (%) → HF_stress≈1; p50/p75/p90/p95:  7.36/15.57/16.94/18.40   (positions with symbol ≥ 5% of collateral)

> Readout >100%: symbol-only haircut cannot reach HF≈1 without moves elsewhere.

> HF_stress < 1 (Aave numerator ÷ debt on line values × LT).

> Aggregates: debt USD = full loan debt; full collateral USD = all enabled collateral in loans with symbol at snapshot; shock leg USD = shocked symbol only; post shock USD = full enabled collateral minus (depeg × shock leg USD) — i.e. value wiped only on the shocked ticker.


| depeg  | accounts | debt USD   | full collateral USD | shock leg USD | post shock USD |
| ------ | -------- | ---------- | ------------------- | ------------- | -------------- |
| 0.25%  | 0        | 0          | 0                   | 0             | 0              |
| 0.50%  | 0        | 0          | 0                   | 0             | 0              |
| 1.00%  | 1        | 1,401,070  | 1,518,100           | 1,518,100     | 1,502,919      |
| 2.00%  | 1        | 1,401,070  | 1,518,100           | 1,518,100     | 1,487,738      |
| 3.00%  | 4        | 46,822,741 | 51,283,116          | 51,283,116    | 49,744,622     |
| 5.00%  | 4        | 46,822,741 | 51,283,116          | 51,283,116    | 48,718,960     |
| 7.00%  | 4        | 46,822,741 | 51,283,116          | 51,283,116    | 47,693,298     |
| 10.00% | 4        | 46,822,741 | 51,283,116          | 51,283,116    | 46,154,804     |
| 15.00% | 5        | 65,569,814 | 74,189,175          | 74,189,175    | 63,060,799     |


#### Per symbol — WETH

> Aggregate enabled e-mode collateral in this ticker: $28,033,921    positions with ≥$1 in this ticker: 296

**Debt-weighted snapshot — positions with ≥$1 enabled collateral in this ticker (same cohort as stress grid: min debt, HF ≤ 50, HF ≥ 1)**


| Metric                                 | Value |
| -------------------------------------- | ----- |
| Debt-weighted avg LTV%                 | 63.61 |
| Debt-weighted avg liq. threshold LTV%  | 86.07 |
| Debt-weighted avg HF (1 ≤ HF ≤ 50)     | 1.532 |
| Debt-weighted avg D/E (where equity>0) | 2.869 |


> Implied loss on shocked symbol only (%) → HF_stress≈1; p50/p75/p90/p95:  50.59/98.62/168.64/300.73   (positions with symbol ≥ 5% of collateral)

> Readout >100%: symbol-only haircut cannot reach HF≈1 without moves elsewhere.

> HF_stress < 1 (Aave numerator ÷ debt on line values × LT).

> Aggregates: debt USD = full loan debt; full collateral USD = all enabled collateral in loans with symbol at snapshot; shock leg USD = shocked symbol only; post shock USD = full enabled collateral minus (depeg × shock leg USD) — i.e. value wiped only on the shocked ticker.


| depeg  | accounts | debt USD  | full collateral USD | shock leg USD | post shock USD |
| ------ | -------- | --------- | ------------------- | ------------- | -------------- |
| 0.25%  | 1        | 789       | 833                 | 833           | 830            |
| 0.50%  | 4        | 3,488     | 3,684               | 3,684         | 3,666          |
| 1.00%  | 13       | 173,475   | 183,995             | 182,836       | 182,167        |
| 2.00%  | 21       | 269,785   | 287,113             | 285,239       | 281,408        |
| 3.00%  | 32       | 752,096   | 808,635             | 806,409       | 784,443        |
| 5.00%  | 50       | 1,296,461 | 1,405,426           | 1,391,685     | 1,335,842      |
| 7.00%  | 55       | 1,375,414 | 1,493,645           | 1,479,793     | 1,390,060      |
| 10.00% | 63       | 3,497,261 | 3,901,925           | 3,888,060     | 3,513,119      |
| 15.00% | 76       | 4,168,690 | 4,715,783           | 4,641,355     | 4,019,580      |


#### Per symbol — EZETH

> Aggregate enabled e-mode collateral in this ticker: $21,119,881    positions with ≥$1 in this ticker: 5

**Debt-weighted snapshot — positions with ≥$1 enabled collateral in this ticker (same cohort as stress grid: min debt, HF ≤ 50, HF ≥ 1)**


| Metric                                                                                 | Value                |
| -------------------------------------------------------------------------------------- | -------------------- |
| Debt-weighted avg LTV%                                                                 | 92.12                |
| Debt-weighted avg liq. threshold LTV%                                                  | 94.95                |
| Debt-weighted avg HF (1 ≤ HF ≤ 50)                                                     | 1.032                |
| Debt-weighted avg D/E (where equity>0)                                                 | 11.880               |
| Implied # of loops (where per-symbol asset ≥ 99% of enabled collateral)                | 31.706               |
| Σ enabled USD in this ticker (≥99% concentration subcohort; % of ≥$1-in-ticker cohort) | $21,095,131 / 99.88% |


> Implied loss on shocked symbol only (%) → HF_stress≈1; p50/p75/p90/p95:  95.68/96.00/120.90/129.19   (positions with symbol ≥ 5% of collateral)

> Readout >100%: symbol-only haircut cannot reach HF≈1 without moves elsewhere.

> HF_stress < 1 (Aave numerator ÷ debt on line values × LT).

> Aggregates: debt USD = full loan debt; full collateral USD = all enabled collateral in loans with symbol at snapshot; shock leg USD = shocked symbol only; post shock USD = full enabled collateral minus (depeg × shock leg USD) — i.e. value wiped only on the shocked ticker.


| depeg  | accounts | debt USD   | full collateral USD | shock leg USD | post shock USD |
| ------ | -------- | ---------- | ------------------- | ------------- | -------------- |
| 0.25%  | 0        | 0          | 0                   | 0             | 0              |
| 0.50%  | 0        | 0          | 0                   | 0             | 0              |
| 1.00%  | 0        | 0          | 0                   | 0             | 0              |
| 2.00%  | 0        | 0          | 0                   | 0             | 0              |
| 3.00%  | 1        | 19,401,387 | 21,030,096          | 21,030,096    | 20,399,193     |
| 5.00%  | 1        | 19,401,387 | 21,030,096          | 21,030,096    | 19,978,591     |
| 7.00%  | 1        | 19,401,387 | 21,030,096          | 21,030,096    | 19,557,989     |
| 10.00% | 1        | 19,401,387 | 21,030,096          | 21,030,096    | 18,927,086     |
| 15.00% | 1        | 19,401,387 | 21,030,096          | 21,030,096    | 17,875,582     |


#### Per symbol — LBTC

> Aggregate enabled e-mode collateral in this ticker: $14,273,797    positions with ≥$1 in this ticker: 19

**Debt-weighted snapshot — positions with ≥$1 enabled collateral in this ticker (same cohort as stress grid: min debt, HF ≤ 50, HF ≥ 1)**


| Metric                                 | Value |
| -------------------------------------- | ----- |
| Debt-weighted avg LTV%                 | 82.28 |
| Debt-weighted avg liq. threshold LTV%  | 90.32 |
| Debt-weighted avg HF (1 ≤ HF ≤ 50)     | 1.215 |
| Debt-weighted avg D/E (where equity>0) | 6.018 |


> Implied loss on shocked symbol only (%) → HF_stress≈1; p50/p75/p90/p95:  47.30/106.88/216.03/399.44   (positions with symbol ≥ 5% of collateral)

> Readout >100%: symbol-only haircut cannot reach HF≈1 without moves elsewhere.

> HF_stress < 1 (Aave numerator ÷ debt on line values × LT).

> Aggregates: debt USD = full loan debt; full collateral USD = all enabled collateral in loans with symbol at snapshot; shock leg USD = shocked symbol only; post shock USD = full enabled collateral minus (depeg × shock leg USD) — i.e. value wiped only on the shocked ticker.


| depeg  | accounts | debt USD  | full collateral USD | shock leg USD | post shock USD |
| ------ | -------- | --------- | ------------------- | ------------- | -------------- |
| 0.25%  | 0        | 0         | 0                   | 0             | 0              |
| 0.50%  | 0        | 0         | 0                   | 0             | 0              |
| 1.00%  | 0        | 0         | 0                   | 0             | 0              |
| 2.00%  | 1        | 9,842     | 11,618              | 11,618        | 11,385         |
| 3.00%  | 1        | 9,842     | 11,618              | 11,618        | 11,269         |
| 5.00%  | 1        | 9,842     | 11,618              | 11,618        | 11,037         |
| 7.00%  | 1        | 9,842     | 11,618              | 11,618        | 10,805         |
| 10.00% | 2        | 2,904,041 | 3,689,680           | 3,689,680     | 3,320,712      |
| 15.00% | 3        | 2,994,693 | 3,812,263           | 3,812,263     | 3,240,424      |


#### Per symbol — SYRUPUSDT

> Aggregate enabled e-mode collateral in this ticker: $10,451,352    positions with ≥$1 in this ticker: 8

**Debt-weighted snapshot — positions with ≥$1 enabled collateral in this ticker (same cohort as stress grid: min debt, HF ≤ 50, HF ≥ 1)**


| Metric                                                                                 | Value                 |
| -------------------------------------------------------------------------------------- | --------------------- |
| Debt-weighted avg LTV%                                                                 | 88.20                 |
| Debt-weighted avg liq. threshold LTV%                                                  | 92.00                 |
| Debt-weighted avg HF (1 ≤ HF ≤ 50)                                                     | 1.044                 |
| Debt-weighted avg D/E (where equity>0)                                                 | 7.712                 |
| Implied # of loops (where per-symbol asset ≥ 99% of enabled collateral)                | 18.185                |
| Σ enabled USD in this ticker (≥99% concentration subcohort; % of ≥$1-in-ticker cohort) | $10,451,352 / 100.00% |


> Implied loss on shocked symbol only (%) → HF_stress≈1; p50/p75/p90/p95:  7.50/13.74/27.72/41.91   (positions with symbol ≥ 5% of collateral)

> Readout >100%: symbol-only haircut cannot reach HF≈1 without moves elsewhere.

> HF_stress < 1 (Aave numerator ÷ debt on line values × LT).

> Aggregates: debt USD = full loan debt; full collateral USD = all enabled collateral in loans with symbol at snapshot; shock leg USD = shocked symbol only; post shock USD = full enabled collateral minus (depeg × shock leg USD) — i.e. value wiped only on the shocked ticker.


| depeg  | accounts | debt USD  | full collateral USD | shock leg USD | post shock USD |
| ------ | -------- | --------- | ------------------- | ------------- | -------------- |
| 0.25%  | 0        | 0         | 0                   | 0             | 0              |
| 0.50%  | 0        | 0         | 0                   | 0             | 0              |
| 1.00%  | 0        | 0         | 0                   | 0             | 0              |
| 2.00%  | 0        | 0         | 0                   | 0             | 0              |
| 3.00%  | 1        | 6,115,815 | 6,834,700           | 6,834,700     | 6,629,659      |
| 5.00%  | 2        | 7,056,017 | 7,896,375           | 7,896,375     | 7,501,557      |
| 7.00%  | 4        | 7,196,350 | 8,060,230           | 8,060,230     | 7,496,014      |
| 10.00% | 5        | 9,119,621 | 10,334,570          | 10,334,570    | 9,301,113      |
| 15.00% | 6        | 9,210,619 | 10,448,438          | 10,448,438    | 8,881,173      |


#### Per symbol — EURC

> Aggregate enabled e-mode collateral in this ticker: $4,696,350    positions with ≥$1 in this ticker: 22

**Debt-weighted snapshot — positions with ≥$1 enabled collateral in this ticker (same cohort as stress grid: min debt, HF ≤ 50, HF ≥ 1)**


| Metric                                 | Value |
| -------------------------------------- | ----- |
| Debt-weighted avg LTV%                 | 46.07 |
| Debt-weighted avg liq. threshold LTV%  | 78.95 |
| Debt-weighted avg HF (1 ≤ HF ≤ 50)     | 1.791 |
| Debt-weighted avg D/E (where equity>0) | 0.907 |


> Implied loss on shocked symbol only (%) → HF_stress≈1; p50/p75/p90/p95:  55.84/76.51/192.59/351.66   (positions with symbol ≥ 5% of collateral)

> Readout >100%: symbol-only haircut cannot reach HF≈1 without moves elsewhere.

> HF_stress < 1 (Aave numerator ÷ debt on line values × LT).

> Aggregates: debt USD = full loan debt; full collateral USD = all enabled collateral in loans with symbol at snapshot; shock leg USD = shocked symbol only; post shock USD = full enabled collateral minus (depeg × shock leg USD) — i.e. value wiped only on the shocked ticker.


| depeg  | accounts | debt USD | full collateral USD | shock leg USD | post shock USD |
| ------ | -------- | -------- | ------------------- | ------------- | -------------- |
| 0.25%  | 0        | 0        | 0                   | 0             | 0              |
| 0.50%  | 0        | 0        | 0                   | 0             | 0              |
| 1.00%  | 0        | 0        | 0                   | 0             | 0              |
| 2.00%  | 0        | 0        | 0                   | 0             | 0              |
| 3.00%  | 0        | 0        | 0                   | 0             | 0              |
| 5.00%  | 0        | 0        | 0                   | 0             | 0              |
| 7.00%  | 0        | 0        | 0                   | 0             | 0              |
| 10.00% | 0        | 0        | 0                   | 0             | 0              |
| 15.00% | 2        | 18,889   | 27,538              | 27,538        | 23,407         |


#### Per symbol — RETH

> Aggregate enabled e-mode collateral in this ticker: $2,062,011    positions with ≥$1 in this ticker: 22

**Debt-weighted snapshot — positions with ≥$1 enabled collateral in this ticker (same cohort as stress grid: min debt, HF ≤ 50, HF ≥ 1)**


| Metric                                                                                 | Value             |
| -------------------------------------------------------------------------------------- | ----------------- |
| Debt-weighted avg LTV%                                                                 | 81.35             |
| Debt-weighted avg liq. threshold LTV%                                                  | 94.44             |
| Debt-weighted avg HF (1 ≤ HF ≤ 50)                                                     | 1.167             |
| Debt-weighted avg D/E (where equity>0)                                                 | 5.122             |
| Σ enabled USD in this ticker (≥99% concentration subcohort; % of ≥$1-in-ticker cohort) | $805,757 / 39.08% |


> Implied loss on shocked symbol only (%) → HF_stress≈1; p50/p75/p90/p95:  30.40/55.94/214.57/250.75   (positions with symbol ≥ 5% of collateral)

> Readout >100%: symbol-only haircut cannot reach HF≈1 without moves elsewhere.

> HF_stress < 1 (Aave numerator ÷ debt on line values × LT).

> Aggregates: debt USD = full loan debt; full collateral USD = all enabled collateral in loans with symbol at snapshot; shock leg USD = shocked symbol only; post shock USD = full enabled collateral minus (depeg × shock leg USD) — i.e. value wiped only on the shocked ticker.


| depeg  | accounts | debt USD | full collateral USD | shock leg USD | post shock USD |
| ------ | -------- | -------- | ------------------- | ------------- | -------------- |
| 0.25%  | 0        | 0        | 0                   | 0             | 0              |
| 0.50%  | 0        | 0        | 0                   | 0             | 0              |
| 1.00%  | 1        | 300      | 318                 | 318           | 315            |
| 2.00%  | 1        | 300      | 318                 | 318           | 312            |
| 3.00%  | 2        | 360,256  | 390,550             | 390,550       | 378,834        |
| 5.00%  | 2        | 360,256  | 390,550             | 390,550       | 371,023        |
| 7.00%  | 2        | 360,256  | 390,550             | 390,550       | 363,212        |
| 10.00% | 3        | 363,567  | 394,381             | 394,381       | 354,943        |
| 15.00% | 3        | 363,567  | 394,381             | 394,381       | 335,224        |


#### Per symbol — CBETH

> Aggregate enabled e-mode collateral in this ticker: $1,851,237    positions with ≥$1 in this ticker: 14

**Debt-weighted snapshot — positions with ≥$1 enabled collateral in this ticker (same cohort as stress grid: min debt, HF ≤ 50, HF ≥ 1)**


| Metric                                                                                 | Value             |
| -------------------------------------------------------------------------------------- | ----------------- |
| Debt-weighted avg LTV%                                                                 | 76.94             |
| Debt-weighted avg liq. threshold LTV%                                                  | 88.72             |
| Debt-weighted avg HF (1 ≤ HF ≤ 50)                                                     | 1.207             |
| Debt-weighted avg D/E (where equity>0)                                                 | 8.283             |
| Implied # of loops (where per-symbol asset ≥ 99% of enabled collateral)                | 34.033            |
| Σ enabled USD in this ticker (≥99% concentration subcohort; % of ≥$1-in-ticker cohort) | $608,931 / 32.89% |


> Implied loss on shocked symbol only (%) → HF_stress≈1; p50/p75/p90/p95:  13.15/64.49/101.29/111.12   (positions with symbol ≥ 5% of collateral)

> Readout >100%: symbol-only haircut cannot reach HF≈1 without moves elsewhere.

> HF_stress < 1 (Aave numerator ÷ debt on line values × LT).

> Aggregates: debt USD = full loan debt; full collateral USD = all enabled collateral in loans with symbol at snapshot; shock leg USD = shocked symbol only; post shock USD = full enabled collateral minus (depeg × shock leg USD) — i.e. value wiped only on the shocked ticker.


| depeg  | accounts | debt USD | full collateral USD | shock leg USD | post shock USD |
| ------ | -------- | -------- | ------------------- | ------------- | -------------- |
| 0.25%  | 0        | 0        | 0                   | 0             | 0              |
| 0.50%  | 0        | 0        | 0                   | 0             | 0              |
| 1.00%  | 0        | 0        | 0                   | 0             | 0              |
| 2.00%  | 0        | 0        | 0                   | 0             | 0              |
| 3.00%  | 2        | 539,743  | 585,577             | 585,577       | 568,010        |
| 5.00%  | 2        | 539,743  | 585,577             | 585,577       | 556,298        |
| 7.00%  | 2        | 539,743  | 585,577             | 585,577       | 544,587        |
| 10.00% | 4        | 877,066  | 964,535             | 872,901       | 877,245        |
| 15.00% | 6        | 878,730  | 966,539             | 874,840       | 835,313        |


#### Per symbol — EBTC

> Aggregate enabled e-mode collateral in this ticker: $1,315,713    positions with ≥$1 in this ticker: 9

**Debt-weighted snapshot — positions with ≥$1 enabled collateral in this ticker (same cohort as stress grid: min debt, HF ≤ 50, HF ≥ 1)**


| Metric                                 | Value |
| -------------------------------------- | ----- |
| Debt-weighted avg LTV%                 | 59.24 |
| Debt-weighted avg liq. threshold LTV%  | 79.73 |
| Debt-weighted avg HF (1 ≤ HF ≤ 50)     | 1.370 |
| Debt-weighted avg D/E (where equity>0) | 1.482 |


> Implied loss on shocked symbol only (%) → HF_stress≈1; p50/p75/p90/p95:  137.67/199.95/692.23/1036.08   (positions with symbol ≥ 5% of collateral)

> Readout >100%: symbol-only haircut cannot reach HF≈1 without moves elsewhere.

> HF_stress < 1 (Aave numerator ÷ debt on line values × LT).

> Aggregates: debt USD = full loan debt; full collateral USD = all enabled collateral in loans with symbol at snapshot; shock leg USD = shocked symbol only; post shock USD = full enabled collateral minus (depeg × shock leg USD) — i.e. value wiped only on the shocked ticker.


| depeg  | accounts | debt USD | full collateral USD | shock leg USD | post shock USD |
| ------ | -------- | -------- | ------------------- | ------------- | -------------- |
| 0.25%  | 0        | 0        | 0                   | 0             | 0              |
| 0.50%  | 0        | 0        | 0                   | 0             | 0              |
| 1.00%  | 0        | 0        | 0                   | 0             | 0              |
| 2.00%  | 0        | 0        | 0                   | 0             | 0              |
| 3.00%  | 0        | 0        | 0                   | 0             | 0              |
| 5.00%  | 0        | 0        | 0                   | 0             | 0              |
| 7.00%  | 0        | 0        | 0                   | 0             | 0              |
| 10.00% | 1        | 954      | 1,220               | 1,220         | 1,098          |
| 15.00% | 1        | 954      | 1,220               | 1,220         | 1,037          |


#### Per symbol — PT-USDE-7MAY2026

> Aggregate enabled e-mode collateral in this ticker: $1,003,442    positions with ≥$1 in this ticker: 2

**Debt-weighted snapshot — positions with ≥$1 enabled collateral in this ticker (same cohort as stress grid: min debt, HF ≤ 50, HF ≥ 1)**


| Metric                                                                                 | Value                |
| -------------------------------------------------------------------------------------- | -------------------- |
| Debt-weighted avg LTV%                                                                 | 71.15                |
| Debt-weighted avg liq. threshold LTV%                                                  | 93.00                |
| Debt-weighted avg HF (1 ≤ HF ≤ 50)                                                     | 1.307                |
| Debt-weighted avg D/E (where equity>0)                                                 | 2.472                |
| Implied # of loops (where per-symbol asset ≥ 99% of enabled collateral)                | 2.670                |
| Σ enabled USD in this ticker (≥99% concentration subcohort; % of ≥$1-in-ticker cohort) | $1,003,442 / 100.00% |


> Implied loss on shocked symbol only (%) → HF_stress≈1; p50/p75/p90/p95:  15.04/19.27/21.82/22.66   (positions with symbol ≥ 5% of collateral)

> Readout >100%: symbol-only haircut cannot reach HF≈1 without moves elsewhere.

> HF_stress < 1 (Aave numerator ÷ debt on line values × LT).

> Aggregates: debt USD = full loan debt; full collateral USD = all enabled collateral in loans with symbol at snapshot; shock leg USD = shocked symbol only; post shock USD = full enabled collateral minus (depeg × shock leg USD) — i.e. value wiped only on the shocked ticker.


| depeg  | accounts | debt USD | full collateral USD | shock leg USD | post shock USD |
| ------ | -------- | -------- | ------------------- | ------------- | -------------- |
| 0.25%  | 0        | 0        | 0                   | 0             | 0              |
| 0.50%  | 0        | 0        | 0                   | 0             | 0              |
| 1.00%  | 0        | 0        | 0                   | 0             | 0              |
| 2.00%  | 0        | 0        | 0                   | 0             | 0              |
| 3.00%  | 0        | 0        | 0                   | 0             | 0              |
| 5.00%  | 0        | 0        | 0                   | 0             | 0              |
| 7.00%  | 1        | 901      | 1,005               | 1,005         | 935            |
| 10.00% | 1        | 901      | 1,005               | 1,005         | 905            |
| 15.00% | 1        | 901      | 1,005               | 1,005         | 855            |


#### Per symbol — PT-USDG-28MAY2026

> Aggregate enabled e-mode collateral in this ticker: $512,646    positions with ≥$1 in this ticker: 1

**Debt-weighted snapshot — positions with ≥$1 enabled collateral in this ticker (same cohort as stress grid: min debt, HF ≤ 50, HF ≥ 1)**


| Metric                                                                                 | Value              |
| -------------------------------------------------------------------------------------- | ------------------ |
| Debt-weighted avg LTV%                                                                 | 92.70              |
| Debt-weighted avg liq. threshold LTV%                                                  | 95.50              |
| Debt-weighted avg HF (1 ≤ HF ≤ 50)                                                     | 1.030              |
| Debt-weighted avg D/E (where equity>0)                                                 | 12.703             |
| Implied # of loops (where per-symbol asset ≥ 99% of enabled collateral)                | 33.590             |
| Σ enabled USD in this ticker (≥99% concentration subcohort; % of ≥$1-in-ticker cohort) | $512,646 / 100.00% |


> Implied loss on shocked symbol only (%) → HF_stress≈1; p50/p75/p90/p95:  2.93/2.93/2.93/2.93   (positions with symbol ≥ 5% of collateral)

> Readout >100%: symbol-only haircut cannot reach HF≈1 without moves elsewhere.

> HF_stress < 1 (Aave numerator ÷ debt on line values × LT).

> Aggregates: debt USD = full loan debt; full collateral USD = all enabled collateral in loans with symbol at snapshot; shock leg USD = shocked symbol only; post shock USD = full enabled collateral minus (depeg × shock leg USD) — i.e. value wiped only on the shocked ticker.


| depeg  | accounts | debt USD | full collateral USD | shock leg USD | post shock USD |
| ------ | -------- | -------- | ------------------- | ------------- | -------------- |
| 0.25%  | 0        | 0        | 0                   | 0             | 0              |
| 0.50%  | 0        | 0        | 0                   | 0             | 0              |
| 1.00%  | 0        | 0        | 0                   | 0             | 0              |
| 2.00%  | 0        | 0        | 0                   | 0             | 0              |
| 3.00%  | 1        | 475,235  | 512,646             | 512,646       | 497,266        |
| 5.00%  | 1        | 475,235  | 512,646             | 512,646       | 487,013        |
| 7.00%  | 1        | 475,235  | 512,646             | 512,646       | 476,761        |
| 10.00% | 1        | 475,235  | 512,646             | 512,646       | 461,381        |
| 15.00% | 1        | 475,235  | 512,646             | 512,646       | 435,749        |


