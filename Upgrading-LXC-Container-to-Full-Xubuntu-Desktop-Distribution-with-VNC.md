### Upgrading LXC Container to Full Xubuntu Desktop Distribution with VNC

1. In container console upgrade all packages
  1. `apt-get update && apt-get upgrade -y`
2. Install tasksel
  1. `apt-get install tasksel`
3. Run tasksel
  1. Select [spacebar] Xubuntu Desktop, then [TAB] to Ok to start installation
4. Install tightvncserver
  1. `apt-get install tightvncserver`
  2. run `vncserver` and complete configuration
  3. run `netstat -plant` to see which port vncserver is using
5. Add port forwarding to container for vncserver port
6. Restart container
7. Remote in to your container
  1. run `vncserver`
  2. (optional) run `vncserver -geometry 1280x780` for specific resolution
  3. use preferred VNC client to connect to forwarding port