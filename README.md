# The Airline - An Ethereum learning DAPP

**Source template for my Udemy Ethereum training course at Udemy**

**If you want to get the final version of the code you can check the [final](https://github.com/CarlosLanderas/udemy-ethereum-the-airline/tree/final) branch**

<img src="http://introtocrypto.com/wp-content/uploads/2017/08/ether@2x.png" height="128" width="128">

> npm install --global windows-build-tools
> npm install solc@0.4.24 --save-dev
> npm install web3@1.0.0-beta.35 --save-dev
> npm install chalk --save-dev
> npm install mocha@5.2.0 --save-dev
> npm install truffle-hdwallet-provider@0.0.6 --save-dev

* After run npm start.

--> inside the chrome developer tools write this:

** ************IMPORTANTE!!!************
**    		ethereum.enable() 		****
** *************************************

> truffle deploy --reset --network development or rinkeby
> truffle networks
> truffle console --network development
> truffle migrate -f 2 --network rinkeby

# Notes:
-- https://iancoleman.io/bip39/  (Mnemonic Code Converter) 

Ethereum Test Network
=====================
Main => 1
Morden => 2 deprecated
Ropsten => 3
Rinkeby => 4
Kovan => 42

Subscribe event from Metamask to web
====================================
this.web3.currentProvider.publicConfigStore.on('update', async function(event){
            this.setState({
                account: event.selectedAddress.toLowerCase()
            }, () => {
                this.load();
            });
        }.bind(this));

Truffle-config.js
=================
module.exports = {
	networks: {
		development: {
			host: 'localhost',
			port: 7545,
			network_id : '*',
			gas: 5000000
		}
	},
    ropsten: {
      provider: () =>
        new HDWalletProvider(process.env.MNEMONIC, `https://ropsten.infura.io/v3/${process.env.INFURA_API_KEY}`),
      network_id: '3',
      gasPrice: 25000000000
    },
    rinkeby: {
      provider: () => new HDWalletProvider(process.env.MNEMONIC, `https://rinkeby.infura.io/v3/${process.env.INFURA_API_KEY}`),
      network_id: '4'
    },
    solc: {
      optimizer: {
        enabled: true,
        runs: 200
      }
    }
}  