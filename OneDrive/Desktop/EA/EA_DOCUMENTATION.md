hxhdhxhduddhxhdhdhhdbxbdhdhdhrbxhxhdhddbhdhdhduxhdhhdhdbxbxhxhdh# Expert Advisors Documentation

## Overview

This directory contains 6 professional MetaTrader 5 Expert Advisors developed by Verlity Capital and Auric Edge Capital. Each EA specializes in different trading methodologies ranging from pure price action to hybrid institutional strategies.

---

## 1. Velity3.0.mql5 - Verlity EA Scalp Pro Fixed

### Summary

Enhanced professional scalping system optimized for gold, indices, forex, and volatility indices. Focuses on ATR-based micro-trend identification with multi-layer confirmation filters.

### Key Features

- **Timeframe**: M1 (1-minute) - required
- **Asset-Specific Optimization**: Detects and adapts to Gold, Index, Forex, or Volatility assets
- **Multi-Layer Filters**:
  1. ATR Expansion Check
  2. Impulse Candle Quality (body ratio ≥ 75% for Gold, 65% for others)
  3. Spread vs ATR Ratio
  4. Micro-Trend Detection (EMA slopes + candle momentum)
  5. RSI Filter (40-70 range for buys, avoid overbought)
  6. Volume Spike Confirmation (≥130% of 10-bar average)
  7. EMA Alignment (13/20/50 ordered correctly)
  8. Market Structure (higher lows for buys, lower highs for sells)

### Risk Management

- **Risk per Trade**: 0.8% (adjustable)
- **Daily Loss Limit**: 3.0% (hard stop)
- **Weekly Loss Limit**: 8.0% (hard stop)
- **Max Consecutive Losses**: 3 (halts trading)
- **Breakeven Management**: Triggered at 40-60% of risk (asset-dependent)
- **Trailing Stop**: Dynamic based on ATR multiplier (0.6-0.8x)

### Parameters by Asset Type

| Setting     | Gold | Index | Forex | Volatility |
| ----------- | ---- | ----- | ----- | ---------- |
| SL ATR Mult | 1.5  | 1.8   | 1.6   | 1.4        |
| TP ATR Mult | 2.5  | 2.8   | 2.4   | 2.2        |
| Trail Mult  | 0.6  | 0.8   | 0.7   | 0.5        |
| BE Trigger  | 0.4R | 0.4R  | 0.35R | 0.3R       |

### Session Filters

- **Gold**: London (07:00-10:00 GMT) + New York morning (13:00-16:00 GMT)
- **Index**: New York open hours (14:00-18:00 GMT)
- **Forex/Volatility**: Avoid 22:00-01:00 GMT (low liquidity)

### Performance Expectations

- Target Win Rate: 60-70%
- R:R Ratio: 1:1.67 (SL:TP varies by asset)
- Maximum Drawdown: 5-8%

---

## 2. Verlity advanced.mql5 - Auric Edge ICT-SMC Hybrid v4.0

### Summary

Institutional liquidity-based execution engine combining ICT (Inner Circle Trader) smart money concepts with SMC (Supply/Demand) price action. Focuses on liquidity sweeps and institutional dealing ranges.bxbdhdh

### Core Methodology

- **Hierarchical Pipeline** (order matters):
  1. **Kill Zone Filter**: London (07:00-10:00) or New York (13:00-16:00) GMT
  2. **Market Structure**: Swing high/low detection (BOS/CHoCH analysis)
  3. **Liquidity Pools**: Equal highs (buy-side) and equal lows (sell-side)
  4. **Liquidity Sweeps**: Wick violation + rejection pattern
  5. **Displacement**: Strong impulse candle (≥65% body ratio)
  6. **Premium/Discount Zones**: 62% premium / 38% discount (ICT standard)
  7. **FVG or Order Block**: Fair Value Gap or rejection candle entry
  8. **Indicator Confirmation**: EMA alignment, RSI, Volume (secondary only)
  9. **Execute Trade**

### Key Parameters

