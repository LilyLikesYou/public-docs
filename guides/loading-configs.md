# Loading Configs

## What is a Config?

Rules and filters that determine what TPM buys and how it handles items.

**Free configs:** Basic filtering, good for learning
**Paid configs:** Optimized for profit, regular updates, support

## Getting a Config

**Paid:**
1. Open ticket in [Config Hub Discord](https://discord.gg/cfghub)
2. Pay via provider's accepted methods
3. Provider adds you to config
4. Load via `/cofl loadconfig`

**Free:**
1. Find config name in community
2. Verify it's publicly available

## Loading

**In-game:**
```
/cofl loadconfig [config-maker] [config-name]
```

**If error:**
- Check spelling
- Verify you have access
- Confirm Cofl subscription active
- Contact config provider

## Configure Settings

**Set thresholds:**
```
/cofl set minprofit 4.9m
/cofl set minprofitpercent 7
```

Adjust based on purse size, risk tolerance, market conditions.

**Edit config.json5:**
```bash
nano config.json5
```

```javascript
{
    igns: ["YourAccount"],
    session: "your-coflnet-password",
    delay: 150,
    bedSpam: false
}
```

Note: File settings apply on startup, Cofl commands apply immediately.

## Switching Configs

```
/cofl loadconfig [new-maker] [new-config]
```

Changes take effect immediately.

## Common Issues

**"Config not found":**
- Check spelling
- Verify access
- Contact provider

**"Failed to load":**
- Check internet connection
- Verify subscription: `/cofl premium`
- Restart TPM

**No flips:**
- Lower thresholds: `/cofl set minprofit 3m`
- Wait 10-15 minutes
- Check subscription active

**Wrong items bought:**
- Adjust filters
- Blacklist bad items at https://sky.coflnet.com/?refId=odeO2g
- Contact config provider

## Best Practices

**Start conservative (500m+ purse):**
```
/cofl set minprofit 4.5m
/cofl set minprofitpercent 10
```

**Monitor first 1-2 hours:**
- Watch purchases
- Check sale success rate
- Adjust as needed

**Report bad flips to config provider**

---

**See also:** [Config Structure](../configuration/config-structure.md) | [Handling Bad Flips](handling-bad-flips.md) | [Manual Pricing](manual-pricing.md)
