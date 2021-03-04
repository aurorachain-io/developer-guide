### AOA JSON-RPC Endpoint
You can start the HTTP JSON-RPC with the --rpc flag
```
aoa --rpc --datadir <storeDir>
```
change the default port(8545) and listing address(localhost) with:

```
aoa --rpc --rpcaddr <ip> --rpcport <portNumber> --datadir <storeDir>
```
If accessing the RPC from a browser, CORS will need to be enabled with the appropriate domain set. Otherwise, JavaScript calls are limit by the same-origin policy and requests will fail:
```
aoa --rpc --rpccorsdomain "http://localhost:8545" --datadir <storeDir>
```
The JSON RPC can also be started from the efsn console using the admin.startRPC(addr, port) command.

### AOA Curl Example Explained
The curl options below might return a response where the node complains about the content type, this is because the --data option sets the content type to application/x-www-form-urlencoded . If your node does complain, manually set the header by placing -H "Content-Type: application/json" at the start of the call.

The examples also do not include the URL/IP & port combination which must be the last argument given to curl e.x. 127.0.0.1:8545

### AOA JSON Rpc Api
- [JSON RPC API](#json-rpc-api)
  - [JSON-RPC methods](#json-rpc-methods)
  - [JSON RPC API Reference](#json-rpc-api-reference)
     - [aoa_accounts](#aoa_accounts)
       - [Parameters](#parameters)
       - [Returns](#returns)
       - [Example](#example)
     - [aoa_blockNumber](#aoa_blocknumber)
       - [Parameters](#parameters-1)
       - [Returns](#returns-1)
       - [Example](#example-1)
     - [aoa_getBlockByNumber](#aoa_getblockbynumber)
       - [Parameters](#parameters-2)
       - [Returns](#returns-2)
       - [Example](#example-2)
     - [aoa_getBlockByHash](#aoa_getblockbyhash)
       - [Parameters](#parameters-3)
       - [Returns](#returns-3)
       - [Example](#example-3)
     - [aoa_getTransactionByHash](#aoa_gettransactionbyhash)
       - [Parameters](#parameters-4)
       - [Returns](#returns-4)
       - [Example](#example-4)
     - [aoa_getTransactionByBlockHashAndIndex](#aoa_gettransactionbyblockhashandindex)
       - [Parameters](#parameters-5)
       - [Returns](#returns-5)
       - [Example](#example-5)
     - [aoa_getTransactionByBlockNumberAndIndex](#aoa_gettransactionbyblocknumberandindex)
       - [Parameters](#parameters-6)
       - [Returns](#returns-6)
       - [Example](#example-6)
     - [aoa_getTransactionCount](#aoa_gettransactioncount)
       - [Parameters](#parameters-7)
       - [Returns](#returns-7)
       - [Example](#example-7)
     - [aoa_getBlockTransactionCountByHash](#aoa_getBlockTransactionCountByHash)
       - [Parameters](#parameters-8)
       - [Returns](#returns-8)
       - [Example](#example-8)
     - [aoa_getBlockTransactionCountByNumber](#aoa_getblocktransactioncountbynumber) 
       - [Parameters](#parameters-9)
       - [Returns](#returns-9)
       - [Example](#example-9)
     - [aoa_getTransactionReceipt](#aoa_gettransactionreceipt)
       - [Parameters](#parameters-10)
       - [Returns](#returns-10)
       - [Example](#example-10)   
     - [aoa_sendTransaction](#aoa_sendtransaction)
       - [Parameters](#parameters-11)
       - [Returns](#returns-11)
       - [Example](#example-11)
     - [aoa_sendRawTransaction](#aoa_sendrawtransaction)
       - [Parameters](#parameters-12)
       - [Returns](#returns-12)
       - [Example](#example-12)
     - [aoa_getBalance](#aoa_getbalance)
       - [Parameters](#parameters-13)
       - [Returns](#returns-13)
       - [Example](#example-13) 
     - [aoa_getDetailBalance](#aoa_getdetailbalance)
       - [Parameters](#parameters-14)
       - [Returns](#returns-14)
       - [Example](#example-14)    
     - [aoa_getAssetBalance](#aoa_getassetbalance)
       - [Parameters](#parameters-15)
       - [Returns](#returns-15)
       - [Example](#example-15)     
     - [aoa_getAssetInfo](#aoa_getassetinfo)
       - [Parameters](#parameters-16)
       - [Returns](#returns-16)
       - [Example](#example-16)
     - [aoa_getDelegateList](#aoa_getdelegatelist)
       - [Parameters](#parameters-17)
       - [Returns](#returns-17)
       - [Example](#example-17)
     - [aoa_getDelegate](#aoa_getdelegate)
       - [Parameters](#parameters-18)
       - [Returns](#returns-18)
       - [Example](#example-18)
     - [aoa_getVotesList](#aoa_getvoteslist)
       - [Parameters](#parameters-19)
       - [Returns](#returns-19)
       - [Example](#example-19)
     - [aoa_pendingTransactions](#aoa_pendingtransactions)
       - [Parameters](#parameters-20)
       - [Returns](#returns-20)
       - [Example](#example-20)
     - [aoa_call](#aoa_call)
       - [Parameters](#parameters-21)
       - [Returns](#returns-21)
       - [Example](#example-21)
     - [aoa_getCode](#aoa_getcode)
       - [Parameters](#parameters-22)
       - [Returns](#returns-22)
       - [Example](#example-22)
     - [aoa_getAbi](#aoa_getabi)
       - [Parameters](#parameters-23)
       - [Returns](#returns-23)
       - [Example](#example-23)
     - [aoa_getStorageAt](#aoa_getstorageat)
       - [Parameters](#parameters-24)
       - [Returns](#returns-24)
       - [Example](#example-24)
     - [aoa_estimateGas](#aoa_estimategas)
       - [Parameters](#parameters-25)
       - [Returns](#returns-25)
       - [Example](#example-25)
     - [aoa_sign](#aoa_sign)
       - [Parameters](#parameters-26)
       - [Returns](#returns-26)
       - [Example](#example-26)
     - [aoa_syncing](#aoa_syncing)
       - [Parameters](#parameters-27)
       - [Returns](#returns-27)
       - [Example](#example-27)
     - [net_version](#net_version)
       - [Parameters](#parameters-28)
       - [Returns](#returns-28)
       - [Example](#example-28)
     - [net_peerCount](#net_peercount)
       - [Parameters](#parameters-29)
       - [Returns](#returns-29)
       - [Example](#example-29)
                              


# JSON RPC API


## JSON-RPC methods

* [aoa_accounts](#aoa_accounts)
* [aoa_blockNumber](#aoa_blocknumber)
* [aoa_getBlockByNumber](#aoa_getblockbynumber)
* [aoa_getBlockByHash](#aoa_getblockbyhash)
* [aoa_getTransactionByHash](#aoa_gettransactionbyhash)
* [aoa_getTransactionByBlockHashAndIndex](#aoa_gettransactionbyblockhashandindex)
* [aoa_getTransactionByBlockNumberAndIndex](#aoa_gettransactionbyblocknumberandindex)
* [aoa_getTransactionCount](#aoa_gettransactioncount)
* [aoa_getBlockTransactionCountByHash](#aoa_getblocktransactioncountbyhash)
* [aoa_getBlockTransactionCountByNumber](#aoa_getblocktransactioncountbynumber)
* [aoa_getTransactionReceipt](#aoa_gettransactionreceipt)
* [aoa_sendTransaction](#aoa_sendtransaction)
* [aoa_sendRawTransaction](#aoa_sendrawtransaction)
* [aoa_getBalance](#aoa_getbalance)
* [aoa_getDetailBalance](#aoa_getdetailbalance)
* [aoa_getAssetBalance](#aoa_getassetbalance)
* [aoa_getAssetInfo](#aoa_getassetinfo)
* [aoa_getDelegateList](#aoa_getdelegatelist)
* [aoa_getDelegate](#aoa_getdelegate)
* [aoa_getVotesList](#aoa_getvoteslist)
* [aoa_pendingTransactions](#aoa_pendingtransactions)
* [aoa_call](#aoa_call)
* [aoa_getCode](#aoa_getcode)
* [aoa_getAbi](#aoa_getabi)
* [aoa_getStorageAt](#aoa_getstorageat)
* [aoa_estimateGas](#aoa_estimategas)
* [aoa_sign](#aoa_sign)
* [aoa_syncing](#aoa_syncing)
* [net_version](#net_version)
* [net_peerCount](#net_peercount)








## JSON RPC API Reference

***

#### aoa_blockNumber

Returns the number of the highest block in local node

##### Parameters

none

##### Returns

`String` - the highest block number in local node(hex value)

##### Example

```
// Request
curl -X POST -H "Content-Type:application/json" --data '{"jsonrpc":"2.0","method":"aoa_blockNumber","params":[],"id":67}'

// Response
{
  "id":67,
  "jsonrpc":"2.0",
  "result": "0x1" // 1
}

```

***

#### aoa_getBlockByNumber

Returns block information by block height

##### Parameters

1. `QUANTITY|TAG` - integer of a block number, or the string `"earliest"`, `"latest"` or `"pending"`, as in the [default block parameter](#the-default-block-parameter).
2. `Boolean` - If `true` it returns the full transaction objects, if `false` only the hashes of the transactions.

```
params: [
   '0x1b4', // 436
   true
]
```

##### Returns

`Object` - A block object, or `null` when no block was found:

  - `number`: `QUANTITY` - the block number. `null` when its pending block.
  - `hash`: `DATA`, 32 Bytes - hash of the block. `null` when its pending block.
  - `parentHash`: `DATA`, 32 Bytes - hash of the parent block.
  - `transactionsRoot`: `DATA`, 32 Bytes - the root of the transaction trie of the block.
  - `stateRoot`: `DATA`, 32 Bytes - the root of the final state trie of the block.
  - `receiptsRoot`: `DATA`, 32 Bytes - the root of the receipts trie of the block.
  - `delegateRoot`: `DATA`,32 bytes - the root of the final delegate trie of the block.
  - `validatorAddress`: `DATA`, 20 Bytes - the address of the beneficiary to whom the mining rewards were given.
  - `validator`: `DATA` - the name of validatorAddress
  - `extraData`: `DATA` - the "extra data" field of this block.
  - `size`: `QUANTITY` - integer the size of this block in bytes.
  - `gasLimit`: `QUANTITY` - the maximum gas allowed in this block.
  - `gasUsed`: `QUANTITY` - the total used gas by all transactions in this block.
  - `timestamp`: `QUANTITY` - the unix timestamp for when the block was collated.
  - `transactions`: `Array` - Array of transaction objects, or 32 Bytes transaction hashes depending on the last given parameter.
  - `ShuffleDelegateListHash`: `DATA`,32 bytes - the rlp encode bytes of shuffle list result
  - `ShuffleBlockNumber`: `QUANTITY` - the block number when shuffle begin


##### Example

```
// Request
curl -X POST -H "Content-Type:application/json" --data '{"jsonrpc":"2.0","method":"aoa_getBlockByNumber","params":["0x1", true],"id":1}'

// Response

{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "ShuffleBlockNumber": 0,
    "ShuffleDelegateListHash": "0x5e38f2283ef64114cb6d742c0c1c43d6324433583c671d4ef481aab775d73fa8",
    "delegateRoot": "0x0f2b7c4cdbbe9e08029c5b71a2eab983e0812280fc2cd6ec38b2a81cf19e3675",
    "extraData": "0x",
    "gasLimit": "0x9f759", // 653145
    "gasUsed": "0x9f759", // 653145
    "hash": "0xfef1c4f14c6c27811780c9d811481da697f58272f04bde4b18f6e9865ba657e1",
    "number": "0x1",
    "parentHash": "0x8defb9b40e66a552b6f82d83ec70740f96a1f0cbcd8239a2d9ff2dd88ee53125",
    "receiptsRoot": "0x56e81f171bcc55a6ff8345e692c0f86e5b48e01b996cadc001622fb5e363b421",
    "size":  "0x027f07", // 163591
    "stateRoot": "0x8f28abc05bead04da9dc4bb40d5ec2b7bb1e856e5d5e4159b3e6bfd9a4f64602",
    "timestamp": "0x5b11012e",
    "transactions": [{...},{ ... }]
    "transactionsRoot": "0x56e81f171bcc55a6ff8345e692c0f86e5b48e01b996cadc001622fb5e363b421",
    "validator": "0x307865323738393330373530324531383461373661413133334634374362363635426646333434434639",
    "validatorAddress": "aoae2789307502e184a76aa133f47cb665bff344cf9"
  }
}

```
***

#### aoa_getBlockByHash

Returns block information by block hash

##### Parameters

1. `DATA`, 32 Bytes - Hash of a block.
2. `Boolean` - If `true` it returns the full transaction objects, if `false` only the hashes of the transactions.

```
params: [
   '0xfef1c4f14c6c27811780c9d811481da697f58272f04bde4b18f6e9865ba657e1',
   true
]
```

##### Returns

See [aoa_getBlockByNumber](#aoa_getblockbynumber)

##### Example

```
// Request
curl -X POST -H "Content-Type:application/json" --data '{"jsonrpc":"2.0","method":"aoa_getBlockByHash","params":["0xfef1c4f14c6c27811780c9d811481da697f58272f04bde4b18f6e9865ba657e1", true],"id":1}'

```

Result see [aoa_getBlockByNumber](#aoa_getblockbynumber)

***

#### aoa_getTransactionByHash

Returns the detail information about a transaction based on the specified transaction hash

##### Parameters

1. `DATA`, 32 Bytes - hash of a transaction

```
params: [
   "0xdb7b0c126e04150459f76a51cbf313b64230737251fe4a662a6dba2585ab87cc"
]
```

##### Returns

`Object` - A transaction object, or `null` when no transaction was found:

  - `hash`: `DATA`, 32 Bytes - hash of the transaction.
  - `nonce`: `QUANTITY` - the number of transactions made by the sender prior to this one.
  - `blockHash`: `DATA`, 32 Bytes - hash of the block where this transaction was in. `null` when its pending.
  - `blockNumber`: `QUANTITY` - block number where this transaction was in. `null` when its pending.
  - `transactionIndex`: `QUANTITY` - integer of the transactions index position in the block. `null` when its pending.
  - `from`: `DATA`, 20 Bytes - address of the sender.
  - `to`: `DATA`, 20 Bytes - address of the receiver. `null` when its a contract creation transaction.
  - `value`: `QUANTITY` - value transferred in Wei.
  - `gasPrice`: `QUANTITY` - gas price provided by the sender in Wei.
  - `gas`: `QUANTITY` - gas provided by the sender.
  - `input`: `DATA` - the data send along with the transaction.
  - `action`: `DATA` - the type of transaction(see [action_explain](#action_explain))
  - `asset`: `DATA` - the address of asset,default nil when transfer aoa
  - `nickname`: `DATA`- the nickname of register agent,only appear when action is 1
  - `votes`: `DATA` - the list of vote data,only appear when action is 2
  - `assetInfo`: `DATA` - the asset info struct,only appear when action is 4
  - `subAddress`: - only appear if the length of receiver address more than 42 


##### Example

```
// Request
curl -X POST -H "Content-Type:application/json" --data '{"jsonrpc":"2.0","method":"aoa_getTransactionByHash","params":["0xdb7b0c126e04150459f76a51cbf313b64230737251fe4a662a6dba2585ab87cc"],"id":1}'

// Response

{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "blockHash": "0x603228b9d896a0415f5e2aa637142e64f7ef76649ffe8cf32e4d7ef0b3a6820f",
    "blockNumber": "0x2",
    "from": "aoae2789307502e184a76aa133f47cb665bff344cf9",
    "gas": "0x61a8",
    "gasPrice": "0x1",
    "hash": "0xdb7b0c126e04150459f76a51cbf313b64230737251fe4a662a6dba2585ab87cc",
    "input": "0x",
    "nonce": "0x0",
    "to": "aoafc3f211fcea1c7fecf204eaed3e33012eb730097",
    "transactionIndex": "0x0",
    "value": "0x84595161401484a000000", // 10000000
    "v": "0x1c",
    "r": "0x7717d1bd7dcf3a6ce20dae78ca186852774f3427bd56bf69d7174479d83e415f",
    "s": "0x739f94d7269ded46f7fe0af1f0b72c7ab0b4e8f4040c361e446a50f669feb225",
    "action": 0
  }
}

```

***

#### aoa_accounts

Returns a list of addresses owned by the local client.


##### Parameters

none

##### Returns

`Array of DATA`, 20 Bytes - owned by the local client.

##### Example

```
// Request
curl -X POST -H "Content-Type:application/json" --data '{"jsonrpc":"2.0","method":"aoa_accounts","params":[],"id":1}'

// Result
{
  "jsonrpc":"2.0",
  "id":1,
  "result":["aoae2789307502e184a76aa133f47cb665bff344cf9","aoafc3f211fcea1c7fecf204eaed3e33012eb730097"]
}
```

***

#### aoa_getTransactionByBlockHashAndIndex

Returns the detail information about a transaction by block hash and transaction index position.

##### Parameters

1. `DATA`, 32 Bytes - hash of a block.
2. `QUANTITY` - integer of the transaction index position.

```
params: [
   '0xfef1c4f14c6c27811780c9d811481da697f58272f04bde4b18f6e9865ba657e1',
   '0x0' // 0
]
```

##### Returns

See [aoa_getTransactionByHash](#aoa_gettransactionbyhash)

##### Example

```
// Request
curl -X POST -H "Content-Type:application/json" --data '{"jsonrpc":"2.0","method":"aoa_getTransactionByBlockHashAndIndex","params":["0xfef1c4f14c6c27811780c9d811481da697f58272f04bde4b18f6e9865ba657e1", "0x0"],"id":1}'

```

Result see [aoa_getTransactionByHash](#aoa_gettransactionbyhash)

***

#### aoa_getTransactionByBlockNumberAndIndex

Returns the detail information about a transaction by block number and transaction index position.

##### Parameters

1. `QUANTITY|TAG` - a block number, or the string `"earliest"`, `"latest"` or `"pending"`, as in the [default block parameter](#the-default-block-parameter).
2. `QUANTITY` - integer of the transaction index position.

```
params: [
   '0x1',
   '0x0' // 0
]
```

##### Returns

See [aoa_getTransactionByHash](#aoa_gettransactionbyhash)

##### Example

```
// Request
curl -X POST -H "Content-Type:application/json" --data '{"jsonrpc":"2.0","method":"aoa_getTransactionByBlockNumberAndIndex","params":["0x1", "0x0"],"id":1}'

```

Result see [aoa_getTransactionByHash](#aoa_gettransactionbyhash)

***

#### aoa_getTransactionCount

Returns the number of transactions *send* from an address

##### Parameters

1. `DATA`, 20 Bytes - address.
2. `QUANTITY|TAG` - integer block number, or the string `"latest"`, `"earliest"` or `"pending"`, see the [default block parameter](#the-default-block-parameter)

``` 
params: [
   'aoae2789307502e184a76aa133f47cb665bff344cf9',
   'latest' // state at the latest block
]

```

##### Returns

`QUANTITY` - integer of the number of transactions send from this address.

##### Example

```
// Request
curl -X POST -H "Content-Type:application/json" --data '{"jsonrpc":"2.0","method":"aoa_getTransactionCount","params":["aoae2789307502e184a76aa133f47cb665bff344cf9","latest"],"id":1}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0x1" // 1
}

```
***

#### aoa_getBlockTransactionCountByHash

Returns the number of transactions in a block from a block matching the given block hash.

##### Parameters

1. `DATA`, 32 Bytes - hash of a block

```
params: [
   '0xfef1c4f14c6c27811780c9d811481da697f58272f04bde4b18f6e9865ba657e1'
]
```

##### Returns

`QUANTITY` - integer of the number of transactions in this block.

##### Example

```
// Request
curl -X POST -H "Content-Type:application/json" --data '{"jsonrpc":"2.0","method":"aoa_getBlockTransactionCountByHash","params":["0xfef1c4f14c6c27811780c9d811481da697f58272f04bde4b18f6e9865ba657e1"],"id":1}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0xb" // 11
}

```

***

#### aoa_getBlockTransactionCountByNumber

Returns the number of transactions in a block matching the given block number.

##### Parameters

1. `QUANTITY|TAG` - integer of a block number, or the string `"earliest"`, `"latest"` or `"pending"`, as in the [default block parameter](#the-default-block-parameter).

```
params: [
   '0xe8', // 232
]

```

##### Returns

`QUANTITY` - integer of the number of transactions in this block.

##### Example

```
// Request
curl -X POST -H "Content-Type:application/json" --data '{"jsonrpc":"2.0","method":"aoa_getBlockTransactionCountByNumber","params":["0xe8"],"id":1}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0xb" // 11
}

```
***

#### aoa_getTransactionReceipt

Returns the receipt of a transaction by transaction hash.

**Note** That the receipt is not available for pending transactions.

##### Parameters

1. `DATA`, 32 Bytes - hash of a transaction

```
params: [
   '0x4b378335fb3ab69bcc31ef2338bce86d9eba7f008e837510ef984127a836e136'
]
```

##### Returns

`Object` - A transaction receipt object, or `null` when no receipt was found:

  - `transactionHash `: `DATA`, 32 Bytes - hash of the transaction.
  - `transactionIndex`: `QUANTITY` - integer of the transactions index position in the block.
  - `blockHash`: `DATA`, 32 Bytes - hash of the block where this transaction was in.
  - `blockNumber`: `QUANTITY` - block number where this transaction was in.
  - `cumulativeGasUsed `: `QUANTITY ` - The total amount of gas used when this transaction was executed in the block.
  - `gasUsed `: `QUANTITY ` - The amount of gas used by this specific transaction alone.
  - `contractAddress `: `DATA`, 20 Bytes - The contract address created, if the transaction was a contract creation or asset publish, otherwise `null`.
  - `logs`: `Array` - Array of log objects, which this transaction generated.
  - `logsBloom`: `DATA`, 256 Bytes - Bloom filter for light clients to quickly retrieve related logs.

It also returns _either_ :

  - `root` : `DATA` 32 bytes of post-transaction stateroot
  - `status`: `QUANTITY` either `1` (success) or `0` (failure) 

##### Example

```
// Request
curl -X POST -H "Content-Type:application/json" --data '{"jsonrpc":"2.0","method":"aoa_getTransactionReceipt","params":["0x4b378335fb3ab69bcc31ef2338bce86d9eba7f008e837510ef984127a836e136"],"id":1}'

// Result

{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "action": 0,
    "blockHash": "0xc0c1ce6853121670f2b2dec4e3fdaeb1ea9f81ab2fad3e88ea4f1d11eb5fd041",
    "blockNumber": "0x1",
    "contractAddress": null,
    "cumulativeGasUsed": "0x61a8",
    "from": "0xd6ced88207f1b308531153897a8aaad43d611793",
    "gasUsed": "0x61a8",
    "logs": [],
    "logsBloom": "0x00...0",
    "root": "0x10bd5192fa1f8b92a0798b73c7051cee2ce0060ee1eddf337b09cdc1abaf8051",
    "to": "aoa55a64640e58397da092adf9ac78fcf168fabc1e0",
    "transactionHash": "0x4b378335fb3ab69bcc31ef2338bce86d9eba7f008e837510ef984127a836e136",
    "transactionIndex": "0x0"
  }
}

```
***

#### aoa_sendTransaction

Creates new message call ordinary transaction,vote transaction,asset create,asset transaction,contract creation or contract call if the data field contains code.

##### Parameters

1. `Object` - The transaction object
  - `from`: `DATA`, 20 Bytes - The address the transaction is send from.
  - `to`: `DATA`, 20 Bytes - (optional when creating new contract) The address the transaction is directed to.
  - `gas`: `QUANTITY`  - (optional, default: 90000) Integer of the gas provided for the transaction execution. It will return unused gas.
  - `gasPrice`: `QUANTITY`  - (optional, default: To-Be-Determined) Integer of the gasPrice used for each paid gas
  - `value`: `QUANTITY`  - (optional) Integer of the value sent with this transaction
  - `data`: `DATA`  - The compiled code of a contract OR the hash of the invoked method signature and encoded parameters. For details see [Aurora Contract ABI](https://github.com/ethereum/wiki/wiki/Ethereum-Contract-ABI)
  - `nonce`: `QUANTITY`  - (optional) Integer of a nonce. This allows to overwrite your own pending transactions that use the same nonce.
  - `action`: `DATA` - the type of transaction(see [action_explain](#action_explain))
  - `asset`: `DATA` - the address of asset,default nil when transfer aoa
  - `nickname`: `DATA`- the nickname of register agent,only appear when action is 1
  - `votes`: `DATA` - the list of vote data,only appear when action is 2
  - `assetInfo`: `DATA` - the asset info struct,only appear when action is 4
  - `subAddress`: - only appear if the length of receiver address more than 42 

```
params: [{
  "from": "aoab60e8dd61c5d32be8058bb8eb970870f07233155",
  "to": "aoad46e8dd67c5d32be8058bb8eb970870f07244567",
  "gas": "0x61a8", // 25000
  "gasPrice": "0xee6b2800", // 4000000000
  "value": "0x9184e72a", // 2441406250
  "data": "0xd46e8dd67c5d32be8d46e8dd67c5d32be8058bb8eb970870f072445675058bb8eb970870f072445675"
  "action":"0",
}]

```

##### Returns

`DATA`, 32 Bytes - the transaction hash, or the zero hash if the transaction is not yet available.

Use [aoa_getTransactionReceipt](#aoa_gettransactionreceipt) to get the contract address or the asset address, after the transaction was success, when you created a contract or published a asset.

##### Example

```
// Request

// aoa transfer
curl -X POST -H "Content-Type:application/json" --data '{"jsonrpc":"2.0","method":"aoa_sendTransaction","params":[{"from":"aoafa204429d90d3c3256ceca9b28f3c3acd211ead8","to":"aoab193ca61b6d73e3cb5082a9d4bb9d2afe2ae2926","gas":"0x61a8","gasPrice":"0xee6b2800","value":"0xde0b6b3a7640000","action":0}],"id":1}'

// register delegate

curl -X POST -H "Content-Type:application/json" --data '{"jsonrpc":"2.0","method":"aoa_sendTransaction","params":[{"from":"aoafa204429d90d3c3256ceca9b28f3c3acd211ead8","gas":"0x61a8","gasPrice":"0xee6b2800","action":1,"nickname":"yujian"}],"id":1}'

// vote delegate

curl -X POST -H "Content-Type:application/json" --data '{"jsonrpc":"2.0","method":"aoa_sendTransaction","params":[{"from":"aoafa204429d90d3c3256ceca9b28f3c3acd211ead8","gas":"0x61a8","gasPrice":"0xee6b2800","action":2,"vote":[{"candidate": "aoafa204429d90d3c3256ceca9b28f3c3acd211ead8", "operation":0}]}],"id":1}'

// asset publish

curl -X POST -H "Content-Type:application/json" --data '{"jsonrpc":"2.0","method":"aoa_sendTransaction","params":[{"from":"aoafa204429d90d3c3256ceca9b28f3c3acd211ead8","action":4,"assetInfo":{"name":"yujianToken","symbol":"ABC","supply":"0x11","desc":"my token"}}],"id":1}' 

// asset transfer

curl -X POST -H "Content-Type:application/json" --data '{"jsonrpc":"2.0","method":"aoa_sendTransaction","params":[{"from":"aoafa204429d90d3c3256ceca9b28f3c3acd211ead8","to":"aoab193ca61b6d73e3cb5082a9d4bb9d2afe2ae2926","value":"0x1","action":0,"asset":"aoacd880e835bba9d65ca486544180897f0b2e893d2"}],"id":1}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0xc9cd75d2c2d922d8423a8371250fbb79a3adc4ce0ea5879956b7ed0035427239"
}

```
***

#### aoa_sendRawTransaction

Creates new message call ordinary transaction,vote transaction,asset create,asset transaction,contract creation or contract call if the data field contains code.

##### Parameters

1. `DATA`, The signed transaction data.

```
params: ["0xf86e80850430e2340082520894baefc34465d73831e01e88049e9163589138fa7787038d7ea4c68000801ba04c4cc6d534b6944f419de57ea5c9a28531763665ed658a4b19fb06c556aa9150a02a2a44d6f3e0ad91ccdc1ee5bf6a8d63011fe56912606325a82431b9f37dbd88808080"]

```

##### Returns

`DATA`, 32 Bytes - the transaction hash, or the zero hash if the transaction is not yet available.

Use [aoa_getTransactionReceipt](#aoa_gettransactionreceipt) to get the contract address or the asset address, after the transaction was success, when you created a contract or published a asset.

##### Example

```
// Request
curl -X POST -H "Content-Type:application/json" --data '{"jsonrpc":"2.0","method":"aoa_sendRawTransaction","params":["0xf86e80850430e2340082520894baefc34465d73831e01e88049e9163589138fa7787038d7ea4c68000801ba04c4cc6d534b6944f419de57ea5c9a28531763665ed658a4b19fb06c556aa9150a02a2a44d6f3e0ad91ccdc1ee5bf6a8d63011fe56912606325a82431b9f37dbd88808080"],"id":1}'

// Result

{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0xe670ec64341771606e55d6b4ca35a1a6b75ee3d5145a99d05921026d1527331"
}

```
***

#### aoa_getBalance

Returns the aoa balance of the account of given address.

##### Parameters

1. `DATA`, 20 Bytes - address to check for balance.
2. `QUANTITY|TAG` - integer block number, or the string `"latest"`, `"earliest"` or `"pending"`, see the [default block parameter](#the-default-block-parameter)

```
params: [
   'aoa407d73d8a49eeb85d32cf465507dd71d507100c1',
   'latest'
]

```

##### Returns

`QUANTITY` - integer of the current balance in wei.


##### Example

```
// Request

curl -X POST -H "Content-Type:application/json" --data '{"jsonrpc":"2.0","method":"aoa_getBalance","params":["aoa407d73d8a49eeb85d32cf465507dd71d507100c1", "latest"],"id":1}'

// Result

{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0x0234c8a3397aab57" 
}

```
***

#### aoa_getDetailBalance

Returns all balances of the account of given address,including asset balance,aoa locked balance, aoa free balance.

##### Parameters

1. `DATA`, 20 Bytes - address to check for balance.
2. `QUANTITY|TAG` - integer block number, or the string `"latest"`, `"earliest"` or `"pending"`, see the [default block parameter](#the-default-block-parameter)

```
params: [
   'aoa407d73d8a49eeb85d32cf465507dd71d507100c1',
   'latest'
]

```

##### Returns

`Object` - all balance of the given address own in wei.

##### Example

```
// Request

curl -X POST -H "Content-Type:application/json" --data '{"jsonrpc":"2.0","method":"aoa_getDetailBalance","params":["aoafa204429d90d3c3256ceca9b28f3c3acd211ead8", "latest"],"id":1}'

// Result

{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "aoaCD880E835bBA9d65ca486544180897F0B2E893D2": "16",
    "aoa_balance": "99999997999300000000000000",
    "aoa_lockBalance": "1000000000000000000",
    "aoa_totalBalance": "99999998999300000000000000"
  }
}

```
***

#### aoa_getAssetBalance

Returns the specified asset balance of the account of given address.

##### Parameters

1. `DATA`, 20 Bytes - address to check for balance.
2. `DATA`, 20 bytes - address of the specified asset
3. `QUANTITY|TAG` - integer block number, or the string `"latest"`, `"earliest"` or `"pending"`, see the [default block parameter](#the-default-block-parameter)

```
params: [
   'aoafa204429d90d3c3256ceca9b28f3c3acd211ead8',
   'aoaCD880E835bBA9d65ca486544180897F0B2E893D2',
   'latest'
]

```

##### Returns

`QUANTITY` - the asset balance of the given address own in wei.

*note*:the aoa denominations you can see [aoa_denominations](#aoa_denominations)

##### Example

```
// Request

curl -X POST -H "Content-Type:application/json" --data '{"jsonrpc":"2.0","method":"aoa_getAssetBalance","params":["aoafa204429d90d3c3256ceca9b28f3c3acd211ead8","aoaCD880E835bBA9d65ca486544180897F0B2E893D2","latest"],"id":1}'

// Result

{
  "jsonrpc": "2.0",
  "id": 1,
  "result":"0x10"
}

```
***

#### aoa_getAssetInfo

Returns the detail information about the specified asset

##### Parameters

1. `DATA`, 20 bytes - address of the specified asset

```
params: [
  'aoaCD880E835bBA9d65ca486544180897F0B2E893D2',
]

```

##### Returns

`Object` - the asset balance of the given address own in wei.

  - `issuer`: `DATA`, 20 Bytes - The address that publish asset.
  - `name`:  `DATA`, - the name of asset.
  - `symbol`: `DATA`,- short name of asset.
  - `supply`: `QUANTITY` - the circulation of asset,the uint is Wei.
  - `desc`: `DATA` - the description of asset 

##### Example

```
// Request

curl -X POST -H "Content-Type:application/json" --data '{"jsonrpc":"2.0","method":"aoa_getAssetInfo","params":["aoafa204429d90d3c3256ceca9b28f3c3acd211ead8", "latest"],"id":1}'

// Result

{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "issuer": "aoafa204429d90d3c3256ceca9b28f3c3acd211ead8", // owner
    "name": "yujianToken", 
    "symbol": "ABC",
    "supply": 17,  // wei
    "desc": "my token"
  }
}

```
***

#### aoa_getDelegateList

Returns a list of delegate in Aurora chain

##### Parameters

1. `QUANTITY|TAG` - integer block number, or the string `"latest"`, `"earliest"` or `"pending"`, see the [default block parameter](#the-default-block-parameter)

```
params: [
   'latest'
]

```

##### Returns

`Object` - the information of all delegates

    - `address`: `DATA`, 20 Bytes - The delegate address.
    - `vote`:  `QUANTITY`, - the total vote number of this delegate.
    - `nickname`: `DATA`,- the name of delegate.
    - `registerTime`: `DATA` - the time that this delgate registered.


##### Example

```
// Request

curl -X POST -H "Content-Type:application/json" --data '{"jsonrpc":"2.0","method":"aoa_getDelegateList","params":["latest"],"id":1}'

// Result

{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "delegateList": [
      {
        "address": "aoaF28B430f6a73017c24E546350aDaa8eB5a91d51B",
        "vote": 0,
        "nickname": "wyy",
        "registerTime": 1528096570
      },
      {
        "address": "aoa4C694dEdED8f660A16eCf22030D4c61f9B0F7621",
        "vote": 2000000,
        "nickname": "aoa-node56",
        "registerTime": 1492009146
      }
    ],
    "delegateNumber": 2
  }
}

```
***

#### aoa_getDelegate

Returns the detail information about the specified delegate

##### Parameters

1. `DATA`,20 bytes - the address of delegate

```
params: [
   'aoaF28B430f6a73017c24E546350aDaa8eB5a91d51B'
]

```

##### Returns

see [aoa_getDelegateList](#aoa_getdelegatelist)

##### Example

```
// Request

curl -X POST -H "Content-Type:application/json" --data '{"jsonrpc":"2.0","method":"aoa_getDelegate","params":["aoaF28B430f6a73017c24E546350aDaa8eB5a91d51B"],"id":1}'

// Result

{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "address": "aoaF28B430f6a73017c24E546350aDaa8eB5a91d51B",
    "vote": 0,
    "nickname": "wyy",
    "registerTime": 1528096570
  }
}

```
***

#### aoa_getVotesList

Returns the vote result about the given address

##### Parameters

1. `DATA`,20 bytes - the vote address

```
params: [
   'aoa12df8ee4b6baec56a86a86bfeb739752ae88aa35'
]

```

##### Returns

`Object` - the list of vote address,the length of list is Less than or equal to the number of top delegate.

##### Example

```
// Request

curl -X POST -H "Content-Type:application/json" --data '{"jsonrpc":"2.0","method":"aoa_getVotesList","params":["aoa12df8ee4b6baec56a86a86bfeb739752ae88aa35"],"id":1}'

// Result

{
  "jsonrpc": "2.0",
  "id": 1,
  "result": [
    "aoa5e4a7f3a438be73f531189ba7cbfd05c17345cde",
    "aoa50c62277d15cd1e78150483f978c04c225b2d71c"
  ]
}

```
***

#### aoa_pendingTransactions

Returns the pending transactions in transaction pool

##### Parameters

none

##### Returns

`Object` - the list of pending transaction 

you can see [aoa_getTransactionByHash](#aoa_gettransactionbyhash)

##### Example

```
// Request

curl -X POST -H "Content-Type:application/json" --data '{"jsonrpc":"2.0","method":"aoa_getPendingTransactions","params":[],"id":1}'

// Result

{
  "jsonrpc": "2.0",
  "id": 1,
  "result": [
    {
      "blockHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
      "blockNumber": null,
      "from": "aoa9d797788c3a3adace9155cfead1c35224e49fa15",
      "gas": "0x61a8",
      "gasPrice": "0xee6b2800",
      "hash": "0x8ee20388ea73b4feeeffdd0e5d8242036f7fa918dc9e17d24fa506e69e499c2e",
      "input": "0x",
      "nonce": "0xb",
      "to": "aoa0315141103b566e3ac49d0011636f88bd1f560dc",
      "transactionIndex": "0x0",
      "value": "0x1",
      "v": "0x1b",
      "r": "0xacecab5a37f341f1fc5ab9e6eeec33d571a1c88b4649afeaca42685b6754f763",
      "s": "0x750512b29c0a2c7e459d1f5439682db014e8bf498e4d1c90a8320713ad851911",
      "action": 0
    }
  ]
}

```
***

#### aoa_call

Executes a new message call immediately without creating a transaction on the block chain.

##### Parameters

1. `Object` - The transaction call object
  - `from`: `DATA`, 20 Bytes - (optional) The address the transaction is sent from.
  - `to`: `DATA`, 20 Bytes  - The address the transaction is directed to.
  - `gas`: `QUANTITY`  - (optional) Integer of the gas provided for the transaction execution. aoa_call consumes zero gas, but this parameter may be needed by some executions.
  - `gasPrice`: `QUANTITY`  - (optional) Integer of the gasPrice used for each paid gas
  - `value`: `QUANTITY`  - (optional) Integer of the value sent with this transaction
  - `data`: `DATA`  - (optional) Hash of the method signature and encoded parameters. It's the same as [Ethereum Contract ABI](https://github.com/ethereum/wiki/wiki/Ethereum-Contract-ABI)
2. `QUANTITY|TAG` - integer block number, or the string `"latest"`, `"earliest"` or `"pending"`, see the [default block parameter](#the-default-block-parameter)

##### Returns

`DATA` - the return value of executed contract.

##### Example
```
// Request
curl -X POST -H "Content-Type:application/json" --data '{"jsonrpc":"2.0","method":"aoa_call","params":[{see above}],"id":1}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0x"
}
```

***

#### aoa_getCode

Returns code at a given address.


##### Parameters

1. `DATA`, 20 Bytes - address
2. `QUANTITY|TAG` - integer block number, or the string `"latest"`, `"earliest"` or `"pending"`, see the [default block parameter](#the-default-block-parameter)

```
params: [
   'aoa6e01f6c27206381f7f605f45f258ec04425c7828',
   '0x2'  // 2
]
```

##### Returns

`DATA` - the code from the given address.


##### Example
```
// Request
curl -X POST -H "Content-Type:application/json" --data '{"jsonrpc":"2.0","method":"aoa_getCode","params":["aoa740cb3be39d2485c96655fc2bbfc12a77fd42688","latest"],"id":1}' 

// Result
{"jsonrpc":"2.0","id":1,"result":"0x608060405260043610610057576000357c0100000000000000000000000000000000000000000000000000000000900463ffffffff168063428ab6cd1461005c578063ce2dcb51146100d4578063f79ec6e61461012b575b600080fd5b6100ba600480360381019080803573ffffffffffffffffffffffffffffffffffffffff169060200190929190803573ffffffffffffffffffffffffffffffffffffffff169060200190929190803590602001909291905050506101a3565b604051808215151515815260200191505060405180910390f35b3480156100e057600080fd5b50610115600480360381019080803573ffffffffffffffffffffffffffffffffffffffff169060200190929190505050610218565b6040518082815260200191505060405180910390f35b610189600480360381019080803573ffffffffffffffffffffffffffffffffffffffff169060200190929190803573ffffffffffffffffffffffffffffffffffffffff1690602001909291908035906020019092919050505061023a565b604051808215151515815260200191505060405180910390f35b600080309050828173ffffffffffffffffffffffffffffffffffffffff1685e0101580156101d15750600083115b1561020b578473ffffffffffffffffffffffffffffffffffffffff168484e1158015610201573d6000803e3d6000fd5b5060019150610210565b600091505b509392505050565b60003373ffffffffffffffffffffffffffffffffffffffff1682e09050919050565b600080309050828173ffffffffffffffffffffffffffffffffffffffff1685e0101580156102685750600083115b1561028e578473ffffffffffffffffffffffffffffffffffffffff168484e29150610293565b600091505b5093925050505600a165627a7a723058209134eaf3b2aa6efd9dcb61d1f21dffaa217f25a3efb69178579fd9d4a322f94c0029"}

```

***

#### aoa_getAbi
Returns the abi of a contract (when the abi is seted on deploying contract).

##### Parameters
1. `DATA`, 20 Bytes - address of the storage.
2. `QUANTITY|TAG` - integer block number, or the string `"latest"`, `"earliest"` or `"pending"`, see the [default block parameter](#the-default-block-parameter)

##### Returns
`DATA` - the abi string of the contract(if exists).

##### Example
```
// Request
curl -X POST -H "Content-Type:application/json" --data '{"jsonrpc":"2.0","method":"aoa_getAbi","params":["aoa740cb3be39d2485c96655fc2bbfc12a77fd42688","latest"],"id":1}' 
// Result
{"jsonrpc":"2.0","id":1,"result":"[{\"constant\":false,\"inputs\":[{\"name\":\"receiver\",\"type\":\"address\"},{\"name\":\"asset\",\"type\":\"address\"},{\"name\":\"value\",\"type\":\"uint256\"}],\"name\":\"TransferAsset\",\"outputs\":[{\"name\":\"\",\"type\":\"bool\"}],\"payable\":true,\"stataoautability\":\"payable\",\"type\":\"function\"},{\"constant\":true,\"inputs\":[{\"name\":\"asset\",\"type\":\"address\"}],\"name\":\"MyAssetBalance\",\"outputs\":[{\"name\":\"\",\"type\":\"uint256\"}],\"payable\":false,\"stataoautability\":\"view\",\"type\":\"function\"},{\"constant\":false,\"inputs\":[{\"name\":\"receiver\",\"type\":\"address\"},{\"name\":\"asset\",\"type\":\"address\"},{\"name\":\"value\",\"type\":\"uint256\"}],\"name\":\"SendAsset\",\"outputs\":[{\"name\":\"\",\"type\":\"bool\"}],\"payable\":true,\"stataoautability\":\"payable\",\"type\":\"function\"}]"}
```

***

#### aoa_getStorageAt

Returns the value from a storage position at a given address. 

##### Parameters

1. `DATA`, 20 Bytes - address of the storage.
2. `QUANTITY` - integer of the position in the storage.
3. `QUANTITY|TAG` - integer block number, or the string `"latest"`, `"earliest"` or `"pending"`, see the [default block parameter](#the-default-block-parameter)

##### Returns

`DATA` - the value at this storage position.

##### Example
Calculating the correct position depends on the storage to retrieve. Consider the following contract deployed at `aoa295a70b2de5e3953354a6a8344e616ed314d7251` by address `aoa391694e7e0b0cce554cb130d723a9d27458f9298`.

```
contract Storage {
    uint pos0;
    mapping(address => uint) pos1;
    
    function Storage() {
        pos0 = 1234;
        pos1[msg.sender] = 5678;
    }
}
```

Retrieving the value of pos0 is straight forward:

```
curl -X POST -H "Content-Type:application/json" --data '{"jsonrpc":"2.0", "method": "aoa_getStorageAt", "params": ["aoa295a70b2de5e3953354a6a8344e616ed314d7251", "0x0", "latest"], "id": 1}' localhost:8545

{"jsonrpc":"2.0","id":1,"result":"0x00000000000000000000000000000000000000000000000000000000000004d2"}
```

Retrieving an elaoaent of the map is harder. The position of an elaoaent in the map is calculated with:
```js
keccack(LeftPad32(key, 0), LeftPad32(map position, 0))
```

This means to retrieve the storage on pos1["0x391694e7e0b0cce554cb130d723a9d27458f9298"] we need to calculate the position with:
```
keccak(decodeHex("000000000000000000000000391694e7e0b0cce554cb130d723a9d27458f9298" + "0000000000000000000000000000000000000000000000000000000000000001"))
```
The aoa console which comes with the web3 library can be used to make the calculation:
```
> key = "000000000000000000000000391694e7e0b0cce554cb130d723a9d27458f9298" + "0000000000000000000000000000000000000000000000000000000000000001"
> web3.sha3(key, {"encoding": "hex"})
"0x6661e9d6d8b923d5bbaab1b96e1dd51ff6ea2a93520fdc9eb75d059238b8c5e9"
```
Now to fetch the storage:
```
curl -X POST -H "Content-Type:application/json" --data '{"jsonrpc":"2.0", "method": "aoa_getStorageAt", "params": ["aoa295a70b2de5e3953354a6a8344e616ed314d7251", "0x6661e9d6d8b923d5bbaab1b96e1dd51ff6ea2a93520fdc9eb75d059238b8c5e9", "latest"], "id": 1}' localhost:8545

{"jsonrpc":"2.0","id":1,"result":"0x000000000000000000000000000000000000000000000000000000000000162e"}

```

***

#### aoa_estimateGas

Generates and returns an estimate of how much gas is necessary to allow the transaction to complete. 
The transaction will not be added to the blockchain. Note that the estimate may be significantly more than the amount of gas 
actually used by the transaction, for a variety of reasons including EVM mechanics and node performance.

##### Parameters

See [aoa_call](#aoa_call) parameters, expect that all properties are optional. If no gas limit is specified aoa 
uses the block gas limit from the pending block as an upper bound. As a result the returned estimate might not be 
enough to executed the call/transaction when the amount of gas is higher than the pending block gas limit.

##### Returns

`QUANTITY` - the amount of gas used.

##### Example

```
// Request
 curl -X POST -H "Content-Type:application/json" --data '{"jsonrpc":"2.0","method":"aoa_estimateGas","params":[{"from":"0xfa204429d90d3c3256ceca9b28f3c3acd211ead8","to":"0xb193ca61b6d73e3cb5082a9d4bb9d2afe2ae2926","gas":"0x61a8","gasPrice":"0xee6b2800","value":"0xde0b6b3a7640000","action":0}],"id":1}'
// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0x61a8" // 25000
}

```
***

#### aoa_sign

The sign method calculates an Aurora specific signature with: `sign(keccak256("\x19Aurora Signed Message:\n" + len(message) + message)))`.

**Note** the address to sign with must be unlocked. 

##### Parameters

account, message

1. `DATA`, 20 Bytes - address
2. `DATA`, N Bytes - message to sign

##### Returns

`DATA`: Signature

##### Example

```
// Request
curl -X POST -H "Content-Type:application/json" --data '{"jsonrpc":"2.0","method":"aoa_sign","params":["0x92445192f1d0602f4aa70cd07d901361704e6587", "0xdeadbeaf"],"id":1}'

// Result

{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0xbb2f2f3e9da5130132b1f92cdf707321b6f52ddf2d435d35b50e373dd506e4cf3ed877927fc33fb0396c21d2fe65b6f203a261843a8b589d98de97e28c3c76271c"
}

```
***

#### aoa_syncing

Returns an object with data about the sync status or `false`.

##### Parameters

none

##### Returns

`Object|Boolean`, An object with sync status data or `FALSE`, when not syncing:
  - `startingBlock`: `QUANTITY` - The block at which the import started (will only be reset, after the sync reached his head)
  - `currentBlock`: `QUANTITY` - The current block, same as aoa_blockNumber
  - `highestBlock`: `QUANTITY` - The estimated highest block

##### Example

```
// Request
curl -X POST -H "Content-Type:application/json" --data '{"jsonrpc":"2.0","method":"aoa_syncing","params":[],"id":1}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": {
    startingBlock: '0x1',
    currentBlock: '0x666',
    highestBlock: '0x888'
  }
}
// Or when not syncing
{
  "id":1,
  "jsonrpc": "2.0",
  "result": false
}

```
***

#### net_version

Returns the current network id.

##### Parameters
none

##### Returns

`String` - The current network id.
- `"1"`: Aurora Mainnet
- `"3"`: Aurora Testnet

##### Example

```
// Request
curl -X POST -H "Content-Type:application/json" --data '{"jsonrpc":"2.0","method":"net_version","params":[],"id":67}'

// Result
{
  "id":67,
  "jsonrpc": "2.0",
  "result": "3"
}

```
***

#### net_peerCount

Returns number of peers currently connected to the client,including common net and top net

*note*: total number of peers is commonNet plus topNet.

##### Parameters

none

##### Returns

`Object` - the number of connected peers,contains common peers and top peers.

    - `commonNet`: `QUANTITY`,- integer of the number of connected common peers.
    - `topNet`:  `QUANTITY`, - the total vote number of connected top peers.

##### Example

```
// Request
curl -X POST -H "Content-Type:application/json" --data '{"jsonrpc":"2.0","method":"net_peerCount","params":[],"id":74}'

// Result

{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "commonNet": 0,
    "topNet": 0
  }
}

```
***

## The default block parameter

The following methods have an extra defualt block parameter:

- [aoa_getBalance](#aoa_getbalance)
- [aoa_getCode](#aoa_getcode)
- [aoa_getTransactionCount](#aoa_gettransactioncount)
- [aoa_getStorageAt](#aoa_getstorageat)
- [aoa_call](#aoa_call)
- [aoa_getAssetBalance](#aoa_getassetbalance)
- [aoa_getDetailBalance](#aoa_getdetailbalance)
- [aoa_getDelegateList](#aoa_getdelegatelist)


#### aoa_denominations

Aurora has a metric systaoa of denominations used as units of aoa. 
Each denomination has its own unique name . The smallest denomination aka base unit of aoa is called Wei. Below is a list of the named denominations and their value in Wei.

| Unit     | Wei Value | Wei                       |
| :------- | :-------- | :------------------------ |
| wei      | 1 wei     | wei                       |
| Kwei     | 1e3 wei   | 1,000                     |
| Mwei     | 1e6 wei   | 1,000,000                 |
| Gwei     | 1e9 wei   | 1,000,000,000             |
| microaoa | 1e12 wei  | 1,000,000,000,000         |
| milliaoa | 1e15 wei  | 1,000,000,000,000,000     |
| aoa      | 1e18 wei  | 1,000,000,000,000,000,000 |

***

#### action_explain

 -  0: ordinary or asset transaction
 -  1: agent registration transaction
 -  2: agent vote transaction
 -  4: asset publish transaction
 -  5: contract create transaction
 -  6: contract call transaction

***