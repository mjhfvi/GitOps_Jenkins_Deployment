# GitHub SSH Certificate

## Create Certificate for GitHub Access

ssh-keygen -t ed25519 -C "GitHub SSH Login Key ed25519 with Password" -f github_ssh_login_key_ed25519 -N PASSWORD

## Add SSH Certificate to GitHub Using GitHub cli

gh repo deploy-key add github_ssh_login_key_ed25519.pub -t 'GitHub SSH Login Key ed25519 with Password' --repo 'mjhfvi/GitOpsAutomation'
gh repo deploy-key list -R 'mjhfvi/GitOpsAutomation'
gh repo deploy-key delete 'KEY_ID' -R 'mjhfvi/GitOpsAutomation'

## Create GPG Certificate to GitHub Using GitHub cli

gpg --batch --full-generate-key <<EOF
Key-Type: EDDSA
Key-Curve: ed25519
Subkey-Type: RSA
Subkey-Length: 4096
Name-Real: Tzahi Cohen
Name-Comment: GitHub SSH Login Key ed25519 with Password
Name-Email: mjhfvi@gmail.com
Expire-Date: 1y
Passphrase: PASSWORD
%commit
EOF

## Add GPG Certificate to GitHub Using GitHub cli

export GPG_KEY_ID=$(gpg --with-colons --fingerprint --list-keys "github" | grep -A 1 "pub:" | grep -Eo "[A-F0-9]{40}")
gpg --armor --export $GPG_KEY_ID > pgp_key.key
gh gpg-key add pgp_key.key -t 'GitHub GPG Key ECC with Password'
gh gpg-key list

# Delete Keys

gh gpg-key delete E9FECD323F7D3C11

gh ssh-key add github_ssh_login_key_ed25519.pub -t 'GitHub SSH Login Key ed25519 with Password'
gh ssh-key list
gh ssh-key delete 'KEY_ID'
