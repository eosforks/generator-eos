# Setup

## eosio-cpp

Requires `eosio-cpp (v1.3.2)` to be installed from the [eosio.cdt](https://github.com/EOSIO/eosio.cdt) package to compile the smart contract.

## Deployment

Fill out the missing private key in `.testnet.env`, `.production.env`.

There's a `npm run init` script that _sets up your contract account_ and test accounts by creating them and transferring them enough EOS + RAM/NET/CPU.

> This should only be run on your local network to create accounts!

To deploy to the network specified in `.<environment>.env`, run:

```
NODE_ENV=testnet npm run deploy
```


## Testing the smart contract

Run a local node:

```
nodeos -c dev.ini --data-dir ~/.local/share/eosio/nodeos/data-dev --contracts-console --verbose-http-errors
```

You can run the following scripts to **automatically create scripts for your actions** defined in the ABI file.

```
npm run create_actions
```

You can then invoke these scripts to push actions to your deployed smart contract **without using cleos**:

```
npm run action -- <actionName>
```

Inspecting the contract's table can be done by:

```
npm run dump_tables
```