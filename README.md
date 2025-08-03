# Nexus Node Setup Guide

This guide helps you deploy a Nexus node on a VPS (e.g., from https://xorek.cloud).

## ✅ Requirements
- VPS with Ubuntu (the more powerful, the better the farming)
- root access (or sudo privileges)

---

## 🐧 Installing Dependencies (Ubuntu)

```bash
sudo apt update
sudo apt install docker.io -y
sudo systemctl enable docker
sudo systemctl start docker

sudo apt install nano -y
sudo apt install screen -y
```

---

## 📥 Install Nexus CLI

```bash
docker pull nexusxyz/nexus-cli:latest
```

---

## 🔗 Get Your Node ID
1. Go to [https://app.nexus.xyz/](https://app.nexus.xyz/)
2. Open the **Node** tab
3. Copy your **Node ID**

---

## 🚀 Start the Node

```bash
screen -S nexus

# Replace <YOUR_ID> with your actual Node ID
docker run -it --init \
  -v ~/.nexus:/root/.nexus \
  nexusxyz/nexus-cli:latest start --node-id <YOUR_ID>
```

### 📤 Detach the screen session (so it keeps running in the background):
Press `CTRL + A`, then `D`

---

## 🔁 Updating the Node

```bash
# Reattach to the session:
screen -r nexus

# Press Q to stop the running process

# Pull the latest Docker image:
docker pull nexusxyz/nexus-cli:latest

# Restart the client:
docker run -it --init \
  -v ~/.nexus:/root/.nexus \
  nexusxyz/nexus-cli:latest start --node-id <YOUR_ID>
```

---

## 🧠 Useful Commands
- `screen -ls` — list screen sessions
- `screen -r nexus` — reattach to the Nexus session
- `CTRL+A+D` — detach
- `exit` inside session — quit screen

---

## 📄 License

MIT License. Feel free to use, fork, and share.

---

### 💬 Author: [your name or nickname]

A simple guide for deploying and maintaining a Nexus node.

Happy farming! 🚜
