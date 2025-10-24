# Loading Configs

This guide explains how to obtain, load, and manage configs for TPM.

## What is a Config?

A config is a set of predefined rules and filters that determine what items TPM will buy and how it will handle them. Configs are created by experienced flippers and optimized for specific strategies.

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
- Examples mentioned by user: "stellaconfig"

## Getting a Config

### Step 1: Obtain Config Access

**For Paid Configs:**
1. Purchase from config provider
2. You'll receive a config name/key
3. Provider will add your account to their config

**For Free Configs:**
1. Find config name in community
2. Verify it's available publicly
3. Note the exact config name

### Step 2: Have Config Name Ready

You'll need the exact config name to load it. Common format:
- `stellaconfig`
- `premiumflips`
- `[creator]config`

## Loading Your Config

### In-Game Method (Recommended)

The primary way to load a config is through Minecraft using Cofl commands.

**Command:**
```
/cofl loadconfig [config-name] [config-name]
```

**Example:**
```
/cofl loadconfig stellaconfig stellaconfig
```

**Note**: You must type the config name twice!

### Step-by-Step Process

1. **Launch Minecraft** and join Hypixel
2. **Join SkyBlock** (any game mode)
3. **Type the command** in chat:
   ```
   /cofl loadconfig [your-config] [your-config]
   ```
4. **Press Enter**
5. **Wait for confirmation** message
6. **Verify** with `/cofl status`

### Confirmation

After loading, you should see:
```
Config loaded successfully!
Active config: [config-name]
```

If you see an error, double-check:
- Config name spelling
- You have access to the config
- Your Cofl subscription is active
- You're connected to Cofl servers

## Configuring After Loading

After loading a config, customize it to your needs:

### Set Profit Thresholds

```
/cofl set minprofit 4.9m
/cofl set minprofitpercent 6
```

Adjust based on:
- Your total purse
- Your risk tolerance
- Market conditions

### Set Price Limits

```
/cofl set maxprice 100m
```

Recommended: 20-30% of your total purse

### Enable Automation

```
/cofl set autofast true
/cofl set bedspam true
```

## Config File Method (TPM Config.js)

You can also set config parameters in your `config.js` file:

```javascript
module.exports = {
    igns: ["YourAccount"],
    session: "your-coflnet-password",

    // Config-specific settings
    delay: 250,
    bedSpam: true,

    percentOfTarget: {
        "0-10000000": 0.95,
        "10000000-999999999": 0.97
    },

    // ... other settings
}
```

**Note**: File settings apply on bot startup, Cofl commands apply immediately.

## Verifying Your Config

### Check Active Config

```
/cofl status
```

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
/cofl loadconfig [new-config] [new-config]
```

**Example:**
```
/cofl loadconfig newconfig newconfig
```

Changes take effect immediately!

### When to Switch

- Different time of day (different markets)
- Different strategy (aggressive vs conservative)
- Testing new configs
- Market conditions change

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
- Sometimes requires reloading: `/cofl loadconfig [name] [name]`

### Manual Updates

For file-based settings:
1. Edit `config.js`
2. Save the file
3. Restart TPM: `node index.js`

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
4. Restart Minecraft if persistent

### Config loads but no flips

**Causes:**
- Profit thresholds too high
- Market is slow
- Config filters too restrictive

**Solutions:**
1. Lower minprofit: `/cofl set minprofit 3m`
2. Lower percentage: `/cofl set minprofitpercent 5`
3. Check `/cofl status` for active filters
4. Wait 10-15 minutes (some periods are slower)

### Wrong items being bought

**Causes:**
- Config not optimized
- Market changed
- Wrong settings

**Solutions:**
1. Adjust filters: `/cofl set minprofit 7m`
2. Blacklist bad items: `/cofl blacklist add "Item"`
3. Contact config provider for update
4. Review your profit thresholds

## Config Best Practices

### 1. Start Conservative

When using a new config:
```
/cofl loadconfig newconfig newconfig
/cofl set minprofit 10m
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
Config: stellaconfig
MinProfit: 5m
MinProfitPercent: 6
MaxPrice: 100m
Works best: 3-8 PM EST
```

### 4. Regular Reviews

- Review weekly
- Adjust for market changes
- Update based on results
- Communicate with config provider

### 5. Backup Configs

Save your `config.js` file regularly:
```bash
cp config.js config.backup.js
```

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
- Join TPM Discord
- Check troubleshooting guide
- Ask in community channels

## Next Steps

Now that your config is loaded:

1. **Configure settings**: Use [Cofl Commands](../configuration/cofl-commands.md)
2. **Learn pricing**: Read [Manual Pricing Guide](manual-pricing.md)
3. **Handle issues**: Check [Handling Bad Flips](handling-bad-flips.md)
4. **Optimize**: Review [Filters and Settings](../configuration/filters-and-settings.md)

## Config Example Workflow

Complete workflow for a new config:

```bash
# 1. In Minecraft
/cofl loadconfig stellaconfig stellaconfig

# 2. Verify loading
/cofl status

# 3. Set thresholds
/cofl set minprofit 5m
/cofl set minprofitpercent 6
/cofl set maxprice 100m

# 4. Enable features
/cofl set autofast true
/cofl set bedspam true

# 5. Start flipping
/cofl start

# 6. Monitor and adjust as needed
```

That's it! Your config is now active and TPM is ready to flip.
