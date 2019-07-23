---
title: Meter Mining Guide

language_tabs: # must be one of https://git.io/vQNgJ
  - bash

toc_footers:
- <a href='./index.html'>Documentation Home</a>
- <a href='./meterify.dapps.html'>DApp Tutorials</a>
- <a href='./meterify.examples.html'>Examples</a>
- <a href='./mining.html'>Mining Guide</a>
- <hr>
- API Documentation
- <a href='./meterify.html'>meterify</a>
- <a href='./meterify.module.options.html'>meterify.module.options</a>
- <a href='./meterify.eth.html'>meterify.eth</a>
- <a href='./meterify.eth.subscribe.html'>meterify.eth.subscribe</a>
- <a href='./meterify.eth.Contract.html'>meterify.eth.Contract</a>
- <a href='./meterify.eth.Iban.html'>meterify.eth.Iban</a>
- <a href='./meterify.eth.personal.html'>meterify.eth.personal</a>
- <a href='./meterify.eth.accounts.html'>meterify.eth.accounts</a>
- <a href='./meterify.eth.ens.html'>meterify.eth.ens</a>
- <a href='./meterify.eth.abi.html'>meterify.eth.abi</a>
- <a href='./meterify.eth.net.html'>meterify.eth.net</a>
- <a href='./meterify.shh.html'>meterify.shh</a>
- <a href='./meterify.utils.html'>meterify.utils</a>
- <hr>  
- <a href='https://www.meter.io/claim-your-meter/'>Request Test Tokens</a>
- <a href='https://www.meter.io'>Meter.io</a>

search: true
---

# Meter Mining Guide

Mining is how cryptocurrency is created and one way to acquire coins. It is an intensive computing activity, and involves the use of specialized hardware to get rewarded for processing transaction blocks on a blockchain. Meter (MTR) itself is no exception to this.

There are a number of interlinked factors to consider when it comes to mining. Just to name a few:

* Whether it is more economical or profitable to mine or buy cryptocurrency.
* What blockchain to focus on, and why.
* How to approach mining. For example, doing it all yourself, cooperating with others, or have somebody else do it for you.

# Making The Case for Mining

Every miner will have their own reasons whether or not to choose mining. For example, under some circumstances it may be highly profitable to mine, while in other situations the costs may be too high and the return on investment too low.

When it comes to owning equipment, the main expenses involved will include the cost of the equipment, and the expenses involved in operating and maintaining it. Mining equipment is specialized hardware that is much more expensive than a standard PC computer, and requires a big upfront investment. That equipment also needs to be housed somewhere, under optimal conditions, such as keeping it cool while running. And, the other big operational factor is the price of electricity and dependability of delivery wherever the equipment is being operated.

When these challenges can be met in the right combination, the other side that needs to be looked at is the return. If the expenses are manageable, and the return on each coin is high enough, then that should equate to a good profit margin. However, it may be the case that at the time of mining a coin it is not actively being traded yet, but the anticipated return sometime later is expected to be profitable.

Mining Meter at this time is in the testing phase, and production mining is set to begin soon. This provides a very good incentive for early adopters to more easily and economically acquire MTR through mining, before it becomes more widely available, and as more miners begin to direct their resources towards the Meter Network.     

# How to Mine

Generally speaking, miners may choose to operate their own equipment, and gain all the rewards for their efforts, or join together with others in a mining pool, and share the rewards (see What is a Mining Pool). In some cases people can subscribe to a pool and gain some of the rewards, but without owning any equipment of their own. This is called cloud mining. Each has its own benefits and drawbacks, and it is up to each person to determine which approach suits them best.

The remainder of this document is in support of those that already operate their own equipment, or wish to, and are interested in mining Meter. Primarily this will include those that will mine directly on their own, mining pools that choose to support Meter, or those that want to setup cloud mining for Meter. However, this information might also be of interest to others, such as those that are already part of a mining pool, and want to request that their pool add support for Meter.  

## What is a Mining Pool?

