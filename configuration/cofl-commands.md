# Cofl Commands

This guide covers the most useful Cofl commands for configuring and controlling TPM in-game.

## Overview

Cofl commands allow you to adjust TPM's behavior without editing config files. These commands are entered in Minecraft chat and take effect immediately.

## Basic Syntax

All Cofl commands start with `/cofl`:

```
/cofl [command] [arguments]
```

## Config Management

### Load Config

Load a config from the Cofl panel.

```
/cofl loadconfig [config-name] [config-name]
```

**Examples:**
```
/cofl loadconfig stellaconfig stellaconfig
/cofl loadconfig myconfig myconfig
```

**Note**: The config name is typically repeated twice.

### Check Status

View your current config and settings.

```
/cofl status
```

Shows:
- Active config
- Connection status
- Current filters
- Bot state

## Profit Settings

### Set Minimum Profit

Set the minimum profit required to purchase an item.

```
/cofl set minprofit [amount]
```

**Examples:**
```
/cofl set minprofit 5m
/cofl set minprofit 10m
/cofl set minprofit 2.5m
```

**Units:**
- `k` = thousand (1k = 1,000)
- `m` = million (1m = 1,000,000)
- `b` = billion (1b = 1,000,000,000)

### Set Minimum Profit Percentage

Set the minimum profit percentage required.

```
/cofl set minprofitpercent [number]
```

**Examples:**
```
/cofl set minprofitpercent 5
/cofl set minprofitpercent 10
/cofl set minprofitpercent 7.5
```

### Set Maximum Price

Set the maximum price you'll pay for any item.

```
/cofl set maxprice [amount]
```

**Examples:**
```
/cofl set maxprice 50m
/cofl set maxprice 100m
/cofl set maxprice 500m
```

## Automation Settings

### Auto Fast

Enable/disable automatic fast purchasing.

```
/cofl set autofast [true|false]
```

**Examples:**
```
/cofl set autofast true   # Enable auto-buy
/cofl set autofast false  # Disable auto-buy
```

When enabled, TPM automatically purchases flips without confirmation.

### Bed Spam

Enable/disable bed spamming for faster claiming.

```
/cofl set bedspam [true|false]
```

**Examples:**
```
/cofl set bedspam true
/cofl set bedspam false
```

Bed spamming helps claim auctions faster in competitive situations.

## Blacklist & Whitelist

### Add to Blacklist

Prevent TPM from buying specific items.

```
/cofl blacklist add [item name]
```

**Examples:**
```
/cofl blacklist add "Aspect of the Dragons"
/cofl blacklist add "Necron's Handle"
```

**Note**: Use quotes for items with spaces in the name.

### Remove from Blacklist

Allow TPM to buy a previously blacklisted item.

```
/cofl blacklist remove [item name]
```

**Examples:**
```
/cofl blacklist remove "Aspect of the Dragons"
```

### View Blacklist

See all blacklisted items.

```
/cofl blacklist list
```

### Add to Whitelist

Only allow TPM to buy specific items.

```
/cofl whitelist add [item name]
```

**Examples:**
```
/cofl whitelist add "Hyperion"
```

**Note**: When whitelist has items, ONLY those items will be purchased.

### Clear Whitelist

Remove all items from whitelist.

```
/cofl whitelist clear
```

## Price Checking

### Cofl Lore

Display detailed price information for an item.

```
/cofl lore
```

**How to use:**
1. Type `/cofl lore` in chat
2. Click on different stats to add them
3. View Cofl's price estimates

**Key Stats:**
- **Median**: Best indicator of current price
- **BIN Price**: Recent Buy It Now prices
- **Finder Estimates**: What Cofl thinks item is worth

**Example:**
```
Item: Hyperion
Median: 850M
BIN: 875M
Finder Estimate: 860M
```

Use median for most accurate pricing!

### Price History

View historical prices for an item.

```
/cofl history [item name]
```

**Examples:**
```
/cofl history "Aspect of the End"
```

## Flip Management

### Skip Current Flip

Skip the current flip opportunity.

