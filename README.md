# Stake wars Fluxus 

This repository contain the steps and outputs from our node creation and development following the orientations in the stake-wars challenges.

&nbsp;
## Stake Wars: Challenge 001 and 002

- First of all, we created a wallet.The account was named as fluxus.shardnet.near and the dependencies like near-cli, python and rust were installed.

![alt text](/img/wallet.png)

- In sequence, we focused on deploying a node. So, the nearcore project was cloned and compile using cargo build. We also generate some files in our directory as config.json and node_key.json. After that, we setup the aws and started running the node.

    Then we logged in the near and setup the credentials to finally Start the validator node.
    The logs that prove we did it are bellow:


![alt text](/img/img1.png)
s
as can be seen, everything is running as it should be.

&nbsp;
## Stake Wars: Challenge 003 ans 004

- With the goal of deploying a staking pool in our near account, we started the third challenge.
Running the given commands, a pool named fluxus.factory.shardnet.near was created.

![alt text](/img/fluxus_factory.png)

- It is possible to confirm our staked balance by using the get_account_staked_balance. The output of this view function in this moment is: 

![alt text](/img/get_account_staked_balance.png)


- After deploying the staking pool, we worked in monitoring node status.

    Calling get_accounts with the near cli, we can see some informations of our node and pool:

![alt text](/img/get_accounts.png)


&nbsp;
## Stake Wars: Challenge 005