# ml-pairs-trading

News-aware pairs trading: cointegration, ML reversion prediction, and NLP news filtering with a live dashboard.

## Overview

Pairs trading is a market-neutral strategy that exploits temporary divergences between two historically linked assets. When their price spread deviates from its long-run equilibrium, the strategy shorts the outperformer and buys the underperformer, betting that the spread will revert.

A key weakness of classical pairs trading is that it cannot tell a temporary divergence from a structural break, such as one caused by a sanctions announcement, a lawsuit or an earnings shock. In those cases the spread never reverts and the trade loses money.

This project builds a news-aware pairs trading system that addresses this weakness.

## Approach

1. **Pair selection.** Cointegrated pairs are identified across a large universe of stocks using a scalable PySpark pipeline.
2. **Reversion prediction.** An XGBoost classifier predicts whether a given divergence is likely to revert, using spread-based features such as z-score, volatility, half-life and momentum.
3. **News filtering.** An NLP module classifies recent news about both companies to flag divergences driven by fundamental events. Those trades are filtered out.

## Evaluation

The system is evaluated with walk-forward backtesting that includes transaction costs. It is compared against a classical z-score strategy on:

- Returns
- Sharpe ratio
- Maximum drawdown
- Win rate

## Dashboard

Results are shown in a live dashboard displaying active pairs, spreads, signals and backtested performance.

## Status

Early stage: project scaffolding only.
