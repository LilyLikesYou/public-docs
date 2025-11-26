# Filters and Settings

Configure TPM's filters to control which flips to buy and how to price items.

## Profit Filters

**Minimum Profit:** `/cofl set minprofit 5m`
- Start 5-10M, adjust based on purse and flip volume
- Higher = safer but fewer flips

**Minimum Profit Percent:** `/cofl set minprofitpercent 6`
- Prevents low-return expensive items
- 5-10% recommended starting range

**Maximum Price:** `/cofl set maxprice 100m`
- Protects from expensive mistakes
- Set 20-30% of total purse

## Skip Filters

Config-based filtering options:

```javascript
skip: {
    lowProfit: 1000000,          // Skip < 1M profit
    profitThreshold: 5000000,    // Auto-buy > 5M profit
    cosmetics: true,             // Skip cosmetics
    finderTypes: ["SNIPER", "USER", "FLIPPER", "STONKS", "TFM"]
}

## Relist Filters

```javascript
doNotRelist: {
    items: ["Item Name"],              // Specific items
    minProfit: 1000000,                // Don't relist if < 1M profit
    tags: ["VERY_SPECIAL", "PET"],     // Don't relist by tag
    finders: ["STONKS", "USER"]        // Don't relist by finder
}
```

## Pricing Strategies

```javascript
percentOfTarget: {
    "0-10000000": 0.95,          // 0.90-0.95 = faster sales, 0.98-0.99 = higher profit
    "10000000-50000000": 0.97,
    "50000000-999999999": 0.98
},

listHours: {
    "0-10000000": 24,            // Auction duration by value
    "10000000-50000000": 48,
    "50000000-999999999": 72
},

roundTo: 4                       // 0=none, 2=100s, 4=10k, 6=1M
```

## Advanced Options

```javascript
angryCoopPrevention: true,    // Prevent claiming from coop members
blockUselessMessages: true,   // Reduce console spam
visitFriend: "Username"       // Private island flipping
```

## In-Game Filter Commands

```
/cofl set minprofit 5m
/cofl set minprofitpercent 7
/cofl set maxprice 100m
/cofl blacklist add "Item Name"
/cofl whitelist add "Item Name"
```

Full commands: [Cofl Commands](cofl-commands.md)

## Strategy Examples

**Conservative (New):**
- minprofit: 10m, minprofitpercent: 10, maxprice: 50m
- percentOfTarget: 0.93
- Safe but fewer flips

**Balanced (Most):**
- minprofit: 5m, minprofitpercent: 6, maxprice: 100m
- percentOfTarget: 0.95-0.97
- Good mix, requires monitoring

**Aggressive (Experienced):**
- minprofit: 3m, minprofitpercent: 4, maxprice: 500m
- percentOfTarget: 0.97-0.98
- Max profit, higher risk

## Adjusting Filters

**Too many flips:** Increase minprofit/percent, decrease maxprice

**Too few flips:** Decrease minprofit/percent, increase maxprice

**Items not selling:** Lower percentOfTarget, adjust listHours

**Wrong items:** Use `/cofl blacklist add "Item"`, adjust skip filters

**Best practice:** Start strict, monitor closely, adjust gradually

---

**See also:** [Cofl Commands](cofl-commands.md) | [Config Structure](config-structure.md) | [Loading Configs](../guides/loading-configs.md)
