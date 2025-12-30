
---
# This file is licensed under the MIT License (MIT) available on
# http://opensource.org/licenses/MIT.

Run a Soteria Node on Ubuntu CLI!

This guide will show you how to get a basic Soteria Node up and running and churning that blockchain!

If you wanted to build a Soteria node to run the blockchain via CLI and these are the methods I used. So hopefully this will help someone in getting it running on Ubuntu Linux.

Starting Out

First you need

    A computer, ideally a well performing one.
    HDD or SSD
    Debian 13 or Xubuntu/Ubuntu 26.04 for Soteria daemon while for any other Linux lower versions stick with Soteria daemon for Old Linux or Legacy Linux to avoid the problem with glibc version incompatability.
    Be in front of it on command line or SSH into your Debian/Ubuntu computer.

I will be listing the linux commands you need to enter in order. We will be building/installing into your user folder under your current user. We will likely need to install Git.

sudo apt install git
sudo apt install unzip

Once you are running Debian/Ubuntu & have git and unzip, we need to get the binary for the Soteria Network node from the official GitHub page!
https://github.com/Soteria-Network/Soteria/releases/tag/v1.1.0

For Debian 13/Ubuntu 24 or 25 run:

wget https://github.com/Soteria-Network/Soteria/releases/download/v1.1.0/soteria-daemon-linux64.zip -O soteria-daemon-linux64.zip 

For other Linux versions run:

wget https://github.com/Soteria-Network/Soteria/releases/download/v1.1.0/soteria-daemon-oldlinux64.zip -O soteria-daemon-oldlinux64.zip 

After downloading the release, extract it and run the following to install into /usr/local/bin so it can be executed globally:  

# For Debian 13 / Ubuntu 24 or 25
unzip soteria-daemon-linux64.zip

# For other Linux versions
unzip soteria-daemon-oldlinux64.zip

sudo cp soteriad /usr/local/bin/
sudo cp soteria-cli /usr/local/bin/

If all went good, you now have Soteria Network Node CLI installed on your computer. Now let us go through the process of configuring it to run for your setup.

Configuring the Node

Here are some commands to configure the node, start the node, and monitor the node. All your config settings can be done via command line or as a config file like most programs. I like to use a config file cause I think it is easier to visualize the options.

First, create a data folder in your home directory. Then run the Python script to generate RPC authentication. Replace the "USERNAME" with your user you are using if there are issues. We will use this in the next step.

python3 ~/rpcuser/rpcuser.py $USER

It will spit out something like this:

rpcauth=ubuebn:63701465552JKCHKJCH81d4ea5AUTHSMUIKNAHAUTHKHFlkfhkjdhfjkdh49bc49708
Your password:
sEjkdhPASSXYZPASS-JYisXKJGHXKGXKJH-u3vUM=

Copy your rpcauth or write it down, we will use it in our config.

Now let us create our config file.

nano /home/$USER/.soteria/soteria.conf

First paste your rpcauth you just generated into the top of the file. You don’t need to include the plain password. At minimum, the config file must contain the rpcauth entry. Other options can remain at defaults if desired. Some of these options are the default behavior.

Here is a example config file to put in:

#RPC authorization - generate this 
rpcauth=ubuebn:SUKALALALALAyourauthcodeXALAL

#Your address to receive any tokens - change to yours
miningaddress=YOURADDRESS

#add a comment to your node info - PUT IN YOUR wallet address
uacomment=YOURWALLET

######################################

#debug - 1 means all
#debug=1

#use only ipv4 - default is all - ipv4/ipv6/onion
#onlynet=ipv4

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
#proxy=127.0.0.1:9050

# Bind to given address and always listen on it. Use [host]:port notation for IPv6
#bind=<addr>

# Bind to given address and whitelist peers connecting to it. Use [host]:port notation for IPv6
#whitebind=<addr>

##############################################################
##            Quick e.g. on addnode vs connect            ##
##  Let's say for instance you use addnode=89.105.213.189:8323          ##
##  addnode will connect you to and tell you about the      ##
##    nodes connected to 89.105.213.189:8323.  In addition it will tell ##
##    the other nodes connected to it that you exist so     ##
##    they can connect to you.                              ##
##  connect will not do the above when you 'connect' to it. ##
##    It will *only* connect you to 89.105.213.189 and no one else.##
##                                                          ##
##  So if you're behind a firewall, or have other problems  ##
##  finding nodes, add some using 'addnode'.                ##
##                                                          ##
##  If you want to stay private, use 'connect' to only      ##
##  connect to "trusted" nodes.                             ##
##                                                          ##
##  If you run multiple nodes on a LAN, there's no need for ##
##  all of them to open lots of connections.  Instead       ##
##  'connect' them all to one node that is port forwarded   ##
##  and has lots of connections.                            ##
##############################################################

# Use as many addnode= settings as you like to connect to specific peers
#addnode=89.105.213.189:8323  // This is our official node

# Alternatively use as many connect= settings as you like to connect ONLY to specific peers
#connect=89.105.213.189:8323

