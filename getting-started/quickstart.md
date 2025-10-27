# Quickstart Guide

## Requirements
- TPM installed ([Installation](installation.md))
- Coflnet Premium/Premium+ active
- Config (get from [Config Hub](https://discord.gg/cfghub))
- 50M+ coins in purse

## 1. Load Config
In-game:
```
/cofl loadconfig [config-name] [config-name]
```
Example: `/cofl loadconfig stellaconfig stellaconfig`

## 2. Set Thresholds
```
/cofl set minprofit 4.9m           # Min profit per flip
/cofl set minprofitpercent 6       # Min profit margin %
/cofl set maxprice 100m            # Max item price (optional)
```

See all commands: [Cofl Commands](../configuration/cofl-commands.md)

## 3. Start TPM
```bash
node index.js
```

You'll see: Bot connecting → Hypixel → Coflnet WebSocket → Ready

## 4. Monitor
- **Discord webhook**: Notifications for purchases, sales, profits
- **In-game**: Chat notifications, purse balance, AH listings
- **Console**: Flip opportunities, actions, errors

## How It Works
```
Coflnet → TPM evaluates → Buy → List on AH → Relist if needed → Sell → Profit
```

## Tips

**Start Conservative:**
- Use higher minprofit initially
- Monitor first few hours
- Adjust based on results

**Bad Flips:**
1. Note item name
2. Check price: `/cofl lore`
3. Report to config provider

## Common Issues

**No flips?**
- Check subscription active
- Verify config loaded: `/cofl status`
- Lower minprofit if too high

**Disconnecting?**
- Check internet/VPS resources
- Verify account credentials
- Delete auth cache: `sudo rm -rf /root/.minecraft/`

**Items not selling?**
- Config may need adjustment
- Check prices: `/cofl lore`
- Contact config provider

Full troubleshooting: [Common Issues](../troubleshooting/common-issues.md)

## Next Steps
- [Config Structure](../configuration/config-structure.md)
- [Manual Pricing](../guides/manual-pricing.md)
- [Auto-Rotation](../advanced/auto-rotation.md)
- [Multiple Accounts](../advanced/multiple-accounts.md)
