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


```html
<h3><strong>Buy (1 AAPL @ €182.55)</strong></h3>
<ul>
    <li>1 User → €182.55 to RH</li>
    <li>2 RH shorts synthetic to user</li>
    <li>3 RH buys 1 AAPL @ $200 via prime broker</li>
    <li>4 RH swaps €→$ for share cost</li>
    <li>5 RH mint(user,1) token</li>
    <li>6 Balances: User +1 token −€182.55 | RH +€182.55 +1 share −1 synthetic</li>
</ul>
<h3><strong>Sell (token price €197.41)</strong></h3>
<ul>
    <li>1 User hits sell</li>
    <li>2 RH buys back synthetic, closes short</li>
    <li>3 RH burn(user,1) token</li>
    <li>4 RH sends €197.41 to user</li>
    <li>5 RH sells 1 AAPL @ $210, swaps $→€</li>
    <li>6 Balances flat; RH keeps spread + FX fee</li>
</ul>
<p>Pricing path: Nasdaq USD price → divide FX → collar ±0.5% → execPrice; only final euros enter mint/burn tx; none of this lives on contract</p>
```
