# Cofl Commands

In-game commands to configure TPM. All commands start with `/cofl` and take effect immediately.

## Config Management

**Load config:**
```
/cofl loadconfig [config-maker] [config-name]
```
Example: `/cofl loadconfig stellaconfig stellaconfig`

**Check status:**
```
/cofl status
```
Shows active config, connection, filters, bot state.

## Profit Settings

**Minimum profit:**
```
/cofl set minprofit 5m
```

**Minimum profit percent:**
```
/cofl set minprofitpercent 7
```

**Max price:**
```
/cofl set maxprice 100m
```

## Price Checking

**Check item value:**
```
/cofl lore
```
Then click stats to view:
- **Median** (most accurate)
- BIN price
- Finder estimate
- Volume

## Blacklist/Whitelist

**Blacklist item:**
```
/cofl blacklist add "Item Name"
```

**Whitelist item:**
```
/cofl whitelist add "Item Name"
```

## Control

**Start/stop flipping:**
```
/cofl flip
```

**Connection test:**
```
/cofl ping
```

## Premium

**Check subscription:**
```
/cofl premium
/cofl licenses
```

## Help

**Command list:**
```
/cofl h c 1
```

Use Tab for autocomplete.

---

**See also:** [Filters & Settings](filters-and-settings.md) | [Manual Pricing](../guides/manual-pricing.md)