- **Structure Bars**: 5 (bars required for swing validation)
- **EQ Tolerance**: 50 points (equal high/low tolerance)
- **Min Pool Touches**: 2 (minimum contacts for valid liquidity)
- **Premium Level**: 0.62 (62% of range = premium zone)
- **Discount Level**: 0.38 (38% of range = discount zone)
- **SL Multiplier**: 2.0 ATR
- **TP Multiplier**: 3.5 ATR
- **Min FVG Size**: 0.3 × ATR

### Risk Management

- **Risk per Trade**: 0.5% of equity
- **Max Daily Loss**: 2.5%
- **Max Consecutive Losses**: 4
- **Max Lot Size**: 5.0 lots
- **Trailing Stop**: 0.5 × ATR (after 1.5R profit)

### Session Focus

- **London Kill Zone**: 07:00-10:00 GMT (highest liquidity)
- **New York Kill Zone**: 13:00-16:00 GMT (strong moves)

### Trade Quality Signals

- Only enters when BOS confirmed (new swing extreme)
- Requires liquidity sweep (institutional distribution/accumulation)
- Enters within FVG or Order Block zones
- Avoids breakout points on S/R (InpSRAvoidBreakouts enabled)

---

## 3. Verlity AI.mql5 - HighAccuracyForexEA v3.2 Final Optimized

### Summary

Professional trading system with adaptive regime detection, multi-timeframe confirmation, and strict safety limits. Combines scalping and grid trading modules with hardened risk controls.

### Key Modules

#### A. Regime Detection (Volatility-Based)

- **Compression** (safe for grid): ATR ratio < 0.6 across timeframes
- **Expansion** (trending): ATR ratio > 1.4
- **Dislocation** (dangerous): Volatility spike > 2.5× normal
- Uses 1M, 5M, and 1H ATR for classification

#### B. Scalping Module (Mean Reversion)

- **Entry**: Price deviation from short-term MA
- **Strategy**: Buy oversold / Sell overbought
- **Lot Size**: 0.25% risk per trade
- **TP**: 6.0 points (adaptive via ATR)
- **SL**: 12.0 points (adaptive via ATR)
- **BE Level**: 3.0 points profit → move to breakeven

#### C. Grid Module (CRITICAL SAFETY - MAXIMUM 3 LEVELS)

- **Regime**: Compression only (NO trading in expansion)
- **Max Levels**: 3 per direction (6 total HARD LIMIT)
- **Lot Scaling**: 1.0 (NO martingale - each level = same size)
- **Grid Spacing**: Dynamic based on ATR
- **Equity Drawdown Cap**: 3% maximum (automatic stop)
- **Exposure Limit**: 0.05 lots total (hard cap)
- **Cooldown**: 30 minutes after forced shutdown
- **Basket Close**: At 0.2% equity profit (all levels close together)

#### D. Trade Quality Scoring (0-100)

Points awarded for:

- Multi-timeframe alignment (20 pts)
- Market structure bullish/bearish (20 pts)
- Volume confirmation (15 pts)
- Trend strength > 60% (15 pts)
- Order block proximity & alignment (15 pts)
- Pattern confirmation (10 pts)
- Compression regime bonus (5 pts)

**Min Quality**: 70/100 required for entry

#### E. Filters

- **Spread**: Max 2.0 pips
- **Slippage**: Max 3 points
- **Tick Volatility**: Max 3.0 × ATR
- **Sessions**: London, New York (Asian avoided)
- **News**: High-impact news times avoided
- **Minimum Interval**: 30 seconds between trades

### Performance Expectations

- Scalp Win Rate: 60-65%
- Grid Survival Rate: 80% (when compression detected)
- Max Equity Risk per Grid: 1.0% of equity
- Monthly Target: 3-5% (conservative)

---

## 4. Verlity hybrid.mql5 - Verlity Institutional Hybrid EA v5.0

### Summary

SMC + ICT + Liquidity Engineering + Indicators combined in strict hierarchical order. Professional institutional-grade strategy using pure price action as primary filter, indicators as confirmation only.

### Execution Hierarchy (MANDATORY ORDER)

