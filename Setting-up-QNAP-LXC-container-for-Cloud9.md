# Welcome to the QNAP-LXC-Cloud9 wiki!

## Thanks to [kdelfour](//github.com/kdelfour/cloud9-docker/) and [nightwing](//github.com/c9/core/issues/197#issuecomment-154320986) for figuring out how to setup Cloud9.

### 1. Create QNAP LXC Container
   Install Container Station from QNAP App Center (if not already installed)
  1. Open Container Station
  2. Click on Create Container
  3. Select Ubuntu LXC and click Create
  4. Change Auto Start to Off (Optional)
  5. Change CPU Limit to 50% (Optional)
  6. Change Memory Limit to 2048MB (Optional)
  7. Click Advanced Settings
    1. Under Network, add port forwarding

### 2. Setup port forwarding