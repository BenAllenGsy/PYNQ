.. _faq:

Frequently Asked Questions (FAQs)
=================================


* Do you support Python 2.7?
   Python 2.7 is loaded on Zynq and Python 2.7 scripts can be executed. Pynq, however, is based on Python 3.4.  No attempts have been made to ensure backward compatibility with Python 2.7.


* What is an overlay?
   FPGA overlays are FPGA designs that are themselves configurable and typically optimized for a given domain.  We refer to them as post-bitstream programmable designs.  Such overlays are created to be re-used in more than one application.

   Consider the example of building a Zynq-based system for controlling a drone.  The designer may design exactly the system he needs for the immediate drone application.  Alternatively he may recognize that many drone controllers have quite similar requirements.  He can design a more configurable, FPGA design and export an API (application programming interface) for use by the embedded software programmers.  This single bitstream can then be customized via its API for use in different drone control projects.

   Note that the use of overlays does not imply the use of partial or dynamic reconfiguration. Some overlays can employ such techniques to good purpose but their use is optional.
   
* I can't connect to the board.
   Check the `Getting Started Guide <2_getting_started.html>`_
   
   Check that you can ping the board from a command prompt or terminal on your host PC
   
   .. code-block:: console
   
      # replace pynq with correct hostname if you have changed it
      ping pynq
      
   Check the ACT and Link LEDs on the PYNQ-Z1 board (near the Ethernet port) for activity. You can also check the activity lights on the Ethernet port on your PC or Laptop (most Ethernet ports will have an orange and green LED indicating connectivity). 
   The Ethernet LEDs on the PYNQ-Z1 should flash periodically when there is activity on the network connection. 
   
   If you are using a docking station, when your laptop is docked, the Ethernet port on the PC may be disabled.  

* I don't have an Ethernet port on my Laptop or PC.
   USB to Ethernet adapters are available. You can also use a USB to Ethernet adapter if you want to maintain a wired network connection, or if you do not want to change the network settings for your existing Ethernet port. 
   
   You can also connect your Pynq board to a network switch (your LAN), and connect to it wirelessly. (You may need to change settings on your Router to enable the Wireless network to communicate with your LAN - check your equipment documentation for details.)
   
* My hostname is not resolving.
   If you know the IP address of the board, you can use it to navigate to the Pynq portal. e.g.  http://192.168.2.99:9090

* I have followed the Getting Started Guide, I see a red LED, but not a green LED when I power on the board. 
   Check the Micro-SD card is inserted correctly (the socket is spring loaded, so push it in until you feel it click into place). Check or reflash the Micro SD card with the latest pynq image. 
   
* My Board is powered on, and I see the Red and Green LEDs, but I can't connect to the Pynq Portal, or see the Samba shared drive.
   By default, the board has DHCP enabled. If you plug the board into a home router, or network switch connected to your network, it should be allocated an IP address automatically. If not, it should fall back to a static IP address of 192.168.2.99
   
   If you plug the Ethernet cable directly to your computer, you will need to configure your network card to have an IP in the same address range. e.g. 192.168.2.1
   
* My board is connected, and I have verified the IP addresses on the board and my network interface, but I cannot connect to the board.
   If you are connected to a VPN, this will block access to local IP addresses, unless you have set the VPN to bypass the board address.

* How do I connect to the board using a terminal?
   To do this, you need to connect to the board using a terminal.
   
   To connect a terminal
   Plug in a USB cable, and connect to the board using a terminal emulator. 
   
   Terminal Settings: 
   
   * 115200 baud
   * 8 data bits
   * 1 stop bit
   * No Parity
   * No Flow Control
   
   Once you connect to the board, you can configure the network interface in Linux
   
* How do I modify the Linux operating system?
   Connect to the board using a terminal, and change the settings as you would for any other Linux machine.  The board comes with a Linux build.
   
* How do I find the IP address of the board?
   Connect to the board using a terminal (see above) and type 'hostname -I' to find the IP address for the eth0 Ethernet adapter
   
* How do I set/change the static IP address on the board?
   The Static IP address is set in /etc/dhcp/dhclient.conf  - you can modify the board's static IP there
   
* How do I find my hostname?
   Connect to the board using a terminal and run 'hostname'
   
* How do I change the hostname?
   If you have multiple boards on the same network, you should give them different host names. 
   You can run the following script to change the hostname:
   sudo /home/xilinx/scripts/hostname.sh NEW_HOST_NAME
   
* What is the user account and password?
   Username and password for all linux, jupyter and samba logins are: xilinx/xilinx
   