## Windows Instructions

### Windows 10

Go to the [Soteria Network releases page](https://github.com/Soteria-Network/Soteria/releases).

Dowload Soteria Core installer to your desktop.

After downloading the file to your desktop or your Downloads folder
(`C:\Users\<YOUR USER NAME>\Downloads`), run it by double-clicking its icon.
Windows will ask you to confirm that you want to run it. Click Yes and the
Soteria installer will start.  It's a typical Windows installer, and it will
guide you through the decisions you need to make about where to install Soteria
Core.


<div class="box" markdown="1">
*To continue, choose one of the following options*

1. If you want to use the Soteria Core Graphical User Interface (GUI),
   proceed to the [Soteria Core GUI](#win10-gui) section below.

2. If you want to use the Soteria Core daemon (soteriad), which is
   useful for programmers and advanced users, proceed to the [Soteria
   Core Daemon](#win10-daemon) section below.

3. If you want to use both the GUI and the daemon, read both the [GUI
   instructions](#win10-gui) and the [daemon
   instructions](#win10-daemon). Note that you can't run both the GUI
   and the daemon at the same time using the same configuration
   directory.



#### Soteria Core GUI


Press the Windows key (`⊞ Win`) and start typing "soteria".  When the
Soteria Core icon appears (as shown below), click on it.

You will be prompted to choose a directory to store the Soteria blockchain
and your wallet.  Unless you have a separate partition or drive
you want to use, click Ok to use the default.

Your firewall may block Soteria Core from making outbound connections.
It's safe to allow Soteria Core to use all networks. (Note: you will
still need to configure inbound connections as described later in the
[Network Configuration](#network-configuration) section.)

Soteria Core GUI will begin to download the blockchain.  This step will take at
least 30-40 minutes, and it may take much more time on a slow Internet connection
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

While running Soteria Core GUI, open the Settings menu and choose
Options.  On the Main tab, click *Start Soteria on system login*.  Click
the Ok button to save the new settings.

The next time you login to your desktop, Soteria Core GUI will be
automatically started minimized in the task bar.



#### Soteria Core Daemon


To start Soteria Core daemon, first open a command window: press the
Windows key (`⊞ Win`) and type "cmd".  Choose the option labeled
"Command Prompt".


If you installed Soteria Core into the default directory, type the
following at the command prompt:

    C:\Program Files\Soteria\daemon\soteriad

Soteria Core daemon should start. To interact with Soteria Core daemon, you will
use the command `soteria-cli` (Soteria command line interface).  If you
installed Soteria Core into the default location, type the following at the
command prompt to see whether it works:

    C:\Program Files\Soteria\daemon\soteria-cli getblockchaininfo


For example, to safely stop your node, run the following command:

    C:\Program Files\Soteria\daemon\soteria-cli stop


<div class="box" markdown="1">
*Optional: Start Your Node At Boot*

Starting your node automatically each time your computer boots makes it
easy for you to contribute to the network.  The easiest way to do this
is to start Soteria Core daemon when you login to your computer.

Start File Explorer and go to:

    C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp

Right-click on the File Explorer window and choose New → Text file.
Name the file `start_soteriad.bat`. Then right-click on it and choose
Open in Notepad (or whatever editor you prefer). Copy and paste the
following line into the file.

    C:\Program Files\Soteria\daemon\soteriad

(If you installed Soteria Core in a non-default directory, use that
directory path instead.)

Save the file. The next time you login to your computer, Soteria Core
daemon will be automatically started.



### Windows 8.x

Go to the [Soteria Core releases page](https://github.com/Soteria-Network/Soteria/releases).

Dowload Soteria Core installer to your desktop.

After downloading the file to your desktop or your Downloads folder
(`C:\Users\<YOUR USER NAME>\Downloads`), run it by double-clicking its icon.
Windows will ask you to confirm that you want to run it. Click Yes and the
Soteria installer will start.  It's a typical Windows installer, and it will
guide you through the decisions you need to make about where to install Soteria
Core.


<div class="box" markdown="1">
*To continue, choose one of the following options*

1. If you want to use the Soteria Core Graphical User Interface (GUI),
   proceed to the [Soteria Core GUI](#win8-gui) section below.

2. If you want to use the Soteria Core daemon (soteriad), which is
   useful for programmers and advanced users, proceed to the [Soteria
   Core Daemon](#win8-daemon) section below.

3. If you want to use both the GUI and the daemon, read both the [GUI
   instructions](#win8-gui) and the [daemon
   instructions](#win8-daemon). Note that you can't run both the GUI
   and the daemon at the same time using the same configuration
   directory.



#### Soteria Core GUI


Press the Windows key (`⊞ Win`) and start typing "soteria".  When the
Soteria Core icon appears (as shown below), click on it.

You will be prompted to choose a directory to store the Soteria block
chain and your wallet.  Unless you have a separate partition or drive
you want to use, click Ok to use the default.


Your firewall may block Soteria Core from making outbound connections.
It's safe to allow Soteria Core to use all networks. (Note: you will
still need to configure inbound connections as described later in the
[Network Configuration](#network-configuration) section.)


Soteria Core GUI will begin to download the blockchain.  This step will take at
least 40-60 minutes, and it may take much more time on a slow Internet connection
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

While running Soteria Core GUI, open the Settings menu and choose
Options.  On the Main tab, click *Start Soteria on system login*.  Click
the Ok button to save the new settings.


The next time you login to your desktop, Soteria Core GUI will be
automatically started minimized in the task bar.



#### Soteria Core Daemon


To start Soteria Core daemon, first open a command window: press the
Windows key (`⊞ Win`) and type "cmd".  Choose the option labeled
"Command Prompt".


If you installed Soteria Core into the default directory, type the
following at the command prompt:

    C:\Program Files\Soteria\daemon\soteriad

Soteria Core daemon should start. To interact with Soteria Core daemon, you will
use the command `soteria-cli` (Soteria command line interface).  If you
installed Soteria Core into the default location, type the following at the
command prompt to see whether it works:

    C:\Program Files\Soteria\daemon\soteria-cli getblockchaininfo


For example, to safely stop your node, run the following command:

    C:\Program Files\Soteria\daemon\soteria-cli stop

<div class="box" markdown="1">
*Optional: Start Your Node At Boot*

Starting your node automatically each time your computer boots makes it
easy for you to contribute to the network.  The easiest way to do this
is to start Soteria Core daemon when you login to your computer.

Start File Explorer and go to:

    C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp

Right-click on the File Explorer window and choose New → Text file.
Name the file `start_soteriad.bat`. Then right-click on it and choose
Open in Notepad (or whatever editor you prefer). Copy and paste the
following line into the file.

    C:\Program Files\Soteria\daemon\soteriad

(If you installed Soteria Core in a non-default directory, use that
directory path instead.)

Save the file. The next time you login to your computer, Soteria Core
daemon will be automatically started.



### Windows 7

Go to the [Soteria Network releases page](https://github.com/Soteria-Network/Soteria/releases).

Dowload Soteria Core installer to your desktop.


After downloading the file to your desktop or your Downloads folder
(`C:\Users\<YOUR USER NAME>\Downloads`), run it by double-clicking its icon.
Windows will ask you to confirm that you want to run it. Click Yes and the
Soteria installer will start.  It's a typical Windows installer, and it will
guide you through the decisions you need to make about where to install Soteria
Core.

<div class="box" markdown="1">
*To continue, choose one of the following options*

1. If you want to use the Soteria Core Graphical User Interface (GUI),
   proceed to the [Soteria Core GUI](#win7-gui) section below.

2. If you want to use the Soteria Core daemon (soteriad), which is
   useful for programmers and advanced users, proceed to the [Soteria
   Core Daemon](#win7-daemon) section below.

3. If you want to use both the GUI and the daemon, read both the [GUI
   instructions](#win7-gui) and the [daemon
   instructions](#win7-daemon). Note that you can't run both the GUI
   and the daemon at the same time using the same configuration
   directory.



#### Soteria Core GUI


Open the *Start* menu, type `soteria` into the search box, and click the
*Soteria Core* icon.


You will be prompted to choose a directory to store the Soteria block
chain and your wallet.  Unless you have a separate partition or drive
you want to use, click Ok to use the default.


Your firewall may block Soteria Core from making outbound connections.
It's safe to allow Soteria Core to use all networks. (Note: you will
still need to configure inbound connections as described later in the
[Network Configuration](#network-configuration) section.)


Soteria Core GUI will begin to download the blockchain.  This step will take at
least several days, and it may take much more time on a slow Internet connection
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

While running Soteria Core GUI, open the Settings menu and choose
Options.  On the Main tab, click *Start Soteria on system login*.  Click
the Ok button to save the new settings.

The next time you login to your desktop, Soteria Core GUI will be
automatically started minimized in the task bar.


##### Soteria Core Daemon


To start Soteria Core daemon, first open a command window: press the
Windows key (`⊞ Win`) and type "cmd". Choose the program named "cmd.exe"


If you installed the Soteria Core into the default directory, type the following at the command prompt :

    C:\Program Files\Soteria\daemon\soteriad

Soteria Core daemon should start. You can now try using Soteria Cli Utility.

To interact with Soteria Core daemon, you will use the command `soteria-cli`
(Soteria command line interface). If you installed Soteria Core into the default
location, type the following at the command prompt to see whether it works:

    C:\Program Files\Soteria\daemon\soteria-cli getblockchaininfo

For example, to safely stop your node, run the following command:

    C:\Program Files\Soteria\daemon\soteria-cli stop


<div class="box" markdown="1">
*Optional: Start Your Node At Boot*

Starting your node automatically each time your computer boots makes it easy for you to contribute to the network. The easiest way to do this is to start Soteria Core daemon when you login to your computer.

Start File Explorer and go to:

    C:\Users\Example\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\StartUp

You can also access this folder by executing the following command after reaching the `Execute...` prompt :

    shell:startup

Right-click on the File Explorer window and choose New → Text file. Name the file `start_soteriad.bat`. Then right-click on it and choose Open in Notepad (or whatever editor you prefer). Copy and paste the following line into the file.

    C:\Program Files\Soteria\daemon\soteriad

(If you installed Soteria Core in a non-default directory, use that directory path instead.)

Save the file. The next time you login to your computer, Soteria Core daemon will be automatically started.


<div class="toccontent-block boxexpand expanded" markdown="1

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

<pre><b>soteria-cli getconnectioncount</b> 12</pre>

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

3. Configuring your firewall to allow inbound connections. This step
   mainly applies to Windows users, as Mac OS X and most Linuxes do not
   enable a firewall by default.



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
the [Router Passwords site](https://www.routerpasswords.com/) provides a
database of known default username and password pairs.

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
computer's network card and add it to the list. This operation differs
by operating system:

* **Windows 7 & 8:** Press Win-R (Windows key plus the R key) to open
  the Run dialog. Type `cmd` to open the console. Type `ipconfig /all` and
  find the result that best matches your connection---usually a wireless
  connection. Look for a line that starts with "Physical Address" and
  contains a value like this:

        Physical Address. . . . . . . . . : 06-23-45-67-89-AD

    Replace all the dashes with colons, so the address looks like this:
    06:23:45:67:89:AD.  Use that address in the instructions below.


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
already) and follow the [Testing Connections](#testing-connections) instructions to test
your connection.

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
and defining a new rule to allow inbound connections to port 8323.  For
additional information for Windows, see the links below:

* [Instructions for Windows Firewall](https://learn.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/create-an-inbound-port-rule)
