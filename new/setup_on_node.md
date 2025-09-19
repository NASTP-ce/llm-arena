## Step 1: 
- Clone this Repository:
```bash
git clone https://github.com/b4rtaz/distributed-llama.git
```
## Step 2:
- Visit this page `
### Ubuntu 24.04 (Noble Numbat)
```bash
wget -qO- https://packages.lunarg.com/lunarg-signing-key-pub.asc | sudo tee /etc/apt/trusted.gpg.d/lunarg.asc
sudo wget -qO /etc/apt/sources.list.d/lunarg-vulkan-noble.list http://packages.lunarg.com/vulkan/lunarg-vulkan-noble.list
sudo apt update
sudo apt install vulkan-sdk
```
### Ubuntu 22.04 (Jammy Jellyfish)
```bash
wget -qO- https://packages.lunarg.com/lunarg-signing-key-pub.asc | sudo tee /etc/apt/trusted.gpg.d/lunarg.asc
sudo wget -qO /etc/apt/sources.list.d/lunarg-vulkan-jammy.list http://packages.lunarg.com/vulkan/lunarg-vulkan-jammy.list
sudo apt update
sudo apt install vulkan-sdk
```

## Step 3: 
- Make sure you are in the directory of the `distributed-llama` after cloning the repo you will see this directory in your current working directory. 
- Now run these commands For GPU: 
```bash
DLLAMA_VULKAN=1 make dllama
DLLAMA_VULKAN=1 make dllama-api
```
