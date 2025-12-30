
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
    It will spit out something like this:
  
    rpcauth=ubuebn:63701465552JKCHKJCH81d4ea5AUTHSMUIKNAHAUTHKHFlkfhkjdhfjkdh49bc49708
    Your password:
    sEjkdhPASSXYZPASS-JYisXKJGHXKGXKJH-u3vUM=

   Copy the `rpcauth` output.

3. **Create config file:**
   ```bash
   nano /home/$USER/.soteria/soteria.conf
   ```
  First paste your rpcauth you just generated into the top of the file. You don’t need to include the plain password. At minimum, the config file must contain the rpcauth entry. Other options can remain at defaults if desired. Some of these options are the default behavior.
  
   Here is a example config file to put in:

   ```ini
   #RPC authorization - generate this 
   rpcauth=USERNAME:AUTHCODE

   #Your address to receive any coins - change to yours
   miningaddress=YOURADDRESS

   #add a comment to your node info - PUT IN YOUR wallet address  
   uacomment=YOURWALLET

   #debug - 1 means all
   debug=1

   #use only ipv4 - default is all - ipv4/ipv6/onion
   onlynet=ipv4

   #listen for incoming connections
   listen=1

   #check mempool every 500 tx
   checkmempool=500

   #max memory used ion MB (530 default)
   maxmempool=800

   #specify the most connections you will make;  more = more memory
   maxconnections=256

   #Set database cache size in megabytes (450mb default)
   dbcache=800

   #run as a server & accept RPC commands
   server=1

   #use upnp=1 if you don't have port 8323 open on your router
   upnp=0

  # Create transactions that have enough fees so they are likely to begin confirmation within n blocks (default: 6).
  txconfirmtarget=5
  
  #Warning: Reverting pruning requires re-downloading the entire blockchain. 
  #(default: 0 = disable pruning blocks, 1 = allow manual pruning via RPC, >550 
  #= automatically prune block files to stay under the specified target size in 
  #MiB)
  prune=1
  
  # Connect via a SOCKS5 proxy
  proxy=127.0.0.1:9050
  
  # Bind to given address and always listen on it. Use [host]:port notation for IPv6
  bind=<addr>
  
  # Bind to given address and whitelist peers connecting to it. Use [host]:port notation for IPv6
  whitebind=<addr>

  ##################################################################
  ##            Quick e.g. on addnode vs connect                  ##
  ##  Let's say for instance you use addnode=89.105.213.189:8323  ##
  ##  addnode will connect you to and tell you about the nodes    ##
  ##  connected to 89.105.213.189:8323. In addition it will       ##
  ##  tell the other nodes.                                       ##
  ##  connected to it that you exist so they can connect to you.  ##
  ##  connect will not do the above when you 'connect' to it.     ##
  ##  It will *only* connect you to 89.105.213.189 and no one     ##
  ##  else.                                                       ## 
  ##                                                              ##
  ##  So if you're behind a firewall, or have other problems      ##
  ##  finding nodes, add some using 'addnode'.                    ##
  ##                                                              ##
  ##  If you want to stay private, use 'connect' to only          ##
  ##  connect to "trusted" nodes.                                 ##
  ##                                                              ##
  ##  If you run multiple nodes on a LAN, there's no need         ##
  ##  for all of them to open lots of connections. Instead        ##
  ##  'connect' them all to one node that is port forwarded       ##
  ##  and has lots of connections.                                ##
  ##################################################################
  
  # Use as many addnode= settings as you like to connect to specific peers
  addnode=89.105.213.189:8323  // This is our official node
  
  # Alternatively use as many connect= settings as you like to connect ONLY to specific peers
  connect=89.105.213.189:8323
  
  # Bind to given address to listen for JSON-RPC connections. Use [host]:port notation for IPv6.
  # This option can be specified multiple times (default: bind to all interfaces)
  rpcbind=<addr>
  
  #If no rpcpassword is set, rpc cookie auth is sought. The default `-rpccookiefile` name
  # is .cookie and found in the `-datadir` being used for soteriad. This option is typically used
  # when the server and client are run as the same user.
  #
  # If not, you must set rpcuser and rpcpassword to secure the JSON-RPC api. The first
  # method(DEPRECATED) is to set this pair for the server and client:
  rpcuser=Alalsseys
  rpcpassword=YourStrongPasswordNumber_DO_NOT_USE_THIS_OR_YOU_WILL_GET_ROBBED_385593
  #
  # The second method `rpcauth` can be added to server startup argument. It is set at initialization time
  # using the output from the script in rpcuser/rpcuser.py after providing a username:
  #
  ./rpcuser/rpcuser.py alexandro
  # String to be appended to soteria.conf:
  rpcauth=alexandro:f7efda5c189b999524f151318c0c86$d5b51b3beffbc02b724e5d095828e0bc8b2456e9ac8757ae3211a5d9b16a22ae
  # Your password:
  # DONT_USE_THIS_YOU_WILL_GET_ROBBED_8ak1gI25KFTvjovL3gAM967mies3E=
  #
  # On client-side, you add the normal user/password pair to send commands:
  rpcuser=alexandro
  rpcpassword=DONT_USE_THIS_YOU_WILL_GET_ROBBED_8ak1gI25KFTvjovL3gAM967mies3E=
  #
  # You can even add multiple entries of these to the server conf file, and client can use any of them:
  rpcauth=silent:b2dd077cb54591a2f3139e69a897ac$4e71f08d48b4347cf8eff3815c0e25ae2e9a4340474079f55705f40574f4ec99
  
  # How many seconds soteria will wait for a complete RPC HTTP request.
  # after the HTTP connection is established. 
  rpcclienttimeout=30
  
  rpcauth=soteria:dcaf822caf8d5c5dd3692aca580a1e$9cbfa46bc3d974d31fec0efa0dfcf4287d7c24f3a1509708c702bcf2eb5383eb
  rpcpassword=BC6QSnOEq1e_kK-li8NRrNJboL7LY8u44Cd1NQh_fIc=
  # By default, only RPC connections from localhost are allowed.
  # Specify as many rpcallowip= settings as you like to allow connections from other hosts,
  # either as a single IPv4/IPv6 or with a subnet specification.
  
  # NOTE: opening up the RPC port to hosts outside your local trusted network is NOT RECOMMENDED,
  # because the rpcpassword is transmitted over the network unencrypted.
  rpcallowip=10.1.1.34/255.255.255.0
  rpcallowip=1.2.3.4/24
  rpcallowip=2001:db8:85a3:0:0:8a2e:370:7334/96  // IPv6 always has lower affinity than IPv4 so we recommend IPv4 more to use than IPv6.
  
  # Listen for RPC connections on this TCP port:
  rpcport=7896
  
  # You can use soteria-cli or soteriad to send commands to soteria-cli/soteriad
  # running on another host using this option:
  rpcconnect=127.0.0.1
  
  # Miscellaneous options
  
  # Pre-generate this many public/private key pairs, so wallet backups will be valid for
  # both prior transactions and several dozen future transactions.
  keypool=250
  
  
  # User interface options
  
  # Start Soteria daemon/qt minimized
  min=1
  
  # Minimize to the system tray
  minimizetotray=1
  
  You will need to come back later to put in your wallet address once we have created the account. Now save your config file by CTRL-X & hit enter.
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
  soteria-cli getblockcount                                    #return block count
  soteria-cli getmempoolinfo                                   #returns memory info
  soteria-cli getdifficulty                                    #return difficulty
  soteria-cli getchaintxstats                                  #returns transaction stats
  soteria-cli abandontransaction "txid"                        #cancel a transaction
  soteria-cli pruneblockchain                                  #deletes old blocks for space
  ```
