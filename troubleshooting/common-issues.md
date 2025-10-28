# Common Issues

Quick solutions for TPM problems.

## Connection Issues

**Can't connect to Hypixel:**
- Delete auth cache: `sudo rm -rf /root/.minecraft/`
- Verify credentials in config.json5
- Check internet: `ping hypixel.net`
- Check Hypixel status: hypixel.net/status

**No Coflnet flips:**
- Check subscription active: `/cofl premium`
- Verify Coflnet online: sky.coflnet.com
- Restart bot: `node index.js`

**Frequent disconnects:**
- Check VPS resources: `free -h` and `top`
- Test network: `ping -c 100 hypixel.net`
- Reduce accounts or increase delay setting

## Bot Not Buying Flips

**No flips coming in:**
- Reload config: `/cofl loadconfig [name] [name]`
- Lower thresholds: `/cofl set minprofit 4.2m` and `/cofl set minprofitpercent 7`
- Check subscription: `/cofl licenses`
- Wait 15-30 min (peak hours: 3-8 PM EST)

**Bot ignoring flips:**
- Check purse has enough coins
- Review skip settings in config.json5

**Bad flips:**
- Adjust filters with `/cofl set` commands
- Report to config provider - see [Handling Bad Flips](../guides/handling-bad-flips.md)

## Authentication Problems

**Can't login:**
- Delete auth cache: `sudo rm -rf /root/.minecraft/`
- Verify credentials in config.json5
- Check if account locked on microsoft.com
- Use correct format: `igns: ["username"]`

## Performance Issues

**Slow/laggy bot:**
- Check resources: `free -h`, `top`, `df -h`
- Restart bot
- Reduce accounts or increase delay
- Upgrade VPS (more RAM/CPU)

**High memory usage:**
- Restart bot daily
- Reduce simultaneous accounts
- Upgrade to 2GB+ RAM for multiple accounts

**Missing flips (too slow):**
- Lower delay in config.json5: `delay: 200`
- Use VPS closer to Hypixel (Chicago recommended)

## Config Issues

**Config won't load:**
- Check spelling: `/cofl loadconfig configmaker-name configname`
- Verify you have access (contact provider)
- Ensure connected to Coflnet

**Syntax errors:**
- Check config.json5 for missing commas, brackets, quotes, colons
- Validate JSON5 syntax

**Settings not applying:**
- Restart bot after config changes
- Ensure file is saved
- Check you're editing correct config.json5 path

## Webhook/Discord Issues

**No notifications:**
- Verify webhook URL in config.json5: `webhook: "https://discord.com/api/webhooks/..."`
- Check webhook has send permissions
- Test: `curl -X POST "webhook-url" -H "Content-Type: application/json" -d '{"content":"Test"}'`
- Check console for errors

**Format issues:**
- Verify placeholder syntax in webhookFormat
- Use valid placeholders: `{itemName}`, `{profit}`, etc.

## VPS Issues

**Can't connect via SSH:**
- Check VPS running in provider dashboard
- Verify IP address correct
- Check port 22 open / UFW status
- Use provider's web console

**Out of space:**
- Check usage: `df -h`
- Clear logs: `rm -rf ~/tpm/logs/*.log`
- Clear cache: `sudo apt clean`
- Upgrade VPS storage

---

## Quick Troubleshooting

When issues occur:
1. Check console/logs for errors (`pm2 logs tpm` or `screen -r tpm`)
2. Verify config.json5 syntax
3. Restart bot: `node index.js`
4. Check internet and service status (Hypixel, Coflnet)
5. Review VPS resources: `free -h`, `top`, `df -h`

**Common errors:**
- `ECONNREFUSED`: Check internet/server status
- `Invalid credentials`: Verify config.json5 credentials
- `Out of memory`: Restart bot or upgrade VPS

## Getting Help

**When asking for help, provide:**
- Exact error messages
- What you were doing
- Config details (remove sensitive info)
- VPS specs and OS
- What you've tried

**Resources:**
- [Installation](../getting-started/installation.md)
- [Config Structure](../configuration/config-structure.md)
- [VPS Setup](../advanced/vps-setup.md)
- TPM Discord server
- Config provider support
