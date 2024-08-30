# unison_profiles
Unison profile files to sync files between Debian 12 and MacOS Sonoma.

> **Note**: Profile folder and filenames can be completely different, choose yours.

## Debian 12 setup
Unison fails to connect from Debian to macOS, but the `ssh` access is correct:
```bash
$ ssh otto@192.168.68.52
(otto@192.168.68.52) Password: ************
Last login: Thu Aug 29 10:47:36 yyyy
(base) ?➜  ~
```
The reason is Unison can´t find the executable into MacOS. To solve the problem set the `servercmd` param to the Unison binary path and `sshargs` to `-C`. The configuration file is located at `~/.unison/DebMacSync.prf`

* Username: `otto`
* MacOs IP address: 192.168.68.52
* Recursively shared folder: `~/DebMacSync`

### Debian 12 DebMacSync.prf profile file

```code
label = Sync Folder /home/otto/DebMacSync
root = /home/otto/DebMacSync
root = ssh://otto@192.168.68.52//Users/otto/DebMacSync
servercmd = /usr/local/bin/unison
sshargs = -C
```

## MacOS Sonoma setup

To connect from MacOs to Debian use the configuration file at `~/Library//Application\ Support//Unison/DebMacSync.prf`

* Username: `otto`
* MacOs IP address: 192.168.68.63
* Recursively shared folder: `~/DebMacSync`

### MacOS Sonoma DebMacSync.prf profile file

```code
# Unison preferences file
root = /Users/otto/DebMacSync
root = ssh://otto@192.168.68.63//home/otto/DebMacSync
```

