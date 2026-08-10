Bitcoin ML Trading Model — Open Record

A machine learning model trading bitcoin, published in full: the methodology behind it, every trade as it happens, and the campaigns that were closed in the red.

Maintained by Adrian Velai.

Methodology: https://www.bitcoinai.pro/ai-trading-models/ Backtest record: https://www.bitcoinai.pro/#record Live trades: https://t.me/bitcoinaiproo Third-party verification: https://www.fxblue.com/users/bitcoinaipro

Approach

XGBoost (gradient boosting) on daily BTCUSD candles. Seven features, all drawn from price structure, realized volatility and candle microstructure — no sentiment data, no calendar encodings (hour-of-day sine/cosine was removed after it captured 60% of model importance in a configuration whose out-of-sample then collapsed).

LSTMs were tested extensively and are not part of this model. On tabular price data, gradient boosting outperformed every hybrid architecture tried, and untethered LSTM training proved non-deterministic enough that single-run results are noise.

Validation is anchored walk-forward with strictly out-of-sample windows, purge gaps between partitions, and pass criteria written down before anything runs. Selection is always by validation — never by test score.

Results, stated honestly

413 modelled trades, January 2018 – August 2026. This is a backtest, not an account statement.

	In-sample	Out-of-sample
Annualised return	+47.1%	+6.7%
Win rate	59.5%	50.5%
Trades	205	208

The gap between the two columns is the point. The model is roughly eight times its out-of-sample self inside the training set. Publishing both numbers side by side is the entire exercise; any strategy showing you only one of them is showing you the wrong one. Transaction costs are included in every figure.

The walk-forward tribunal returned a verdict of promising but unproven on this candidate: the only virgin window with a sufficient sample delivered an SQN of +0.52 — positive, but below the pre-registered threshold.

The forward test, running in public

Because the backtest verdict was inconclusive, the model is being settled the only way it can be: forward, on data nobody has seen.

Trades run on a simulated account with real spreads, swaps and commissions (Afterprime), and are posted to Telegram at the moment of execution — timestamps precede outcomes. The account is read independently by FXBlue.

Kill criteria are pre-registered: automatic pause if net P&L is at or below zero after a fixed number of trades or months, and immediate pause at a drawdown ceiling the backtest never touched.

What was rejected

Roughly 65,000 optimization trials across more than a dozen campaigns on BTCUSD, SPX500, XAUUSD and volatility derivatives produced one production system and one validated candidate. Everything else was archived with a written closing verdict: nine bitcoin timeframe configurations, three gold campaigns, five architectures on crypto candles, and one volatility campaign closed on transaction costs alone.

A pipeline that only produces approvals is validating nothing. The rejection rate is the certificate of authenticity.

Full details of the graveyard, including the discarded feature list, are on the methodology page.

Scope of this repository

This repository documents methodology and aggregate results. Exact hyperparameters, trained model artifacts and execution parameters are not published.

Disclaimer

Not investment advice. Not directed at US residents. Backtested and simulated results have inherent limitations and do not reflect the impact of real capital on the market. Past performance, simulated or real, is not a reliable indicator of future results.
