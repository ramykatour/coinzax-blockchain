# COINZAX Blockchain

Welcome to the official repository of **COINZAX** — a powerful and scalable Ethereum-based blockchain designed to support decentralized applications (dApps), transactions, and more.

---

## 🛠️ **Table of Contents**

- [Introduction](#introduction)
- [Key Features](#key-features)
- [Setup](#setup)
- [Deployment](#deployment)
- [Network Configuration](#network-configuration)
- [API Documentation](#api-documentation)
- [GitHub Repository](#github-repository)
- [FAQ](#faq)
- [License](#license)

---

## 📌 **Introduction**

COINZAX is a customized Ethereum-based blockchain designed for high-performance and scalability. It features an easy-to-use architecture, ensuring a secure and reliable environment for decentralized applications. This blockchain supports native transactions and smart contracts, built on the **COINZAX** token (symbol: ZAX).

---

## ⚡ **Key Features**

- **Ethereum-based**: Built on Ethereum’s robust architecture.
- **Custom Token**: Supports the COINZAX (ZAX) token.
- **Mining**: Supports Proof of Work (PoW) consensus with mining capability.
- **Scalable**: Optimized for high-performance transaction handling.
- **Private Network**: Can be customized and deployed as a private blockchain.

---

## 🖥️ **Setup**

To set up the COINZAX blockchain, follow the steps below:

1. **Clone the repository**:
    ```bash
    git clone https://github.com/ramykatour/coinzax.git
    cd coinzax
    ```

2. **Install Dependencies**:
    Ensure you have the necessary dependencies installed:
    ```bash
    sudo apt update
    sudo apt install -y geth
    ```

3. **Configure the Geth Node**:
    - Set up a private Ethereum network with custom configurations.
    - Use `geth` to initialize the blockchain with a specified genesis block.

    Example Geth command to start the node:
    ```bash
    geth --networkid 1310 --datadir /path/to/data --http --http.addr 0.0.0.0 --http.port 8545 --http.api web3,eth,net,debug,miner --mine --miner.threads 1
    ```

4. **Start the Geth Node**:
    Run the following to start the blockchain and begin mining:
    ```bash
    nohup geth --networkid 1310 --datadir /path/to/data --http --http.addr 0.0.0.0 --http.port 8545 --http.api web3,eth,net,debug,miner --mine --miner.threads 1 &
    ```

---

## 🚀 **Deployment**

Once the Geth node is running, you can deploy your dApps or interact with the blockchain through the RPC endpoint. You can configure the Nginx server to forward traffic to the blockchain:

1. **Set up Nginx as a reverse proxy** for your RPC endpoint:
    ```nginx
    server {
        listen 443 ssl;
        server_name rpc.coinzax.com;

        ssl_certificate /etc/letsencrypt/live/rpc.coinzax.com/fullchain.pem;
        ssl_certificate_key /etc/letsencrypt/live/rpc.coinzax.com/privkey.pem;
        include /etc/letsencrypt/options-ssl-nginx.conf;
        ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem;

        location / {
            proxy_pass http://localhost:8545;
            proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        }
    }
    ```

## 🌍 **Network Configuration**

- **Network ID**: 1310
- **RPC URL**: [https://rpc.coinzax.com](https://rpc.coinzax.com)
- **Explorer URL**: [https://scan.coinzax.com](https://scan.coinzax.com)

You can connect to the **COINZAX** network using your Ethereum wallet by adding the network via MetaMask:

```javascript
{
  "chainId": "0x51E",  // 1310 in hex
  "chainName": "COINZAX",
  "rpcUrls": ["https://rpc.coinzax.com"],
  "nativeCurrency": {
    "name": "COINZAX",
    "symbol": "ZAX",
    "decimals": 18
  },
  "blockExplorerUrls": ["https://scan.coinzax.com"]
}

```

## 📜 **API Documentation**

The COINZAX blockchain exposes a JSON-RPC API, accessible through the RPC endpoint [https://rpc.coinzax.com](https://rpc.coinzax.com). The following methods are available:

### `eth_blockNumber`
Returns the number of the most recent block.

### `eth_getBlockByNumber`
Returns information about a block by block number.

### `eth_getTransactionByHash`
Returns the information about a transaction requested by transaction hash.

### `eth_getBalance`
Returns the balance of the account of the given address.

For more detailed API documentation, please refer to the [Ethereum JSON-RPC documentation](https://eth.wiki/json-rpc/API).

---

## 📂 **GitHub Repository**

You can find the source code for the COINZAX blockchain on GitHub:

- **GitHub Repo**: [https://github.com/ramykatour/coinzax](https://github.com/ramykatour/coinzax-blockchain.git)

Feel free to contribute, raise issues, or submit pull requests to improve the COINZAX blockchain.

---

## ❓ **FAQ**

### 1. **What is COINZAX?**
COINZAX is a customized Ethereum-based blockchain designed to support high-performance decentralized applications (dApps) and transactions. It features its native token, **ZAX**, and is built to offer scalable solutions.

### 2. **How do I interact with the COINZAX blockchain?**
You can interact with the COINZAX blockchain through its RPC endpoint [https://rpc.coinzax.com](https://rpc.coinzax.com) using Web3.js or by connecting your Ethereum wallet (e.g., MetaMask).

### 3. **How do I mine COINZAX?**
You can mine COINZAX using Geth on the COINZAX private network. For more information, see the [Setup](#setup) section.

### 4. **Where can I see transaction details?**
You can explore the COINZAX blockchain using the [COINZAX Blockchain Explorer](https://scan.coinzax.com).
