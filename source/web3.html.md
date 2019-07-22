---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript

toc_footers:
  - <a href='https://www.meter.io/claim-your-meter/'>Request Test Tokens</a>
  - <a href='https://www.meter.io'>Meter.io</a>

search: true
---

# Web3


The Web3 class is a wrapper to house all Ethereum related modules.


## Initiating of Web3

Parameter | Default | Description
--------- | ------- | -----------
`provider` | `string|object` | A URL or one of the Web3 provider classes.
`net` | `net.Socket` | (optional) The net NodeJS package.
`options` | `object` | (optional) The Web3 :ref:`options <web3-module-options>`

```javascript

    import Web3 from 'web3';

    // "Web3.givenProvider" will be set in a Ethereum supported browser.
    const web3 = new Web3(Web3.givenProvider || 'ws://some.local-or-remote.node:8546', net, options);

```

# Web3.modules

This Static property will return an object with the classes of all major sub modules, to be able to instantiate them manually.

```javascript
  Web3.modules
```

> Returns a list of modules in an `Object`

```javascript
{
  Eth(provider, net, options),
  Net(provider, net, options),
  Personal(provider, net, options),
  Shh(provider, net, options),
}
```

Module | Type | Description
--------- | ------- | -----------
`Eth` | `Function` | Module for interacting with the Ethereum network see :ref:`web3.eth <eth>` for more.
`Net` | `Function` | Module for interacting with network properties see :ref:`web3.eth.net <eth-net>` for more.
`Personal` | `Function` | Module for interacting with the Ethereum accounts see :ref:`web3.eth.personal <eth-personal>` for more.
`Shh` | `Function` | Module for interacting with the whisper protocol see :ref:`web3.shh <shh>` for more.

.. include:: include_package-core.rst

# version

Property of the Web3 class.

```javascript
    web3.version
```

Contains the version of the `web3` wrapper class.

> Returns a `String` with the current version.

```javascript
"1.0.0"
```
