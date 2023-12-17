
## Step-by-Step Guide to Running a Zora Node

**Title**: How to Run a Zora Node: A Comprehensive Guide

**Introduction**: Discover how to contribute to the Zora Network by setting up your own node. This guide will take you through each step, ensuring a smooth setup.

**VPS Requirements**: Start by ensuring your VPS is equipped with a minimum of 
> 8 GB RAM - 16 GB

> 100 GB - 200 Gb of NVMe space

**Installing Dependencies**
   

	sudo apt-get update 
	sudo apt install curl build-essential git screen jq pkg-config libssl-dev libclang-dev ca-certificates gnupg lsb-release -y 
    
    curl gnupg sudo install -m 0755 -d /etc/apt/keyrings 
    
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg 
    
    sudo chmod a+r /etc/apt/keyrings/docker.gpg 
            
    echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \ $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null 
    
    sudo apt-get update 
    sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

**Create Eth RPC on Alchemy**:
1.  Sign up or log in to your Alchemy account.
2.  Navigate to the dashboard and create a new app.
3.  Choose the Ethereum network for your app (Mainnet).
4.  Name your app and select the environment (Production).
5.  After creating the app, go to the app's details page.
6.  Here, you'll find your new Ethereum RPC URL and replace in zora configuration.

**Configuring Zora Node**:
	
    screen -S zora
    
    echo "export CONDUIT_NETWORK=zora-mainnet-0" >> ~/.bashrc
    
    git clone https://github.com/conduitxyz/node.git
    cd node
 
    export CONDUIT_NETWORK=zora-mainnet-0"
    ./download-config.py zora-mainnet-0
    cp .env.example .env
    nano .env

    
   Replace OP_NODE_L1_ETH_RPC ETH rpc url copied from Alchemy.  
   >    OP_NODE_L1_ETH_RPC=https://eth-mainnet.g.alchemy.com/v2/**REPLACE_WITH_YOUR_KEY**

 - Save File by pressing ctrl + x 
 - Type `Y` 
 - Enter

### Start Zora Node

    docker compose up --build        
    ctrl + a + d

> Follow [ShineCryptic](https://twitter.com/ShineCryptic).