When miners group together to use their combined processing power this is called a mining pool. The rewards from mining are split proportionally according to the amount of hash power miners contribute to the pool.

Mining pools can be split into both public ones and private ones. Public pools will generally charge a fee

Mining is strictly voluntary, and as such miners can opt to switch their mining capabilities whenever they choose, according to their own objectives or criteria. For example, if a miner that traditionally was in a Bitcoin mining pool decided to divert some or all processing power to mine another blockchain, such as Meter, it is simply a case of making a few minor configuration changes to point the mining equipment to the new pool.

# Mining Hardware

ASIC miners are specialized hardware machines that are required to efficiently mine Meter.

Since Meter uses SHA256, the same as Bitcoin, miners can use the same hardware for mining both coins, and the mining setup for the two is very similar.

## Hardware Setup Guide

Meter uses an account based system, rather than the UTXO based method that Bitcoin uses. However, this difference only amounts to a small change that needs to be made in the configuration.

Follow [this guide](https://www.bitcoin.com/get-started/how-to-setup-a-bitcoin-asic-miner-and-what-they-are) on installing and configuring your ASICs.

# The Meter Mining Pool

Meter is actively working with mining pools for support. However, in the meantime there are two dedicated Meter mining pools currently running for test purposes:

```
stratum+tcp://34.222.111.82:3256
stratum+tcp://54.184.235.97:3256
```

The following are the rough production parameters for different mining hardware on the Meter testnet, tuned to 1 meter = 10 kwh on an Antminer S9:

|                      | Power | Hash | Efficiency | Meter/Day | Margin Index |
|----------------------|-------|------|------------|-----------|--------------|
| AntMiner S9          | 1323  | 13.5 | 98         | 31.75     | 1.00         |
| WhatsMiner M10       | 3500  | 55   | 63.64      | 129.36    | 1.54         |
| Inno Silicon T3+ 52T | 2200  | 52   | 42.31      | 79.42     | 2.32         |
| AntMiner S17Pro      | 2094  | 53   | 39.51      | 80.95     | 2.48         |

These results are still relatively slow now. However, closer to the mainnet launch, parameters will be tuned to more efficient mining hardware, and achieve faster end results.

The Meter mining pool status statistics can be viewed at http://54.184.235.97:8088/stats.

## Joining the Meter Mining Pool

!> BE AWARE NO REWARD will be distributed from these pools, as the logic has not been implemented yet.

In order to configure a miner to join a Meter mining pool, the following fields in the `Miner configuration` tab of the ASIC's web panel need to be set:

![miner_configuration_example](./conf_s9.png)

Where:

* `URL` is the address of the mining pool.
* `Worker` is the Meter wallet address.
* `Password` is the password associated with the wallet.

# Starting a Mining Pool on the Meter Network

An example implementation of the Meter mining pool is available on [GitHub](https://github.com/meterio/meter-nomp), based on the open source nomp Bitcoin mining pool. This code has been provided to show the changes needed compared to standard bitcoin mining pools, and is not intended to be used in a production environment.

## Requirements

There are three things required to run Meter nomp: Node.js, a database (Redis or MySQL), and a connection to a coin daemon on the Meter Network, which is a Meter full node that monitors transactions on both the Meter PoW and PoS chains.

On the testnet, coin deamons have already been setup by the Meter team. Normally a pool operator would setup its own coin daemon, and this will be possible in the future.

The following are the minimal version requirements for Node.js and Redis. If older versions than the following are used (e.g. installed by a package manager) then problems will arise:

* [Node.js](http://nodejs.org/) v0.10+ ([follow these installation instructions](https://tecadmin.net/install-nodejs-with-nvm/#))
* [Redis](http://redis.io/) v2.6+ ([follow these instructions](http://redis.io/topics/quickstart))

**Important Warning!** It is always a good idea to learn about and understand any software that you are using. An important security measure to implement for nomp is to secure the database so it cannot be accessed externally. An easy way to do this for Redis is to include `bind 127.0.0.1` in your `redis.conf` file, and use a firewall with strict rules in place to only allow accessing Redis locally. For more information please read [Security](http://redis.io/topics/security). Another good place to start for additional information about using Redis for nomp is [Data Persistence](http://redis.io/topics/persistence).

## Downloading & Installing

Clone the repository and run `npm update` for all the dependencies to be installed:

```bash
git clone https://github.com/meterio/meter-nomp.git
cd meter-nomp
npm install
```

## Using Docker

> meter-nomp/docker-compose.yml

```bash
version: '3.5'
services:
  redis:
    image: "redis:alpine"
    networks:
      backend:
        ipv4_address: 172.16.238.10
  node:
    image: "node:10"
    user: "node"
    working_dir: /home/node/meter-nomp
    volumes:
      - ./:/home/node/meter-nomp
    networks:
      backend:
        ipv4_address: 172.16.238.11
    ports:
    # The following ports should be exposed to support
    # the example setup in the remainder of this document.
      # Web interface
      - "8088:8088"
      # CLI
      - "17117:17117"
      # Algorithm Switching
      - "3333:3333"
      - "4444:4444"
      - "5555:5555"
      # Payment Processing Daemon Port
      - "8332:8332"
      # Pool Connection Ports
      - "3008:3008"
      - "3032:3032"
      - "3256:3256"
      # MySQL Port (not enabled in the example)
      # - "3306:3306"
      # Other ports as required
    command: >
      sh -c "npm update &&
             node init.js"

networks:
  backend:
    name: nomp_backend
    driver: bridge
    ipam:
      driver: default
      config:
      - subnet: 172.16.238.0/24
```

This is completely optional. Rather than using the host system's Redis and Node.js, it is possible to containerize everything using Docker. The following describes this optional approach with Docker Compose. Do the following before continuing with the remaining steps, and in further sections any additional adjustments that need to be made will be highlighted.

Create the following `docker-compose.yml` file inside the `meter-nomp` sub-directory in the previous step.


## Portal Configuration

> Make the following changes in config.json

```js
"redis": {
    "host": "172.16.238.10",
    "port": 6379
}
```

Inside the `config_example.json` file, ensure the default configuration will work for your environment, then copy the file to `config.json`. If using the Docker example outlined above, change the `redis` sections to replace `127.0.0.1` with `172.16.238.10` as follows:

> Field Description

```js
{
    /* Specifies the level of log output verbosity. Anything more severe than the level specified
       will also be logged. */
    "logLevel": "debug", //or "warning", "error"

    /* By default meter-NOMP logs to console and gives pretty colors. If you direct that output to a
       log file then disable this feature to avoid nasty characters in your log file. */
    "logColors": true,


    /* The NOMP CLI (command-line interface) will listen for commands on this port. For example,
       blocknotify messages are sent to NOMP through this. */
    "cliPort": 17117,

    /* By default 'forks' is set to "auto" which will spawn one process/fork/worker for each CPU
       core in your system. Each of these workers will run a separate instance of your pool(s),
       and the kernel will load balance miners using these forks. Optionally, the 'forks' field
       can be a number for how many forks will be spawned. */
    "clustering": {
        "enabled": true,
        "forks": "auto"
    },

    /* Pool config file will inherit these default values if they are not set. */
    "defaultPoolConfigs": {

        /* Poll RPC daemons for new blocks every this many milliseconds. */
        "blockRefreshInterval": 1000,

        /* If no new blocks are available for this many seconds update and rebroadcast job. */
        "jobRebroadcastTimeout": 55,

        /* Disconnect workers that haven't submitted shares for this many seconds. */
        "connectionTimeout": 600,

        /* (For MPOS mode) Store the block hashes for shares that aren't block candidates. */
        "emitInvalidBlockHashes": false,

        /* This option will only authenticate miners using an address or mining key. */
        "validateWorkerUsername": true,

        /* Enable for client IP addresses to be detected when using a load balancer with TCP
           proxy protocol enabled, such as HAProxy with 'send-proxy' param:
           http://haproxy.1wt.eu/download/1.5/doc/configuration.txt */
        "tcpProxyProtocol": false,

        /* If under low-diff share attack we can ban their IP to reduce system/network load. If
           running behind HAProxy be sure to enable 'tcpProxyProtocol', otherwise you'll end up
           banning your own IP address (and therefore all workers). */
        "banning": {
            "enabled": true,
            "time": 600, //How many seconds to ban worker for
            "invalidPercent": 50, //What percent of invalid shares triggers ban
            "checkThreshold": 500, //Perform check when this many shares have been submitted
            "purgeInterval": 300 //Every this many seconds clear out the list of old bans
        },

        /* Used for storing share and block submission data and payment processing. */
        "redis": {
            "host": "127.0.0.1",
            "port": 6379
        }
    },

    /* This is the front-end. Its not finished. When it is finished, this comment will say so. */
    "website": {
        "enabled": true,
        /* If you are using a reverse-proxy like nginx to display the website then set this to
           127.0.0.1 to not expose the port. */
        "host": "0.0.0.0",
        "port": 8088,
        /* Used for displaying stratum connection data on the Getting Started page. */
        "stratumHost": "example.com",
        "stats": {
            /* Gather stats to broadcast to page viewers and store in redis for historical stats
               every this many seconds. */
            "updateInterval": 15,
            /* How many seconds to hold onto historical stats. Currently set to 24 hours. */
            "historicalRetention": 43200,
            /* How many seconds worth of shares should be gathered to generate hashrate. */
            "hashrateWindow": 300
        },
        /* Not done yet. */
        "adminCenter": {
            "enabled": true,
            "password": "password"
        }
    },

    /* Redis instance of where to store global portal data such as historical stats, proxy states,
       ect.. */
    "redis": {
        "host": "127.0.0.1",
        "port": 6379
    },


    /* With this switching configuration, you can setup ports that accept miners for work based on
       a specific algorithm instead of a specific coin. Miners that connect to these ports are
       automatically switched a coin determined by the server. The default coin is the first
       configured pool for each algorithm and coin switching can be triggered using the
       cli.js script in the scripts folder.

       Miners connecting to these switching ports must use their public key in the format of
       RIPEMD160(SHA256(public-key)). An address for each type of coin is derived from the miner's
       public key, and payments are sent to that address. */
    "switching": {
        "switch1": {
            "enabled": false,
            "algorithm": "sha256",
            "ports": {
                "3333": {
                    "diff": 10,
                    "varDiff": {
                        "minDiff": 16,
                        "maxDiff": 512,
                        "targetTime": 15,
                        "retargetTime": 90,
                        "variancePercent": 30
                    }
                }
            }
        },
        "switch2": {
            "enabled": false,
            "algorithm": "scrypt",
            "ports": {
                "4444": {
                    "diff": 10,
                    "varDiff": {
                        "minDiff": 16,
                        "maxDiff": 512,
                        "targetTime": 15,
                        "retargetTime": 90,
                        "variancePercent": 30
                    }
                }
            }
        },
        "switch3": {
            "enabled": false,
            "algorithm": "x11",
            "ports": {
                "5555": {
                    "diff": 0.001
                }
            }
        }
    },

    "profitSwitch": {
        "enabled": false,
        "updateInterval": 600,
        "depth": 0.90,
        "usePoloniex": true,
        "useCryptsy": true,
        "useMintpal": true
    }
}
```

## Coin Configuration

> coins/meter.json

```js
{
    "name": "Meter",
    "symbol": "MTR",
    "algorithm": "sha256",
}
```

Inside the `coins` directory, ensure that a json file exists for Meter coin, and if no create it. Here is an example of what the file should look like:

For additional documentation on how to configure coins and their different algorithms see [these instructions](github.com/meterio/meter-stratum-pool#module-usage).

## Pool Configuration

> Make the followig change in the daemons section of pool_configs/meter.json

```js
[
    {
        "host": "127.0.0.1",
        "port": 8332,
        "user": "testuser",
        "password": "testpass"
    }
]
```

> pool_configs/meter.json

```js
{
    "enabled": true, //Set this to false and a pool will not be created from this config file
    "coin": "meter.json", //Reference to coin config file in 'coins' directory

    "address": "mi4iBXbBsydtcc5yFmsff2zCFVX4XG7qJc", //Address to where block rewards are given

    /* Block rewards go to the configured pool wallet address to later be paid out to miners,
       except for a percentage that can go to, for examples, pool operator(s) as pool fees or
       or to donations address. Addresses or hashed public keys can be used. Here is an example
       of rewards going to the main pool op, and pool co-owner.*/
    "rewardRecipients": {
        "n37vuNFkXfk15uFnGoVyHZ6PYQxppD3QqK": 1.5, //1.5% goes to pool op
        "mirj3LtZxbSTharhtXvotqtJXUY7ki5qfx": 0.5, //0.5% goes to a pool co-owner
    },

    /* this is Pos beneficiary. It is 20 bytes address. Mining reward goes to this address in Pos ssytem. */
    "rewardBeneficiary": "0a05c2d862ca051010698b69b54278cbaf945ccb",

    /* payment must be disabled */
    "paymentProcessing": {
        "enabled": false,

        /* Every this many seconds get submitted blocks from redis, use daemon RPC to check
           their confirmation status, if confirmed then get shares from redis that contributed
           to block and send out payments. */
        "paymentInterval": 30,

        /* Minimum number of coins that a miner must earn before sending payment. Typically,
           a higher minimum means less transactions fees (you profit more) but miners see
           payments less frequently (they dislike). Opposite for a lower minimum payment. */
        "minimumPayment": 0.01,

        /* This daemon is used to send out payments. It MUST be for the daemon that owns the
           configured 'address' that receives the block rewards, otherwise the daemon will not
           be able to confirm blocks or send out payments. */
        "daemon": {
            "host": "127.0.0.1",
            "port": 8332,
            "user": "testuser",
            "password": "testpass"
        }
    },

    /* Each pool can have as many ports for your miners to connect to as you wish. Each port can
       be configured to use its own pool difficulty and variable difficulty settings. varDiff is
       optional and will only be used for the ports you configure it for. */
    "ports": {
        "3008": {
            "diff": 1
        },

        "3032": { //A port for your miners to connect to
            "diff": 32, //the pool difficulty for this port

            /* Variable difficulty is a feature that will automatically adjust difficulty for
               individual miners based on their hashrate in order to lower networking overhead */
            "varDiff": {
                "minDiff": 8, //Minimum difficulty
                "maxDiff": 512, //Network difficulty will be used if it is lower than this
                "targetTime": 15, //Try to get 1 share per this many seconds
                "retargetTime": 90, //Check to see if we should retarget every this many seconds
                "variancePercent": 30 //Allow time to very this % from target without retargeting
            }
        },
        "3256": { //Another port for your miners to connect to, for ASIC miner
            "diff": 200000 //The pool difficulty
            "varDiff": {
                "minDiff": 100000,
                "maxDiff": 2000000,
                "targetTime": 15,
                "retargetTime": 90,
                "variancePercent": 30
            }

        }
    },

    /* More than one daemon instances can be setup in case one drops out-of-sync or dies. */
    "daemons": [
        {   //Main daemon instance
            "host": "127.0.0.1",
            "port": 8332,
            "user": "testuser",
            "password": "testpass"
        }
    ],

    /* This allows the pool to connect to the daemon as a node peer to receive block updates.
       It may be the most efficient way to get block updates (faster than polling, less
       intensive than blocknotify script). It requires the additional field "peerMagic" in
       the coin config. */
    "p2p": {
        "enabled": false,

        /* Host for daemon */
        "host": "127.0.0.1",

        /* Port configured for daemon (this is the actual peer port not RPC port) */
        "port": 19333,

        /* If your coin daemon is new enough then it will support a p2p
           feature that prevents the daemon from spamming our peer node with unnecessary
           transaction data. Assume its supported but if you have problems try disabling it. */
        "disableTransactions": true
    },

    /* Enabled this mode and shares will be inserted into in a MySQL database. You may also want
       to use the "emitInvalidBlockHashes" option below if you require it. The config options
       "redis" and "paymentProcessing" will be ignored/unused if this is enabled. */
    "mposMode": {
        "enabled": false,
        "host": "127.0.0.1", //MySQL db host
        "port": 3306, //MySQL db port
        "user": "me", //MySQL db user
        "password": "mypass", //MySQL db password
        "database": "mtr", //MySQL db database name

        /* Checks for valid password in database when miners connect. */
        "checkPassword": true,

        /* Unregistered workers can automatically be registered (added to database) on stratum
           worker authentication if this is true. */
        "autoCreateWorker": false
    }
}
```

There is a json config file `meter.json` in the `pool_configs` sub-directory. Make sure to configure the appropriate fields in this file, especially the address fields and the `daemon`/`daemons` fields.

For example, assuming the miner's account in Meter for receiving a reward is the `rewardBeneficiary` field, in the example configuration below the value is `0a05c2d862ca051010698b69b54278cbaf945ccb`. In the same example, the value for Meter test coin in the `daemons` section is configured.

Many of these pool config files can be created. If this is the case, they must have unique stratum ports.

For more information on these configuration options see the [pool module documentation](https://github.com/meterio/meter-stratum-pool#module-usage).

## Start the Portal

After all the configuration files have been set up, it is time to start the mining pool.

### Using Local Host Resources (no Docker)

> Start the portal (no Docker)

```bash
$ node init.js
```

If everything is installed locally on the host, initiate using the following:

### Using Docker


#### Step 1: Remove dependencies

> Remove all modules from node_modules

```bash
$ rm -fr node_modules/*
```
> Or remove node_modules entirely:

```bash
$ rm -fr node_modules
```

If using the Docker approach, make sure on first run to remove the dependencies in `node_modules` and it is empty.

The reason for this is that there may be a version mismatch if dependencies were installed outside the container, as might have happened if `npm install` or `npm update` were run from the host. The `docker-compose.yml` file takes care of installing the dependencies, and automatically starting the application.

#### Step 2: Get the latest `docker-compose`

> Install docker-compose

```bash
$ sudo curl -L https://github.com/docker/compose/releases/download/1.24.1/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
$ sudo chmod +x /usr/local/bin/docker-compose
```
Ensure the latest version of `docker-compose` is installed.

#### Step 3: Check `docker-compose` version

```bash
$ docker-compose --version
docker-compose version 1.24.1, build 4667896b
```

Check that `docker-compose` was installed correctly.

#### Step 4: Start Docker.

```bash
docker-compose up
```

Double check the configuration details and then start Docker.

#### Step 5: Watch log output

> Known errors when daemon is not running.

```bash
[Payments]	[meter] Error with payment processing daemon {"type":"offline","message":"connect ECONNREFUSED 127.0.0.1:8332"}
[Website]	[meter] Could not dumpprivkey for meter {"type":"offline","message":"connect ECONNREFUSED 127.0.0.1:8332"}
[Pool]	[meter] (Thread 2) Could not start pool, error with init batch RPC call: {"type":"offline","message":"connect ECONNREFUSED 127.0.0.1:8332"}
[Pool]	[meter] (Thread 1) Could not start pool, error with init batch RPC call: {"type":"offline","message":"connect ECONNREFUSED 127.0.0.1:8332"}
```
Watch the log output for any errors. Errors are known to occur upon startup when the daemon is not running in the background:

#### Step 6: Stop Docker

```bash
Gracefully stopping... (press Ctrl+C again to force)
Stopping meter-nomp_node_1  ... done
Stopping meter-nomp_redis_1 ... done
```

Press `Ctrl+C` to stop.

#### Step 7: Using detached mode

```bash
docker-compose up -d
```

When wishing to start again in detached mode us the `-d` flag with `docker-compose`.
