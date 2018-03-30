Homework (Setup an Ethereum Miner)

This weeks homework is to setup an Ethereum miner to familiarize yourself with this crucial part of the ecosystem. Remember to turn it off after you start it. This is very likely not a profitable venture right now as the price of Ether is so volatile. The point of this exercise is to get you familiar with the process of initiating a miner.

Setup an AWS account if you haven't yet here .

Then, the steps are as follows

Go to your EC2 console in AWS and change the zone to US-West (N Cali). This zone happens to be the cheapest for the type of instance we’ll be using, and also contains a community AMI that has all the required mining libraries already installed for instant use.
Under Instances, select Spot Instances and click ‘Request Spot Instances’.
Search for a community AMI called ami-e326daa7 and select it.  
Under Instance type choose g2.8xlarge.
Review and Launch!
How to start mining
To start mining, you’ll need an Ethereum wallet and to join a mining pool.

To generate a wallet, simply go to https://www.myetherwallet.com and follow the steps. By the end of the process, you’ll receieve a wallet address.

We’ll be using Dwarfpool for mining, which is rated in the top best mining pools. Feel free to use others if you like.

Simply SSH to your instance and type:

## SSH
chmod 400 ethermine.pem
ssh -i ethermine.pem ubuntu@ec2-54-219-143-56.us-west-1.compute.amazonaws.com

ethminer -G -F http://eth-eu.dwarfpool.com/0x64D5075c709eE3975d24A6B2edE15E3ae3B24C8f/imageproof@protonmail.com



Leave tmux session:
ctrl + b then d

attach to existing session:
tmux attach




> tmux
> ethminer -G -F http://eth-eu.dwarfpool.com/{WALLET ADDRESS}/{YOUR_EMAIL ADDRESS} --cl-local-work 256 --cl-global-work 16384
Tmux allows you to keep a process running after closing your SSH connection.

Ethminer is an Ethereum GPU mining worker. Entering your email address allows you to receive notifications on payouts. The other parameters are for mining optimizations.

That’s it!

You should soon see a DAG file generated and right afterward, your mining should start. To view your stats, simply go to https://dwarfpool.com/eth and in ‘Worker stats’ enter your wallet address.

For more information on Ether mining see the README of the official GitHub repository https://github.com/ethereum-mining/ethminer
