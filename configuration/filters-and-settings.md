# Filters and Settings

This guide explains TPM's filtering system and how to customize your bot's behavior to match your flipping strategy.

## Understanding Filters

Filters determine which flips TPM will purchase and how it will handle items. Proper filter configuration is crucial for profitable flipping.

## Profit Filters

### Minimum Profit

The minimum profit an item must have for TPM to purchase it.

**Config Setting:**
```javascript
// Set in config or via Cofl command
/cofl set minprofit 5m
```

**Examples:**
- `1m` = Only buy items with 1M+ profit
- `5m` = Only buy items with 5M+ profit
- `10m` = Only buy items with 10M+ profit

**Tips:**
- Start higher (5-10M) and gradually lower
- Adjust based on your purse size
- Higher profits = safer but fewer flips

### Minimum Profit Percentage

The minimum profit percentage an item must have.

**Config Setting:**
```javascript
/cofl set minprofitpercent 6
```

**Examples:**
- `5` = 5% profit margin minimum
- `10` = 10% profit margin minimum
- `15` = 15% profit margin minimum

**Tips:**
- Important for low purse sizes
- Prevents buying expensive items with low returns
- 5-10% is a good starting range

### Maximum Price

The maximum price TPM will pay for any single item.

**Config Setting:**
```javascript
/cofl set maxprice 100m
```

**Examples:**
- `50m` = Never buy items over 50M
- `100m` = Maximum 100M per item
- `500m` = Allow up to 500M purchases

**Tips:**
- Protect your purse from expensive mistakes
- Set based on your total purse
- Recommended: 20-30% of total purse

## Skip Filters

Control which items TPM automatically skips or instantly purchases.

### Auto-Skip Low Profit

Skip items below a certain profit threshold.

**Config:**
```javascript
skip: {
    lowProfit: 1000000  // Skip items with < 1M profit
}
```

### Auto-Buy High Profit

Instantly purchase items above a profit threshold without confirmation.

**Config:**
```javascript
skip: {
    profitThreshold: 5000000  // Auto-buy if profit > 5M
}
```

### Skip Cosmetics

Skip cosmetic items that may be hard to sell.

**Config:**
```javascript
skip: {
    cosmetics: true
}
```

### Finder Type Filters

Skip or prioritize flips from specific finder types.

**Config:**
```javascript
skip: {
    finderTypes: ["SNIPER", "USER", "FLIPPER"]
}
```

Common finder types:
- `SNIPER` - Sniper finder flips
- `USER` - User-reported flips
- `FLIPPER` - Flipper flips
- `STONKS` - Stonks finder
- `TFM` - TFM finder

## Relist Filters

Control which items get relisted if they don't sell.

### Do Not Relist Items

Specify items that should never be relisted.

**Config:**
```javascript
doNotRelist: {
    items: [
        "Aspect of the Dragons",
        "Hyperion",
        "Necron's Handle"
    ]
}
```

### Do Not Relist by Profit

Don't relist items below a certain profit.

**Config:**
```javascript
doNotRelist: {
    minProfit: 1000000  // Don't relist if profit < 1M
}
```

### Do Not Relist by Tags

Don't relist items with specific tags.

**Config:**
```javascript
doNotRelist: {
    tags: ["VERY_SPECIAL", "PET", "SKIN"]
}
```

### Do Not Relist by Finder

Don't relist items from certain finders.

**Config:**
```javascript
doNotRelist: {
    finders: ["STONKS", "USER"]
}
```

## Pricing Strategies

### Percent of Target

Set how aggressively to price items based on their value.

**Config:**
```javascript
percentOfTarget: {
    "0-10000000": 0.95,          // List at 95% of target for items under 10M
    "10000000-50000000": 0.97,   // List at 97% for 10M-50M items
    "50000000-999999999": 0.98   // List at 98% for items over 50M
}
```

**Strategies:**
- **Conservative**: 0.90-0.95 (sell faster, lower profit)
- **Balanced**: 0.95-0.97 (good mix)
- **Aggressive**: 0.98-0.99 (higher profit, slower sales)

### List Duration

Set auction duration based on item value.

**Config:**
```javascript
listHours: {
    "0-10000000": 24,        // 24 hours for cheap items
    "10000000-50000000": 48, // 48 hours for medium items
    "50000000-999999999": 72 // 72 hours for expensive items
}
```

### Rounding

Round prices to cleaner numbers.

**Config:**
```javascript
roundTo: 4  // Round to nearest 10,000
```

