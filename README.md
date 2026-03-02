# Run SearXNG on Android with Termux (No Root) #
   This guide explains how to run SearXNG inside Termux using udocker, without root access.\
   It also includes optional automation using Termux:Boot.

**Requirements:** Termux

Optional: Termux:Boot

**After installing:** Open each app at least once and disable battery optimization. If battery optimization is not disabled, Android may murder them and their blood will be on your hands.

**Update Termux packages**\
   Open Termux and run:
         
    $ pkg update && pkg upgrade -y
   If prompted during the first update:\
      Press Enter to select the defaults

**Install Udocker:**

    $ pkg install udocker -y

**Pull the SearXNG Docker Image**

    $ udocker pull docker.io/searxng/searxng:latest
   Note: Download may take several minutes.

**Create the Container**
   
    $ udocker create --name=searxng docker.io/searxng/searxng:latest
   Note: It may take a few minutes.

**Run SearXNG**\

    $ udocker run searxng
   Wait until [INFO] Started worker-1 appears on your screen before continuing.
   
   Open your browser and go to:

    http://127.0.0.1:8080
   If SearXNG loads, it is working.
   
   Note: You can stop the server with:
      
    CTRL + C
**Optional: Auto-Start on Boot**

   Requires Termux:Boot.
   
   Create Boot Directory

    $ mkdir -p ~/.termux/boot
   Create Startup Script

    $ nano ~/.termux/boot/start-searxng
Paste:

    #!/bin/bash
    termux-wake-lock
    udocker run searxng
   Save file:
   
    CTRL + O
   
    Press Enter
   
    CTRL + X
      
   Make it executable:

    $ chmod +x ~/.termux/boot/start-searxng
Test Boot Script Without Reboot

    $ cd ~/.termux/boot/
    
    ./start-searxng
   If it starts, it will also start after device reboot.

**Useful**

   SearXNG configuration File:

    /data/data/com.termux/files/home/.udocker/containers/searxng/ROOT/etc/searxng/settings.yml
   [SearXNG](https://docs.searxng.org)\
   [Termux](https://termux.dev)
   
