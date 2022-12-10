#  Back up your wallet, then download your wallet and signet.conf files!
Make sure you backed up your wallet file! Feel free to get more coins from the faucet whenever you want/need them, but if you copy that wallet file between the different projects you'll be able to bring your coins with you on the Base58 Signet as you do these exercises.

When you load the wallet into the new repl's bitcoind, it will go look at the blockchain for any bitcoins locked to any addresses associated with your wallet. The bitcoins exist on the chain, the wallet is just the information required to spend them. So you can load the wallet into multiple repls and you'll "have" your bitcoin in all of them. But they're not in the repl, they're on the blockchain. It can get a little confusing, but it's an important part of understanding bitcoin!

In case you need it again, here's the command to dump your wallet file.

```
bitcoin-cli -signet dumpwallet b58signetwallet
```