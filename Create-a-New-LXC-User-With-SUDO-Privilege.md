### Create a new user with SUDO privilege for LXC/Docker container
[Initial Server Setup with Ubuntu 14.04](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-14-04)

Run the following commands as root

1. `adduser demo`
2. `gpasswd -a demo sudo`
3. `su - demo`
4. to list all users `cut -d: -f1 /etc/passwd`
5. To change the password for a user `sudo passwd username`