# Decentraland
Decentraland is an open-source initiative to build a decentralized virtual reality. Blockchain technology is used to claim and transfer land, keeping a permanent record of ownership. [Try it now](https://decentraland.org/app/).

## Stack
* [bcoin](https://github.com/bcoin-org/bcoin): forked a bitcoin's full-node implementation in JS.
* [Webtorrent](https://github.com/feross/webtorrent): leveraged torrent protocol to distribute world’s land content.

## How It Works?
Decentraland runs on top of its own blockchain. A modified Bitcoin’s blockchain to represent a non fungible asset, a.k.a. *land*. Transactions in Decentraland’s protocol can transfer land’s ownership and change its content.

The ownership of land is handled just like bitcoin, by using asymmetric cryptography and a stack-based scripting language.

The land’s content can be any type of file and the blockchain will only store a hash of it. The original file will be distributed via torrent’s protocol.

Finally, the network is secured by Bitcoin’s proof-of-work algorithm. Rewarding its miners not with coins, but with *land*.

Below a summary of the main differences with Bitcoin’s blockchain:

### Transaction:
* Removed *Output*’s *value* field.
* Add *x*, *y* and *content* fields to *Output*.
* Each *Output* must have the same *x* and *y* as the corresponding *Input*.
* A *Landbase* transaction must claim land adjacent to existing one.

### RPC:
* *gettile* call to fetch land’s file url.
* *settile* call to create a transaction that updates land’s file content.

### Network:
* Time between blocks: 10 minutes (for testnet).
* Seed land’s file descriptors through torrent network.


# How to run a node?
```
docker run decentraland
```

# How can I edit the land I own?
Once you mined some land, you can use Unity to edit it's content. Check out [this repo](https://github.com/decentraland/bronzeage-editor) for more information.


# Development

## Run node
```bash
docker-compose build
docker-compose up
```

## Set tile
```bash
docker-compose run app ./bin/cli --apikey="38Dpwnjsj2zn3QETJ6GKv8YkHomA" --url=app:8301 rpc settile 0 1 /data/hola.png
```
