# Quickstart Guide

Get up and running with TPM quickly with this step-by-step guide.

## Before You Begin

Make sure you have:
- TPM installed and configured (see [Installation](installation.md))
- A Coflnet account with Premium or Premium+
- A config to use (free or paid)
- At least 50M coins in your purse

## Step 1: Load Your Config

After purchasing or obtaining a config, load it in-game:

```
/cofl loadconfig [config-name] [config-name]
```

For example, if your config is named "stellaconfig":

```
/cofl loadconfig stellaconfig stellaconfig
```

You should see a confirmation message that the config has been loaded.

## Step 2: Configure Your Settings

Set your minimum profit and profit percentage thresholds using Cofl commands:

### Set Minimum Profit

```
/cofl set minprofit 4.9m
```

This ensures TPM only buys items with at least 4.9 million coins profit. Adjust this based on your strategy.

### Set Minimum Profit Percentage

```
/cofl set minprofitpercent 6
```

This ensures TPM only buys items with at least 6% profit margin. This is especially important if you have a low purse.

### Other Useful Commands

```
/cofl set maxprice 100m        # Maximum price to pay for an item

For more commands, see the [Cofl Commands](../configuration/cofl-commands.md) documentation.

## Step 3: Start TPM

If TPM isn't already running, start it:

```bash
node index.js
```

You should see:
1. Bot connecting to Minecraft
2. Joining Hypixel
3. Connecting to Coflnet WebSocket
4. Ready to receive flips

## Step 4: Monitor Your Bot

### Discord Notifications

If you configured a webhook, you'll receive Discord notifications for:
- Bot startup/shutdown
- Purchases made
- Items sold
- Profits earned
- Errors or issues

### In-Game Monitoring

You can also monitor directly in Minecraft:
- Watch chat for flip notifications
- Check your purse balance
- View your auction house listings

### Console Output

The console will show:
- Flip opportunities received
- Actions taken (buy/skip)
- Errors or warnings
- Connection status

## Step 5: Your First Flips

Once TPM is running:

1. **Wait for flips**: Coflnet will send flip opportunities that match your config
2. **Automatic purchase**: TPM will automatically buy items that meet your criteria
3. **Automatic listing**: Items are automatically listed on the auction house
4. **Automatic relisting**: If items don't sell, they're relisted with adjusted pricing

You don't need to do anything - TPM handles it all!

## Understanding the Workflow

Here's what happens for each flip:

```
Coflnet sends flip → TPM evaluates → Meets criteria? → Buy item → List on AH → Monitor → Relist if needed → Item sells → Profit!
```

## Tips for New Users

### Start Conservative

- Use higher minimum profit thresholds initially
- Monitor closely for the first few hours
- Adjust settings based on results

### Watch for Bad Flips

If TPM buys an item that's hard to sell:
1. Note the item name
2. Check the price using `/cofl lore` (see [Manual Pricing](../guides/manual-pricing.md))
3. Report to your config provider so they can fix it

### Optimize Your Config

After running for a while:
- Review your profit margins
- Adjust min profit and percentage
- Fine-tune item filters
- Consider upgrading to a paid config

## Common First-Time Issues

### No Flips Coming In

**Solutions:**
- Verify your Coflnet subscription is active
- Check your config is loaded: `/cofl status`
- Ensure your minprofit isn't too high
- Verify bot is connected to Coflnet

### Bot Keeps Disconnecting

**Solutions:**
- Check your internet connection
- Verify Minecraft account credentials
- Ensure VPS has enough resources
- Check Hypixel isn't experiencing issues

### Items Not Selling

**Solutions:**
- Your config might need adjustment
- Market conditions may have changed
- Use `/cofl lore` to check current prices
- Contact your config provider

See the [Troubleshooting Guide](../troubleshooting/common-issues.md) for more solutions.

## Next Steps

Now that you're up and running:

1. **Learn about configs**: Read the [Config Structure](../configuration/config-structure.md) guide
2. **Master pricing**: Check out [Manual Pricing](../guides/manual-pricing.md)
3. **Advanced features**: Explore [Auto-Rotation](../advanced/auto-rotation.md) and [Multiple Accounts](../advanced/multiple-accounts.md)
4. **Optimize**: Fine-tune your [Filters and Settings](../configuration/filters-and-settings.md)

## Getting Help

Need assistance?
- Join the TPM Discord server
- Contact your config provider
- Check the [Troubleshooting Guide](../troubleshooting/common-issues.md)
- Review the [full documentation](../README.md)

Happy flipping!
