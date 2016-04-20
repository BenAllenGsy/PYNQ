.. _faq:

Frequently Asked Questions (FAQs)
=================================

Why ...
-------

... What is Jupyter?
   


... Do you support Python 2.7?
   Python 2.7 is loaded on Zynq and Python 2.7 scripts can be executed. Pynq, however, is based on Python 3.  No attempts have been made to ensure backward compatibility with Python 2.7.


... What is an overlay
   FPGA overlays are FPGA designs that are themselves configurable and typically optimized for a given domain.  We refer to them as post-bitstream programmable designs.  Such overlays are created to be re-used in more than one application.

   Consider the example of building a Zynq-based system for controlling a drone.  The designer may design exactly the system he needs for the immediate drone application.  Alternatively he may recognize that many drone controllers have quite similar requirements.  He can design a more configurable, FPGA design and export an API (application programming interface) for use by the embedded software programmers.  This single bitstram can then be customized via its API for use in different drone control projects.

   Note that the use of overlays does not imply the use of partial or dyamic reconfiguration. Some overalys can employ such techniques to good pupose but their use is optional.
   
... I can't connect to the board
   Check the [Getting Started Guide](2.-Getting-started.html)
   
   Check that you can ping the board from a command prompt or terminal on your host PC
   
   ping <Board IP Address>
  
   
... My hostname is not resolving
   If you know the IP addresso of the board, you can use it to navigate to the Pynq portal. e.g. http://192.168.0.10:9090

... I have followed the Getting Started Guide, I see a Red Led, but not a green Led when I power on the board. 
   Check the Micro-SD card is inserted correctly (the socket is spring loaded, so push it in until you feel it click into place). Check or reflash the Micro SD card with eh pynq image. 
   
... My Board is powered on, and I see the Red and Green LEDs, but I can't connect to the Pynq Portal, or see the Samba shared drive.
   By default, the board has DHCP enabled. If you plug the board into a home router, or network switch connected to your netwrok, it should be allocated an IP address automatically. 
   
   If you plug the ethernet cable directly to your computer, you will need to manually configure a static IP address.

... How do I set a static IP address
   To do this, you need to connect to the board using a terminal.
   
   To connect a terminal
   Plug in a USB cable, and connect to the board using a terminal emulator. 
   
   Terminal Settings: 
   
   * 115200 baud
   * 8 data bits
   * 1 stop bit
   * No Parity
   * No Flow Control
   
   Once you connect to the board, you can configure the network interface in Ubuntu
   
   e.g. sudo ifconfig eth0 192.168.0.10 
   
   You will need to stop the dhclient first
   
   run ps -ef | grep dhclient to find the process id of the dhclient, and then use sudo to kill it:

   .. image:: ./images/terminal_static_ip_address.jpg
      :align: center
   
   You can check Ubuntu documentation for further information.
   
   The password for sudo is pynq (or xpp if using an older image)
   
   run ifconfig again to confirm the ethernet settings
   
... Find the IP address
   Connect to the board using a terminal (see above) and type ifconfig to find the IP address for the eth0 ethernet adapter
   
... Change the hostname
   If you have multiple boards on the same network, you should give them different host names. You can do this from Ubuntu.
   
.. What is the user account and password?
   If you have an old image, the username and also the password is xpp
   
   If you have a new image, the username and password is pynq