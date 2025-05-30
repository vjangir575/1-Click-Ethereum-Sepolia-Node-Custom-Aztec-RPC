

````markdown
# 🟣 1-Click Ethereum Sepolia Node + Custom Aztec RPC

**Powered by Noderhunterz**

यह repo एक पूरी तरह automated, one-click script प्रदान करता है जिससे आप अपने VPS पर full Ethereum Sepolia node launch कर सकते हैं — वो भी Geth (execution client) और Prysm (consensus client) के साथ। इसमें Aztec नेटवर्क के लिए custom RPC endpoints भी शामिल हैं।

---

## 🚀 Features

- ✅ One-click setup for Geth + Prysm (via Docker)
- 🔐 Secure JWT secret generation
- ⚙️ Full Sepolia node sync
- 🌐 Aztec-compatible RPC endpoints
- 🧰 Auto dependency + Docker installation
- 👨‍💻 Ideal for developers & node runners

---

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

**Made with ❤️ by Noderhunterz**

```

</details>

---

2. अब वापस जाओ GitHub के उस पेज पर (जो तुम्हारी screenshot में है)  
   और जहाँ लिखा है `Enter file contents here`, वहाँ **Paste कर दो** (Ctrl + V)

3. नीचे जाओ और **Commit message** में कुछ लिख दो, जैसे:

```

Added full custom Ethereum + Aztec node README 🚀

```

4. अब **Commit changes...** बटन दबाओ (हरा बटन)

---

अब आपकी repo में ये सुंदर README.md दिखेगा और जो भी आपकी repo खोलेगा, उसे सारी details साफ़-साफ़ समझ आएँगी ✅

कोई दिक्कत आए तो मैं यहीं हूँ bhai!
```
