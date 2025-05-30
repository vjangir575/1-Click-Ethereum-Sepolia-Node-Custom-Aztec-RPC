
## ⚡ Quick Start

```bash
sudo apt-get -qq update && sudo apt-get upgrade -y
sudo apt -qq install curl -y
curl -s https://raw.githubusercontent.com/codedialect/geth-prysm-rpc-node/main/setup_geth_prysm.sh | sudo bash
````

---

## 📁 What It Sets Up

* `/root/ethereum/execution` → Geth data
* `/root/ethereum/consensus` → Prysm data
* `/root/ethereum/jwt.hex` → Shared JWT secret

Docker Services:

* 🔹 Geth (Execution Client)
* 🔹 Prysm (Consensus Client)

---

## 🌐 Aztec RPC Endpoints

| Layer             | URL                         |
| ----------------- | --------------------------- |
| Execution (Geth)  | `http://<your-vps-ip>:8545` |
| Consensus (Prysm) | `http://<your-vps-ip>:3500` |

> इन RPC URLs को आप Aztec CLI या Sequencer configuration में उपयोग कर सकते हैं।

---

## 🔥 Recommended Firewall Rules

### Basic Geth P2P:

```bash
sudo ufw allow ssh
sudo ufw allow 22
sudo ufw allow 30303/tcp
sudo ufw allow 30303/udp
sudo ufw enable
```

### Local RPC Access:

```bash
sudo ufw allow from 127.0.0.1 to any port 8545 proto tcp
sudo ufw allow from 127.0.0.1 to any port 3500 proto tcp
sudo ufw reload
```

### Specific VPS Access:

```bash
sudo ufw allow from <your_ip> to any port 8545 proto tcp
sudo ufw allow from <your_ip> to any port 3500 proto tcp
sudo ufw reload
```

### Remote Access from Any VPS:

```bash
sudo ufw allow 8545/tcp
sudo ufw allow 3500/tcp
sudo ufw reload
```

---

## 📡 Sync Status Checks

### Geth (Execution):

```bash
curl -X POST -H "Content-Type: application/json" \
--data '{"jsonrpc":"2.0","method":"eth_syncing","params":[],"id":1}' \
http://localhost:8545
```

### Prysm (Consensus):

```bash
curl http://localhost:3500/eth/v1/node/syncing
```

---

## 📜 Logs

### Prysm Logs:

```bash
sudo docker logs prysm -fn 100
```

### Geth Logs:

```bash
sudo docker logs geth -fn 100
```

---

## 🤝 Contributing

आपके पास कोई idea, improvement या नया feature है?
Pull requests भेजें और decentralization को आगे बढ़ाएँ!

---

**Made with ❤️ by Billionaire man
```
