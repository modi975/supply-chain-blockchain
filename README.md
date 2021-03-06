# Supply Chain Dapp

## Goal

To provide a secured and public access to all the transactions over blockchain network. Implementation of a supply chain management smart contract deployed on a test blockchain running on a local network. 

## Required dependencies

### A running node

You must run a node on your computer, whether its a real or virtual one. For development speed reasons, the best choice is to use testrpc because you have as much ether as you want and don't need to mine transactions.

#### Install instructions
Install following packages to get started -
- Install ```MetaMask 3.5.2``` Chrome Extension. [Github Releases](https://github.com/MetaMask/metamask-extension/releases)
- Install Node JS. [NodeJS](https://nodejs.org/en/)
- ```npm install -g node-gyp```
- ```npm install -g ethereum-testrpc```
- ```npm install -g truffle```
- ```npm install express@4.16.4```
- ```npm install cors@2.8.4```
- ```npm install fs@0.0.1-security```
- ```npm install path@0.12.7```
- ```npm install solc@0.4.25```

##### Windows

[The ethereumjs-testrpc package needs much more things to be installed on your machine to work on Windows.](https://github.com/ethereumjs/testrpc/wiki/Installing-TestRPC-on-Windows)

If you can't afford this, we've covered you with [*Vagrant*](https://www.vagrantup.com/). This piece of software allows you to run a lightweight linux virtual machine in the terminal. Thus, it uses much less power than a full VM and you can still enjoy your Windows environment and tools you are used to, while providing you linux compatibility for terminal tools.

To do so, it's as easy as:

- [**Downloading and installing Vagrant**](https://releases.hashicorp.com/vagrant/1.9.2/vagrant_1.9.2.msi?_ga=1.13795955.512399365.1487957654)
- Run ```vagrant up``` in a terminal opened at the project root. It may take some time as it must download an ubuntu ISO the first time it runs.
- Then run ```vagrant ssh```. If it doesn't work (it probably won't in fact) you can use **Git bash** if you already have it on your computer. If you don't, [follow those instructions](http://tech.osteel.me/posts/2015/01/25/how-to-use-vagrant-on-windows.html).

And that's it ! Now you can run ```testrpc``` and you should see your node running.

### Truffle - Compile & Migrate contracts to the blockchain

```
sudo npm install -g truffle
```

> **Note :** ```npm install -g truffle``` on Windows.

## Instructions

### Setting up the devTools and client dependencies

```
npm install
```

> **Note :** If install fails on windows (particularly if node-gyp is the issue), run Powershell as administrator and run ```npm install -g windows-build-tools```. It will allow you to install and use native node packages.

### Run your ethereum node

#### With testrpc

- ```testrpc --account="0x....., 10000000000000000000"``` you can get account address from MetaMask Extenstion
- ```truffle compile``` and ```node server.js``` from contract-server dir
> Visit http://localhost:3000 to view the compiled smart contract.

#### With Geth

##### Locally

- [Install Ethereum on your machine](https://github.com/ethereum/go-ethereum/wiki/Building-Ethereum)
- ```npm run geth``` to initialize and run the ethereum node with geth console
- ```personal.unlockAccount("ACCOUNT_TO_UNLOCK_ADDRESS", "pass")``` (see Note if you don't get it)
- ```miner.start()```

**Note :** At least the first time, you need to run those commands to create an account to mine on

- ```personal.newAccount("pass")```
- ```personal.unlockAccount("ACCOUNT_ADDRESS", "pass")```

### Deploy the smart contracts to the node

In another terminal, run ```truffle compile``` and then ```truffle migrate --reset```

**Warning here:** You have to re-run those commands when you modify your contracts so that they are re-deployed to the blockchain.

> **Note :** There is an experimental watcher that launch these commands when you save a contract.
> It may not work but it's worth the shot : ```npm run watch-contracts```

### Running the client app

With your node running and the smart contracts deployed to it, run in terminal ```npm run start``` from contract-client dir.

You're done !
> Visit http://localhost:8080 to interact with web application.

## FAQ

* __Why is there both a truffle.js file and a truffle-config.js file?__

    Truffle requires the truffle.js file be named truffle-config on Windows machines. Feel free to delete the file that doesn't correspond to your platform.


* __How can I create app with react and truffle?__

    You can recreate this project with [truffle-box-react](https://github.com/truffle-box/truffle-box-react/) which is a marriage of [Truffle](http://truffleframework.com/) and a React setup created with [create-react-app](https://github.com/facebookincubator/create-react-app/blob/master/packages/react-scripts/template/README.md). Either one would be a great place to start!
