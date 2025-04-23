# Nexus zkVM Prover v3 Installation Guide (Ubuntu 22)

This guide explains how to install the zkVM prover node for Nexus on Ubuntu 22.04.

## 1. Create Your Node in Nexus

1. Go to [https://app.nexus.xyz/](https://app.nexus.xyz/) and sign in with your email or wallet.
2. Click `Nodes`.
3. Click `+ ADD NODE` → `Add cli node`.
4. Copy your **Node ID** and save it.

## 2. Prepare Your VPS

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install build-essential pkg-config libssl-dev git-all -y
sudo apt install -y protobuf-compiler
sudo apt install cargo
sudo apt install unzip
sudo apt install screen
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source $HOME/.cargo/env
echo 'export PATH="$HOME/.cargo/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
rustup update
sudo apt remove -y protobuf-compiler
curl -LO https://github.com/protocolbuffers/protobuf/releases/download/v25.2/protoc-25.2-linux-x86_64.zip
unzip protoc-25.2-linux-x86_64.zip -d $HOME/.local
export PATH="$HOME/.local/bin:$PATH"
protoc --version
```
*You should see `libprotoc 25.2` or higher.*

## 3. Launch the Node

Open a screen session:
```bash
screen -S nexus
```

Install the Nexus CLI and start the node:
```bash
curl https://cli.nexus.xyz/ | sh
```
*Press `Y` and `ENTER` if prompted.*

When asked:
- Type `2` (for prover node) and press `ENTER`.
- Enter your **Node ID** from the Nexus website and press `ENTER`.

---

**Good luck and happy node running!**
