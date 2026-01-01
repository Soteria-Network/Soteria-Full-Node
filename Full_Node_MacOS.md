## macOS Instructions

### macOS

Go to the [Soteria Core releases page](https://github.com/Soteria-Network/Soteria/releases).

Download Soteria Core installer to your Downloads folder.

After downloading the file to your Downloads folder
(`/Users/<YOUR USER NAME>/Downloads`), run it by double-clicking
its icon. macOS will open a Finder window for you to drag *Soteria Core* to your
Applications folder.



#### Soteria Core GUI


The first time running *Soteria Core*, macOS will ask you to confirm that
you want to run it:


You will be prompted to choose a directory to store the Soteria blockchain
and your wallet.  Unless you have a separate partition or drive
you want to use, click Ok to use the default.


Soteria Core GUI will begin to download the blockchain.  This step will take at
least 30 minutes, and it may take much more time on a slow Internet connection
or with a slow computer.  During the download, Soteria Core will use a
part of your connection bandwidth.  You can stop Soteria Core at any
time by closing it; it will resume from the point where it stopped the next time
you start it.


After download is complete, you may use Soteria Core as your wallet or
you can just let it run to help support the Soteria network.

<div class="box" markdown="1">
*Optional: Start Your Node At Login*

Starting your node automatically each time you login to your computer
makes it easy for you to contribute to the network. The easiest way
to do this is to tell Soteria Core GUI to start at login.

While running Soteria Core GUI, open the Soteria Core menu and choose
Preferences.  On the Main tab, click *Start Soteria on system login*.  Click
the Ok button to save the new settings.


The next time you login to your desktop, Soteria Core GUI will be
automatically started minimized in the task bar.



#### Soteria Core Daemon


The Soteria Core daemon (soteriad) is not included in the .dmg file you may have downloaded to install Soteria-QT. Soteriad, along with its support binaries, is instead included in the macOS.zip file listed on the official Soteria Network releases page. To download this file using Terminal, execute the following command:

    curl -O https://github.com/Soteria-Network/Soteria/releases/download/v1.1.1/soteria-Core-macOS.zip

Extract soteriad and its support binaries from the archive we just downloaded by running this command in Terminal:

    unzip Soteria-Core-macOS.zip

Now we'll move the executables into your default path to make running and stopping soteriad easier. To move the executables, run these commands (note that we have to use `sudo` to perform these commands since we are modifying directories owned by root):

    sudo mkdir -p /usr/local/bin
    sudo cp soteria-Core-macOS* /usr/local/bin/.

To clean up the directory we've been working in, run:

    rm -rf soteria-Core-macOS*

You should now be able to start up your full node by running `soteriand -daemon` in any Terminal window. If you need to stop soteriad for any reason, the command is `soteria-cli stop`

<div class="box" markdown="1">
*Optional: Start Your Node At Login*

Starting your node automatically each time you login to your computer makes it easy for you to contribute to the network. The easiest way to do this is to tell Soteria Core Daemon to start at login. In macOS, the way to start background programs at login is using a Launch Agent. Here is how to install a Launch Agent for Soteria Core daemon on your machine:

    mkdir ~/Library/LaunchAgents
    curl https://github.com/Soteria-Network/Soteria/blob/master/contrib/init/org.soteria.soteriad.plist > ~/Library/LaunchAgents/org.soteria.soteriad.plist

The next time you login to your desktop, Soteria Core daemon will be automatically started.
You have now completed installing Soteria Core.



## Upgrading Soteria Core

If you are running an older version, shut it down. Wait until it has completely
shut down (which might take a few seconds for older versions), then just
copy over /Applications/Soteria-Qt (on macOS).

The blockchain and wallet files in the data directory are compatible between
versions so there is no requirement to make any changes to the data directory
when upgrading. Occasionally the format of those files changes, but the new
Soteria Core version will include code that automatically upgrades the files to
the new format so no manual intervention is required.

Sometimes upgrade of the blockchain data files from very old versions to the new
versions is not supported. In those cases it may be necessary to redownload the
blockchain. Check the release notes of the new version if you are planning to
upgrade from a very old version.

Sometimes downgrade is not possible because of changes to the data files. Again,
check the release notes for the new version if you are planning to downgrade.



## Network Configuration

If you want to support the Soteria network, you must allow inbound
connections.

When Soteria Core starts, it establishes 10 outbound connections to other
full nodes so it can download the latest blocks and transactions. If you
just want to use your full node as a wallet, you don't need more than
these 10 connections---but if you want to support lightweight clients and
other full nodes on the network, you must allow inbound connections.

Servers connected directly to the Internet usually don't require any
special configuration.  You can use the testing instructions below to
confirm your server-based node accepts inbound connections.

Home connections are usually filtered by a router or modem. Soteria
Core will request your router automatically configure itself to allow
inbound connections to Soteria's port, port 8323. Unfortunately many
routers don't allow automatic configuration, so you must manually
configure your router. You may also need to configure your firewall to
allow inbound connections to port 8323. Please see the following
subsections for details.



### Testing Connections

You must first ensure that your node is fully synced with the blockchain. 

For confirmation that you accept inbound connections, you can use
Soteria Core. Soteria Core can't tell you directly whether you allow
inbound connections, but it can tell you whether or not you currently
have any inbound connections. If your node has been online for at least
5 minutes, it should normally have inbound connections. If want to
check your peer info using Soteria Core, choose the appropriate
instructions below:

* [Peer info in Soteria Core GUI](#gui-peer-info)

* [Peer info in Soteria Core daemon](#daemon-peer-info)



#### GUI Peer Info

In the bottom right corner of the Soteria Core GUI are several icons.
If you hover over the signal strength icon, it will tell you how many
connections you have. The icon won't turn green until you have more
than 10 active connections, which only happens if inbound connections
are allowed.

For confirmation, you can go to the Help menu, choose Debug Window, and
open the Information tab. In the Network section, it will tell you
exactly how many inbound connections you have. If the number is greater
than zero, then inbound connections are allowed.

If you don't have inbound connections, please read the instructions for [enabling inbound
connections.](#enabling-connections)

#### Daemon Peer Info

The getconnectioncount command will tell you how many connections you have. 
If you have more than 10 connections, inbound connections are allowed. For example:

<b>soteria-cli getconnectioncount</b> 12

For confirmation, you can use the `getpeerinfo` command to get
information about all of your peers.  Each peer's details will include
an `inbound` field set to true if the connection is inbound.  If you
have any inbound connections, then inbound connections are allowed.

If you don't have inbound connections, please read instructions for [enabling inbound
connections.](#enabling-connections)

### Enabling Connections

If Soteria Core can't automatically configure your router to open port
8323, you will need to manually configure your router.  We've tried to
make the following instructions generic enough to cover most router
models; if you need specific help with your router, please ask for help
on a tech support site such as [SuperUser](https://superuser.com/).

Enabling inbound connections requires two steps, plus an extra third
step for firewall users:

1. Giving your computer a static (unchanging) internal IP address by
   configuring the Dynamic Host Configuration Protocol (DHCP) on your
   router.

2. Forwarding inbound connections from the Internet through your
   router to your computer where Soteria Core can process them.

3. Configuring your firewall to allow inbound connections. 
  macOS does not enable a firewall by default.

#### Configuring DHCP

In order for your router to direct incoming port 8323 connections to
your computer, it needs to know your computer's internal IP address.
However, routers usually give computers dynamic IP addresses that change
frequently, so we need to ensure your router always gives your computer
the same internal IP address.

Start by logging into your router's administration interface.  Most
routers can be configured using one of the following URLs, so keep
clicking links until you find one that works.  If none work, consult
your router's manual.

* <http://192.168.0.1> (some Linksys/Cisco models)
* <http://192.168.1.1> (some D-Link/Netgear models)
* <http://192.168.2.1> (some Belkin/SMC models)
* <http://192.168.123.254> (some US Robotics models)
* <http://10.0.1.1> (some Apple models)

Upon connecting, you will probably be prompted for a username and
password.  If you configured a password, enter it now.  If not,
the [Router Passwords site](https://www.routerpasswords.com/) provides a database of known
default username and password pairs.

After logging in, you want to search your router's menus for options
related to DHCP, the Dynamic Host Configuration Protocol.  These options
may also be called Address Reservation.  For example, the router page
shown below calls the option we need "DHCP Reservation":


In the reservation configuration, some routers will display a list of
computers and devices currently connected to your network, and then let
you select a device to make its current IP address permanent:


If that's the case, find the computer running Soteria Core in the list,
select it, and add it to the list of reserved addresses. Make a note of
its current IP address---we'll use the address in the next section.

Other routers require a more manual configuration. For these routers,
you will need to look up the fixed address (MAC address) for your
computer's network card and add it to thhe list. This operation differs
by operating system:


* **macOS:** open a terminal and type `ifconfig`. Find the result
  that best matches your connection---a result starting with `en1`
  usually indicates a wireless connection. Find the field that starts
  with `ether:` and copy the immediately following field that looks like
  01:23:45:67:89:ab. Use that value in the instructions below.

Once you have the MAC address, you can fill it into your router's
manual DHCP assignment table, as illustrated below. Also choose an IP
address and make a note of it for the instructions in the next
subsection. After entering this information, click the Add or Save
button.


Then reboot your computer to ensure it gets assigned the address you
selected and proceed to the Port Forwarding instructions below.

#### Port Forwarding

For this step, you need to know the local IP address of the computer
running Soteria Core. You should have this information from configuring
the DHCP assignment table in the subsection above.

Login to your router using the same steps described near the top of the
[DHCP subsection](#configuring-dhcp).  Look for an option called Port Forwarding, Port
Assignment, or anything with "Port" in its name.  On some routers,
this option is buried in an Applications & Gaming menu.

The port forwarding settings should allow you to map an external port on
your router to the "internal port" of a device on your network as shown
in the screenshot below.


Both the external port and the internal port should be 8323 for Soteria.
Make sure the IP address you enter is the same one you configured
in the previous subsection.

After filling in the details for the mapping, save the entry. You should
not need to restart anything. Start Soteria Core (if you haven't
already) and follow the [Testing Connections](#testing-connections)
instructions to test your connection.

If you still can't connect and you use a firewall, you probably need to
change your firewall settings. See the Firewall section below.

If something else went wrong, it's probably a problem with your router
configuration. Re-read the instructions above to see if you missed
anything, search the web for help with "port forwarding", and ask for
help on sites like [SuperUser](https://superuser.com).

We can't provide direct support, but if you see a way to improve these
instructions, please [open an issue.](https://github.com/Soteria-Network/Soteria-Full-Node/issues/new)

#### Firewall Configuration

Firewalls block inbound connections.  To use Soteria, you need to
configure your computer's firewall to allow connections to port 8323.
This is usually as easy as starting your firewall configuration software
and defining a new rule to allow inbound connections to port 8323. 
