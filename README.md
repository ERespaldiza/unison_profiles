# unison_profiles
Unison profile files to sync files in Debian 12 and MacOS Sonoma.

## Debian 12 profile
Unison fails to connect from Debian to macOS, but the ssh access is correct:
```bash
(otto@192.168.68.52) Password: ************
Last login: Thu Aug 29 10:47:36 yyyy
(base) ?➜  ~
```
The reason is Unison can´t find the executable into MacOS. To solve the problem set the `servercmd` param to the Unison binary path and `sshargs` to `-C`

Configuration file `~/.unison/DebMacSync.prf`

```code
# DebMacSync.prf profile. Debian 12 - Unison preferences
label = Sync Folder /home/otto/DebMacSync
root = /home/otto/DebMacSync
root = ssh://otto@192.168.68.52//Users/otto/DebMacSync
servercmd = /usr/local/bin/unison
sshargs = -C
```

## MacOS Sonoma profile

To connect from MacOs to Debian use the configuration file '~/Library//Application\ Support//Unison/DebMacSync.prf'

```code
# Unison preferences file
root = /Users/otto/DebMacSync
root = ssh://otto@192.168.68.63//home/otto/DebMacSync
```