1. **ICT Time Windows**: London/NY kill zones only
2. **Market Structure**: Identify bias (HH/HL bullish, LL/LH bearish)
3. **Liquidity Sweep**: Non-negotiable entry trigger
4. **Displacement**: Strong impulse candle confirmation
5. **Premium/Discount**: Dealing range zone validation
6. **FVG/OB Mitigation**: Entry location selection
7. **Support/Resistance**: Confluence & breakout avoidance
8. **Indicator Confirmation**: EMA, RSI, Volume (secondary only)
9. **Risk Filters**: Position management
10. **Execute Trade**

### Structure Detection

- **Swing Points**: Min 5 bars to validate
- **Higher High + Higher Low** = Bullish bias
- **Lower High + Lower Low** = Bearish bias
- **Neutral**: No clear structure

### Liquidity Framework

- **Equal Highs**: Buy-side liquidity (swept when violated)
- **Equal Lows**: Sell-side liquidity (swept when violated)
- **Sweep Rules**: Wick must exceed pool level + minimum wick ratio
- **Displacement**: Confirms sweep with strong directional candle (≥65% body)

### Dealing Range

- **High**: Most recent swing high
- **Low**: Most recent swing low
- **Equilibrium**: (High + Low) / 2
- **Premium**: Price > EQ (optimal for shorts after buyside sweep)
- **Discount**: Price < EQ (optimal for longs after sellside sweep)

### Entry Mechanics

- **FVG Entry**: Price touches 3-candle gap zone
- **OB Entry**: Price enters rejection candle zone
- **Minimum FVG Size**: 0.3 × ATR
- **OB Body Ratio**: Minimum 50% of candle range

### Support/Resistance

- Uses swing highs (resistance) and lows (support)
- Tolerance: 20 points default
- Avoids breakout trades (InpSRAvoidBreakouts=true)
- Adjusts TP to stop before major S/R levels

### Risk Management

- **Risk per Trade**: 0.5% of equity
- **Max Daily Loss**: 2.5%
- **Max Consecutive Losses**: 3
- **SL**: 2.0 × ATR beyond liquidity/OB
- **TP**: 3.5 × ATR at opposing liquidity

### Session Filter

- London: 07:00-10:00 GMT
- New York: 13:00-16:00 GMT
- Other times: reduced activity

---

## 5. Verlity.mql5 - Auric Edge ICT-SMC Pure v5.0

### Summary

Pure institutional execution engine with NO indicators. Uses only price action: structure, liquidity pools, FVGs, and order blocks. Focused on ICT kill zones and smart money distribution/accumulation.

### Core Concepts

- **No Indicators**: Price action only
- **Market Structure**: Swing identification → Bias determination
- **Liquidity Pools**: Equal highs/lows = smart money accumulation zones
- **Fair Value Gaps**: 3-candle gaps for entry location
- **Order Blocks**: Rejection candles = institutional orders
- **Dealing Range**: Premium/discount zones for directional bias

### Swing Detection

- **Swing High**: 2+ bars higher on both sides
- **Swing Low**: 2+ bars lower on both sides
- **Min Lookback**: 50 bars
- **Trend State**:
  - **BULLISH**: Higher Highs + Higher Lows (HH/HL)
  - **BEARISH**: Lower Highs + Lower Lows (LH/LL)
  - **NEUTRAL**: Mixed structure

### Liquidity Mechanics

- **Buy-Side Pools**: Equal highs (institutions accumulate)
- **Sell-Side Pools**: Equal lows (institutions distribute)
- **Sweep Trigger**: Wick violates pool + rejects
- **Cooldown**: One trade per sweep (minimum 5-minute wait)

### Entry Conditions

After liquidity sweep:

1. **Displacement**: Strong impulse candle (≥60% body)
2. **Trend Alignment**: Structure confirms entry direction
3. **Premium/Discount**: Price in appropriate zone
4. **FVG/OB Mitigation**: Entry within gap or rejection zone

### Stop Loss & Take Profit

- **SL**: Below nearest swept liquidity pool + buffer (10 points)
- **TP**: Next unswept pool in trade direction
- **Fallback**: ATR-based if no pools nearby

### Risk Parameters

- **Risk per Trade**: 1.0% (adjustable)
- **Max Concurrent Trades**: 1
- **Max Daily Loss**: 3.0%
- **Max Spread**: 30 points

### Session Schedule

