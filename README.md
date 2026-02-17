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
