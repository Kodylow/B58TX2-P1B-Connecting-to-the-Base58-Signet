# Splitting your UTXO

Now you've got a single UTXO, but for most of our exercises we'll want a bunch of different ones. Let's split this UTXO into 5 different sized coins. Run the following command to send coins to 4 new addresses and a change address:

- [ ] Create 4 new addresses with `bitcoin-cli -signet getnewaddress`
- [ ] Use the "sendmany" command to send 0.0001, 0.0002, 0.0003, and 0.0004 to the 4 addresses. It'll look like:

`bitcoin-cli -signet sendmany '' '{"address1": 0.0001, "address2": 0.0002, "address3": 0.0003, "address": 0.0004}'`

If you did it correctly, your shell will spit out a txid. Copy and paste that txid into the [base58.space](https://base58.space) block explorer to see a detailed visualization of the transaction. You'll notice that your wallet automatically calculated fees and added a 5th output for the change.