- **London**: 02:00-05:00 server time
- **New York**: 08:00-11:00 server time
- (Adjust for your broker's GMT offset)

### Performance Profile

- **Win Rate**: 55-60% (institutional context trades)
- **R:R Ratio**: 1:2 to 1:3 (large TP distances)
- **Trade Frequency**: 2-5 trades per week (selective)
- **Drawdown**: 5-10% (large moves anticipated)

---

## 6. win.mql5 - Verlity Professional 98% Win Rate

### Summary

High-frequency professional strategy combining smart grid recovery, mean reversion, and multi-confirmation signal generation. Targets instant profit exits for rapid-fire scalping.

### Strategies

1. **Smart Grid Recovery**: Martingale-style recovery with 1.5× lot multiplier
2. **Breakout Confirmation**: Entry on established breakouts
3. **Mean Reversion**: Entry on oversold/overbought
4. **Trend + Momentum**: EMA + RSI confluence

### Instant Profit Exit

- **Min Profit**: 2.0 points (automatic close)
- **Virtual TP**: 15.0 points (manual close if hit)
- **Max Loss**: 30.0 points per trade (hard stop)

### Multi-Confirmation System (≥5 required)

1. ADX > 25 (trend strength)
2. EMA alignment (Fast > Medium > Slow for buys)
3. RSI extremes (< 30 oversold or > 70 overbought)
4. Bollinger Bands (price at bands)
5. Stochastic crossover (K > D for buys)
6. Volume spike (> 1.2× average)
7. Multi-timeframe alignment (higher TF trend)
8. Support/Resistance confluence

### Smart Grid System

- **Max Levels**: 4 grids
- **Grid Multiplier**: 1.5× (each level = 1.5 × previous lot)
- **Grid Spacing**: 20 points
- **Basket TP**: Close all when profitable together
- **Lot Limit**: Respects broker minimums/maximums

### Session Filters

- **Trade Only Trending**: Requires ADX ≥ 25.0
- **Avoid Choppy**: Market structure validation
- **London Session**: 08:00-16:00 (main activity)
- **New York Session**: 13:00-22:00 (strong moves)
- **Avoid Weekend**: Close all Friday 18:00+

### Risk Management

- **Risk per Trade**: 0.5% fixed fractional
- **Daily Risk Limit**: 2.0% maximum
- **Daily Profit Target**: 3.0% (stops trading when reached)
- **Max Drawdown**: 5.0% (emergency close-all)
- **Max Consecutive Loss**: 3 (halts trading)

### Performance Expectations

- **Win Rate Target**: 70-80% (high bar)
- **Trade Duration**: 5-15 minutes
- **Daily Trades**: 10-20 (grid-heavy)
- **Monthly Return**: 5-10% (conservative)

---

## Comparison Table

| Feature         | Velity3.0 | Adv       | AI        | Hybrid       | Pure    | Win       |
| --------------- | --------- | --------- | --------- | ------------ | ------- | --------- |
| Timeframe       | M1        | M1        | M1        | M1           | M1      | M1        |
| Indicators      | EMA/RSI   | EMA/RSI   | Full      | EMA/RSI      | None    | Full      |
| Risk Model      | 0.8%      | 0.5%      | 0.25-1%   | 0.5%         | 1.0%    | 0.5%      |
| Max Daily Loss  | 3%        | 2.5%      | Variable  | 2.5%         | 3%      | 2%        |
| Max Consecutive | 3         | 4         | Varies    | 3            | N/A     | 3         |
| Grid Trading    | No        | No        | Yes       | No           | No      | Yes       |
| Kill Zones      | Yes       | Yes       | Session   | Yes          | Yes     | Yes       |
| Best For        | Scalping  | Liquidity | Versatile | Institutions | Purists | High-Freq |

---

## Setup Instructions

### Common Requirements

1. **MetaTrader 5** installed and running
2. **Minimum Account**: $500 (micro trading)
3. **Recommended**: $5000+ (comfortable position sizing)
4. **Internet**: Stable, low-latency connection
5. **VPS**: Recommended for always-on trading

### Installation

1. Copy .mql5 files to `C:\Users\[YourUser]\AppData\Roaming\MetaQuotes\Terminal\[TerminalID]\MQL5\Experts\`
2. Restart MetaEditor or MetaTrader5
3. In MetaTrader5: File → Open Data Folder → MQL5 → Experts
4. Each EA should appear in Expert Advisors list

### Activation on Chart

1. Open desired symbol on M1 timeframe
2. In Navigator panel: Experts → Right-click desired EA
3. Select "Attach to a chart"
4. Review and adjust parameters
5. Click "OK"

### Backtesting (Before Live)

1. Strategy Tester: View → Strategy Tester (Ctrl+R)
2. Select EA from dropdown
3. Symbol & Period: M1 (required for most)
4. Model: "Every tick based on real ticks" (most accurate)
5. Optimize: Test different parameter sets
6. Report: Check win rate, drawdown, profit factor

### Parameter Adjustment

- **Risk%**: Start conservative (0.25-0.5%), increase after 100+ profitable trades
- **Daily Loss**: Match your risk tolerance (2-5%)
- **Kill Zones**: Adjust hour parameters to your broker's GMT offset
- **Spreads**: Check your broker's typical spreads, set filter appropriately

---

## Troubleshooting

### Common Issues

**Problem**: EA not trading

- Check: Algo trading enabled in terminal
- Check: Symbol matches input
- Check: Timeframe = M1 (if required)
- Check: Kill zones match current time
- Check: Account balance sufficient for minimum lot

**Problem**: High slippage

- Solution: Increase Slippage_Points parameter
- Solution: Change fill mode (IOC → RETURN)
- Solution: Use low-slippage broker/instrument

**Problem**: Grid positions not closing

- Check: Close_Grid_In_Profit enabled (for grid EAs)
- Check: Basket TP percentage set correctly
- Manual: Close positions manually if stuck

**Problem**: Indicator errors

- Solution: Compile EA fresh (Tools → Compile)
- Solution: Restart MetaTrader5
- Solution: Check indicator availability on symbol

---

## Live Trading Checklist

- [ ] Backtested on 6+ months of data
- [ ] Win rate ≥ 55% (minimum)
- [ ] Profit factor ≥ 1.3 (minimum)
- [ ] Max drawdown < 15%
- [ ] Started on demo for 2+ weeks
- [ ] Risk per trade ≤ 0.5% (conservative start)
- [ ] Stop-loss & take-profit hardcoded
- [ ] Daily risk limit set
- [ ] Kill switches enabled
- [ ] Notifications tested
- [ ] VPS configured (if running 24/7)
- [ ] Broker verified (regulated, good reviews)

---

## Support & Optimization

### Optimization Tips

1. **Symbol-Specific**: Optimize parameters per symbol
2. **Timeframe-Specific**: M1 parameters differ from H1
3. **Broker-Specific**: Spreads vary; adjust kill zones for GMT offset
4. **Market-Specific**: Trending vs ranging market adjustments
5. **Session-Specific**: Different behavior in London vs NY hours

### Monitoring

- Daily: Check P/L, drawdown, win rate
- Weekly: Review trade logs for patterns
- Monthly: Analyze performance by session/symbol
- Quarterly: Reoptimize parameters to market conditions

### Adjusting for Trending Markets

- Increase TP multiplier
- Loosen filter confirmations
- Reduce grid complexity
- Extend kill zone hours

### Adjusting for Ranging Markets

- Enable grid trading (if available)
- Tighten SL levels
- Increase filter requirements
- Add support/resistance filters

---

## Risk Disclaimer

**IMPORTANT**: Trading futures, forex, indices, and cryptocurrencies carries substantial risk of loss. These EAs are provided as-is without guarantees. Past performance is not indicative of future results.

- **Start Small**: Demo trading or micro lots first
- **Never Overtrade**: Follow position sizing rules
- **Set Limits**: Daily/weekly loss limits are mandatory
- **Monitor Closely**: First 100 trades require daily review
- **Protect Capital**: Kill switches exist for critical situations
- **Test Thoroughly**: Backtest extensively before live trading

---

## Contact & Updates

For questions or updates to these EAs:

- Review: Strategy principles & logic in source code
- Backtest: Each symbol/broker combination separately
- Monitor: Live performance metrics systematically

**Last Updated**: January 2026
**Version**: Complete Suite v5.0

---
