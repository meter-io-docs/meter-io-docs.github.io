---
title: meterify.module.options

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

# meterify.module.options

> Example

```javascript

    import Web3 from 'web3';

    const meterify = require("meterify").meterify;

    const options = {
        defaultAccount: '0x0',
        defaultBlock: 'latest',
        defaultGas: 1,
        defaultGasPrice: 0,
        transactionBlockTimeout: 50,
        transactionConfirmationBlocks: 24,
        transactionPollingTimeout: 480,
        transactionSigner: new CustomTransactionSigner()
    }

    const web3 = new Web3('http://test.meter.io:8669', null, options);

    const meterify = meterify(web3, "http://test.meter.io:8669");
```


A module does provide several options for configuring the transaction confirmation workflow or for defining default values.
This document describes the available option properties on a module.


# defaultBlock


```javascript

    web3.defaultBlock
    web3.eth.defaultBlock
    web3.shh.defaultBlock
    ...
```

> Example:

```javascript
web3.eth.getBalance();
web3.eth.getCode();
web3.eth.getTransactionCount();
web3.eth.getStorageAt();
web3.eth.call();
new web3.eth.Contract() -> myContract.methods.myMethod().call();`
```

The default block is used for all methods which have a block parameter.
You can override it by passing the block parameter if a block is required.


Returns

The `defaultBlock` property can return the following values:

Value | Type | Description
--------- | ------- | -----------
a number | 'Number' | A block number
`genesis` | `String` | The genesis block
`latest` | `String` | The latest block (current head of the blockchain)
`pending` | `String` | The currently mined block (including pending transactions)

Default is `latest`


# defaultAccount


```javascript

    web3.defaultAccount
    web3.eth.defaultAccount
    web3.shh.defaultAccount
    ...
```

This default address is used as the default `"from"` property, if no `"from"` property is specified.

Returns

Type | Description
------- | -----------
`String` - 20 Bytes | Any Ethereum address. You need to have the private key for that address in your node or keystore. (Default is ``undefined``)

# defaultGasPrice

```javascript

    web3.defaultGasPrice
    web3.eth.defaultGasPrice
    web3.shh.defaultGasPrice
    ...
```

The default gas price which will be used for a request.

Returns

Type | Description
------- | -----------
`string` or `number` | The current value of the defaultGasPrice property.

# defaultGas


```javascript

    web3.defaultGas
    web3.eth.defaultGas
    web3.shh.defaultGas
    ...
```

The default gas which will be used for a request.

Returns

Type | Description
------- | -----------
`string` or `number` | The current value of the defaultGas property.

# transactionBlockTimeout

```javascript

    web3.transactionBlockTimeout
    web3.eth.transactionBlockTimeout
    web3.shh.transactionBlockTimeout
    ...
```

The `transactionBlockTimeout` will be used over a socket based connection. This option does define the amount of new blocks it should wait until the first confirmation happens.
This means the PromiEvent rejects with a timeout error when the timeout got exceeded.


Returns

Type | Description
------- | -----------
`number` | The current value of transactionBlockTimeout

# transactionConfirmationBlocks

```javascript

    web3.transactionConfirmationBlocks
    web3.eth.transactionConfirmationBlocks
    web3.shh.transactionConfirmationBlocks
    ...
```

This defines the number of blocks it requires until a transaction will be handled as confirmed.


Returns

Type | Description
------- | -----------
`number` | The current value of transactionConfirmationBlocks

# transactionPollingTimeout

```javascript

    web3.transactionPollingTimeout
    web3.eth.transactionPollingTimeout
    web3.shh.transactionPollingTimeout
    ...
```

The `transactionPollingTimeout`  will be used over a HTTP connection.
This option does define the amount of polls (each second) it should wait until the first confirmation happens.


Returns

Type | Description
------- | -----------
`number` | The current value of transactionPollingTimeout


# transactionSigner

```javascript

    web3.eth.transactionSigner
    ...
```


The `TransactionSigner` property does provide us the possibility to customize the signing process
of the `Eth` module and the related sub-modules.

The interface of a `TransactionSigner`:

```javascript

    interface TransactionSigner {
        sign(txObject: Transaction): Promise<SignedTransaction>
    }

    interface SignedTransaction {
        messageHash: string,
        v: string,
        r: string,
        s: string,
        rawTransaction: string
    }
