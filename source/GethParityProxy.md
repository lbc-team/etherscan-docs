# Geth/Parity Proxy APIs

节点服务代理API，接口的参数说明请参考[Etherscan API 约定](Introduction.md), 文档中不单独说明。

The following are the limited list of supported Proxied APIs for Geth available through Etherscan. For the list of the parameters and descriptions please see https://github.com/ethereum/wiki/wiki/JSON-RPC. Parameters provided should be named like in the examples below. For compatibility with Parity, please prefix all hex strings with "0x"

## 获取最近区块号

Returns the number of most recent block

```
https://api.etherscan.io/api?module=proxy&action=eth_blockNumber&apikey=YourApiKeyToken
```

## eth_getBlockByNumber

Returns information about a block by block number

```
https://api.etherscan.io/api?module=proxy&action=eth_getBlockByNumber&tag=0x10d4f&boolean=true&apikey=YourApiKeyToken
```

## eth_getUncleByBlockNumberAndIndex

Returns information about a uncle by block number

```
https://api.etherscan.io/api?module=proxy&action=eth_getUncleByBlockNumberAndIndex&tag=0x210A9B&index=0x0&apikey=YourApiKeyToken
```

## eth_getBlockTransactionCountByNumber

Returns the number of transactions in a block from a block matching the given block number

```
https://api.etherscan.io/api?module=proxy&action=eth_getBlockTransactionCountByNumber&tag=0x10FB78&apikey=YourApiKeyToken
```

## eth_getTransactionByHash

Returns the information about a transaction requested by transaction hash

```
https://api.etherscan.io/api?module=proxy&action=eth_getTransactionByHash&txhash=0x1e2910a262b1008d0616a0beb24c1a491d78771baa54a33e66065e03b1f46bc1&apikey=YourApiKeyToken
```

## eth_getTransactionByBlockNumberAndIndex

Returns information about a transaction by block number and transaction index position

```
https://api.etherscan.io/api?module=proxy&action=eth_getTransactionByBlockNumberAndIndex&tag=0x10d4f&index=0x0&apikey=YourApiKeyToken
```

## eth_getTransactionCount

Returns the number of transactions sent from an address


```
https://api.etherscan.io/api?module=proxy&action=eth_getTransactionCount&address=0x2910543af39aba0cd09dbb2d50200b3e800a63d2&tag=latest&apikey=YourApiKeyToken

```

## eth_sendRawTransaction

Creates new message call transaction or a contract creation for signed transactions


```
https://api.etherscan.io/api?module=proxy&action=eth_sendRawTransaction&hex=0xf904808000831cfde080&apikey=YourApiKeyToken
```

(Replace the hex value with your raw hex encoded transaction that you want to send.
Send as a POST request, if your hex code is particularly long)

## eth_getTransactionReceipt

Returns the receipt of a transaction by transaction hash


```
https://api.etherscan.io/api?module=proxy&action=eth_getTransactionReceipt&txhash=0x1e2910a262b1008d0616a0beb24c1a491d78771baa54a33e66065e03b1f46bc1&apikey=YourApiKeyToken
```

## eth_call

Executes a new message call immediately without creating a transaction on the block chain


```
https://api.etherscan.io/api?module=proxy&action=eth_call&to=0xAEEF46DB4855E25702F8237E8f403FddcaF931C0&data=0x70a08231000000000000000000000000e16359506c028e51f16be38986ec5746251e9724&tag=latest&apikey=YourApiKeyToken
```
## eth_getCode

Returns code at a given address


```
https://api.etherscan.io/api?module=proxy&action=eth_getCode&address=0xf75e354c5edc8efed9b59ee9f67a80845ade7d0c&tag=latest&apikey=YourApiKeyToken
```
## eth_getStorageAt (**experimental)

Returns the value from a storage position at a given address


```
https://api.etherscan.io/api?module=proxy&action=eth_getStorageAt&address=0x6e03d9cce9d60f3e9f2597e13cd4c54c55330cfd&position=0x0&tag=latest&apikey=YourApiKeyToken
```
## eth_gasPrice

Returns the current price per gas in wei


```
https://api.etherscan.io/api?module=proxy&action=eth_gasPrice&apikey=YourApiKeyToken
```
## eth_estimateGas

Makes a call or transaction, which won't be added to the blockchain and returns the used gas, which can be used for estimating the used gas


```
https://api.etherscan.io/api?module=proxy&action=eth_estimateGas&to=0xf0160428a8552ac9bb7e050d90eeade4ddd52843&value=0xff22&gasPrice=0x051da038cc&gas=0xffffff&apikey=YourApiKeyToken
```

