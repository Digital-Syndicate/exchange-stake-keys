# Known Exchange Stake and Wallet Keys
For minting services, please set up your engines to triage transactions that come from wallets associated to these wallet/stake keys.  It'll save allot of heartache from your fan base.

Set a daily service to pull down the latest file.

## Example cronjob
1) sudo su
2) crontab -e
3) add "0 */8 * * * su -s /bin/sh yourlogonID -c 'cd /path/youre/using/exchange-stake-keys && /usr/lib/git-core/git pull -q origin main'"

Above job runs every 8 hours

# Example use in python
ignored_utxos = []

import json
with open('./exchange-stake-keys/exchange_stakekeys.json', 'r') as f:
    exchange_wallets = json.loads(f.read())

if sender_addr in exchange_wallets:
    triage_utxo(tx_hash)
    ignored_utxos.append(tx_hash)

def your_mint_action_def():
    ...
    if tx_hash in ignored_utxos:
        i += 1
        continue
    ...

# Adding to this repo
Edit the exchange-stake-keys.json file and add known keys.  The Repo will do a basic json lint check, but please use jsonlint.com to first verify you are saving in a proper json format.
