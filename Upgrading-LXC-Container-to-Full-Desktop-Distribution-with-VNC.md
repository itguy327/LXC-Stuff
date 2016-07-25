### Upgrading LXC Container to Full Xubuntu Desktop Distribution with VNC

1. In container console upgrade all packages
  1. `apt-get update && apt-get upgrade -y`
2. Install tasksel
  1. `apt-get install tasksel`
3. Run tasksel
  1. Select [spacebar] Xubuntu Desktop, then [TAB] to Ok to start installation
4. Install VNC Server
  1. (Option 1) Install tightvncserver <https://forum.qnap.com/viewtopic.php?t=120564>
    1. `apt-get install tightvncserver`
    2. run `vncserver` and complete configuration
    3. run `netstat -plant` to see which port vncserver is using
  2. (Option 2) Install Vino VNC <https://wiki.ubuntu.com/Lubuntu/RemoteDesktop>
    1. `sudo apt-get install vino`
    2. (Optional) Create and login as a non-root user
    3. `vino-preferences`
5. (Optional) Clean up APT
  1. run: `apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*`
6. Add port forwarding to container for vncserver port
7. Restart container
8. Remote in to your container
  1. run `vncserver`
  2. (optional) run `vncserver -geometry 1280x780` for specific resolution
  3. use preferred VNC client to connect to forwarding port