**Examples:**
- `0` = No rounding (12,345,678)
- `2` = Round to 100s (12,345,700)
- `4` = Round to 10,000s (12,350,000)
- `6` = Round to 1M (12,000,000)

## Advanced Filters

### Angry Coop Prevention

Prevent claiming auctions from coop members.

**Config:**
```javascript
angryCoopPrevention: true
```

### Block Useless Messages

Reduce console spam.

**Config:**
```javascript
blockUselessMessages: true
```

Hides non-essential logs like minor updates and status messages.

### Visit Friend

Enable private island flipping.

**Config:**
```javascript
visitFriend: "FriendUsername"
```

Bot will visit friend's island for special access or private flips.

## Cofl Command Filters

In addition to config file settings, you can adjust filters in-game with Cofl commands.

### Common Cofl Filter Commands

```
/cofl set minprofit 5m
/cofl set minprofitpercent 7
/cofl set maxprice 100m
/cofl set autofast true
/cofl set bedspam true
/cofl blacklist add "Item Name"
/cofl blacklist remove "Item Name"
/cofl whitelist add "Item Name"
```

See the [Cofl Commands](cofl-commands.md) documentation for a complete list.

## Filter Strategy Examples

### Conservative Strategy (New Users)

```javascript
{
    minprofit: "10m",
    minprofitpercent: 10,
    maxprice: "50m",

    percentOfTarget: {
        "0-999999999": 0.93
    },

    skip: {
        lowProfit: 5000000,
        cosmetics: true
    }
}
```

**Pros**: Safe, predictable, lower risk
**Cons**: Fewer flips, lower total profit

### Balanced Strategy (Most Users)

```javascript
{
    minprofit: "5m",
    minprofitpercent: 6,
    maxprice: "100m",

    percentOfTarget: {
        "0-10000000": 0.95,
        "10000000-999999999": 0.97
    },

    skip: {
        lowProfit: 1000000,
        profitThreshold: 10000000
    }
}
```

**Pros**: Good mix of safety and volume
**Cons**: Requires some monitoring

### Aggressive Strategy (Experienced Users)

```javascript
{
    minprofit: "3m",
    minprofitpercent: 4,
    maxprice: "500m",

    percentOfTarget: {
        "0-10000000": 0.97,
        "10000000-999999999": 0.98
    },

    skip: {
        profitThreshold: 15000000
    }
}
```

**Pros**: Maximum profit potential
**Cons**: Higher risk, needs close monitoring

## Testing Your Filters

### Step 1: Start Conservative

Begin with strict filters to ensure safety.

### Step 2: Monitor Results

Track:
- Purchase frequency
- Sale success rate
- Actual profits vs expected
- Items that don't sell

### Step 3: Adjust Gradually

Make small changes based on observations:
- Lower minprofit if too few flips
- Raise minprofit if too many bad flips
- Adjust percentOfTarget based on sale times

### Step 4: Optimize

Fine-tune for your specific goals:
- Volume: Lower thresholds
- Safety: Higher thresholds
- Speed: Lower percentOfTarget
- Profit: Higher percentOfTarget

## Common Filter Issues

### Too Many Flips

**Problem**: Bot buying too many items, purse running low
**Solution**:
- Increase minprofit
- Increase minprofitpercent
- Decrease maxprice
- Add more skip filters

### Too Few Flips

**Problem**: Bot rarely buying anything
**Solution**:
- Decrease minprofit
- Decrease minprofitpercent
- Increase maxprice
- Remove some skip filters

### Items Not Selling

**Problem**: Inventory full of unsold items
**Solution**:
- Lower percentOfTarget
- Adjust listHours
- Add items to doNotRelist
- Review pricing strategy

### Wrong Items Being Purchased

**Problem**: Bot buying items you don't want
**Solution**:
- Add to blacklist: `/cofl blacklist add "Item"`
- Adjust skip filters
- Review config finder filters
- Contact config provider

## Best Practices

1. **Start Strict**: Begin with conservative filters
2. **Monitor Closely**: Watch your bot for first few days
3. **Adjust Slowly**: Make incremental changes
4. **Document Changes**: Note what you changed and results
5. **Test Separately**: Test new filters on one account first
6. **Review Regularly**: Adjust for market changes

## Next Steps

- Learn about [Cofl Commands](cofl-commands.md) for live adjustments
- Read [Config Structure](config-structure.md) for technical details
- Check [Loading Configs](../guides/loading-configs.md) to apply changes
