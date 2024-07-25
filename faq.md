# FAQ

## How to Generate Raw Transaction

Phalcon Block supports various automated blocking methods, allowing users to submit signed raw transactions to the system.&#x20;

When the Phalcon Block system meets the triggering conditions, it automatically sends the signed raw transaction to perform further actions, e.g., **pausing** the protocol or other activities.

This document shows how to generate a signed raw transation.

### JavaScript

#### Install the Web3 library

```
npm install web3
```

#### Execute the script

The following is a sample script to show how to get a raw transaction using the Web3 JavasScript library.&#x20;

Note that this script is for demo purposes. Some variables, e.g., endpoint URL, gasPrice, and number of generated raw transactions, must be changed accordingly.

```javascript
const { Web3 } = require('web3');

async function signPauseTransaction(gasLimit,gasPrice,i) {
  let contractInstance = new web3Instance.eth.Contract(abi, contractAddr);
  let txCount = await web3Instance.eth.getTransactionCount(senderAddr);
  const txObj = {
      gasLimit: Web3.utils.toHex(gasLimit),
      gasPrice: Web3.utils.toHex(gasPrice),
      to: contractAddr,
      nonce:  txCount + i,
      data: contractInstance.methods.pause().encodeABI()
  }
  let tx = await web3Instance.eth.accounts.signTransaction(txObj, privateKey);
  console.log(txObj.nonce,":",tx.rawTransaction);
}


const privateKey = ""; //Private key of sender address
const senderAddr = ""; //Sender address
const contractAddr = ""; //Contract address
const gasLimit = 100000; //gasLimit
//change the gasPrice if needed
const gasPrice = 51 * 1e9; //gasPrice
//change the URL
const web3Instance = new Web3("https://binance.llamarpc.com");
//change to the ABI of your contract
const abi = [{"anonymous":false,"inputs":[{"indexed":true,"internalType":"address","name":"previousOwner","type":"address"},{"indexed":true,"internalType":"address","name":"newOwner","type":"address"}],"name":"OwnershipTransferred","type":"event"},{"anonymous":false,"inputs":[{"indexed":false,"internalType":"address","name":"account","type":"address"}],"name":"Paused","type":"event"},{"anonymous":false,"inputs":[{"indexed":false,"internalType":"address","name":"account","type":"address"}],"name":"Unpaused","type":"event"},{"inputs":[{"internalType":"address","name":"","type":"address"},{"internalType":"address","name":"","type":"address"}],"name":"balances","outputs":[{"internalType":"uint256","name":"","type":"uint256"}],"stateMutability":"view","type":"function"},{"inputs":[{"internalType":"address","name":"tokenAddress","type":"address"},{"internalType":"uint256","name":"amount","type":"uint256"}],"name":"deposit","outputs":[],"stateMutability":"nonpayable","type":"function"},{"inputs":[],"name":"owner","outputs":[{"internalType":"address","name":"","type":"address"}],"stateMutability":"view","type":"function"},{"inputs":[],"name":"pause","outputs":[],"stateMutability":"nonpayable","type":"function"},{"inputs":[],"name":"paused","outputs":[{"internalType":"bool","name":"","type":"bool"}],"stateMutability":"view","type":"function"},{"inputs":[],"name":"renounceOwnership","outputs":[],"stateMutability":"nonpayable","type":"function"},{"inputs":[{"internalType":"address","name":"newOwner","type":"address"}],"name":"transferOwnership","outputs":[],"stateMutability":"nonpayable","type":"function"},{"inputs":[],"name":"unpause","outputs":[],"stateMutability":"nonpayable","type":"function"},{"inputs":[{"internalType":"address","name":"tokenAddress","type":"address"},{"internalType":"uint256","name":"amount","type":"uint256"}],"name":"withdraw","outputs":[],"stateMutability":"nonpayable","type":"function"}];

//Print transactions with consecutive Nonce values.
for (var i = 0; i < 5; i++) { 
    signPauseTransaction(gasLimit, gasPrice, i);
}
```

### Python

To add.

## How to Setup a Telegram Bot

Please refer to this [document](faq.md#how-to-setup-a-telegram-bot).