```
/cofl skip
```

### Stop Flipping

Pause flip notifications temporarily.

```
/cofl stop
```

### Resume Flipping

Resume flip notifications.

```
/cofl start
```

## Premium Features

### Show Premium Info

Display your Cofl subscription details.

```
/cofl premium
```

Shows:
- Subscription tier (Premium/Premium+)
- Expiration date
- Active features

### Flip Delay

Set delay between flip notifications.

```
/cofl set delay [milliseconds]
```

**Examples:**
```
/cofl set delay 250
/cofl set delay 500
```

## Information Commands

### Help

Display available Cofl commands.

```
/cofl help
```

### Version

Show your Cofl mod version.

```
/cofl version
```

### Connection Status

Check connection to Cofl servers.

```
/cofl ping
```

## Advanced Commands

### Macro Settings

Configure macro behavior (requires specific permissions).

```
/cofl macro [setting] [value]
```

### Finder Settings

Adjust finder-specific settings.

```
/cofl finder [finder-name] [setting]
```

### Debug Mode

Enable detailed logging for troubleshooting.

```
/cofl debug [true|false]
```

## Useful Command Combinations

### Quick Setup

Set up basic filters quickly:

```
/cofl set minprofit 5m
/cofl set minprofitpercent 6
/cofl set maxprice 100m
/cofl set autofast true
/cofl set bedspam true
```

### Conservative Mode

Make TPM more selective:

```
/cofl set minprofit 10m
/cofl set minprofitpercent 10
/cofl set maxprice 50m
/cofl set autofast false
```

### Aggressive Mode

Maximize flip volume:

```
/cofl set minprofit 3m
/cofl set minprofitpercent 4
/cofl set maxprice 500m
/cofl set autofast true
```

## Command Tips

### Use Tab Completion

Press Tab while typing a command to see suggestions.

### Commands Take Effect Immediately

No need to restart TPM after using commands.

### Check Your Settings

Use `/cofl status` to verify changes.

### Save Important Settings

Document your optimal settings in case you need to reconfigure.

### Test Before Committing

Try new settings with higher thresholds first, then adjust down.

## Common Command Sequences

### Starting Fresh

```
/cofl loadconfig [name] [name]
/cofl set minprofit 5m
/cofl set minprofitpercent 6
/cofl status
/cofl start
```

### Troubleshooting Bad Flips

```
/cofl stop
/cofl blacklist add "Bad Item Name"
/cofl set minprofit 7m
/cofl status
/cofl start
```

### Checking Item Prices

```
/cofl lore
[Click on item stats]
/cofl history "Item Name"
```

### Adjusting for Market Changes

```
/cofl status
/cofl set minprofitpercent 8
/cofl set maxprice 75m
/cofl status
```

## Command Reference Table

| Command | Purpose | Example |
|---------|---------|---------|
| `/cofl loadconfig` | Load config | `/cofl loadconfig myconfig myconfig` |
| `/cofl status` | Check settings | `/cofl status` |
| `/cofl set minprofit` | Min profit | `/cofl set minprofit 5m` |
| `/cofl set minprofitpercent` | Min profit % | `/cofl set minprofitpercent 6` |
| `/cofl set maxprice` | Max price | `/cofl set maxprice 100m` |
| `/cofl set autofast` | Auto-buy | `/cofl set autofast true` |
| `/cofl set bedspam` | Bed spam | `/cofl set bedspam true` |
| `/cofl blacklist add` | Block item | `/cofl blacklist add "Item"` |
| `/cofl whitelist add` | Allow only | `/cofl whitelist add "Item"` |
| `/cofl lore` | Price info | `/cofl lore` |
| `/cofl start` | Resume flips | `/cofl start` |
| `/cofl stop` | Pause flips | `/cofl stop` |

## Next Steps

- Learn about [Filters and Settings](filters-and-settings.md) for advanced configuration
- Read [Config Structure](config-structure.md) for file-based settings
- Check [Manual Pricing Guide](../guides/manual-pricing.md) to use `/cofl lore` effectively
