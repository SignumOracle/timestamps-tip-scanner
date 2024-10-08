### Scan timestamps for Autopay tips

Steps:
```
python3 -m venv venv
source venv/bin/activate
git clone https://github.com/SignumOracle/timestamps-tip-scanner.git
pip install -e .
```

pre-requisite

```shell
# register address to keyfile
chained add <choose-acct-name> <private-key>
```

First scan oracle for your reports:

Linux:
```shell
scanner scan 369 -a PulsechainAccount --start-block 21610542
```
Windows:
```shell
python /mnt/your/path/to/tenv/bin/scanner scan 369 -a PulsechainAccount --start-block 21610542
```

Then, to claim tips:

- one time tips:

Linux:
```shell
scanner claim-one-time-tip 369 -a PulsechainAccount
```
Windows:
```shell
python /mnt/your/path/to/tenv/bin/scanner claim-one-time-tip 369 -a PulsechainAccount
```

- feed tips:

Linux:
```shell
scanner claim-tip 369 -a PulsechainAccount
```
Windows:
```shell
python /mnt/your/path/to/tenv/bin/scanner claim-tip 369 -a PulsechainAccount
```

###### Supported Networks:

- 369 (pulsechain)

###### API

```
uvicorn timestamps_tip_scanner.api.main:app --reload
```

###### Enpoints

```
/reports/{chain_id}?address={address}&starting_block={starting_block}
/feed_tips/{chain_id}?address={address}
/tips/{chain_id}?address={address}
```

:warning: Disclaimer - Code hasn't been fully tested so use at own risk!
