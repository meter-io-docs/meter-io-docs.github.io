---
title: DApps Using Meter

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript

toc_footers:
- <a href='./index.html'>Documentation Home</a>
- <a href='./meterify.dapps.html'>DApp Tutorials</a>
- <a href='./meterify.examples.html'>Examples</a>
- <a href='./meterify.mining.html'>Mining Guide</a>
- <hr>
- API Documentation
- <a href='./meterify.html'>meterify</a>
- <a href='./meterify.module.options.html'>meterify.module.options</a>
- <a href='./meterify.eth.html'>meterify.eth</a>
- <a href='./meterify.eth.subscribe.html'>meterify.eth.subscribe</a>
- <a href='.meterify.eth.Contract.html'>meterify.eth.Contract</a>
- <a href='.meterify.eth.Iban.html'>meterify.eth.Iban</a>
- <a href='.meterify.eth.personal.html'>meterify.eth.personal</a>
- <a href='.meterify.eth.accounts.html'>meterify.eth.accounts</a>
- <a href='.meterify.eth.ens.html'>meterify.eth.ens</a>
- <a href='.meterify.eth.abi.html'>meterify.eth.abi</a>
- <a href='.meterify.eth.net.html'>meterify.eth.net</a>
- <a href='./meterify.shh.html'>meterify.shh</a>
- <a href='./meterify.utils.html'>meterify.utils</a>
- <hr>  
- <a href='https://www.meter.io/claim-your-meter/'>Request Test Tokens</a>
- <a href='https://www.meter.io'>Meter.io</a>

search: true
---

# DApps Using Meter

DApps are decentralized applications that utilize blockchains to store their history of operation (e.g. transactions). They can also consist of functional code, called smart contracts, that is published to the blockchain. The same as any kind of application, a DApp will have some kind of an interface, which might be a graphical client, a command line client or an API.

At this time, DApps are generally related to categories such as finance, exchanges, and gambling, but social applications and games also exist. At the same time, there are numerous untapped opportunities to develop DApps for other categories that don't yet exist, or for which there are few DApps for at this time.

<a name="example-dapp"/>

## Developing an Example DApp

The Meter blockchain provides a great foundation for creating DApps, using common development tools that are also used for other blockchains. One prime example is that it is possible to utilize `Web3` with Meter using the `Meterify` library.

As with any app, a DApp needs an identified use case. In the blockchain world the most common use case is a transaction, where cryptocurrency is sent between two accounts. It is very easy to create an example of this kind of transaction using Web3 and the Meter blockchain, where Alice wishes to send some MTR and MTRG to Bob's account.  

There are two approaches below for building the example app on Linux, one with Docker and one without.

<a name="example-with-docker"/>

## Building the Example on Linux Using Docker

### Step 1: Ensure the latest version of `docker-compose` is installed.

```bash
$ sudo curl -L https://github.com/docker/compose/releases/download/1.24.1/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
$ sudo chmod +x /usr/local/bin/docker-compose
```

### Step 2: Check that docker-compose was installed correctly.

```bash
$ docker-compose --version
docker-compose version 1.24.1, build 4667896b
```

### Step 3: Create a project directory (e.g. `meter-dapp`).

```bash
$ mkdir meter-dapp
$ cd meter-dapp
```

### Step 4: Initialize the app directory.

```bash
$ npm init
```

### Step 5: Create a `docker-compose.yml` file.

