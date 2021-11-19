
# raptoreum-cli wallet guide

  

This will guide you through the basic setup and usage of raptoreum-cli

  
  

## Setup

### 1) Install

1) Head to https://github.com/Raptor3um/raptoreum/releases

2) Download raptoreum core and extract it

3) Open the extracted folder in Terminal

4) Run `./raptoreumd --daemon`

5) Run `./raptoreum-cli` to execute commands

  

Once you are up and running you can use `./raptoreum-cli -?` to get a list of available commands

### 2) Sync

- If you are running the wallet for the first time it may take several minutes to an hour to sync

-  **The wallet must sync fully to the current network block height before you can see your current balance or send funds from it!**

You can always check the network block height at: [https://explorer.raptoreum.com/](https://explorer.raptoreum.com/)

![Block heights](https://i.imgur.com/ua6uq52.png)

  

To check sync progress execute ``./raptoreum-cli getblockcount`` and compare the block counts.

Or `./raptoreum-cli getblockchaininfo` and look at "verificationprogress". (Its synced when it reaches 1)

  

## Using the wallet

### 1) Encrypting & Backup (Recommended)

  

**A) Encrypting**

- Private keys are stored in your `wallet.dat`, when you first start raptoreum core the wallet gets generated without encryption.

1) To encrypt your wallet run:

`./raptoreum-cli encryptwallet "Your password"`

2) After the wallet gets encrypted the raptoreum core server will stop, you need to start it up again!

3) To unlock wallet run:

`./raptoreum-cli walletpassphrase "Your password" 60` (This will unlock the wallet for 60 seconds)

  

**B) Backup**

- If you encrypted your wallet you will need to unlock it before creating backups!

1) To backup **Single Address Private Key:**

`./raptoreum-cli dumpprivkey ADDRESS`

  

2) To backup **Entire Wallet All Keys:**

`./raptoreum-cli dumpwallet FILENME` (This will dump all of your keys to a text file)

  

### 2) Wallet status (Balance ..etc)

![getwalletinfo](https://i.imgur.com/bCW9sCk.png)

To get information about your wallet run:

`./raptoreum-cli getwalletinfo`

Alternatively you can use `./raptoreum-cli getbalance` to only display your balance.

  

**Balances:**

- "balance" = Total confirmed balance of the wallet

- "privatesend_balance" = PrivateSend balance

- "unconfirmed_balance" = Total unconfirmed balance of the wallet

- "immature_balance" = Total immature balance of the wallet

- "txcount" = Total number of transactions in the wallet

  

### 3) Send
- If you encrypted your wallet you will need to unlock it before sending!

To send an x amount of RTM to a given address use:

`./raptoreum-cli sendtoaddress "address" ammount`

Example:

`./raptoreum-cli sendtoaddress "XwnLY9Tf7Zsef8gMGL2fhWA9ZmMjt4KPwG" 0.1`


Arguments:
1) "address" (string, required) The raptoreum address to send to.
2) "amount" (numeric or string, required) The amount in RTM to send. eg 0.1
3) "comment" (string, optional) A comment used to store what the transaction is for.
4) "comment_to" (string, optional) A comment to store the name of the person or organization
5) subtractfeefromamount (boolean, optional, default=false) The fee will be deducted from the amount being sent.
6) "use_ps" (bool, optional, default=false) Use PrivateSend funds only
7) conf_target (numeric, optional) Confirmation target (in blocks)
8) "estimate_mode" (string, optional, default=UNSET) The fee estimate mode, must be one of: "UNSET" "ECONOMICAL" "CONSERVATIVE"
  

### 4) Receive
- To receive RTM you need to get a new receive address.

To do get a new receive address run:

`./raptoreum-cli getnewaddress`

![Grabbing a new address](https://i.imgur.com/gRvLrJI.png)

### 5) Transactions
You can list the last 10 transactions by running:

`./raptoreum-cli listtransactions`

Alternatively you can specify the number of transactions to list:

`./raptoreum-cli listtransactions 100` (This will list the last 100 transactions)

## Help
- You can use  `./raptoreum-cli help` to get a list of all available commands.
- You can also use `./raptoreum-cli help "command"` for help regarding a specific command.
