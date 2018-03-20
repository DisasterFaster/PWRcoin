### PWR Coin <img src="https://d25lcipzij17d.cloudfront.net/badge.svg?id=gh&type=6&v=1.0.0.0&x2=0">

<p style="text-align:center;"><img src="https://pwr-coin.com/wp-content/uploads/2018/02/PWR-Coin-1.jpg"></p>

**Important Notice:** While Power Coin is a great coin it suffers some nearly fatal issues that must be addressed. Without getting overly technical let's simply say that the code has issues which create an out of control staking situtation. Over time this has led to broken wallets, negative balances, exchange de-listings, coin devaluation and other problems. 

At the moment it appears that the best path to healing this coin will include a major rebranding, a new digital footprint, code rework and fixes all followed by a paid marketing push. The current development team is already in motion handling this variety of tasks and will give new updates as they become available.

**Development Updates**

  * New block explorer https://blockexplorer.pwr-coin.com/
  * New website is being developed https://pwr-coin.com
  * New ANN at BitcoinTalk https://bitcointalk.org/index.php?topic=2868184.0
  * You can buy and sell PWR coin at CryptoHub Exchange at https://cryptohub.online/market/PWR/
  * You can follow the PWR coin market cap statistics at https://cryptocapworld.com/coin/PWR
  * Follow us on Facebook at https://www.facebook.com/pwrcoin/
  * Follow us on Twitter at https://twitter.com/pwr_coin
  * Follow us on Google Plus at https://plus.google.com/u/0/b/111766350022342218047/111766350022342218047
  * Follow us on YouTube at https://www.youtube.com/channel/UCVb0ZIaNjIjZc6HLE0RwVlg
  * Join our Discord channel at https://discord.gg/8jhcqqs

**Current tasks that are being worked on include:**

 * New block explorer - Completed
 * New Professionally Managed Github Repository – Completed
 * New ANN Announcement – Completed
 * New Name And Tagline – Completed
 * Listing At A New Market Cap Site – Completed
 * New Social Pages At Facebook, Twitter, Google Plus, YouTube & Discord – Done
 * New Logo – Completed
 * Listing At A New Exchange – Completed
 * New Social Media Graphics – Completed
 * Review And Analysis Of Existing Code Deficiencies – Completed
 * New Website – In Progress
 * Set Up VPS Node For TestNet Testing – In Progress
 * New RoadMap – On The Do List
 * 2nd Block Explorer – On The Do List
 * Multiple VPS Seed Nodes – On The Do List
 * Code Rework & Release Of New Binaries – On The Do List
 * New White Paper – On The Do List

**Important Note:** *The current development team handling the tasks listed above have no connection to nor assocation with any other group and specifically the individual or group that has been conducting a swap of these coins for tokens on the Waves platform.*


**PWR coin (PWR) Old Specifications**

```
Name: PWR coin
Ticker: PWR
Powercoin Maturity: 30 Blocks
Block Size: 8MB
Block time: 60 seconds
Algo: Nist5 (Quite,Low Consumption,GPU Optimized with BLAKE - Grøstl - JH - Keccak - Skein)
Pow supply: 50021000 (25 Millions Distribuited by Airdrop Form Application)
        + Dpos (Power Stages) with 3200000 PWR minted first 60 days Dpos + Fixed Pos subsidy at 5% Yearly
Pos: 5% Annually - Minimum Stake Age: 8 Hours - Max Stake Age: Unlimited
Powercoin Distribution: 50% Airdrop Form Application + 50% PoW
Port: 4504
Rpcport: 4502 


Block Reward:
Blocks 0-10: Airdrop PWR
Blocks 10-100 0 PWR
350 PWR first 43100 Blocks
230 PWR until PoW end,Block 86400
```

```
PowerPos:
Blocks: 86000-86400: 5 PWR (Warm-Up)
Blocks: 86400-100800: 10 PWR (1 Stage)
Blocks: 100800-115200: 25 PWR (2 Stage)
Blocks: 115200-129600: 50 PWR (3 Stage)
Blocks: 129600-144000: 100 PWR (Full Power)
Blocks: 144000-158400: 20 PWR (5 Stage)
Blocks: 158400-172800: 15 PWR (6 Stage)
Blocks: 172800 > 5% Fixed Yearly 
Approx: 2 Months PowerPoS
```