A copy of this file can be found here: [examples/meter-dapp/docker-compose.yml](https://github.com/xiaohanzhu/docs/blob/master/examples/meter-daap/docker-compose.yml)

```
version: '3.5'
services:
  node:
    image: "node:10"
    user: "node"
    working_dir: /home/node/meter-daap
    volumes:
      - ./:/home/node/meter-daap
    command: >
      sh -c "rm -rf node_modules
            npm init -y &&
            npm install meterify --save &&
            rm -rf node_modules/*/.git/
            npm install web3@1.0.0-beta.37 --save &&
            npm install solc@0.4.24 --save &&
            node index.js"
```

### Step 6: Create a file called `index.js`.

This will initially test the connection to the testnet.

```js
const meterify = require("meterify").meterify;
const Web3 = require("web3");
const web3 = meterify(new Web3(), "http://test.meter.io:8669");
```

### Step 7: Run `docker-compose` to use the test application.

```bash
$ docker-compose up
```

If there are no errors the connection was successful.

### Step 8: Stop Docker using `Ctrl+C`.

```bash
Ctrl+C
```

Continue to *Building the Main App* below the next section.

<a name="example-no-docker"/>

## Building the Example on Linux Without Docker

### Step 1: Ensure Node.js version 10.15.1 or above is installed.

[Here is a guide](https://tecadmin.net/install-nodejs-with-nvm/#) on how to install Node.js and manage different versions.

### Step 2: Create a project directory (e.g. `meter-dapp`).

```bash
$ mkdir meter-dapp
$ cd meter-dapp
```

### Step 3: Initialize the app directory.

```bash
$ npm init
```

### Step 4: Install the app prerequisites.

- [meterify](https://www.npmjs.com/package/meterify)
- [web3](https://www.npmjs.com/package/web3/v/1.0.0-beta.37) version 1.0.0-beta.37
- [solc](https://www.npmjs.com/package/solc/v/0.4.24) version 0.4.24

```bash
npm install meterify --save
npm install web3@1.0.0-beta.37 --save
npm install solc@0.4.24 --save
```

### Step 5: Create a file called `index.js`.

This will initially test the connection to the testnet.

```js
const fs = require("fs");
const meterify = require("meterify").meterify;
const Web3 = require("web3");
const web3 = meterify(new Web3(), "http://test.meter.io:8669");
```

### Step 6: Run the test connection app.

```bash
$ node index.js
```

If the code above runs without any errors the connection was successful.

<a name="create-application-functions"/>

## Create the Application Functions

<!--For the example please refer to this asciinema:

![](./_media/meterify.svg "web3 meterify example") -->

Next, follow each step to add function and other code snippets `index.js`. The full file project files can also be found here:

* [examples/meter-dapp/index.js](https://github.com/xiaohanzhu/docs/blob/master/examples/meter-daap/index.js)
* [examples/meter-dapp/sample_token.sol](https://github.com/xiaohanzhu/docs/blob/master/examples/meter-daap/sample_token.sol)
* [examples/meter-dapp/docker-compose.yml](https://github.com/xiaohanzhu/docs/blob/master/examples/meter-daap/docker-compose.yml)

### Step 1:" Create two accounts, one for Alice and one for Bob.

```js
function createAccounts(accounts){
  console.log("Creating Accounts");

  for(key in accounts){
    accounts[key] = web3.eth.accounts.create();
    console.log("Account "+accounts[key].address+" Created.");
  }

  console.log("All Accounts Created");
  return accounts;
}
```

### Step 2: Add the account private keys for each account to the wallet.

```js
function addAccountsToWallet(accounts){
  console.log("Adding Accounts to Wallet");

  for(var key in accounts){
    web3.eth.accounts.wallet.add(accounts[key].privateKey);
    console.log("Added Private Key "+accounts[key].privateKey+" to Wallet");
  }

  console.log("Added All Accounts to Wallet");
  return;
}
```

### Step 3: Send MTR from one account to another.

*Note:* The unit in `meterify` is Wei, where 1 MTR = 10e18 Wei.

```js
function send_MTR(fromAddress,toAddress){
  console.log("Sending MTR");

  web3.eth.sendTransaction(
    {
      from: fromAddress,
      to: toAddress,
      value: '1000000000000000000',
      data: '00'
    }
  ).then(
    receipt => {}
  ).then(
    data => {
      console.log("MTR sent: "+JSON.stringify(data));
      next();
    }
  ).catch(function(error){
    console.log("Error: "+error);
  });
}
```

### Step 4: Send MTRG from one account to another.

*Note:* The unit in meterify is Wei, where 1 MTRG = 10e18 WeiG.

```js
function send_MTRG(fromAddress,toAddress){
  console.log("Sending MTRG");

  web3.eth.sendTransaction(
    {
      from: fromAddress,
      to: toAddress,
      value: '1000000000000000000',
      data: '01'
    }
  ).then(
    receipt => {}
  ).then(
    data => {
      console.log("MTRG sent: "+JSON.stringify(data));
      next();
    }
  ).catch(function(error){
    console.log("Error: "+error);
  });
}
```

### Step 10: Begin the function calling sequence.

This code can go either before or after the functions.

```js
var accounts = createAccounts({"bob":{}});

/* Alice should be a pre-existing account that already contains some MTR.
 * Add Alice's public and private keys to the following object.
 */
accounts.alice = {"address":"0x...","privateKey":"0x..."};
addAccountsToWallet(accounts);

send_MTR(accounts.alice.address, accounts.bob.address);
send_MTRG(accounts.alice.address, accounts.bob.address);

```

### Step 11: Run the application.

_Using Docker:_

```bash
$ docker-compose up
```

_Without Docker:_

```bash
$ node index.js
```

### Step 12 (Docker Only): Comment out dependency installation.

Do this after the first run in `docker-compose.yml` to stop repeated initialization and dependency installation on each Docker run.

```
version: '3.5'
services:
  node:
    image: "node:10"
    user: "node"
    working_dir: /home/node/meter-daap
    volumes:
      - ./:/home/node/meter-daap
    command: node index.js
#    command: >
#      sh -c "rm -rf node_modules
#            npm init -y &&
#            npm install meterify --save &&
#            rm -rf node_modules/*/.git/
#            npm install web3@1.0.0-beta.37 --save &&
#            npm install solc@0.4.24 --save &&
#            node index.js"
```
<a name="example-smart-contract"/>

## Load, Deploy, and Test a Smart Contract

The following modifications to the example demonstrate the use of a sample smart contract on the Meter blockchain. Again, follow the steps to add code snippets to the existing `index.js` file.

### Step 1: Load the sample smart contract.

The file can be found here: [examples/meter-dapp/sample_token.sol](https://github.com/xiaohanzhu/docs/blob/master/examples/meter-daap/sample_token.sol)

```js
function loadContract(file){
  console.log("Loading contract: "+file);
  const contractFile = fs.readFileSync(file).toString();
  const solc = require('solc');
  const compiledCode = solc.compile(contractFile);

  var data = {};

  data.token_abiDefinition = JSON.parse(compiledCode.contracts[':SAMPLEToken'].interface)
  let token_byteCode = compiledCode.contracts[':SAMPLEToken'].bytecode
  data.token_byteCode = "0x" + token_byteCode;

  console.log("Contract Loaded.");
  return data;
}
```

### Step 2: Deploy the contract byte code to blockchain.

```js
function deployContract(data,address){
  console.log("Deploying contract.");

  contractInstance = new web3.eth.Contract(data.token_abiDefinition)
  contractInstance.options.data = data.token_byteCode
  contractInstance.deploy(
    {
      arguments: [
        address,
        '1000000000',
        'Sample Token',
        '3',
        'STOKEN'
      ]
    }
  ).send(
    {
      from: address,
      gas: 4700000
    }
  ).then(
    (
      newContractInstance
    ) => {
      console.log("Contract deployed.");
      contractInstance.options.address = newContractInstance.options.address;
      registerEvents(contractInstance);
    }
  );
}
```

### Step 3: Register contract events.

Additionally, call some example functions within `contractReady` when the contract is ready.

```js
function registerEvents(contractInstance){
  contractInstance.events.allEvents(
    {}, (error, result) => {
      if (error) {
          console.log(error)
      } else {
        console.log("Contract Ready.");
          contractReady(result,contractInstance);
      }
  })
}

function contractReady(result,contractInstance){
  transferFrom(contractInstance, accounts.alice.address, accounts.bob.address);
}

```

### Step 4: Transfer cryptocurrency between two accounts.

```js
function transferFrom(contractInstance, fromAddress, toAddress){
  contractInstance.methods._transferFrom(
    fromAddress,
    toAddress,
    '9999'
  ).send(
    {
      from:fromAddress,
      gas: 4700000
    }
  ).then(
    data => {
      console.log(data)}
    ).catch(
      err => {console.log(err)}
  )
}
```

### Step 4: Get an account balance.

```js
function getAccountBalanceOf(contractInstance,address){
  contractInstance.methods.getAccountBalanceOf(
    address
  ).send(
    {
      from: address,
      gas: 4700000
    }).then(
      data => {
        console.log(data)
      }
    ).catch(err => {
      console.log(err)
    }
  )
}
```

### Step 5: Minting some coins.

```js
function mintToken(contractInstance,address){
  contractInstance.methods.mintToken(
    address,
    '99999999999999999999999'
  ).send(
    {
      from: address,
      gas: 4700000
    }
  ).then(
    data => {
      console.log(data)
    }
  ).catch(
    err => {
      console.log(err)
    }
  )
}

```

### Step 6: Add the `loadContract` and `deployContract` function calls.

```js
var accounts = createAccounts({"bob":{}});

/* Alice should be a pre-existing account that already contains some MTR.
 * Add Alice's public and private keys to the following object.
 */
accounts.alice = {"address":"0x...","privateKey":"0x..."};
addAccountsToWallet(accounts);

send_MTR(accounts.alice.address, accounts.bob.address);
send_MTRG(accounts.alice.address, accounts.bob.address);

var data = loadContract('sample_token.sol');

/* The following function requires some energy first. Uncomment when the Alice account has some.*/

deployContract(data, accounts.alice.address);
```

### Step 7: Run the application.

_Using Docker:_

```bash
$ docker-compose up
```

_Without Docker:_

```bash
$ node index.js
```
