# Manual Pricing

Sometimes TPM buys too many items and you need to manually determine their value and auction them. This guide teaches you how to use Cofl lore and other tools to price items correctly.

## When You Need Manual Pricing

You'll need to manually price items when:
- Bot bought an item but can't auto-list it
- Item failed to sell multiple times
- Market price changed significantly
- Unusual or rare item variation
- Need to verify bot's pricing

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
- Represents true market value
- More stable than other metrics
- What most buyers expect to pay

**Example:**
```
Median: 15.5M
```
This means most items sell around 15.5M coins.

#### BIN (Buy It Now) Price

Recent prices for items sold with "Buy It Now".

**Characteristics:**
- Shows recent instant sales
- Can be inflated
- Less reliable than median
- Good for trend checking

**Example:**
```
BIN: 16.2M
```

**Note**: BIN is often higher than actual value!

#### Finder Estimates

Cofl's algorithm estimate of item worth.

**Characteristics:**
- Based on recent data
- Updates regularly
- Usually accurate
- Only shows up sometimes

**Example:**
```
Finder Estimate: 15.8M
```

#### Volume

Number of recent sales.

**High Volume** (50+ sales):
- More reliable data
- Easier to sell
- Price is stable

**Low Volume** (< 10 sales):
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
Volume: 45 sales
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
List at: Median * 0.95 to Median * 1.00
```

**Example:**
```
Median: 15.5M
List at: 14.7M - 15.5M
```

**For items with low volume:**
```
List at: Median * 0.90 to Median * 0.95
```

More aggressive pricing helps items sell faster.

## Alternative Pricing Methods

### SkyBlock Menu (/ah)

Use the auction house directly.

**Step 1**: Open auction house
```
/ah
```

**Step 2**: Search for your item
- Type item name in search
- Look at active listings

**Step 3**: Check current listings
- What are similar items listed at?
- Are they selling?
- How old are the listings?

**Step 4**: Undercut competition
```
Lowest listing: 16M
Your price: 15.8M (slightly lower)
```

### SkyCrypt / Sky.Shiiyu.Moe

External websites for price checking.

**SkyCrypt**: skycrypt.me
**Sky.Shiiyu**: sky.shiiyu.moe

**How to use:**
1. Search your username
2. View your inventory
3. Check item value estimates

**Note**: These are estimates, not always accurate.

### Cofl Website

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

**Examples:**
- Dragon items
- Popular dungeon gear
- Common accessories

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
- Special abilities

**Strategy:**
1. Check exact pet + level with Cofl lore
2. Use median price
3. Adjust for candy (-5% per candy)
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
- Good for rare items

**Buy It Now (BIN):**
- Instant sale
- Set at target price
- Good for common items

**Recommendation**: Use both
```
Starting Bid: 14M
BIN: 15.5M
```

### Cookies and Fees

**Without Cookie:**
- Listing fee: 0 coins
- Sale fee: 1% of sale price

**With Cookie:**
- Listing fee: 0 coins
- Sale fee: 0% (no fee!)

**Always use cookies if available!**

## Monitoring Your Listings

### Check Regularly

Use in-game menu:
```
/ah
Click "Your Auctions"
```

**Look for:**
- Bids received
- Time remaining
- Comparison to new listings

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

### Mistake 5: Not Using Cookies

**Problem**: Paying 1% fee on every sale
**Solution**: Always use booster cookies!

## Example Pricing Scenarios

### Scenario 1: Common Item

```
Item: Aspect of the End
/cofl lore results:
  Median: 10.5M
  BIN: 11M
  Volume: 120 sales

Decision:
  List at: 10.2M (median * 0.97)
  Duration: 24 hours
  Expected: Sells within 12 hours
```

### Scenario 2: Rare Item

```
Item: Special Pet (Rare Variant)
/cofl lore results:
  Median: 50M
  BIN: 55M
  Volume: 8 sales

Decision:
  List at: 46M (median * 0.92)
  Duration: 72 hours
  Expected: May take 2-3 days to sell
```

### Scenario 3: Market Drop

```
Item: Popular Sword
/cofl lore results:
  Median: 20M (was 25M yesterday)
  BIN: 18M
  Volume: 200 sales

Analysis: Price is dropping!
Decision:
  List at: 18.5M (between BIN and median)
  Duration: 24 hours
  Expected: Sell quickly before more drops
```

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

See [Handling Bad Flips](handling-bad-flips.md) for more details.

## Tips for Successful Manual Pricing

1. **Always use /cofl lore first** - Most reliable method
2. **Median > BIN** - Median is more accurate
3. **Check volume** - More sales = more reliable
4. **List competitively** - 90-95% of median
5. **Use cookies** - Save 1% on every sale
6. **Be patient** - Wait 24 hours before panicking
7. **Monitor regularly** - Check listings daily
8. **Learn from experience** - Note what prices work
9. **Adjust for market** - Prices change over time
10. **Report issues** - Help improve your config

## Quick Reference

### Command Cheat Sheet

```
/cofl lore          # Price checking tool
/ah                 # View auction house
/cofl status        # Check bot status
/cofl blacklist add # Block problematic items
```

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
