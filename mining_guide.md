
---


# How to Mine SOTER

## Q: Is my GPU supported?
**A:** If it’s a GPU equipped with at least 2 GB of memory, then most likely you can use it to mine.

SOTER is a more core‑oriented than memory‑oriented coin, so keep this in mind when you do overclocking.

---

## Step 1 — Download the Wallet
Download the latest official wallet version for your OS from this link:  
[https://github.com/Soteria-Network/Soteria/releases](https://github.com/Soteria-Network/Soteria/releases)

---

## Step 2 — Get a Wallet Address
Inside the wallet, go to **Request Payment** to generate a new Soteria (SOTER) Wallet Address.

**Note:** It’s not recommended to use a cryptocurrency exchange address for mining.

Before you start mining, you need a wallet address.

I highly recommend you use a wallet that allows you to access your private keys. In crypto, if you don’t own your private keys, then you don’t own your crypto!

**Official QT Wallet** — Windows/Mac/Linux/Aarch64/Arm32.  
You own the private keys. Fast, convenient, and secure.

---

## Step 3 — Choose a Mining Pool
A great way to stack coins faster is to use:

[https://pool.coin-miners.info/](https://pool.coin-miners.info/) — Coin Miners Pool,
SOTER mining with a 1% pool fee for shared mining and 1.5% for solo mining.


### How to Mine with pool.coin-miners.info
- Choose your stratum location from the dropdown list: 
  Europe Stratum, US East Stratum, Singapore Stratum  
- Choose Coin: **Soteria (SOTER)**  
- Your Wallet Address: Enter your wallet address  
- Rig (optional): Your rig name  
- Choose type: Shared or Solo  

---



#### Shared Mining


  ```  
- Europe:  
 ``` 
  -a soterg -o stratum+tcp://eu.coin-miners.info:25100 -u WALLET_ADDRESS.WORKER_NAME -p c=SOTER
  ```
- US East:  
  ```
  -a soterg -o stratum+tcp://us-east.coin-miners.info:25100 -u WALLET_ADDRESS.WORKER_NAME -p c=SOTER
  ```
- Asia:  
  ```
  -a soterg -o stratum+tcp://sg.coin-miners.info:25100 -u WALLET_ADDRESS.WORKER_NAME -p c=SOTER



#### Solo Mining


  ```  
- Europe:  
 ``` 
  -a soterg -o stratum+tcp://eu.coin-miners.info:25100 -u WALLET_ADDRESS.WORKER_NAME -p c=SOTER,m=solo
 ```
- US East:  
  ```
  -a soterg -o stratum+tcp://us-east.coin-miners.info:25100 -u WALLET_ADDRESS.WORKER_NAME -p c=SOTER,m=solo
  ```
- Asia:  
  ```
  -a soterg -o stratum+tcp://sg.coin-miners.info:25100 -u WALLET_ADDRESS.WORKER_NAME -p c=SOTER,m=solo



**Payouts** are made automatically for all balances above 0.1. For the first time you join the pool, you should wait at least 14 hours to get your first payout because the Soteria Network uses a coinbase maturity of 4200 blocks.

---

## Mining Software
- For Linux with support up to CUDA 12.0:  
  [ccminer-soteria-cuda12.8](https://github.com/Soteria-Network/ccminer-soterg/releases/download/v1.0.0/ccminer-soteria-cuda12.8)

- For Windows with support up to CUDA 12.0:  
  [ccminer-soteria-win.zip](https://github.com/Soteria-Network/ccminer-soterg/releases/download/v1.0.0/ccminer-soteria-win.zip)

- For Linux with support for old CPU:  
  [FavoritCoinMiner_All.zip](https://github.com/FavoritCoin/Soteria/releases/download/v2.0.0/FavoritCoinMiner_All.zip)

- For Linux with support for new CPU:  
  [FavoritCoinMiner_linux.zip](https://github.com/FavoritCoin/Soteria/releases/download/v2.0.0/FavoritCoinMiner_linux.zip)

- For HiveOS (custom miner):  
  [FavoritCoinMiner-hive.tar.gz](https://github.com/FavoritCoin/Soteria/releases/download/v2.0.0/FavoritCoinMiner-hive.tar.gz)

For any questions about the pool, visit the official pool owner’s Discord channel:  
[https://discord.gg/szzvMEBNje](https://discord.gg/szzvMEBNje)

---

## Network Stats
- Estimated average time to find a block at full pool speed: **12 seconds**  
- Estimated minimum time to find a block at full pool speed: **9 seconds**  
- **Total supply:** 1.5M coins  

---

## Alternative Solutions
If you find that mining is not profitable for you, don’t worry — we have a solution. Simply mine and hold in your own wallet, and with the next release you will begin receiving rewards automatically every 21 days, at a rate of at least **12–14% APY** (allocated up to 8% from the accumulated block reward to staking).

If you don’t want to mine, deal with technical specifics, invest in a high‑end GPU, keep your PC running 24/7, or face high electricity prices in your region, then the best solution is to buy directly from the exchange:  
[https://flexex.io/market/SOTER_USDT](https://flexex.io/market/SOTER_USDT)  
This is a trustworthy and transparent exchange.

You can also receive at least **2× your donation back every 21 days**, automatically in your wallet, for a period of 3 years if you support our project with a donation (allocated up to 30% from the accumulated block reward to donors), plus a bonus airdrop when we launch multichain tokens.

In the meantime, please provide us with your donated address and your current active SOTER address (by active we mean it should have at least 0.02 SOTER balance in the wallet) so we can send you rewards continuously every 21 days. Later, we are working on automating this procedure so donors can simply insert their donated address and current active SOTER address.

These all solutions are voluntary and entirely up to each person to decide.

---

## Use of Donations
The donations we receive will be used to:
- Launch more nodes  
- Launch a second and third blockchain explorer  
- Provide liquidity on exchanges  
- List on additional exchanges  
- Develop a stronger ecosystem  

---

## Donation Addresses
- **BTC**  
  bc1qkgw84hausumxunjsmfcwlzdndh07ghh6qk58du

- **ETH (Ethereum Network)**  
  0x9faD689248eb635E1BcD1D0588b66f304a52Bb8C

- **USDT (Ethereum Network)**  
  0x9faD689248eb635E1BcD1D0588b66f304a52Bb8C

- **USDT (BSC Network)**  
  0x9faD689248eb635E1BcD1D0588b66f304a52Bb8C

- **BNB (BSC Network)**  
  0x9faD689248eb635E1BcD1D0588b66f304a52Bb8C

- **SOL**  
  6DAbnUaAtRci1cTwTW6W2THMghEuMzZboVpsepPvXgaD

- **Dogecoin**  
  DTrK2KobaiY7UUwxDG9XnJR3KksgTf5dcE
```
