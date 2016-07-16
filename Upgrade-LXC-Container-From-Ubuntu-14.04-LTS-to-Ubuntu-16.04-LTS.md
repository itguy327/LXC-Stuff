1. Create a Ubuntu 14.04 LXC Container
2. As root run `apt-get update && apt-get upgrade -y`
3. Install Update Manager Core `apt-get install -y update-manager-core`
4. Make sure config is set for LTS `/etc/update-manager/release-upgrades` <https://wiki.ubuntu.com/XenialXerus/ReleaseNotes>
4. Run `do-release-upgrade`
  1. If you get error `No new release found`, then run `do-release-upgrade -d` <https://www.digitalocean.com/community/tutorials/how-to-upgrade-to-ubuntu-16-04-lts>