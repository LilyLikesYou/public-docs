# Handling Bad Flips

What to do when TPM buys an item that's hard to sell or not profitable. This guide helps you identify, handle, and prevent bad flips.

## What is a Bad Flip?

A bad flip is when TPM purchases an item that:
- Doesn't sell within 72 hours
- Sells for less profit than expected
- Has inaccurate pricing data
- Low market demand
- Overpaid compared to actual value

## Immediate Actions

When you identify a bad flip, take these steps immediately:

### Step 1: Don't Panic

- Bad flips happen to everyone
- One bad flip won't ruin your profits
- Most items will eventually sell
- Learn from the experience

### Step 2: Check Current Price

Use Cofl lore to verify current market value:

```
/cofl lore
```

Look at:
- **Median price** - True market value
- **Volume** - How many recent sales
- **BIN price** - Recent instant sales

See [Manual Pricing Guide](manual-pricing.md) for detailed instructions.

### Step 3: Determine Item Status

**Item worth more than you paid?**
- Good! You can still profit
- List at median * 0.95
- Be patient

**Item worth same as you paid?**
- Break-even situation
- List at cost
- Won't profit but won't lose money

**Item worth less than you paid?**
- True bad flip
- May need to take a loss
- List competitively to minimize loss

### Step 4: Prevent Future Purchases

Block the item immediately:

```
/cofl blacklist add "[Item Name]"
```

**Examples:**
```
/cofl blacklist add "Aspect of the Dragons"
/cofl blacklist add "Special Pet"
```

This prevents TPM from buying the same bad item again.

## Selling Bad Flips

### Strategy 1: Competitive Pricing

List below current market to ensure sale:

```
Current median: 15M
List at: 14M (93% of median)
```

**When to use:**
- Need coins urgently
- Want to move inventory
- Item has decent demand

### Strategy 2: Patient Approach

List at fair price and wait:

```
Current median: 15M
List at: 14.5M (97% of median)
Duration: 72 hours
```

**When to use:**
- No urgency
- Item has some demand
- Not losing much money

### Strategy 3: Cut Losses

Accept the loss and sell quickly:

```
Paid: 15M
Current value: 12M
List at: 11.5M
```

**When to use:**
- Need purse space
- Item value dropping
- Unlikely to sell at higher price

### Strategy 4: Long-Term Hold

Keep item and wait for market recovery:

**When to use:**
- Have purse space
- Item value may increase
- Can afford to wait weeks/months

**Risks:**
- Ties up coins
- May never recover
- Opportunity cost

## Listing Recommendations

### For Slightly Bad Flips (Small Loss)

```
Starting Bid: Cost - 5%
BIN: Cost
Duration: 48 hours
```

### For Moderately Bad Flips (Medium Loss)

```
Starting Bid: Median * 0.85
BIN: Median * 0.93
Duration: 72 hours
```

### For Very Bad Flips (Large Loss)

```
Starting Bid: Median * 0.75
BIN: Median * 0.85
Duration: 72 hours
```

## Reporting to Config Provider

**Always report bad flips to your config provider!**

This helps them improve the config and prevent future bad purchases.

### What to Include in Report

**Required Information:**
1. Item name
2. Amount paid
3. Current median price (from `/cofl lore`)
4. Sales volume
5. Why it's a bad flip

**Example Report:**
```
Bad flip report:

Item: Aspect of the Dragons
Paid: 18M
Median: 15M (45 sales)
Issue: Bot overpaid by 3M, item has low demand

Please add to config filter or adjust max price.
```

### When to Report

Report if:
- Same item bought multiple times
- Bot consistently overpays
- Item has very low volume (< 5 sales)
- Profit significantly lower than expected
- Item doesn't sell after 72 hours

### How to Report

**Discord:**
- DM config provider
- Post in support channel
- Include screenshot of `/cofl lore`

**In-Game:**
- Note item name
- Document details
- Report when convenient

## Analyzing Why It Happened

Understanding why helps prevent future bad flips.

### Common Causes

#### 1. Outdated Price Data

**Cause:**
- Market price dropped recently
- Cofl data hasn't updated
- Bot using old target price

**Solution:**
- Config provider updates data
- Temporary blacklist item
- Wait for data refresh

#### 2. Low Volume Item

**Cause:**
- Item rarely sells
- Not enough data points
- Price estimates unreliable

**Solution:**
- Blacklist low-volume items
- Adjust config to skip low-volume
- Use higher profit thresholds

#### 3. Special Variant

**Cause:**
- Item has specific attribute
- Bot can't distinguish variants
- Variant worth less than standard

**Solution:**
- Blacklist specific variant
- Config provider adds variant filter
- Manual oversight for that item type

#### 4. Market Crash

**Cause:**
- Supply increased suddenly
- Demand decreased
- Hypixel update changed meta

**Solution:**
- Can't always predict
- Monitor market news
- Adjust filters after crashes
- Take loss and move on

#### 5. Profit Calculation Error

**Cause:**
- Target price incorrect
- Fees not calculated properly
- Profit percentage misleading

