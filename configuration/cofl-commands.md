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

### Stop/Resume flipping

```
/cofl flip
```

## Premium Features

### Show Premium Info

Display your Cofl subscription details.

```
/cofl licenses
```

Shows:
- Subscription tier (Premium/Premium+)
- Expiration date

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

## Useful Command Combinations

### Quick Setup

Set up basic filters quickly:

```
/cofl set minprofit 5m
/cofl set minprofitpercent 6
```

### Conservative Mode

Make TPM more selective:

```
/cofl set minprofit 10m
/cofl set minprofitpercent 10
```

### Aggressive Mode

Maximize flip volume:

```
/cofl set minprofit 4.2m
/cofl set minprofitpercent 6
```

## Command Tips

### Use Tab Completion

Press Tab while typing a command to see suggestions.

### Commands Take Effect Immediately

No need to restart TPM after using commands.

### Check Your Settings

Use `/cofl status` to verify changes.

## Next Steps

- Learn about [Filters and Settings](filters-and-settings.md) for advanced configuration
- Read [Config Structure](config-structure.md) for file-based settings
- Check [Manual Pricing Guide](../guides/manual-pricing.md) to use `/cofl lore` effectively
