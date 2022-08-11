# Stake wars Fluxus 

This repository contain the steps and outputs from our node creation and development following the orientations in the stake-wars challenges.

&nbsp;
## Stake Wars: Challenge 001 and 002

- First of all, we created a wallet. The account was named as fluxus.shardnet.near and the dependencies like near-cli, python and rust were installed. All the commands used are bellow:
  
Installing node
```
curl -sL https://deb.nodesource.com/setup_18.x | sudo -E bash -  
sudo apt install build-essential nodejs
PATH="$PATH"
```
Installing near-cli
```
curl -sL https://deb.nodesource.com/setup_18.x | sudo -E bash -  
sudo apt install build-essential nodejs
PATH="$PATH"
```
Installing docker and python
```
sudo apt install python3
sudo apt install docker-ce
```
Installing building env
```
sudo apt install clang build-essential make
```
Installing rust
```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

- The account as created in https://wallet.shardnet.near.org/create. 

<p align="center">
  <img src="/img/wallet.png" />
</p>


- In sequence, we focused on deploying a node. So, the nearcore project was cloned and compile using cargo build. We also generate some files in our directory as config.json and node_key.json. After that, we setup the aws and started running the node.

    Then we logged in the near and setup the credentials to finally Start the validator node.
    The logs that prove we did it are bellow. As can be seen, everything is running as it should be.


<p align="center">
  <img src="/img/img1.png" />
</p>

The used commands for this step were:

Cloning repository
```
git clone https://github.com/near/nearcore
cd nearcore
git fetch
```

Building
```
cargo build -p neard --release --features shardnet
```

Generating initial files 
```
./target/release/neard --home ~/.near init --chain-id shardnet --download-genesis
```

Installing aws 
```
sudo apt-get install awscli -y
```

Running the node
```
cd ~/nearcore 
./target/release/neard --home ~/.near run
```

Starting the validator node
```
target/release/neard run
```

Enable neard
```
sudo systemctl enable neard
```

Starting neard
```
sudo systemctl start neard
```


&nbsp;
## Stake Wars: Challenge 003 ans 004

- With the goal of deploying a staking pool in our near account, we started the third challenge.
Running the given commands, a pool named fluxus.factory.shardnet.near was created.

Deploy pool
```
near call factory.shardnet.near create_staking_pool '{"staking_pool_id": "fluxus", "owner_id": "fluxus.shardnet.near", "stake_public_key": "<public key>", "reward_fee_fraction": {"numerator": 5, "denominator": 100}, "code_hash":"DD428g9eqLL8fWUxv8QSpVFzyHi1Qd16P8ephYCTmMSZ"}' --accountId="fluxus.shardnet.near" --amount=30 --gas=300000000000000
```

Depositing near
```
near call <pool_id> deposit_and_stake --amount 800 --accountId <accountId> --gas=300000000000000

```

<p align="center">
  <img src="/img/fluxus_factory.png" />
</p>


- It is possible to confirm our staked balance by using the get_account_staked_balance. The output of this view function in this moment is: 

```
near view <pool_id> get_account_staked_balance '{"account_id": "<accountId>"}'
```

<p align="center">
  <img src="/img/get_account_staked_balance.png" />
</p>


- After deploying the staking pool, we worked in monitoring node status.

    Calling get_accounts with the near cli, we can see some informations of our node and pool:

```
near view fluxus.factory.shardnet.near get_accounts '{"from_index": 0, "limit": 10}' --accountId fluxus.shardnet.near
```

<p align="center">
  <img src="/img/get_accounts.png" />
</p>


&nbsp;
## Stake Wars: Challenge 005