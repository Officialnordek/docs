---
description: For Nodes, Bootnodes and Validators
---

# Upgrade Guide

{% hint style="info" %}
This guide assumes that you have created your node using our [quickstart script](https://github.com/fuseio/fuse-network/blob/master/scripts/quickstart.sh). If you have built your own client using our specifications, make sure that your client matches the officially supported [client ](https://github.com/fuseio/fuse-network/blob/master/Dockerfile#L23)and that you are using the most up-to-date [chain spec](https://github.com/fuseio/fuse-network/blob/master/config/spec.json).
{% endhint %}

### Prerequisites

Before starting, make sure you have at least 20GB of free disk space, as the update will pull the latest database from our latest snapshot.

### Step 1 - CD to the location of quickstart.sh and update quickstart

```
cd <location of quickstart.sh>
wget -O quickstart.sh https://raw.githubusercontent.com/PrimalDev/Nordek/master/scripts/quickstart.sh
```

### Step 2 - Run quickstart and agree to upgrade

```
sudo ./quickstart.sh
Agree [Y] when prompted to upgrade
Wait for script to complete
```

### Step 3 - Verify Upgrade

* Check your node on our [health site](https://status.nordekscan.com).
* Your node should be online, and the client should be "OpenEthereum//v3.2.6-stable".
* Ensure that your node is connected to peers and is syncing or in sync.
