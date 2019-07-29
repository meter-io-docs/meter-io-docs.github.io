---
title: Meterify

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript

toc_footers:
  - <a href='./meterify.bzz.html'>meterify.bzz</a>
  - <a href='./meterify.eth.html'>meterify.eth</a>
  - <a href='./meterify.shh.html'>meterify.shh</a>
  - <a href='./meterify.utils.html'>meterify.utils</a>
  - <hr>
  - <a href='./meterify.utils.html'>DApp Tutorials</a>
  - <a href='./meterify.utils.html'>Examples</a>
  - <a href='./meterify.utils.html'>Mining Guide</a>
  - <hr>  
  - <a href='https://www.meter.io/claim-your-meter/'>Request Test Tokens</a>
  - <a href='https://www.meter.io'>Meter.io</a>

search: true
---

# meterify

The `meterify` package is a wrapper to house all Meter related modules, to interact with a Meter blockchain and deployed smart contracts.

`meterify` depends on the `web3.js` library. Developers will work primarily with the `meterify.eth` module in the vast majority of cases.

> Example

```javascript
const meterify = require("meterify").meterify;
const Web3 = require("web3");
const web3 = meterify(new Web3(), "http://test.meter.io:8669");
```

Property | Type | Description
--------- | ------- | -----------
web3Instance | `Object` | A `web3` instance.
host | `String` | The Meter host url (and port if applicable).
timeout | `Number` | Request timeout value.

> Returns an `Object`

```javascript
{
  bzz: {
    givenProvider: null,
    pick: {…},
    currentProvider: null,
    isAvailable: ƒ,
    upload: ƒ, …
  },
  eth: {
    _requestManager: RequestManager,
    givenProvider: MetamaskInpageProvider,
    providers: {…},
    _provider: MeterProvider, 
    …
  },
  givenProvider: {
    mux: ObjectMultiplex,
    publicConfigStore: ObservableStore,
    rpcEngine: RpcEngine,
    send: ƒ
  },
  providers: {
    WebsocketProvider: ƒ,
    HttpProvider: ƒ,
    IpcProvider: ƒ
  },
  shh: {
    _requestManager: RequestManager,
    givenProvider: MetamaskInpageProvider,
    providers: {…},
    _provider: MeterProvider, 
    …
  },
  utils: {
    _fireError: ƒ,
    _jsonInterfaceMethodToString: ƒ,
    _flattenTypes: ƒ,
    randomHex: ƒ,
    _: ƒ, 
    …
  },
  version: "1.0.0-beta.37",
  _provider: {
    _events: Events,
    _eventsCount: 1,
    RESTHost: "http://test.meter.io:8669",
    WSHost: "ws://test.meter.io:8669",
    timeout: 0, 
    …
  },
  _requestManager: {
    provider: MeterProvider,
    providers: {…},
    subscriptions: {…}
  }
}
```

Parameters of the `meterify` return object

Property | Type | Description
--------- | ------- | -----------
BatchRequest | `function` |  Sets a `RequestManager` object and initiates batch requests (see: ).
bzz | `Object` | A `Bzz` object (see: ).
currentProvider | `function` | Get or set the current provider.
eth | `Object` | An `Eth` object (see: ).
givenProvider | `Object` | Return the given provider object.
providers | `Object` | A list of providers.
provider | `Object` | The current provider object.
\_requestManager | `Object` | A RequestManager object.
setProvider | `function` | Set the current provider.
shh | `Object` |  An `Shh` object (see: )
utils | `Object` |  A `utils` object (see: )

# MODULES

## bzz

## eth

## shh

## utils

# METHODS

## BatchRequest


## currentProvider


## setProvider

# PROPERTIES

## givenProvider


## providers


## provider


## \_requestManager
