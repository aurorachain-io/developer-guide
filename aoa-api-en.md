#### start mainNet step:

* Git clone mainNet code，suppose the folder is go-aoa
* cd go-aoa
* make aoa : complier code ，generate binary file,suppose the file is in the folder that named home.
* start mainNet:  home/aoa --datadir home/aurora/aoa-data

* attach the console: home/aoa attach  home/aurora/aoa-data/aoa.ipc



#### AOA Mainnet console command:

* Query current block number：aoa.blockNumber
* Transfer：

```
// aoa token transfer,the feee is 0.0001aoa
aoa.sendTransaction({from: "aoa43f4fc95485110683f745cd4a6362497c832a774",to: "aoa8ea2354ba012628dd1dad9e44500a70075664a16",value: web3.toWei(1,"aoa"),action:0})

// aoa token transfer with sub address, the sub address = normal address + md5 value
aoa.sendTransaction({from: "aoa43f4fc95485110683f745cd4a6362497c832a774",to: "aoa8ea2354ba012628dd1dad9e44500a70075664a16202cb962ac59075b964b07152d234b70",value: web3.toWei(1,"aoa"),action:0})
```

* query trx by trxId：aoa.getTransaction('trxid')
* query trx receipt by trxId：aoa.getTransactionReceipt('trxId')

* Unlock the local account：personal.unlockAccount('address','password')

* create local account：personal.newAccount('password')

* add a p2p node：admin.addPeer("enode://302d9156a3ad8ab535093b89457f7b02e2fb99b4560f135ce9779772e1fe51fe8f4b62a62aeb68b80edd8fb1fa9023ed70c57486845c3922c3a26b03e068c0d1@127.0.0.1:30303")

* Look up accounts：aoa.accounts
* Query the info of block：aoa.getBlock($blockNumber or blockHash)
* Query the trx count of a address：aoa.getTransactionCount($address)
* Query a asset info：aoa.getAssetInfo($assetId)
* Query aoa balance of a address: web3.fromWei(aoa.getBalance($address),"aoa")
* Query asset balance of a address：aoa.getAssetBalance($address,assetId)



##### trx action value explain

* 0：aoa token or asset transfer
* 1：Agent register
* 2：Agent vote（AddVote）
* 3：Agent vote（SubVote）
* 4：asset publish
* 5：contract create
* 6：contract call