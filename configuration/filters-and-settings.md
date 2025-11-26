# Filters and Settings

## In-Game Filters

**Profit filters:**
```
/cofl set minprofit 5m           # Start 5-10m, adjust based on purse
/cofl set minprofitpercent 6     # 5-10% recommended
/cofl set maxprice 100m          # Set 20-30% of total purse
```

**Item filters:**
```
/cofl blacklist add "Item Name"
/cofl whitelist add "Item Name"
```

## Config File Filters

**Skip filters:**
```javascript
skip: {
    lowProfit: 1000000,             // Skip < 1m profit
    profitThreshold: 5000000,       // Auto-buy > 5m (HIGHER BAN RISK)
    cosmetics: true,
    finderTypes: ["SNIPER", "USER", "FLIPPER", "STONKS", "TFM"]
}
```

**Relist exclusions:**
```javascript
doNotRelist: {
    items: ["Item Name"],
    minProfit: 1000000,
    tags: ["VERY_SPECIAL", "PET"],
    finders: ["STONKS", "USER"]
}
```

## Pricing Strategy

**Price markup:**
```javascript
percentOfTarget: {
    "0-10000000": 0.95,          // 0.90-0.95 = faster, 0.98-0.99 = higher profit
    "10000000-50000000": 0.97,
    "50000000-999999999": 0.98
}
```

**Listing duration:**
```javascript
listHours: {
    "0-10000000": 24,
    "10000000-50000000": 48,
    "50000000-999999999": 72
}
```

**Rounding:**
```javascript
roundTo: 0    // 0=none, 2=100s, 4=10k, 6=1M
```

## Strategy Presets

**Conservative (new users):**
- minprofit: 10m, minprofitpercent: 10, maxprice: 50m
- percentOfTarget: 0.93

**Balanced (most users):**
- minprofit: 5m, minprofitpercent: 6, maxprice: 100m
- percentOfTarget: 0.95-0.97

**Aggressive (experienced):**
- minprofit: 3m, minprofitpercent: 4, maxprice: 500m
- percentOfTarget: 0.97-0.98

## Adjustment Guide

**Too many flips:** Increase minprofit/percent, decrease maxprice

**Too few flips:** Decrease minprofit/percent, increase maxprice

**Items not selling:** Lower percentOfTarget, adjust listHours

**Wrong items:** Blacklist items, adjust skip filters

Start strict, monitor, adjust gradually.

---

**See also:** [Cofl Commands](cofl-commands.md) | [Config Structure](config-structure.md)