# Bind to given address to listen for JSON-RPC connections. Use [host]:port notation for IPv6.
# This option can be specified multiple times (default: bind to all interfaces)
#rpcbind=<addr>

#If no rpcpassword is set, rpc cookie auth is sought. The default `-rpccookiefile` name
# is .cookie and found in the `-datadir` being used for soteriad. This option is typically used
# when the server and client are run as the same user.
#
# If not, you must set rpcuser and rpcpassword to secure the JSON-RPC api. The first
# method(DEPRECATED) is to set this pair for the server and client:
#rpcuser=Alalsseys
#rpcpassword=YourStrongPasswordNumber_DO_NOT_USE_THIS_OR_YOU_WILL_GET_ROBBED_385593
#
# The second method `rpcauth` can be added to server startup argument. It is set at initialization time
# using the output from the script in rpcuser/rpcuser.py after providing a username:
#
# ./rpcuser/rpcuser.py alexandro
# String to be appended to soteria.conf:
# rpcauth=alexandro:f7efda5c189b999524f151318c0c86$d5b51b3beffbc02b724e5d095828e0bc8b2456e9ac8757ae3211a5d9b16a22ae
# Your password:
# DONT_USE_THIS_YOU_WILL_GET_ROBBED_8ak1gI25KFTvjovL3gAM967mies3E=
#
# On client-side, you add the normal user/password pair to send commands:
#rpcuser=alexandro
#rpcpassword=DONT_USE_THIS_YOU_WILL_GET_ROBBED_8ak1gI25KFTvjovL3gAM967mies3E=
#
# You can even add multiple entries of these to the server conf file, and client can use any of them:
# rpcauth=silent:b2dd077cb54591a2f3139e69a897ac$4e71f08d48b4347cf8eff3815c0e25ae2e9a4340474079f55705f40574f4ec99

# How many seconds soteria will wait for a complete RPC HTTP request.
# after the HTTP connection is established. 
#rpcclienttimeout=30

#rpcauth=soteria:dcaf822caf8d5c5dd3692aca580a1e$9cbfa46bc3d974d31fec0efa0dfcf4287d7c24f3a1509708c702bcf2eb5383eb
#rpcpassword=BC6QSnOEq1e_kK-li8NRrNJboL7LY8u44Cd1NQh_fIc=
# By default, only RPC connections from localhost are allowed.
# Specify as many rpcallowip= settings as you like to allow connections from other hosts,
# either as a single IPv4/IPv6 or with a subnet specification.

# NOTE: opening up the RPC port to hosts outside your local trusted network is NOT RECOMMENDED,
# because the rpcpassword is transmitted over the network unencrypted.
#rpcallowip=10.1.1.34/255.255.255.0
#rpcallowip=1.2.3.4/24
#rpcallowip=2001:db8:85a3:0:0:8a2e:370:7334/96  // IPv6 always has lower affinity than IPv4 so we recommend IPv4 more to use than IPv6.

# Listen for RPC connections on this TCP port:
#rpcport=7896

# You can use soteria-cli or soteriad to send commands to soteria-cli/soteriad
# running on another host using this option:
#rpcconnect=127.0.0.1

# Miscellaneous options

# Pre-generate this many public/private key pairs, so wallet backups will be valid for
# both prior transactions and several dozen future transactions.
#keypool=250


# User interface options

# Start Soteria daemon/qt minimized
#min=1

# Minimize to the system tray
#minimizetotray=1

You will need to come back later to put in your wallet address once we have created the account. Now save your config file by CTRL-X & hit enter.

Starting Soteria Newtork Node

Let us fire it up! Run the following command that launches soteriad, the program name of our node:

soteriad -upgradewallet -debug=1 -printtoconsole

This will start our Soteria network node and start connecting to other peers! It will be spitting out a ton of debug info and printing to the screen so you can make sure it is running. We just wanted to make sure it starts so we know it worked before proceeding. Let it run for a minute or so & then to stop soteriad, either hit CTRL-C on the keyboard, or preferred, in a different command terminal type "soteria-cli stop".

The first full run may take around 40 minutes to sync the blockchain and generate necessary files. It is also creating all our other files we need to run under the .soteria directory. Lets get it so it starts itself on boot.

🔧 Creating the systemd service

We need to create a service in Debian/Ubuntu that we will use to handle the starting/stoping of our soteriad.

sudo systemctl --force --full edit soterianode → this opens a systemd override editor. It’s useful if you’re modifying an existing unit, but for a new custom service it’s not the cleanest way.

Better approach: create a new unit file directly:

sudo nano /etc/systemd/system/soterianode.service

Copy and paste this for the program into our service file:

[Unit]
Description=soteriad network
After=network-online.target

[Service]
User=YOURUSER
Group=YOURUSER
Type=simple
PIDFile=/home/YOURUSER/.soteria/soteria.pid
ExecStart=soteriad
Restart=always
TimeoutStopSec=60s
TimeoutStartSec=20s
StartLimitInterval=60
StartLimitBurst=5

