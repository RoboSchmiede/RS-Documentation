# Things you should not do on [Linux](https://github.com/torvalds/linux) terminal

Some times I do stupid things only to fix some other stupidities.
Here some examples of unpleasant moves:

## rename /lib64
```
sudo mv /lib64 /li64
```
As a result you can not execute a command anymore.
When rebooting you will end up in kernel panic.
Confirmed 'working' on Debian Bookworm.

### Fix:
Boot from another drive and rename the directory(link) back to /lib64.
```
sudo mv /li64 /lib64
```

## a function called recursively
```
:(){ :|:& };:
```
can crash your linux system as non root user

 
## delete all
```
rm * -rf
```
Using command history allot, I (as root) accidental ended up removing `*` in `/`.
### Prevention:
Do not use `rm * -rf`.
Do not use `root` user whenever possible.
