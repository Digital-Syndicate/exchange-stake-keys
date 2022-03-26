# Known Exchange Stake and Wallet Keys
For minting services, please set up your engines to triage transactions that come from wallets associated to these wallet/stake keys.  It'll save allot of heartache from your fan base.
Set a daily service to pull down the latest file.

## Example cronjob
1) sudo su
2) crontab -e
3) add "*/1 * * * * su -s /bin/sh nobody -c 'cd /path/youre/using/exchange-stake-keys && /usr/lib/git-core/git pull -q origin main'"
