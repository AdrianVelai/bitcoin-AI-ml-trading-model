# Bitcoin ML Trading Model — Open Record

A machine learning model trading bitcoin, published in full: every trade as it 
happens, the methodology behind it, and the parts that don't work.

**Live record:** https://www.bitcoinai.pro  
**Methodology:** https://www.bitcoinai.pro/ai-trading-models/  
**Trades:** https://t.me/bitcoinaiproo

## Approach

Gradient-boosted trees for directional classification, combined with a recurrent 
network for sequence structure. Features are price and volume derivatives, 
realised volatility, funding rates and on-chain network measures. No sentiment data.

Validation is anchored walk-forward with strictly out-of-sample windows and 
pre-registered pass criteria.

## Results, stated honestly

413 modelled trades, January 2018 – August 2026:

| | In-sample | Out-of-sample |
|---|---|---|
| Annualised return | +47.1% | +6.7% |
| Win rate | 59.5% | 50.5% |
| Trades | 205 | 208 |

The gap between the two columns is the point. Results come from a simulated 
account under live market conditions.

## Disclaimer

Not investment advice. Not directed at US residents. Past performance, simulated 
or real, is not a reliable indicator of future results.
