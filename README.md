# How to run SearXNG on android with Termux without root.

**Requirements:**
   - Termux - Disable battery optimizations in phone settings, launch at least once
        - Optional: Termux:Boot (for automation) - Disable battery optimizations in phone settings, launch at least once

Termux setup:
Updating Termux packages
1 pkg update && pkg upgrade -y
   - when prompted during the first pkg update select the default option by pressing enter.
Installing Udocker
2 pkg install udocker -y

Udocker setup:
Pulling SearXNG docker image, more info at docs.searxng.org/admin/installation-docker.html
1 udocker pull docker.io/searxng/searxng:latest
Creating udocker container - might take a bit
2 udocker create --name=searxng docker.io/searxng/searxng:latest
Running the container
3 udocker run searxng
now you can test if it's working by opening a webbrowser and going to localhost:8080 or 127.0.0.1:8080
Config full path "/data/data/com.termux/files/home/.udocker/containers/searxng/ROOT/etc/searxng/settings.yml"

Termux:Boot Setup
1 mkdir ~/.termux/boot
2 nano ~/.termux/boot/start-searxng
#!/bin/bash
termux-wake-lock
udocker run searxng
3 chmod +x ~/.termux/boot/start-searxng
