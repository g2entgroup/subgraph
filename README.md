<p align="center">
  <a href="https://github.com/g2entgroup">
    <img src="https://www.creativeplatform.io/img/Creative_logo.png?raw=true" alt="PoolTogether Brand" style="max-width:100%;" width="200">
  </a>
</p>

<br />

## CREATIVE v3 Subgraph

The official Creative v3 subgraph.

#### Quick-use:

```sh
$ yarn clean && yarn prepare:local && graph gen:local && yarn create:local && yarn deploy:local
```

###### For Kovan:
```sh
$ yarn clean && yarn prepare:kovan && yarn gen:kovan && yarn deploy:kovan
```

###### For Rinkeby:
```sh
$ yarn clean && yarn prepare:rinkeby && yarn gen:rinkeby && yarn deploy:rinkeby
```

#### Local Setup

First you'll need to setup a graph node, then you can deploy the project to it.

###### Local Graph Node

1. Clone the Graph Node repo:

```bash
$ git clone https://github.com/graphprotocol/graph-node/
```

2. Enter the dir

```bash
$ cd graph-node/docker
```

3. If using Linux, fix the local IP address:

```bash
$ ./setup.sh
```

4. Spin up the node

```bash
$ sudo docker-compose up
```

###### Deploying the CREATIVE Contracts Locally

Make sure you've already deployed the CREATIVE contracts.  If you haven't done so, check out the [contracts repo](https://github.com/g2entgroup/creative-contracts).  

1. Change the `localhost` target url to 0.0.0.0:8545 in `builder.network.js`

2. Run `yarn` to install the contract repo dependencies.

3. Start a local ganache-cli instance using `ganache-cli -h 0.0.0.0 --chainId 31337`. This facilates the local subgraph docker node to observe the local blockchain instance.

4. In a different terminal window, run `yarn deploy localhost` to compile and deploy the smart contracts to the local ganache-cli blockchain instance.

5. In a different terminal window, run `yarn console localhost` to interact with the contracts.



###### Deploying the Subgraph Locally

Once the contracts are deployed, you can now set up the subgraph:

1. In this subgraph repo, install deps

```bash
$ yarn
```

2. Ensure generated code is up-to-date:

```bash
$ yarn codegen
```

3. Update `networks/local.json` to the correct contract addresses deployed locally

4. Run `yarn clean && yarn prepare:local && graph gen:local && yarn create:local && yarn deploy:local`
