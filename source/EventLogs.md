# 事件日志 (Event Logs)

事件日志相关 API，接口的参数说明请参考[Etherscan API 约定](Introduction.md), 文档中不单独说明。

[Beta] The Event Log API was designed to provide an alternative to the native eth_getLogs. Below are the list of supported filter parameters:

    * fromBlock, toBlock, address
    * topic0, topic1, topic2, topic3 (32 Bytes per topic)
    * topic0_1_opr (and|or between topic0 & topic1), topic1_2_opr (and|or between topic1 & topic2), topic2_3_opr (and|or between topic2 & topic3), topic0_2_opr (and|or between topic0 & topic2), topic0_3_opr (and|or between topic0 & topic3), topic1_3_opr (and|or between topic1 & topic3)

* fromBlock and toBlock accepts the blocknumber (integer, NOT hex) or 'latest' (earliest & pending is NOT supported yet)
* Topic Operator (opr) choices are either 'and' or 'or' and are restricted to the above choices only
* fromBlock and toBlock parameters are required
* Either the address and/or topic(X) parameters are required, when multiple topic(X) parameters are used the topicX_X_opr (and|or operator) is also required
* For performance & security considerations, only the first 1000 results are return. So please narrow down the filter parameters


Here are some examples of how this filter maybe used:

## 通过指定区块获取日志

如获取地址为 0x33990122638b9132ca29c723bdf037f1a891a70c 区块从 379224 到最新区块 主题 topic[0] = 0xf63780e752c6a54a94fc52715dbc5518a3b4c3c2833d301a204226548a2a8545 的事件日志的方法为：

```
https://api.etherscan.io/api?module=logs&action=getLogs
&fromBlock=379224
&toBlock=latest
&address=0x33990122638b9132ca29c723bdf037f1a891a70c
&topic0=0xf63780e752c6a54a94fc52715dbc5518a3b4c3c2833d301a204226548a2a8545
&apikey=YourApiKeyToken
```

## 通过指定区块获取日志

Get Event Logs from block number 379224 to block 400000 , where log address = 0x33990122638b9132ca29c723bdf037f1a891a70c, topic[0] = 0xf63780e752c6a54a94fc52715dbc5518a3b4c3c2833d301a204226548a2a8545 'AND' topic[1] = 0x72657075746174696f6e00000000000000000000000000000000000000000000

```
https://api.etherscan.io/api?module=logs&action=getLogs
&fromBlock=379224
&toBlock=400000
&address=0x33990122638b9132ca29c723bdf037f1a891a70c
&topic0=0xf63780e752c6a54a94fc52715dbc5518a3b4c3c2833d301a204226548a2a8545
&topic0_1_opr=and
&topic1=0x72657075746174696f6e00000000000000000000000000000000000000000000
&apikey=YourApiKeyToken
```
