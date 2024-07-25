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

Phalcon can message the alerts into Telegram. The basic idea is first to create a Telegram Bot and then send the messages on behalf of this Telegram Bot. Users can add this Telegram Bot to any Telegram group or directly communicate it with a Telegram user.

Note that, in both cases, Phalcon will send messages on behalf of the Telegram Bot. We require two pieces of information.

* API Token: _**the token used to send messages on behalf of the bot.**_
* Chat ID: the chat ID. This information **denotes the destination of the alerts**, which can be a telegram group (which the Telegram bot joins) or a telegram user (with a direct conversation with the Bot).

{% hint style="info" %}
Related Resources:

[https://core.telegram.org/bots/features](https://core.telegram.org/bots/features)
{% endhint %}

### How to Create and Get a Bot's API Token?

Creating a bot is streamlined by Telegram’s Bot API, which gives the tools and framework required to integrate your code. You can also use BotFatther to create a bot.

Search "BotFather" on your Telegram, message [@BotFather](https://t.me/botfather) on Telegram to register a name for your bot, and receive its API token.

{% hint style="danger" %}
_Your bot token is its unique identifier – store it in a secure place and only share it with people who need direct access to the bot. Everyone who has your token will have complete control over your bot._
{% endhint %}

<figure><img src=".gitbook/assets/image (5).png" alt="" width="375"><figcaption></figcaption></figure>

### How to Get the Chat ID

#### The Chat ID of a Telegram Group

If you have added the bot to a Telegram group, we need to know the chat ID of the group since Phalcon's alerts will be sent to the group.&#x20;

**Option 1: Use a @getmyid\_bot**

Invite a bot named  [https://t.me/getmyid\_bot](https://t.me/getmyid\_bot) into the Telegram group, and the Chat ID will be automatically returned by the bot (_**remember to remove the bot after obtaining the Chat ID**_).

<figure><img src=".gitbook/assets/image (1) (1).png" alt="" width="337"><figcaption></figcaption></figure>

Note that, there are other similar bots available, use the one you are familiar with.

#### **Option 2: Use Telegram API**

* Step 1: Invite the bot you created to a designated Telegram group, and then send a message in that Telegram chat.
* Step 2: Enter https://api.telegram.org/bot<mark style="color:red;">**Token**</mark>/getUpdates in your browser. Replace the red text with the API token provided by @BotFather, and you will receive the following JSON.

{% code overflow="wrap" %}
```
"my_chat_member": {
    "chat": {
        "id": -41XXXXXXXX,
        "title": "XXXXXXX",   <--- This is the Telegram group name you created
        "type": "group", 
        "all_members_are_administrators": false
    },
}   
```
{% endcode %}

* Step 3: Find the Chat ID from "chat:" id":-41XXXXXXXX.

#### The Chat ID of a Direct Telegram Conversation

The message can also be sent to a direct telegram conversation with a user. Let's say the user is @TESTUSER, and he/she can directly communicate with this bot.

* Step 1: Send a message to the Telegram Bot, e.g., `hello`.

<figure><img src=".gitbook/assets/image (2) (1).png" alt="" width="375"><figcaption></figcaption></figure>

* Step 2: Enter https://api.telegram.org/bot<mark style="color:red;">**Token**</mark>/getUpdates in your browser. Replace the red text with the API token provided by @BotFather, and you will receive the following JSON. Find the `hello` message you just sent in the returned JSON.

```
"message": {
    "message_id": 9,
    "from": {
        "id": 14xxxxxxxx,    <--- The chat ID of TESTUSER
        "is_bot": false,
        "first_name": "TEST",  
        "last_name": "USER",
        "username": "XXXXX",
        "language_code": "en"
    },
    "date": 1707293332,
    "text": "hello"          <-- The hello message
}
```

Step 3: Find the Chat ID that matches the message `hello`.