```


Returns

Type | Description
------- | -----------
`TransactionSigner` | A JavaScript class of type TransactionSigner.



# setProvider

```javascript

    web3.setProvider(myProvider)
    web3.eth.setProvider(myProvider)
    web3.shh.setProvider(myProvider)
    ...
```

> Example

```javascript

    import Web3 from 'web3';

    const web3 = new Web3('http://localhost:8545');

    // or
    const web3 = new Web3(new Web3.providers.HttpProvider('http://localhost:8545'));

    // change provider
    web3.setProvider('ws://localhost:8546');
    // or
    web3.setProvider(new Web3.providers.WebsocketProvider('ws://localhost:8546'));

    // Using the IPC provider in node.js
    const net = require('net');
    const web3 = new Web3('/Users/myuser/Library/Ethereum/geth.ipc', net); // mac os path

    // or
    const web3 = new Web3(new Web3.providers.IpcProvider('/Users/myuser/Library/Ethereum/geth.ipc', net)); // mac os path
    // on windows the path is: '\\\\.\\pipe\\geth.ipc'
    // on linux the path is: '/users/myuser/.ethereum/geth.ipc'
```


Will change the provider for its module.

Note: When called on the umbrella package `web3` it will also set the provider for all sub modules `web3.eth`, `web3.shh`, etc.

Parameters

Type | Description
------- | -----------
`Object` or `String` | `provider`: a valid provider
`Net` | `net`: (optional) the node.js Net package. This is only required for the IPC provider.

Returns

`Boolean`


# providers

```javascript

    Web3.providers
    Eth.providers
    ...
```

> Example

```javascript

    const Web3 = require('web3');
    // use the given Provider, e.g in Mist, or instantiate a new websocket provider
    const web3 = new Web3(Web3.givenProvider || 'ws://localhost:8546');
    // or
    const web3 = new Web3(Web3.givenProvider || new Web3.providers.WebsocketProvider('ws://localhost:8546'));

    // Using the IPC provider in node.js
    const net = require('net');

    const web3 = new Web3('/Users/myuser/Library/Ethereum/geth.ipc', net); // mac os path
    // or
    const web3 = new Web3(new Web3.providers.IpcProvider('/Users/myuser/Library/Ethereum/geth.ipc', net)); // mac os path
    // on windows the path is: '\\\\.\\pipe\\geth.ipc'
    // on linux the path is: '/users/myuser/.ethereum/geth.ipc'
```


Contains the current available providers.

`Object` with the following providers:

Property | Name | Description
--------- | ------- | -----------
`Object` | `HttpProvider` | The HTTP provider is **deprecated**, as it will not work for subscriptions.
`Object` | `WebsocketProvider` | The Websocket provider is the standard for usage in legacy browsers.
`Object` | `IpcProvider` | The IPC provider is used node dapps when running a local node. Gives the most secure connection.



# givenProvider

```javascript
    Web3.givenProvider
    web3.eth.givenProvider
    web3.shh.givenProvider
    ...
```

> Example

```javascript

    web3.setProvider(Web3.givenProvider || 'ws://localhost:8546');
```


When using web3.js in an Ethereum compatible browser, it will set with the current native provider by that browser.
Will return the given provider by the (browser) environment, otherwise `null`.


Returns

Type | Description
------- | -----------
`Object` | The given provider set or `false`.


# currentProvider

```javascript

    web3.currentProvider
    web3.eth.currentProvider
    web3.shh.currentProvider
    ...
```

> Example

```javascript

    if (!web3.currentProvider) {
        web3.setProvider('http://localhost:8545');
    }
```

Will return the current provider.


Returns

Type | Description
------- | -----------
`Object` | The current provider set.




# BatchRequest

```javascript

    new web3.BatchRequest()
    new web3.eth.BatchRequest()
    new web3.shh.BatchRequest()
    ...
```

> Example

```javascript

    const contract = new web3.eth.Contract(abi, address);

    const batch = new web3.BatchRequest();
    batch.add(web3.eth.getBalance.request('0x0000000000000000000000000000000000000000', 'latest'));
    batch.add(contract.methods.balance(address).call.request({from: '0x0000000000000000000000000000000000000000'}));
    batch.execute().then(...);
```


Class to create and execute batch requests.

Parameters

none

Returns

Type | Description
------- | -----------
`Object` | Contains the following methods:

Method | Description
--------- | ------- | -----------
`add(request)` | To add a request object to the batch call.
`execute()` | Will execute the batch request.
