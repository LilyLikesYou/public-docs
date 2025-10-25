# Manual Pricing

Sometimes TPM buys too many items and you need to manually determine their value and auction them. This guide teaches you how to use Cofl lore and other tools to price items correctly.

## When You Need Manual Pricing

You'll need to manually price items when:
- Bot bought an item but can't auto-list it
- Item failed to sell multiple times
- Market price changed significantly
- Unusual or rare item variation

## Using Cofl Lore

Cofl lore is the primary tool for checking item prices.

### How to Use Cofl Lore

**Step 1**: Type the command in Minecraft chat
```
/cofl lore
```

**Step 2**: Click on different stats to add them

The command will show you an interactive menu where you can click various statistics.

**Step 3**: Review the information

You'll see several important metrics (see below).

### Understanding Cofl Lore Stats

#### Median Price (MOST IMPORTANT)

The median price is the **best indicator** of what an item is currently worth.

**Why Median is Best:**
- Removes outliers (very high/low sales)
- Represents true market value (often, can still be wrong)
- More stable than other metrics
- What most buyers expect to pa

#### BIN (Buy It Now) Price

Recent prices for items sold with "Buy It Now".

**Characteristics:**
- Shows recent instant sales
- Can be inflated
- Less reliable than median
- Good for trend checking

**Note**: BIN is often higher than actual value!

#### Finder Estimates

Cofl's algorithm estimate of item worth.

**Characteristics:**
- Based on recent data
- Updates regularly
- Usually accurate
- Only shows up sometimes

#### Volume

Number of recent sales.

**High Volume** (5+ sales):
- More reliable data
- Easier to sell
- Price is stable

**Low Volume** (< 0.5 sales):
- Less reliable data
- Harder to sell
- Price varies more

### Pricing Decision Process

**Step 1**: Check all metrics
```
/cofl lore
[Click to view stats]

Median: 15.5M
BIN: 16.2M
Finder Estimate: 15.8M
Volume: 4 sales
```

**Step 2**: Prioritize median
- Use median as base price
- Check if volume is sufficient (20+ sales)

**Step 3**: Compare with other metrics
- BIN higher than median? List near median
- BIN lower than median? Market may be dropping
- Finder estimate close? Good confirmation

**Step 4**: Decide listing price

**For items with good volume:**
```
List at: Median * 0.95 to Median
```

**Example:**
```
Median: 15.5M
List at: 14.7M to 15.5M
```

**For items with low volume:**
```
List at: Median * 0.90 to Median * 0.95
```

More aggressive pricing helps items sell faster.

**Note: Median may be inaccurate for determing items which have a very low volume.**

## Cofl Website

Check prices on the Cofl website.

**URL**: sky.coflnet.com

**Steps:**
1. Go to website
2. Search for item name
3. View price history graph
4. Check recent sales

**Useful for:**
- Seeing price trends
- Identifying price drops
- Verifying Cofl lore data

## Pricing Different Item Types

### Common Items (High Volume)

**Characteristics:**
- Sell quickly
- Stable prices
- Easy to value

**Strategy:**
```
List at: Median * 0.95
Duration: 24 hours
```

### Rare Items (Low Volume)

**Characteristics:**
- Sell slowly
- Unstable prices
- Hard to value

**Strategy:**
```
List at: Median * 0.90
Duration: 48-72 hours
```

**Examples:**
- Specific pet variants
- Rare crafting materials
- Special event items

### Reforged/Modified Items

**Additional Considerations:**
- Reforge value
- Enchantments
- Stars/upgrades
- Recombobulated

**Strategy:**
1. Check base item median
2. Add reforge value
3. Add enchantment value
4. Multiply by 0.95

**Example:**
```
Base item: 10M
Withered reforge: +2M
Enchants: +1M
Total: 13M
List at: 12.35M (13M * 0.95)
```

### Pets

Pets are complex to price.

**Factors:**
- Rarity (Common to Legendary)
- Level (especially 100)
- Candy used
- Skins

**Strategy:**
1. Check exact pet + level with Cofl lore
2. Use median price
3. Adjust for candy (-3% per candy)
4. List at 0.92-0.97 of median

## Listing Your Item

### Setting Duration

**For high-demand items:**
```
24 hours - sells quickly
```

**For medium-demand items:**
```
48 hours - normal timeframe
```

**For low-demand items:**
```
72 hours - maximum time
```

### Starting Bid vs BIN

**Starting Bid:**
- Set 10-20% below BIN
- Allows bidding wars
- Good for some items like Runebooks or enchanted Talisman

**Buy It Now (BIN):**
- Instant sale
- Set at target price
- Good for common items

**Always use cookies if available!**

## Monitoring Your Listings

### Adjusting Price

If item not selling:

**After 24 hours:**
- Check current median again
- Lower price by 5%
- Relist

**After 48 hours:**
- Lower price by 10%
- Consider longer duration
- Check if item has value

**After 72 hours:**
- Significant price drop may be needed
- Check if item is sellable
- Contact config provider

## Common Pricing Mistakes

### Mistake 1: Trusting BIN Too Much

**Problem**: BIN prices can be inflated
**Solution**: Always prioritize median

### Mistake 2: Listing Too High

**Problem**: Item never sells
**Solution**: List at 90-95% of median

### Mistake 3: Panicking and Lowering Too Fast

**Problem**: Selling for less than worth
**Solution**: Wait at least 24 hours before adjusting

### Mistake 4: Ignoring Volume

**Problem**: Using unreliable data
**Solution**: Check sales volume, adjust expectations

## When to Report Bad Flips

If you consistently need to manually price items, it may indicate a config issue.

### Report to Config Provider If:

1. Same item keeps being bought
2. Item consistently doesn't sell
3. Bot overpays compared to median
4. Item has low volume (< 5 sales)

**How to Report:**
```
"Config bought [Item Name]
Paid: [Amount]
Median: [Amount]
Can't sell, please fix filter"
```
**Or forward the webhook message to then.**

See [Handling Bad Flips](handling-bad-flips.md) for more details.

## Tips for Successful Manual Pricing

1. **Always use /cofl lore first** - Most reliable method
2. **Median > BIN** - Median is more accurate
3. **Check volume** - More sales = more reliable
4. **List competitively** - 90-95% of median
5. **Be patient** - Wait 24 hours before relisting
6. **Learn from experience** - Note what prices work
7. **Adjust for market** - Prices change over time
8. **Report issues** - Help improve your config

## Quick Reference

### Pricing Formula

```
Common items:  Median * 0.95
Rare items:    Median * 0.90-0.92
Fast sale:     Median * 0.88-0.90
```

### Duration Guide

```
High demand:   24 hours
Medium demand: 48 hours
Low demand:    72 hours
```

## Next Steps

- Learn about [Handling Bad Flips](handling-bad-flips.md)
- Review [Cofl Commands](../configuration/cofl-commands.md)
- Understand [Filters and Settings](../configuration/filters-and-settings.md)
