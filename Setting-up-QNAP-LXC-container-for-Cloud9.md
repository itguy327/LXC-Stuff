# Welcome to the QNAP-LXC-Cloud9 wiki!

## Thanks to [kdelfour](//github.com/kdelfour/cloud9-docker/) and [nightwing](//github.com/c9/core/issues/197#issuecomment-154320986) for figuring out how to setup Cloud9. This should work for any LXC container e.g. DigitalOcean

### 1. Create QNAP LXC Container
   Install Container Station from QNAP App Center (if not already installed)
  1. Open Container Station
  2. Click on Create Container
  3. Select Ubuntu LXC and click Create
  4. (Optional) Change Auto Start to Off
  5. (Optional) Change CPU Limit to 50%
  6. (Optional) Change Memory Limit to 2048MB or number lower than max memory
  7. Click Advanced Settings
    1. Under Network, add port forwarding
      1. Host: 8000, Container: 80, Protocol: TCP (update host port to another port if its already used)
      2. Host: 3000, Container: 3000, Protocol: TCP (update host port to another port if its already used)
    2. Click Create

### 2. Setup LXC environment
  1. Within LXC container: `apt-get update && apt-get -y upgrade`
  2. Install build tools: `apt-get install -y build-essential g++ curl libssl-dev apache2-utils git libxml2-dev sshfs python2.7 python2.7-dev`