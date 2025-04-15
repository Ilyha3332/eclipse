# Eclipse BITZ PoW
## Guide to Bitz Miner (Inspired by https://x.com/0xMoei)
#You need:
- Eclipse wallet with >0.0005 ETh
- Min 1 CPU
- Ubuntu 22.04
## Install Dependecies
**1. Install Packages**
```bash
sudo apt-get update && sudo apt-get upgrade -y

sudo apt install screen curl nano  -y
```
**2. Install Rust**
```bash
 curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```
* When Prompted, press Enter and wait unti installation compelete.
```bash
source $HOME/.cargo/env
```
**3. Install Solana CLI:**
```bash
curl --proto '=https' --tlsv1.2 -sSfL https://solana-install.solana.workers.dev | bash
```
* Close and reopen your Terminal.
```
solana --version
```
* If you get `solana: command not found` RUN :
```bash
echo 'export PATH="/root/.local/share/solana/install/active_release/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```
```
solana --version
```

**4. Switch RPC**
```bash
solana config set --url https://eclipse.helius-rpc.com/
```
- Or
```bash
solana config set --url https://mainnetbeta-rpc.eclipse.xyz
```
- Or
```bash
solana config set --url https://bitz-000.eclipserpc.xyz
```
---

## Wallet CLI
### 1. Create a CLI wallet
```bash
solana-keygen new
```
* Set a password or skip by pressing `Enter`.
* Save your Seed-Phrase & Public-Key
* `Public-Key`: Is your node **Eclipse wallet address**.

### 2. Export `Private-key`

1- Find Keypair path:
```bash
solana config get
```
* It gives your Keypair path like this: `~/.config/solana/id.json`

2- Export `Private-key`:
```bash
cat ~/.config/solana/id.json
```
* The exported array is your `Private-Key`, Save it. It must include [123.....]

### 3. Import and Fund Node Wallet
* Import `Private-Key` into your `Backpack` wallet.
* Fund it with `ETH` on `Eclipse` Network

---

## Install Bitz
```bash
cargo install bitz
```

---

## Run Bitz Miner
### 1. Open a screen
By opening a screen, you can run any process in the background, so it won't get terminated if you closed your VPS. (Windows users must keep their terminal open)
```bash
screen -S bitz
```

### 2. Start Miner(Instead of 2 write number of your cores)
```bash
bitz collect 2
```
### 3. Start Miner with automatic rerun
1. Create file
```bash
nano ~/start_bitz.sh
```
2. Paste it(Instead of 2 write number of your cores)
```bash
while true
do
  echo "Starting Bitz node..."
  bitz collect --cores 2
  echo "Bitz node stopped. Restarting in 5 seconds..."
  sleep 5
done
```
3. Start this proccess
```bash
chmod +x ~/start_bitz.sh
```
4. Run it on your screen
```bash
screen -S bitz ~/start_bitz.sh
```
* Your Miner Node is Running successfully now.
* * detach screen: `Ctrl+A+D`
* return screen: `screen -r bitz`
* stop the node while in screen: `Ctrl+C`

### Usefull Commands
* You have to enter these out of the screen session Ctrl A+D

**Check account info:**
```bash
bitz account
```
**Claim Bitz to your Node Wallet:**
```bash
bitz claim
```
**Stake Bitz:**
```bash
bitz stake
```
**All Commands List:**
```bash
bitz -h
```
# Thank you for information to:
- https://github.com/0xmoei/eclipse/blob/main/README.md
- https://x.com/ArshiaXBT
# My X: https://x.com/brouk_16
