
# How to setup SSH

======================================
cd ~
mkdir -p .ssh                # -p ensures it doesn't error if .ssh already exists
chmod 700 .ssh               # should be 700, not 600 — directory needs execute permission
cd .ssh/

# Generate a new SSH key (ed25519 is recommended). RSA supported everywhere, ed25519is supported by modern systems (GitHub, OpenSSH ≥ 6.5)
ssh-keygen -t ed25519 -C "your-github-email@example.com"
# When prompted, save as: id_ed25519 (default is fine)

# View the public key to copy to GitHub
cat ~/.ssh/id_ed25519.pub

# Start the SSH agent
eval "$(ssh-agent -s)"

# Add your private key to the agent
ssh-add ~/.ssh/id_ed25519

# Ensure private key has correct permissions
chmod 600 ~/.ssh/id_ed25519

# Test the SSH connection to GitHub
ssh -T git@github.com

=======================================
