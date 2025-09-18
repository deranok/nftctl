nftctl
======

This project allows you to:
  - Start/stop nftables. When stopping, all the rules are flushed.
  - Enable/disable rules. You add scripts to the `/etc/nftables/rules.d/` directory then enable or disable rules with `nftctl enrule/disrule $rulename`.
  - List all active rules. When nft is running, you can view the loaded rules.
  - Save all active rule. When nft is running, you can save the active rules to a file.

Usage
=====

Place the `nft` scripts in `/etc/nftables/rules.d/` and make sure they have `.rules` as file extension.

To start nft, you can use 
```bash
nftctl start
```
To stop, use
```bash
nftctl stop
```
To restart, use
```bash
nftctl restart
```
To list all rules:
```bash
nftctl list
```
To list enable a rule:
```bash
nftctl enrule $rulename
nftctl restart
```
To list all rules:
```bash
nftctl disrule $rulename
nftctl restart
```


When you run `nftctl start --confirm` or `nftctl restart --confirm` from a terminal, it will apply your rules and ask you to check your network connection. When your network is still working as desired, you have 20 seconds to press Ctrl+C to leave your rules applied. When the timeout expires, `nftablesctl stop` will be called in order to flush all rules and make your network accessable again. This should prevent you from locking yourself out from your (remote) machine accidently by applying flawed rules.

Credits
=======
This project is a modified copy of [nftables-systemd](https://github.com/alfredkrohmer/nftables-systemd).
