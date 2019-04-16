# 账号(Account) 

账号及地址相关的 API，接口的参数说明请参考[Etherscan API 约定](Introduction.md), 文档中不单独说明。

##  获取单个账号余额

``` note::
 译者注: 
    英文 `balance` 有人翻译为`金额`，译者习惯称为`余额`。
    账号和地址大部分也是指一个意思。
```

接口:

```
/api?module=account&action=balance&address=0x&tag=latest&apikey=YourApiKeyToken
```

返回:
```json
{
    status: "1",
    message: "OK",
    result: "40807178566070000000000"
}
```

说明:

余额的单位都是最小单位`wei`， 更多单位换算可阅读：[以太单位换算](https://learnblockchain.cn/2018/02/02/solidity-unit/)

请求样例[URL](https://api.etherscan.io/api?module=account&action=balance&address=0xde0b295669a9fd93d5f28d9ec85e40f4cb697bae&tag=latest&apikey=YourApiKeyToken)，点击可在浏览器查看效果。


##  获取多个账号余额

接口:
```
/api?module=account&action=balancemulti&address=0xabc,0x63..,0x198..&tag=latest&apikey=YourApiKeyToken
```
使用`,`来分割地址，一次请求最多20个账号。

返回：

```json
{
status: "1",
message: "OK",
result: [
{
account: "0xddbd2b932c763ba5b1b7ae3b362eac3e8d40121a",
balance: "40807178566070000000000"
},
{
account: "0x63a9975ba31b0b9626b34300f7f627147df1f526",
balance: "332567136222827062478"
}
]
}
```


请求样例[URL](https://api.etherscan.io/api?module=account&action=balancemulti&address=0xddbd2b932c763ba5b1b7ae3b362eac3e8d40121a,0x63a9975ba31b0b9626b34300f7f627147df1f526,0x198ef1ec325a96cc354c7266a038be8b5c558f67&tag=latest&apikey=YourApiKeyToken)


## 获取地址(普通)交易列表

接口：

```
/api?module=account&action=txlist&address=&apikey=YourApiKeyToken
```

可选参数：`startblock` 、`endblock`、`sort`

返回：

```json
{
	"status": "1",
	"message": "OK",
	"result": [{
		"blockNumber": "47884",
		"timeStamp": "1438947953",
		"hash": "0xad1c27dd8d0329dbc400021d7477b34ac41e84365bd54b45a4019a15deb10c0d",
		"nonce": "0",
		"blockHash": "0xf2988b9870e092f2898662ccdbc06e0e320a08139e9c6be98d0ce372f8611f22",
		"transactionIndex": "0",
		"from": "0xddbd2b932c763ba5b1b7ae3b362eac3e8d40121a",
		"to": "0x2910543af39aba0cd09dbb2d50200b3e800a63d2",
		"value": "5000000000000000000",
		"gas": "23000",
		"gasPrice": "400000000000",
		"isError": "0",
		"txreceipt_status": "",
		"input": "0x454e34354139455138",
		"contractAddress": "",
		"cumulativeGasUsed": "21612",
		"gasUsed": "21612",
		"confirmations": "7525550"
	}]
}
```

说明:

 **isError**： 0= 没错, 1=出错
 最多返回最近的10000个交易
 
 返回字段中出现的关键字可参考[以太坊设计与实现-术语](https://learnblockchain.cn/books/geth/term.html)。


请求样例[URL](http://api.etherscan.io/api?module=account&action=txlist&address=0xddbd2b932c763ba5b1b7ae3b362eac3e8d40121a&startblock=0&endblock=99999999&sort=asc&apikey=YourApiKeyToken)

也可以使用分页，参数说明请参考[Etherscan API 约定](Introduction.md)，分页请求样例[URL](https://api.etherscan.io/api?module=account&action=txlist&address=0xddbd2b932c763ba5b1b7ae3b362eac3e8d40121a&startblock=0&endblock=99999999&page=1&offset=10&sort=asc&apikey=YourApiKeyToken)



## 获取地址”内部”交易列表

内部交易只指引一个正常（外部）交易（连带）触发的交易，比如过一个合约调用触发的内部交易。

接口：
```
/api?module=account&action=txlistinternal&address=
```

可选参数：`startblock` 、`endblock`、`sort`

返回结果和普通交易列表JSON结构一样。

请求样例[URL](http://api.etherscan.io/api?module=account&action=txlistinternal&address=0x2c1ba59d6f58433fb1eaee7d20b26ed83bda51a3&startblock=0&endblock=2702578&sort=asc&apikey=YourApiKeyToken)


## 获取地址ERC20转账交易列表

转账交易是通过`Transfer`事件来判定的。


接口：
```
/api?module=account&action=tokentx&address=&contractaddress
```

说明： 可选参数：`startblock` 、`endblock`、`contractaddress` 、`sort`
可以通过参数`contractaddress`来指定某一个合约的交易。


返回和上面普通交易列表JSON结构一样。

请求样例：

1. [使用普通地址请求ERC20转账列表](http://api.etherscan.io/api?module=account&action=tokentx&address=0x4e83362442b8d1bec281594cea3050c8eb01311c&startblock=0&endblock=999999999&sort=asc&apikey=YourApiKeyToken)
2. [仅使用合约地址请求ERC20转账列表](https://api.etherscan.io/api?module=account&action=tokentx&contractaddress=0x9f8f72aa9304c8b593d555f12ef6589cc3a579a2&page=1&offset=100&sort=asc&apikey=YourApiKeyToken)
3. [同时使用普通地址和合约地址请求ERC20转账列表](https://api.etherscan.io/api?module=account&action=tokentx&contractaddress=0x9f8f72aa9304c8b593d555f12ef6589cc3a579a2&address=0x4e83362442b8d1bec281594cea3050c8eb01311c&page=1&offset=100&sort=asc&apikey=YourApiKeyToken)

## 获取地址所挖区块列表

接口：
```
/api?module=account&action=getminedblocks&address=&blocktype=blocks
```

说明：blocktype 值为 blocks（仅显示主链块） 或 uncles （仅显示叔块） ， blocks为默认值 


返回：

```json
{
status: "1",
message: "OK",
result: [
{
blockNumber: "3462296",
timeStamp: "1491118514",
blockReward: "5194770940000000000"
},
{
blockNumber: "2691400",
timeStamp: "1480072029",
blockReward: "5086562212310617100"
}
]
}
```

说明：
**blockReward** ：区块奖励， 同样使用最小单位`wei`， 更多单位换算可阅读：[以太单位换算](https://learnblockchain.cn/2018/02/02/solidity-unit/)



请求样例[URL](https://api.etherscan.io/api?module=account&action=getminedblocks&address=0x9dd134d14d1e65f84b706d6f205cd5b1cd03a46b&blocktype=blocks&apikey=YourApiKeyToken)及[分页请求](https://api.etherscan.io/api?module=account&action=getminedblocks&address=0x9dd134d14d1e65f84b706d6f205cd5b1cd03a46b&blocktype=blocks&page=1&offset=10&apikey=YourApiKeyToken)