## PWR Coin Daemon Compile on Ubuntu 16.04.4 x 64 - Tested 3-19-2018

Install Dependencies
---------------------
When running the commands in the build instructions below, copy and paste one line and let it complete before running the next line. Watch for prompts in case you need to respond to a requested input and also to watch for any errors if they occur.

```
sudo apt-get install build-essential
sudo apt-get update
sudo apt-get install libssl-dev
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install libboost-all-dev
sudo apt-get install libqrencode-dev
sudo apt-get install libminiupnpc-dev
sudo apt-get install software-properties-common
sudo add-apt-repository ppa:bitcoin/bitcoin
sudo apt-get update
sudo apt-get install libdb4.8-dev libdb4.8++-dev
sudo apt-get install libqt5gui5 libqt5core5a libqt5dbus5 qttools5-dev qttools5-dev-tools libprotobuf-dev protobuf-compiler
sudo apt-get install make
sudo apt-get install g++
sudo apt-get update
```

Get The Source Code And Compile
---------------------

```
git clone https://github.com/PWRcoin/PWRcoin.git pwrcoin
cd pwrcoin/src
make clean -f makefile.unix
make -f makefile.unix

```
**Note:** *It's possible the compile may fail and give an error message that you have run out of memory. If this happens please follow the steps below to create a swap file:*  

```
fallocate -l 2G /swapfile
chown root:root /swapfile
chmod 0600 /swapfile
sudo bash -c "echo 'vm.swappiness = 10' >> /etc/sysctl.conf"
mkswap /swapfile
swapon /swapfile
```
After creating the swap file above run the folowing commands again:

```
make clean -f makefile.unix
make -f makefile.unix
```

Setup And Launch The Daemon
---------------------

```
./powercoind -daemon -txindex=1
```
**Note:** *The above command will launch the daemon and create some necessary files however it will fail with a complaint that your powercoin.conf file is not setup properly:*

Navigate to the default location where the powercoin.conf file will need to be setup at:  ``` /root/.powercoin/ ```
If you have problems finding the correct location: ``` find /root -iname “wallet.dat” ```

Once you are inside the ``` .powercoin/ ``` directory you will need to create and setup the powercoin.conf file:

```
sudo nano powercoin.conf
```

The bare minimum powercoin.conf configuration required to get the daemon running is:

```
rpcuser=PutRpcUserHere
rpcpassword=PutPasswordHere
```
**Note:** *The rpcuser and rpcpassword can't be the same they must be different from one another!*

While each powercoin.conf file may need different setup depending on what you are doing a typical configuration for something like a blockexplorer might look like this:

```
rpcuser=PutRpcUserHere
rpcpassword=PutPasswordHere
listen=1
server=1
maxconnections=500
addnode=SomeIPAddressHere
addnode=SomeIPAddressHere
addnode=SomeIPAddressHere
addnode=SomeIPAddressHere
addnode=SomeIPAddressHere
```

Now that you have created, setup and saved the powercoin.conf file you should set it to read only:

```
sudo chmod 400 powercoin.conf
```

Now you will need to navigate back to the directory where the PWR coin daemon is. If you have problems finding the correct location: ``` find /root -iname “powercoind” ``` 

Once you are in the proper directory where the daemon is located you are ready to launch again:

```
./powercoind -daemon -txindex=1
```

You should get a message that says, "powercoin serving starting."

Give it a few seconds and check that it is running:

```
./powercoind getinfo
```
You should get a full response with all of the getinfo output. If you take a look at "blocks": make a note of the block number.

Let the daemon run for several more minutes and once again check it with:

```
./powercoind getinfo
```

You should compare the block number now to the last one you saw and you should see it climbing higher because it is synchronizing the blockchain. If the number stays at 0 you need to revisit your powercoin.conf file and try some different addnodes. A good place to get those is here https://cryptohub.online/glossary/ajax_coin_nodes/58/ or here https://blockexplorer.pwr-coin.com/network

Let your daemon run and check it periodically. Once the block number in getinfo matches the block number on the block explorer you are fully synchronized. If you notice that your daemon reaches a certain block height but then stops synchronizing for any reason it's always a good idea to try stopping and restarting it using the commands listed below:

If for any reason you want to stop the daemon from running use this command:

```
./powercoind stop
```

If for any reason you need to start the daemon use this command:

```
./powercoind -daemon -txindex=1
```




