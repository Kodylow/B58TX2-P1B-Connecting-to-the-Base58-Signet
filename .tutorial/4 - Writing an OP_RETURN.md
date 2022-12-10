#  Write a message to the blockchain with OP_RETURN

The Bitcoin blockchain is an immutable public ledger: anyone can write to it, if they're willing to pay a miner to include the transaction in a block. We've been writing standard transactions to the chain: locking and unlocking bitcoin to different scripts, encoded as addresses, to make payments. But you can do a lot more than just payments if you want! 

Bitcoin Script has an "OP_RETURN" code that lets you write a message to the blockchain as part of a transaction. There are a couple ways to do this, but using OP_RETURN tells other nodes on the network "this is a message, it will be unspendable, it's not a payment, you don't have to keep track of it if you don't want to". Using OP_RETURN, we can commit a message to the bitcoin blockchain to prove something, but allow anyone uninterested in that proof to ignore it and not have to keep track of it. If you've done some of the hashing exercises, you'll notice that this is an extremely cool way to do those hash commitment systems you learned about by publishing the hash as an op_return :)

Some people do silly things with OP_RETURNs, [like Rick Rolling by writing the lyrics of "Never Gonna Give You Up" to the chain](https://mempool.space/tx/d29c9c0e8e4d2a9790922af73f0b8d51f0bd4bb19940d9cf910ead8fbe85bc9b) (hit "Details" then scroll to the bottom to see the translated hex. Other people write messages celebrating anniversaries, weddings, & births. People don't use them too often because block space is valuable, but they're fun and we're on signet so let's do an OP_RETURN transaction commemorating this moment on your path to becoming a Bitcoin developer!

- [ ] Encode a message as hexadecimal: "your-replit-handle is one step closer to becoming a Bitcoin Dev" . You can do this with python in the console with the following command, which will print a long hex string:
```
print("example-handle is one step closer to becoming a Bitcoin Dev".encode().hex())
```

Now we'll build, fund, sign, and broadcast the transaction using the same steps we learned in the previous regtest exercise. To do an OP_RETURN, we just have to change the `createrawtransaction` command. Instead of paying an amount to an address like this:
```
bitcoin-cli -signet createrawtransaction '[]' '{"address-here: 0.001}'
```

We specify the output with the key, value pair: {"data": "my-hex-data"}

So to create the transaction structure for an op_return of: "satoshi is a bitcoin developer", we'd convert it to hex and then use the command:
```
bitcoin-cli -signet createrawtransaction '[]' '{"data": "7361746f736869206973206120626974636f696e20646576656c6f706572"}'
```
- [ ] Create your OP_RETURN transaction structure with the `createrawtransaction` command

The next steps are exactly the same as you'd expect:

We need to fund the transaction (add inputs & a change output. OP_RETURN are 0 amount outputs so any input that covers fees will do), sign the transaction, then broadcast the transaction.
- [ ] Add inputs and a change output to the transaction with the command `bitcoin-cli -signet fundrawtransaction your-tx-hex`
- [ ] Sign the transaction with the command `bitcoin-cli -signet signrawtransactionwithwallet your-funded-tx-hex
- [ ] Broadcast the signed transaction with the command `bitcoin-cli -signet sendrawtransaction you-signed-tx-hex`

Then go look up your txid (the hex returned by the sendrawtransaction command) on the base58 block explorer! You'll see the tx has your message in the OP_RETURN output! Congratulations, you're a bitcoin developer!

### That's it! Head on back to the course page to continue on your path to bitcoin wizardry!