Guillaume Ross

Jul 1, 2018
(https://blog.caffeinesecurity.com/installing-a-lab-security-onion-vm-to-inspect-other-local-vms-56f6c448fbe3)

## Installing a lab Security Onion VM to inspect other local VMs

As I (
Guillaume Ross
) am hosting a security workshop at the MacAdmins Conference at Penn State on July 10th, I need to send instructions to attendees.

Yesterday, I posted Creating a macOS High Sierra VM for VirtualBox (Mac Host).

Today, we’ll look at how we can build a Security Onion environment that will inspect the traffic from that Mac VM.

For a complete introduction to Security Onion, you can see my course, Network Security Monitoring with Security Onion. If you do not have a Pluralsight account, you can sign up for a trial here.

MacAdmins attendees: You do NOT need this Security Onion VM. If your laptop is not powerful enough to run the Mac VM and this one, favor the Mac VM. It will be very useful if you do have it, however.

### Download and verify the Security Onion ISO.
Create a VM with at least 4GB of RAM, 50GB of storage, and two network interfaces. If your machine can take it, make sure to give it two cores and 8GB of RAM. Specify Ubuntu 64 as the OS.

The first interface will be NAT’d or bridged, to reach the Internet. Be aware that bridged may not work well if you’re on a typical “public Wi-Fi”, so NAT’d is safer.

The second interface will be on a NAT Network(or VM team network if you’re on VMware), configured to promiscuous mode, to ensure it sees other VMs. Any networking model that allows it to see VMs is fine — but having a mode that allows the Mac VM to reach the Internet using the monitored interface will make many things easier.
Boot the installer.


Installing Security Onion

Boot the ISO, then run the installer on the desktop.

Proceed through the wizard, with default options except:

*  Check Download Updates while installing Security Onion.
*  Set the location/timezone to UTC/GMT, because only monsters have servers and centralized logging systems set to anything else.Once the installer finishes copying, restart.
*  On reboot, login and run Setup from the desktop.
    Proceed with the wizard — let it configure all the services it lists.
    Click “Yes, configure /etc/network/interfaces!” — this is where we will tell SO that eth0 is for management/internet and eth1 is the monitoring interface… or whatever they’re called with this crazy new-fangled stuff (enp0s3 and enp0s8? You may need to run ifconfig and check IP addresses to figure out which is which).
    Configure the management interface to use DHCP — in production that wouldn’t make much sense, but this is a local lab VM.
    Click “Yes, configure sniffing interfaces.”
    Select the remaining interface.
    Make changes and reboot.
    Run setup again, but this time skip the network configuration.
    Skip through the RAM and amount of core warnings if your VM is underpowered.
    Configure it in Evaluation Mode — this will ensure all features are on a single VM.
    The monitoring interface should already be pre-selected, continue.
    Configure a user/password combo, and configure services.
    Reboot

Testing Setup

Now that we have Security Onion setup, we need to see that it is monitoring the traffic to our Mac VM properly.

    Ensure your Mac VM is on the same NAT Network (Or VM Team — or whatever your hypervisor calls them) as the monitoring interface we configured before setup.
    Run sudo tcpdump -i enp0s8 (or whatever your monitoring interface is). You should see some packets from the Mac VM.
    Open Sguil on the Security Onion desktop.
    On the Mac VM, browse to http://testmyids.com.
    In Sguil, you should see an alert like this pop up.
