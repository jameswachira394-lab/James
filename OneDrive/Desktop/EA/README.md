# Verlity Capital - Expert Advisor Suite v5.0

Professional MetaTrader 5 Expert Advisors for automated forex, indices, gold, and volatility trading.

## 📦 Repository Contents

### Expert Advisors (6 Total)

1. **Velity3.0.mql5** - ATR-based Scalping System
   - Asset-specific optimization (Gold, Index, Forex, Volatility)
   - Multi-layer confirmation filters
   - Win rate target: 60-70%

2. **Verlity advanced.mql5** - ICT-SMC Hybrid (Liquidity-Focused)
   - Kill zone execution (London & NY sessions)
   - Liquidity sweep detection
   - Premium/Discount zone trading
   - Win rate target: 55-65%

3. **Verlity AI.mql5** - Adaptive Regime Detection v3.2
   - Compression/Expansion/Dislocation detection
   - Scalping module (mean reversion)
   - Grid trading (max 3 levels, strict safety)
   - Quality score validation (min 70/100)

4. **Verlity hybrid.mql5** - Institutional Hybrid EA v5.0
   - Structure → Liquidity → Premium/Discount → FVG/OB → Indicators
   - Hierarchical execution pipeline
   - Support/Resistance confluence
   - Target: 70-80% win rate

5. **Verlity.mql5** - Pure Price Action v5.0
   - NO indicators (pure ICT-SMC)
   - Market structure analysis
   - Order block & FVG detection
   - Selective trading (2-5 trades/week)

6. **win.mql5** - Professional Multi-Confirmation v4.0
   - Smart grid recovery (1.5× lot multiplier)
   - Instant profit exits (2.0 points)
   - 8-signal confirmation system
   - High-frequency scalping target

### Documentation

- **EA_DOCUMENTATION.md** - Complete guide for all EAs
  - Strategy explanations
  - Parameter details
  - Risk management specifications
  - Setup & backtesting instructions
  - Troubleshooting guide

## 🚀 Quick Start

### Prerequisites
- MetaTrader 5 (MT5)
- Minimum account: $500
- Recommended: $5000+
- Stable internet connection

### Installation
1. Copy `.mql5` files to: `C:\Users\[YourUser]\AppData\Roaming\MetaQuotes\Terminal\[TerminalID]\MQL5\Experts\`
2. Restart MetaTrader 5
3. Open chart (M1 timeframe required)
4. In Navigator: Experts → Right-click EA → Attach to Chart

### Backtesting (Recommended First Step)
1. View → Strategy Tester (Ctrl+R)
2. Select EA from dropdown
3. Set Symbol & Period to M1
4. Model: "Every tick based on real ticks"
5. Test on 6+ months of historical data

### Live Trading Checklist
- [ ] Win rate ≥ 55% on backtest
- [ ] Profit factor ≥ 1.3
- [ ] Max drawdown < 15%
- [ ] Tested on demo for 2 weeks
- [ ] Risk per trade ≤ 0.5%
- [ ] Daily loss limit set
- [ ] Broker verified (regulated)

## ⚙️ Key Parameters

### Risk Management (All EAs)
| Parameter | Default | Range |
|-----------|---------|-------|
| Risk per Trade | 0.5% | 0.25-1.0% |
| Daily Loss Limit | 2.5% | 2.0-5.0% |
| Max Consecutive Loss | 3-4 | 2-5 |
| Max Drawdown | 5-10% | 3-15% |

### Session Filtering
- **London Kill Zone**: 07:00-10:00 GMT (highest liquidity)
- **New York Kill Zone**: 13:00-16:00 GMT (strong directional moves)
- **Off-hours**: Reduced activity or disabled

### Strategy Comparison

| Feature | Velity3.0 | Advanced | AI | Hybrid | Pure | Win |
|---------|-----------|----------|----|----|------|-----|
| Timeframe | M1 | M1 | M1 | M1 | M1 | M1 |
| Indicators | EMA/RSI | EMA/RSI | Full Suite | EMA/RSI | None | Full |
| Grid Trading | No | No | Yes | No | No | Yes |
| Win Rate Target | 60-70% | 55-65% | Varies | 70-80% | 55-60% | 70-80% |
| Best For | Scalping | Liquidity | Versatility | Institutions | Purists | High-Frequency |

## 📊 Performance Expectations

- **Monthly Return**: 3-10% (depending on EA & market conditions)
- **Trade Frequency**: 5-50+ trades/month (varies by strategy)
- **Typical Drawdown**: 5-10%
- **Recovery Time**: 1-4 weeks (from peak drawdown)

## ⚠️ Risk Management Features

All EAs include:
- ✅ Daily loss limits (hard stops)
- ✅ Weekly loss limits (auto-disable)
- ✅ Max consecutive loss protection
- ✅ Breakeven management
- ✅ Trailing stop functionality
- ✅ Session filtering (kill zones)
- ✅ Spread checking
- ✅ Slippage limits
- ✅ Position sizing (risk-based)

## 🔍 Testing & Optimization

### Recommended Workflow
1. **Backtest**: 6+ months historical data
2. **Out-of-Sample**: Test on forward data not used for optimization
3. **Demo Trading**: 2-4 weeks with real (but paper) money
4. **Live Start**: Micro lots on live account
5. **Monitor**: Daily performance review for first 100 trades

### Optimization Parameters
- Adjust risk% per symbol/broker
- Modify kill zone hours for GMT offset
- Tune indicator periods for market conditions
- Scale lot size based on market volatility

## 📝 Troubleshooting

### EA Won't Trade
- Check: Algo trading enabled in MT5
- Check: Correct symbol on chart
- Check: Timeframe = M1
- Check: Kill zones match current time
- Check: Account balance ≥ minimum lot requirement

### High Slippage
- Increase `Slippage_Points` parameter
- Use low-slippage broker
- Trade during peak liquidity hours

### Grid Positions Stuck
- Ensure `Close_Grid_In_Profit` is enabled
- Check basket TP percentage
- Manual close if persistent (emergency option)

## 📖 Documentation Files

- **EA_DOCUMENTATION.md** - Comprehensive guide
  - 40+ pages of strategy details
  - Parameter-by-parameter explanations
  - Risk management specifications
  - Setup instructions with screenshots
  - Troubleshooting FAQ

## 🤝 Support

For issues, optimization, or questions:
1. Review strategy logic in source code
2. Backtest thoroughly before adjusting
3. Test each parameter change separately
4. Monitor live performance systematically

## 📈 Version History

- **v5.0** (Current) - Complete suite, hardened risk controls
- **v4.0** - Added grid safety limits
- **v3.2** - Regime detection & adaptive parameters
- **v3.0** - Multi-asset optimization
- **v1.0** - Initial release

## ⚖️ Disclaimer

**IMPORTANT**: Trading derivatives carries substantial risk of loss. These EAs are provided as-is without any performance guarantees. Past performance is not indicative of future results.

- **Risk Management**: Always use stop-losses
- **Position Sizing**: Never risk more than 1% per trade
- **Account Capital**: Start with capital you can afford to lose
- **Testing**: Extensive backtesting & demo trading required
- **Monitoring**: Active monitoring recommended for first 100+ trades

## 📄 License

Copyright © 2024-2026 Verlity Capital | Auric Edge Capital

All Expert Advisors are proprietary. Use only on authorized accounts.

---

**Last Updated**: January 2026
**Version**: 5.0 Complete Suite
**Language**: MQL5 (MetaTrader 5)
**Compatibility**: Windows 7+, MetaTrader 5.0+

For inquiries: trading@verlity.com

