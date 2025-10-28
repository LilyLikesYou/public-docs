# Handling Bad Flips

A bad flip is an item that doesn't sell within 72h, sells for less profit, or was overpaid for.

## Immediate Actions

**1. Check Current Price**
```
/cofl lore
```
Check median, volume, and BIN price. See [Manual Pricing](manual-pricing.md).

**2. Determine Status**
- **Worth more than paid:** List at median × 0.95, be patient
- **Worth same as paid:** List at cost, break even
- **Worth less than paid:** List aggressively to minimize loss

**3. Prevent Future Purchases**
```
/cofl blacklist add "[Item Name]"
```

## Listing Strategies

**Small loss:** List at cost, 48h duration

**Medium loss:** List at median × 0.85-0.93, 72h duration

**Large loss:** List at median × 0.75-0.85, 72h duration

**Long-term hold:** Keep if you have purse space and price may recover (risks: tied up coins, may not recover)

## Reporting to Config Provider

**Report Example:**
```
Item: [Name]
Paid: [Amount]
Median: [Amount] ([Volume] sales)
Issue: [Why it's bad]
```

**Report if:**
- Same item bought repeatedly
- Bot consistently overpays
- Volume < 5 sales
- Doesn't sell after 72h

Forward webhook message or DM config provider with `/cofl lore` screenshot.

## Common Causes

**Outdated price data:** Market dropped, Cofl data not updated
- Blacklist temporarily, wait for refresh

**Low volume item:** Unreliable estimates, hard to sell
- Blacklist, adjust config to skip low-volume items

**Special variant:** Bot can't distinguish, variant worth less
- Blacklist specific variant

**Market crash:** Supply/demand changed, Hypixel update
- Monitor news, adjust filters, take loss

**Profit calculation error:** Target price incorrect
- Report to provider

## Prevention

**Proper filters:**
```
/cofl set minprofit 5m
/cofl set minprofitpercent 6
/cofl set maxprice 100m
```

**Maintain blacklist:** Add items that didn't sell or you overpaid for

**Monitor actively:** Review purchases, check values, adjust filters

**Use quality configs:** Reputable providers, keep updated

**Switch configs if:** 3+ bad flips/day, consistent losses, config outdated

---

**Key:** Handle quickly, learn, prevent repeats. Bad flips happen - proper management keeps them rare and minimal.

**See also:** [Manual Pricing](manual-pricing.md) | [Filters and Settings](../configuration/filters-and-settings.md) | [Cofl Commands](../configuration/cofl-commands.md)