[Install]
WantedBy=multi-user.target

You must replace the YOURUSER a total of 3 times here with your username you have installed this under. We cannot use a wildcard here because systemd requires an explicit user. What this is telling the computer is to start the soteriad program after the network comes online and runs in the background.

Now hit CTRL-X and type yes, and hit enter to keep the default save location. We now have our service created! To enable it to start automatically on boot:

sudo systemctl daemon-reload

sudo systemctl enable soterianode

And Lastly, if everything went as it should, lets start it up!

sudo systemctl start soterianode

If everything went good you should see nothing. Let us check our service status by seeing if it started correctly.

sudo systemctl status soterianode  

You should see Active (running).

If not then modify Systemd service run:

sudo nano /etc/systemd/system/soterianode.service

Use the full path instead:

ExecStart=/usr/local/bin/soteriad 

Now let us look how you interact with the soteriad via command line.

Interacting with soteriad

We use a program called soteria-cli to control/interact with soteriad. All commands start with the program soteria-cli

Here is the command that will return the network status:

soteria-cli getnetworkinfo

Here is how to get blockchain sync info:

soteria-cli getblockchaininfo

Here are more commands to help you work with soteriad with descriptions:

Blockchain Commands:

soteria-cli getblockcount   #return block count
soteria-cli getmempoolinfo   #returns memory info
soteria-cli getdifficulty   #return difficulty
soteria-cli getchaintxstats   #returns transaction stats
soteria-cli abandontransaction "txid"   #cancel a transaction
soteria-cli pruneblockchain   #deletes old blocks for space

Wallet Commands:

soteria-cli listwallets   #lists wallets open
soteria-cli listaccounts   #list accounts under wallet
soteria-cli getwalletinfo   #returns summary wallet info
soteria-cli getbalance "walletAddress"   #returns specific wallet balance 
soteria-cli getunconfirmedbalance   #returns pending balance
soteria-cli getaddressesbyaccount "accountName"   #returns RVN address
soteria-cli validateaddress "walletAddress"   #verifies address
soteria-cli getaccountaddress "accountName"   #gets a new RVN address
soteria-cli backupwallet "destination"  #makes copy of wallet
soteria-cli dumpprivkey "walletAddress"   #retrieves private key
soteria-cli importprivkey "privkey" ( "label" ) ( rescan )   #import pvt key
soteria-cli importpubkey "pubkey" ( "label" rescan )   #import pub key
soteria-cli importaddress "address" ( "label" rescan p2sh )   #import address
soteria-cli mnemonic "your words"    #space separated list of 12-words to import
soteria-cli mnemonicpassphrase "password"  #secures your 12-word mnemonic word
soteria-cli getmywords # retrieve your BIP44 words
soteria-cli encryptwallet "passphrase"   #encrypts wallet with passphrase
soteria-cli listaddressgroupings   #shows accounts with balances
soteria-cli listassetbalancesbyaddress "address"   #returns assets for wallet
soteria-cli move "fromaccount" "toaccount" amount  #send between *accounts*
soteria-cli sendfrom "fromaccount" "toaddress" amount  #send to different wallet

Network Commands:

soteria-cli getpeerinfo    #returns connected peers and stats
soteria-cli getconnectioncount   #returns count of peers
soteria-cli getnettotals    #returns data totals
soteria-cli getnetworkinfo    #returns network status
soteria-cli setnetworkactive "true|false"   #turns on/off networking

You need a wallet so here is how you go about getting your wallet address and creating new ones. After soterianode is started and synced:

soteria-cli getaccountaddress "accountName"

It will return your wallet address for the new account in your wallet you just created!

Lets see it added now to our account account list:

soteria-cli listaccounts

or

soteria-cli listaddressgroupings

That will list the accounts you have setup and their balances in that current wallet.

For a list of your transactions, put in your account you want to audit and it will return a list of them:

soteria-cli listtransactions "account"

Wanna move between the accounts in your wallet?

soteria-cli move "fromaccount" "toaccount" amount

If it is successful it will return true.

Send money to someones wallet? Note,it is your account to send from, not wallet.

soteria-cli sendfrom "fromaccount" "toaddress" amount

It will return your TX hash if successful.

Network Setup

I can't go into much here because everyones setup is different. You need to port forward 8323 to your soterianode. Usually you set a DHCP reservation on your private network and then forward the port to that so it never changes.

If you cannot open the port manually, setupnp=1in the config file to enable automatic port forwarding.

This should be it for running a basic Soteria node! You can check https://explorer.soteria-network.online/network if you server is listed by searching for your external IP. It will take a 40-60 minutes or so to first appear. You wanna keep your node up and running as much as possible. Even a slight downtime will hurt your percent online.

Thanks for reading my guide!

If you find errors or something doesn't work, feel free to send me a message on Telegram/Discord or on twitter. I try to make it as easy to run as possible but sometimes I make errors, like everyone.