**Solution:**
- Report to config provider
- Verify profit calculations
- Use realistic expectations

## Preventing Bad Flips

### 1. Proper Filter Configuration

Set appropriate thresholds:

```
/cofl set minprofit 5m
/cofl set minprofitpercent 6
/cofl set maxprice 100m
```

See [Filters and Settings](../configuration/filters-and-settings.md) for details.

### 2. Maintain Blacklist

Regularly update your blacklist:

```
/cofl blacklist add "Problematic Item"
```

Review and add:
- Items that didn't sell
- Items with low volume
- Items you overpaid for

### 3. Monitor Actively

Check bot regularly:
- Review recent purchases
- Check item values
- Verify listings
- Adjust filters as needed

### 4. Use Quality Configs

- Use reputable config providers
- Keep configs updated
- Pay for quality if needed
- Test configs carefully

### 5. Start Conservative

When testing new configs:

```
/cofl set minprofit 10m
/cofl set minprofitpercent 10
```

Gradually lower thresholds after confirming quality.

## Managing Multiple Bad Flips

If you have several bad flips:

### Step 1: Triage

Categorize items:

**Category A** - Small loss (< 1M)
- List competitively
- Sell quickly

**Category B** - Medium loss (1-5M)
- Price carefully
- Wait up to 1 week

**Category C** - Large loss (> 5M)
- Evaluate carefully
- Consider long-term hold or cut losses

### Step 2: Prioritize Sales

Focus on:
1. Items losing value fast
2. High-value items (free up coins)
3. Items with decent demand

### Step 3: Batch Report

Send comprehensive report to config provider:

```
Bad flips batch report:

1. Item A - paid 18M, median 15M
2. Item B - paid 45M, median 40M
3. Item C - paid 22M, low volume

Please review and update filters.
```

### Step 4: Adjust Strategy

If consistent bad flips:
- Raise profit thresholds
- Reduce max price
- Switch configs
- Pause flipping temporarily

## Learning from Bad Flips

### Keep Records

Document bad flips:

```
Date: [Date]
Item: [Name]
Paid: [Amount]
Sold: [Amount]
Loss: [Amount]
Lesson: [What you learned]
```

### Identify Patterns

Look for:
- Common item types
- Specific finders
- Time of day
- Price ranges

### Adjust Accordingly

Based on patterns:
- Blacklist item types
- Avoid certain finders
- Adjust during certain times
- Change price ranges

## Bad Flip Examples

### Example 1: Minor Bad Flip

```
Item: Shadow Assassin Chestplate
Paid: 12M
Median: 11.5M
Volume: 80 sales

Action:
- Listed at 11.3M
- Sold in 18 hours
- Loss: 700k
- Not significant, monitor item

Result: Acceptable
```

### Example 2: Moderate Bad Flip

```
Item: Special Pet (Rare)
Paid: 35M
Median: 30M
Volume: 12 sales

Action:
- Blacklisted item
- Listed at 29M
- Sold in 3 days
- Loss: 6M
- Reported to config provider

Result: Learning experience
```

### Example 3: Severe Bad Flip

```
Item: Expensive Weapon
Paid: 150M
Median: 120M
Volume: 3 sales

Action:
- Immediately blacklisted
- Reported to provider
- Holding for market recovery
- Temporarily increased min profit

Result: Reevaluating config
```

## When to Switch Configs

Consider switching if:
- 3+ bad flips per day
- Consistent losses
- Config not updated
- Better options available
- Strategy doesn't match goals

## Recovery Tips

### Mental Approach

- Don't let bad flips discourage you
- Everyone has losses
- Focus on overall profit
- Learn and improve

### Financial Recovery

- Review and adjust filters
- Focus on safer flips temporarily
- Rebuild confidence with smaller flips
- Track recovery progress

## Quick Reference

### Immediate Actions Checklist

- [ ] Check current price with `/cofl lore`
- [ ] Blacklist item: `/cofl blacklist add "Item"`
- [ ] List item competitively
- [ ] Report to config provider
- [ ] Document for records
- [ ] Adjust filters if needed

### Reporting Template

```
Item: [Name]
Paid: [Amount]
Median: [Amount]
Volume: [Number]
Issue: [Description]
Request: Please update config filter
```

### Prevention Checklist

- [ ] Proper min profit set
- [ ] Appropriate min profit percent
- [ ] Reasonable max price
- [ ] Active blacklist maintained
- [ ] Regular monitoring
- [ ] Quality config in use

## Next Steps

- Review [Manual Pricing](manual-pricing.md) to price items correctly
- Learn about [Filters and Settings](../configuration/filters-and-settings.md)
- Check [Cofl Commands](../configuration/cofl-commands.md) for adjustments
- Read [Troubleshooting](../troubleshooting/common-issues.md) for more help

## Remember

**Bad flips are part of flipping.** The key is to:
1. Handle them quickly
2. Learn from them
3. Prevent repeats
4. Don't let them discourage you

With proper management, bad flips should be rare and minimal losses!
