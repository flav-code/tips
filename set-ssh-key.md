# Authorize your machine to connect with a ssh key

## Generate the key
```
ssh-keygen -t rsa -b 4096
```

## Windows => Linux

Add your key to your linux server from your windows machine
```
$USER_AT_HOST="your-user-name-on-host@hostname"
$PUBKEYPATH="$HOME\.ssh\id_rsa.pub"

$pubKey=(Get-Content "$PUBKEYPATH" | Out-String); ssh "$USER_AT_HOST" "mkdir -p ~/.ssh && chmod 700 ~/.ssh && echo '${pubKey}' >> ~/.ssh/authorized_keys && chmod 600 ~/.ssh/authorized_keys"
```


## Linux => Linux
```
export USER_AT_HOST="your-user-name-on-host@hostname"
export PUBKEYPATH="$HOME/.ssh/id_pub.pub"

ssh-copy-id -i "$PUBKEYPATH" "$USER_AT_HOST"
```
