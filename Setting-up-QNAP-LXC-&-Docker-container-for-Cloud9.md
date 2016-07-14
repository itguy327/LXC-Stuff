## Thanks to [kdelfour](//github.com/kdelfour/cloud9-docker/) and [nightwing](//github.com/c9/core/issues/197#issuecomment-154320986) for figuring out how to setup Cloud9. This should work for any LXC container e.g. DigitalOcean

### 1. Create QNAP LXC Container (should also work for QNAP Ubuntu Docker container)
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

### 2. Setup base environment
  1. Within LXC container: `apt-get update && apt-get -y upgrade`
  2. Install build tools: `apt-get install -y build-essential g++ curl libssl-dev apache2-utils git libxml2-dev sshfs python2.7 python2.7-dev`
  3. (Optional) Update container time zone for correct file timestamp with Git (QNAP timezone by default is Taiwan)
    1. run: `dpkg-reconfigure tzdata`

### 3. Install latest Node.js 6.x
   <https://nodejs.org/en/download/package-manager/>
  1. run: `curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -`
  2. run: `apt-get install -y nodejs`
  3. (Optional) Install NVM (Node Version Manager)
    1. run: `curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.31.2/install.sh | bash`

### 4. Install Cloud9
  1. run: `git clone https://github.com/c9/core.git /cloud9`
  2. run: `cd /cloud9`
  3. run: `scripts/install-sdk.sh`
  4. go get some coffee

### 5. Fix PTY
  1. run: `C9_DIR=$HOME/.c9`
  2. run: `PATH="$C9_DIR/node/bin/:$C9_DIR/node_modules/.bin:$PATH"`
  3. run: `cd $C9_DIR`
  4. run: `npm install pty.js`
  5. (Optional) make the path permanent for future C9 updates
    1. modify .bashrc in /root directory and add the following lines
      1. `export C9_DIR=$HOME/.c9`
      2. `export PATH="$C9_DIR/node/bin/:$C9_DIR/node_modules/.bin:$PATH"`

### 6. Tweak standlone.js conf
  1. run: `sed -i -e 's_127.0.0.1_0.0.0.0_g' /cloud9/configs/standalone.js`

### 7. Add workspace
  1. run: `mkdir /workspace`

### 8. (Optional) Clean up APT
  1. run: `apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*`

### 9. Run Cloud9
  1. (Option 1) run: `node /cloud9/server.js --listen 0.0.0.0 --port 80 -w /workspace`
  2. (Option 2: see all directories in C9) run: `node /cloud9/server.js --listen 0.0.0.0 --port 80 -w /`

### 10. Clone or Export Container as Backup Image