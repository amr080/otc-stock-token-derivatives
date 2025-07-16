**Stock Token Trading Setup:**

Excel columns: Symbol | USD_Price | FX_Rate | Base_EUR | Collar_Range | Exec_Price | FX_Fee | Net_Cost | Position | Unrealized_P/L

Formulas:
- `Base_EUR = USD_Price / FX_Rate`
- `Upper = Base_EUR * 1.005`
- `Lower = Base_EUR * 0.995`
- `FX_Fee = Exec_Price * Qty * 0.003`
- `Net_Cost = (Exec_Price * Qty) + FX_Fee`
- `Unrealized_P/L = (Current_Base_EUR - Avg_Cost) * Position`

**TradFi Equivalent - Currency Hedged ETF:**

Excel columns: ETF_Price | NAV | Premium/Discount | Hedge_Ratio | Hedge_Cost | Creation_Units | Arb_Opportunity

Example: VTI (US) vs VXUS.L (London-listed, EUR hedged)

**Stock Token Flow:**
Buy AAPL token → Pay €182.55 → Hold 1 synthetic AAPL → Sell for €197.41

**ETF Arb Flow:**
1. Buy VTI shares ($100) + EUR/USD forward hedge
2. Package into creation units → Deliver to ETF issuer
3. Receive ETF shares trading at €91.50
4. Sell ETF shares → Profit from premium/discount + hedge differential

**Key Difference:**
- Token: Single synthetic instrument with built-in FX handling
- ETF: Multi-leg trade (equity + FX hedge + creation/redemption mechanism)

Both profit from price discrepancies and FX movements, but ETF requires more complex hedging infrastructure.
