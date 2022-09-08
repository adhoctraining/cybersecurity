## How to send email notifications using Gmail SMTP server on Linux
https://www.xmodulo.com/send-email-notifications-gmail-smtp-server-linux.html

Requirements

    Outgoing mail server (SMTP server): smtp.gmail.com
    Use authentication: yes
    Use secure connection: yes
    Username: your Gmail account ID (e.g., alice if your email is alice@gmail.com)
    Password: your Gmail password
    Port: 587 (TLS) or 465 (SSL) 
    
    Install Mutt a command line mail tool.
 The victim machine for the first lesson will be a Ubuntu docker
 image modified to resemble vulnhub box Gibson. 
 Ubuntu 14.04
 Apache2.4.7
 Open sshd 6.6
 
 ## Linux: How to install certain old version of a software via apt-get
  sudo apt-get install <pkg_name>=<pkg_version>
 

## WinterMute: 1
A new OSCP style lab involving 2 vulnerable machines, themed after the cyberpunk classic Neuromancer - a must read for any cyber-security enthusiast. This lab makes use of pivoting and post exploitation, which I've found other OSCP prep labs seem to lack. The goal is the get root on both machines. All you need is default Kali Linux.

I'd rate this as Intermediate. No buffer overflows or exploit development - any necessary password cracking can be done with small wordlists. It's much more related to an OSCP box vs a CTF. I've tested it quite a bit, but if you see any issues or need a nudge PM me here.

Virtual Box Lab setup instructions are included in the zip download, but here's a quick brief:

Straylight - simulates a public facing server with 2 NICS. Cap this first, then pivot to the final machine. Neuromancer - is within a non-public network with 1 NIC. Your Kali box should ONLY be on the same virtual network as Straylight.
This works better with VirtualBox rather than VMware
### Download
>  Please remember that VulnHub is a free community resource so we are unable to check the machines that are provided to us. Before you download, please read our FAQs sections dealing with the dangers of running unknown VMs and our suggestions for “protecting yourself and your network. If you understand the risks, please download!

    Wintermute-v1.zip (Size: 2.4 GB)
    Download: https://drive.google.com/open?id=1bHgdx0iI24jv7MDzKcrIPtd9rVFaVokR
    Download (Mirror): https://download.vulnhub.com/wintermute/Wintermute-v1.zip
    Download (Torrent): https://download.vulnhub.com/wintermute/Wintermute-v1.zip.torrent   (

    Magnet)

