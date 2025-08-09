# Github SSH setup

## Generate key

1. ssh-keygen -t ed25519 -C "gritty.desk3330@fastmail.com"
2. eval "$(ssh-agent -s)"
3. ssh-add ~/.ssh/id_ed25519
4. cat ~/.ssh/id_ed25519.pub

## Add key to Github

1. Go to Settings > SSH and GPG keys
2. Paste key
