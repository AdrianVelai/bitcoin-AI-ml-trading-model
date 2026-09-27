# BitcoinAI.Pro — Open Bitcoin ML Trading Research

A public research project focused on **machine-learning Bitcoin trading models**, with forward trades published openly, historical research separated from live tracking, and failed experiments documented instead of hidden.

The project has now passed **1,000,000+ machine-learning, execution and robustness trials**. Only two BTCUSD D1 production generations have made it into operation:

- **T1071** — the legacy Bitcoin model.
- **Frontier Model** — the current production model.

The current Frontier keeps the strongest part of the T1071 research lineage: a **frozen XGBoost BTCUSD D1 signal model with 7 engineered inputs**, no LSTM inference and no automatic production retraining. Its execution layer was subsequently re-audited and improved separately.

Website: https://www.bitcoinai.pro/  
Methodology: https://www.bitcoinai.pro/ai-trading-models/  
Forward trades: https://t.me/freebitcoincryptomodel

---

## Current production model — Frontier Model

| Item | Current Frontier |
|---|---|
| Market | BTCUSD |
| Timeframe | D1 |
| Signal model | Frozen XGBoost directional classifier |
| Production inputs | 7 engineered Bitcoin features |
| LSTM | Off |
| Automatic retraining | No |
| Research history | Jan 2018 → Aug 2026 |
| First strict post-weight entry | 30 Jul 2022 |
| Research leverage | 1:1 notional-equivalent |
| Maximum live leverage ceiling | 2:1 |
| Stop loss | 7.75 ATR from entry |
| Take profit — SHORT | 2.40 ATR |
| Take profit — LONG | 2.52 ATR |
| TP timing | Activated from D1 #2 |
| Gap-close exit rule | Off |

The signal model and the execution layer are treated as separate research objects. The signal binary is frozen; exit changes were tested independently rather than silently changing both model selection and trade management at once.

---

## Research results

### Chronological research blocks

These are the clean phase metrics used for the public IS/OOS comparison.

| Metric | In-sample | Strict model-weight OOS |
|---|---:|---:|
| Period | Jan 2018 → Jul 2022 | 30 Jul 2022 → Aug 2026 |
| Trades | 151 | 210 |
| SQN | 5.348 | 2.129 |
| Simple return | +733.7 pt | +253.9 pt |
| Win rate | 63.6% | 50.5% |
| Maximum drawdown | -31.04 pt | -25.34 pt |
| Profit / drawdown | 23.63 | 10.02 |
| Research leverage | 1:1 | 1:1 |

**Important:** these returns are **simple percentage points summed trade by trade**, not compounded account returns and not a CAGR.

### Full continuous trade-by-trade replay

The uninterrupted V111 replay preserves position/state continuity across the July 2022 research boundary:

- **361 exact trades**
- **4 Jan 2018 → 3 Aug 2026**
- **+992.65 simple percentage points**
- **56.2% win rate**
- **-31.04 pt maximum drawdown**
- **+2.75 pt average trade**
- **+0.91 pt median trade**
- **Best trade: +33.34 pt**
- **Worst trade: -20.18 pt**
- **192 LONG / 169 SHORT**
- **5 D1 bars median holding period**
- **6.54 D1 bars average holding period**

The continuous replay finishes at **+992.65 pt**, rather than the **+987.6 pt** obtained by simply adding the isolated IS and OOS phase totals. This is expected: the continuous replay preserves the exact portfolio/trade state across the cutoff, while the phase statistics are calculated as separately evaluated research blocks.

---

## What changed from legacy T1071

Legacy T1071 remains important because it was the previous operational BTCUSD D1 generation and the source of the frozen signal lineage.

The main recent research result was not “retrain more often”. It was the opposite.

Repeated rolling refits failed to reproduce the persistence of the exact frozen signal model strongly enough to justify replacing it. The production signal binary therefore remains frozen, while the exit layer was audited separately.

The current Frontier uses:

- a much wider **catastrophic SL: 7.75 ATR**
- **SHORT TP: 2.40 ATR**
- **LONG TP: 2.52 ATR**
- SL active immediately on entry
- strategy TP activated only from the start of the second D1 bar

This timing matters. Historical testing showed that the stop could be active from entry without altering the selected historical stream, while immediate day-one TP activation changed a small number of trades without producing a stable improvement across time.

---

## Validation philosophy

The purpose of this repository is not to show the prettiest backtest.

The research process is designed to reject models and execution ideas that do not survive chronology, replication and robustness checks.

Core principles:

1. **Chronology first** — later data must not influence earlier model selection.
2. **Validation is not TEST** — TEST is not used as an optimisation target.
3. **Frozen means frozen** — a production signal model is not silently retrained or mutated.
4. **Signal and execution research are separated** — changing exits must not masquerade as a new predictive model.
5. **Plateaus matter more than peaks** — broad stable regions are preferred to isolated optimum points.
6. **Trade streams are compared directly** — not only headline SQN.
7. **Monte Carlo and seed robustness are checks, not decoration.**
8. **Failed campaigns stay documented.**

Across the wider BitcoinAI.Pro programme, more than **1,000,000 model, execution and robustness trials** have been run. The overwhelming majority were rejected or archived.

---

## Forward record

Backtests are not live track records.

The current Frontier is therefore followed separately through a forward execution record:

- new positions are published when opened
- the initial trade can open **without a take profit**
- the TP is added from **D1 #2**
- TP changes are published
- TP and SL executions are published
- the tracked account and the historical research curve are treated as separate datasets

Forward trades are published on Telegram:

https://t.me/freebitcoincryptomodel

The independently tracked account is shown on BitcoinAI.Pro through FXBlue:

https://www.bitcoinai.pro/

---

## Repository scope

This repository is a public research archive, not a copy-trading product.

It may include:

- research scripts
- validation code
- walk-forward experiments
- Monte Carlo / seed robustness studies
- execution audits
- historical model documentation
- public research outputs

It does **not** provide:

- a managed account
- investment advice
- a paid signals service
- a public auto-copying service
- a guarantee that historical performance will persist

Some production artefacts and exact execution internals are intentionally not published.

---

## Costs and interpretation

Historical research includes the commission assumptions defined by the corresponding experiment. Research returns are reported as **simple trade percentage points at 1:1 notional-equivalent exposure** unless explicitly stated otherwise.

They should not be interpreted as:

- compounded account returns
- a guaranteed future return
- a live account equity curve
- results multiplied by the maximum live leverage ceiling

Real execution can differ because of spread, slippage, financing, funding, margin rules, venue-specific contract specifications and market stress.

---

## Full methodology and model report

For the complete methodology, current Frontier statistics, historical lineage and research discussion:

https://www.bitcoinai.pro/ai-trading-models/

For the public home, current forward record and model updates:

https://www.bitcoinai.pro/

---

## Disclaimer

This repository is for **research and educational purposes only**.

Nothing here is investment advice, a recommendation to trade, or a solicitation to buy or sell any financial instrument. Bitcoin, CFDs, futures and perpetual contracts can produce rapid and substantial losses.

Past performance — backtested, simulated or live — is not a reliable indicator of future results.

---

**BitcoinAI.Pro**  
Open research. Forward trades. Failed experiments included.
