# Manual Pricing

*Budda Dog is the goat at manual pricing btw*

Use Cofl lore to manually price items when auto-listing fails or items don't sell.

## Using Cofl Lore

**Check price in-game:**
```
/cofl lore
```
Click stats to view metrics.

**Key Stats:**

**Median Price (MOST IMPORTANT):**
- Best indicator of value
- Removes outliers
- Use as base price
- **Warning:** Inaccurate for very low volume items

**BIN Price:**
- Recent instant sales
- Often inflated
- Less reliable than median

**Volume:**
- High (20+ sales): Reliable data, easier to sell
- Low (< 0.5 sales): Unreliable data, harder to sell

**Finder Estimate:**
- Algorithm-based estimate
- Usually accurate
- Only shows sometimes

## Pricing Formula

**High volume items:**
```
List at: Median × 0.95
```

**Low volume items:**
```
List at: Median × 0.90 to 0.92
```

**Fast sale needed:**
```
List at: Median × 0.88 to 0.90
```

## Cofl Website

Check price history at **sky.coflnet.com**:
1. Search item name
2. View price graph
3. Check recent sales

## Special Cases

**Reforged/Modified Items:**
```
Base median + reforge value + enchant value
Then multiply by 0.95
```

**Pets:**
- Check exact pet + level with `/cofl lore`
- Adjust for candy (-3% per candy)
- List at 0.92-0.97 of median

## Listing Duration

- High demand: 24 hours
- Medium demand: 48 hours
- Low demand: 72 hours

**Starting Bid:** Set 10-20% below BIN for bidding wars (good for Runebooks, enchanted Talismans)

**BIN:** Instant sale at target price (good for common items)

**Always use cookies if available!**

## If Item Doesn't Sell

**After 24h:** Check median again, lower 5%, relist

**After 48h:** Lower 10%, extend duration

**After 72h:** Major price drop needed or contact config provider

## Common Mistakes

1. **Trusting BIN too much** → Always prioritize median
2. **Listing too high** → List at 90-95% of median
3. **Lowering too fast** → Wait 24h before adjusting
4. **Ignoring volume** → Low volume = unreliable data

## Reporting Bad Flips

If bot repeatedly buys unsellable items, report to config provider:
```
"Config bought [Item Name]
Paid: [Amount]
Median: [Amount]
Can't sell, please fix filter"
```

Or forward webhook message. See [Handling Bad Flips](handling-bad-flips.md).

## Key Takeaways

- Use `/cofl lore` first - most reliable
- Median > BIN
- Check volume (more sales = more reliable)
- List at 90-95% of median
- Wait 24h before relisting
- Report persistent issues

---

**See also:** [Handling Bad Flips](handling-bad-flips.md) | [Cofl Commands](../configuration/cofl-commands.md) | [Filters and Settings](../configuration/filters-and-settings.md)