- Wallet info:
  ```bash
  soteria-cli listwallets                                      #lists wallets open
  soteria-cli listaccounts                                     #list accounts under wallet
  soteria-cli getwalletinfo                                    #returns summary wallet info
  soteria-cli getbalance "walletAddress"                       #returns specific wallet balance 
  soteria-cli getunconfirmedbalance                            #returns pending balance
  soteria-cli getaddressesbyaccount "accountName"              #returns SOTER address
  soteria-cli validateaddress "walletAddress"                  #verifies address
  soteria-cli getaccountaddress "accountName"                  #gets a new SOTER address
  soteria-cli backupwallet "destination"                       #makes copy of wallet
  soteria-cli dumpprivkey "walletAddress"                      #retrieves private key
  soteria-cli importprivkey "privkey" ( "label" ) ( rescan )   #import pvt key
  soteria-cli importpubkey "pubkey" ( "label" rescan )         #import pub key
  soteria-cli importaddress "address" ( "label" rescan p2sh )  #import address
  soteria-cli mnemonic "your words"                            #space separated list of 12-words to import
  soteria-cli mnemonicpassphrase "password"                    #secures your 12-word mnemonic word
  soteria-cli getmywords                                       #retrieve your BIP44 words
  soteria-cli encryptwallet "passphrase"                       #encrypts wallet with passphrase
  soteria-cli listaddressgroupings                             #shows accounts with balances
  soteria-cli listassetbalancesbyaddress "address"             #returns assets for wallet
  soteria-cli move "fromaccount" "toaccount" amount            #send between *accounts*
  soteria-cli sendfrom "fromaccount" "toaddress" amount        #send to different wallet
  ```
- Network info:
  ```bash
  soteria-cli getpeerinfo                                      #returns connected peers and stats
  soteria-cli getconnectioncount                               #returns count of peers
  soteria-cli getnettotals                                     #returns data totals
  soteria-cli getnetworkinfo                                   #returns network status
  soteria-cli setnetworkactive "true|false"                    #turns on/off networking
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

