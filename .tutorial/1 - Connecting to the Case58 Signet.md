# Connecting to the Base58 Signet

So far we've been using regtest, our own private bitcoin network. It's much more fun to connect a node to and use one of the public networks though: we can send and receive bitcoin from other people, inspect their transactions, basically just use Bitcoin the way it was meant to be used.

Base58 runs a Signet with a [faucet, base58.money](base58.money) and [block explorer, base58.space](base58.space). We'll show you how to connect your node to it in this repl. Feel free to use this signet for any of your projects, we built it for you! Let us know if there's anything you'd like us to change or add to it!

### A bitcoin.conf for Base58's Signet
We've included a configuration file in this repl with settings to connect to Base58's signet. You can see it in the `signet.conf` file. It's got a couple new parameters set, as well as the ones we learned about in the previous exercise...

The "signetseednode" parameter tells your node where it can get a "seed" for the Base58 signet: the node at that IP address will tell your node about a bunch of peers you can randomly connect to. Yur node will try connecting to those nodes to get the blockchain data (and get even more nodes to connect to).

The "signetchallenge" parameter tells your node how to verify the blocks it receives from that signet. It's a hardcoded value that ensures everyone accepts the same blocks from Base58's signature generating miner instead of relying on Proof of Work like the bitcoin mainnet and testnet. There's a default signet, we're not connecting to that one so need to specify the base58 signet through the challenge.

The final new parameter is "txindex", which tells your node to create an index over all the transactions across the entire blockchain to make searching for TXs faster. When you leave this parameter to false, your node won't track which block each transaction was in. This is a useful space saving option if you want to run a lightweight node on a phone or something, indexing the Bitcoin mainnet transactions is almost 50GB, but Base58's signet is tiny so we'll index the transactions.

### Part A: Connect to Base58's signet

Start your node by passing in the signet.conf file
- [ ] `bitcoind -conf=$(pwd)/signet.conf`

Check that your node has started and is syncing to the Base58 chain
- [ ] `bitcoin-cli -signet -getinfo`

Fully syncing should take a couple minutes.