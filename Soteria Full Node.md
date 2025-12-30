
---

# Soteria Network Full Node Setup Guide (Ubuntu/Debian CLI)

This guide shows you how to get a basic **Soteria Network Full Node** up and running on Ubuntu/Debian via CLI.

---

## 📦 Requirements

- A computer (preferably well‑performing).
- HDD or SSD, at least 20GB free
- **Debian 13** or **Xubuntu/Ubuntu 24 & 25** for the latest Soteria daemon.  
- **For older Linux versions**, use the **Legacy or old daemon** to avoid `glibc` incompatibility.
- Access via command line or SSH.

---

## 🔧 Install Dependencies

```bash
sudo apt update
sudo apt install -y git unzip
```

---

## 📥 Download Binaries

Get the binaries from the [official GitHub release](https://github.com/Soteria-Network/Soteria/releases/tag/v1.1.0).

- **Debian 13 / Ubuntu 24 or 25:**
  ```bash
  wget https://github.com/Soteria-Network/Soteria/releases/download/v1.1.0/soteria-daemon-linux64.zip -O soteria-daemon-linux64.zip
  unzip soteria-daemon-linux64.zip
  ```

- **Other Linux versions:**
  ```bash
  wget https://github.com/Soteria-Network/Soteria/releases/download/v1.1.0/soteria-daemon-oldlinux64.zip -O soteria-daemon-oldlinux64.zip
  unzip soteria-daemon-oldlinux64.zip
  ```

Install globally:

```bash
sudo cp soteriad /usr/local/bin/
sudo cp soteria-cli /usr/local/bin/
```

---

## ⚙️ Configure the Node

1. **Generate RPC authentication:**
   ```bash
   python3 ~/rpcuser/rpcuser.py $USER
   ```
   Copy the `rpcauth` output.

2. **Create config file:**
   ```bash
   nano /home/$USER/.soteria/soteria.conf
   ```

   Minimal example:

   ```ini
   rpcauth=USERNAME:AUTHCODE
   miningaddress=YOURADDRESS
   uacomment=YOURWALLET
   listen=1
   server=1
   upnp=0
   prune=1
   ```

---

## 🚀 Start the Node

```bash
soteriad -upgradewallet -debug=1 -printtoconsole
```

Stop with:

```bash
soteria-cli stop
```

First sync may take ~40 minutes.

---

## 🔧 Create a Systemd Service

Create service file:

```bash
sudo nano /etc/systemd/system/soterianode.service
```

Paste:

```ini
[Unit]
Description=Soteria daemon
After=network-online.target

[Service]
User=YOURUSER
Group=YOURUSER
Type=simple
PIDFile=/home/YOURUSER/.soteria/soteria.pid
ExecStart=/usr/local/bin/soteriad
Restart=always
TimeoutStopSec=60s
TimeoutStartSec=20s
StartLimitInterval=60
StartLimitBurst=5

[Install]
WantedBy=multi-user.target
```

Enable and start:

```bash
sudo systemctl daemon-reload
sudo systemctl enable soterianode
sudo systemctl start soterianode
sudo systemctl status soterianode
```

---

## 🖥️ Interacting with `soteriad`

Use `soteria-cli`:

- Blockchain info:
  ```bash
  soteria-cli getblockchaininfo
  soteria-cli getblockcount               #return block count
  soteria-cli getmempoolinfo              #returns memory info
  soteria-cli getdifficulty               #return difficulty
  soteria-cli getchaintxstats             #returns transaction stats
  soteria-cli abandontransaction "txid"   #cancel a transaction
  soteria-cli pruneblockchain             #deletes old blocks for space
  ```
- Wallet info:
  ```bash
  soteria-cli getwalletinfo
  soteria-cli getbalance "walletAddress"
  ```
- Network info:
  ```bash
  soteria-cli getpeerinfo
  soteria-cli getconnectioncount
  ```

---

## 🌐 Network Setup

- Forward port **8323** to your node.  
- If you cannot open the port manually, set:
  ```ini
  upnp=1
  ```
  in `soteria.conf`.

Check your node on the [Explorer](https://explorer.soteria-network.online/network) by searching your external IP. It may take 40–60 minutes to appear.

---

## 🎉 Conclusion

You now have a basic Soteria Network Node running! Keep it online as much as possible to maintain uptime percentage.

---

## 📬 Support

If you find errors or something doesn’t work, reach out on **Telegram, Discord, or Twitter**.  

---

