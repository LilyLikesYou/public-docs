# Loading Configs

This guide explains how to obtain, load, and manage configs for TPM.

## What is a Config?

A config is a set of predefined rules and filters that determine what items TPM will buy and how it will handle them. Configs are created by experienced flippers and optimized for the most profitable strategies.

## Types of Configs

### Free Configs

- Available from the community
- Basic filtering and settings
- Good for learning and testing
- May not be as optimized

### Paid Configs

- Created by professional config makers
- Optimized for maximum profit
- Regular updates and support
- Usually include custom filters and strategies

## Getting a Config

### Step 1: Obtain Config Access

**For Paid Configs:**
1. Open in a ticket in [config hub](https://discord.gg/cfghub/) for your chosen config
2. Provide payment via one of their accepted methods (usually crypto, paypal f&f)
3. Provider will add your account to their config
4. Load the config via a SkyCofl command

**For Free Configs:**
1. Find config name in community
2. Verify it's available publicly
3. Note the exact config name

### Step 2: Have Config Name Ready

You'll need the exact config name to load it.

## Loading Your Config

The primary way to load a config is through Minecraft using Cofl commands or via TPM once logged into Cofl.

**Command:**
```
/cofl loadconfig [config-maker] [config-name]
```

If you see an error, double-check:
- Config name spelling
- You have access to the config
- Your Cofl subscription is active
- You're connected to Cofl servers

If none of these work, contact the config provider and ask for help. 

## Configuring After Loading

After loading a config, customize it to your needs:

### Set Profit Thresholds

**Example:**
```
/cofl set minprofit 4.9m 
/cofl set minprofitpercent 7
```

Adjust based on:
- Your total purse
- Your risk tolerance
- Market conditions

  
## TPM config (config.json5)

You can also set config parameters in your `config.json5` file:

```javascript
module.exports = {
    igns: ["YourAccount"],
    session: "your-coflnet-password", // filled automatically 

    // Config-specific settings
    delay: 150,
    bedSpam: false,

    // ... other settings
}
```

The command to modify your TPM config is `nano config.json5`

**Note**: File settings apply on bot startup, Cofl commands apply immediately.

## Verifying Your Config

### Check Active Config

Look for:
- **Active config**: Should show your config name
- **Connection**: Should be "Connected"
- **Filters**: Should show your profit thresholds

### Test with a Flip

1. Wait for a flip notification
2. Check if it matches your expected criteria
3. Verify profit thresholds are working
4. Confirm items match your strategy

## Switching Configs

### Load Different Config

To switch to a different config:

```
/cofl loadconfig [new-config-maker] [new-config]
```

Changes take effect immediately!

## Multiple Accounts

If running TPM on multiple accounts, each can use different configs:

### In config.js

```javascript
// Account 1 uses config A
// Account 2 uses config B
igns: ["Account1", "Account2"]
```

Then load configs separately on each account in-game.

### Best Practices

- Use different configs for different purse sizes
- Test new configs on one account first
- Keep notes on which config works for which account

## Config Updates

### Automatic Updates

Most paid configs update automatically:
- Config creator updates their config
- Changes apply next time you load it
- Sometimes requires reloading: `/cofl loadconfig [config-maker] [name]`

## Common Issues

### "Config not found"

**Causes:**
- Wrong config name
- No access to config
- Config doesn't exist

**Solutions:**
1. Double-check spelling
2. Verify you purchased/have access
3. Contact config provider
4. Try `/cofl status` to see current config

### "Failed to load config"

**Causes:**
- Not connected to Cofl
- Subscription expired
- Server issues

**Solutions:**
1. Check internet connection
2. Verify Cofl subscription: `/cofl premium`
3. Try again in a few minutes
4. Restart TPM if persistent

### Config loads but no flips

**Causes:**
- Profit thresholds too high
- Market is slow (off-peak hours)
- Config filters too restrictive

**Solutions:**
1. Lower minprofit: `/cofl set minprofit 3m`
2. Lower percentage: `/cofl set minprofitpercent 10`
3. Wait 10-15 minutes (some periods are slower)

### Wrong items being bought

**Causes:**
- Config not optimized
- Market changed
- Wrong settings

**Solutions:**
1. Adjust filters: `/cofl set minprofit 7m`
2. Blacklist bad items: Visit https://sky.coflnet.com/
3. Contact config provider for update
4. Review your profit thresholds

## Config Best Practices

### 1. Start Conservative

When using a new config (assuming 500m+ purse): 
```
/cofl loadconfig newconfig newconfig
/cofl set minprofit 4.5m
/cofl set minprofitpercent 10
```

### 2. Monitor Closely

- Watch for first 1-2 hours
- Check what items are purchased
- Verify sale success rate
- Adjust as needed

### 3. Document Your Settings

Keep notes on optimal settings:
```
MinProfit: 4.2m
MinProfitPercent: 8
```

### Report bad flips to the creator of your config.

## Getting Help with Configs

### Config Provider Support

Most paid config providers offer:
- Discord support
- Setup assistance
- Regular updates
- Custom adjustments

Contact them if:
- Config not loading
- Too many bad flips
- Need optimization help
- Questions about settings

### TPM Support

For TPM-specific issues:
- Join TPM Discord (https://discord.gg/n7t8StBCHr)
- Check troubleshooting guide
- Ask in community channels

## Next Steps

Now that your config is loaded:

1. **Configure settings**: Use [Cofl Commands](../configuration/cofl-commands.md)
2. **Learn pricing**: Read [Manual Pricing Guide](manual-pricing.md)
3. **Handle issues**: Check [Handling Bad Flips](handling-bad-flips.md)
4. **Optimize**: Review [Filters and Settings](../configuration/filters-and-settings.md)
