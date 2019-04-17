# 代币信息 Token

代币信息API，接口的参数说明请参考[Etherscan API 约定](Introduction.md), 文档中不单独说明。

## 通过合约地址获取ERC20 Token总供应量

了解[ERC20 代币定义与创建](https://learnblockchain.cn/2018/01/12/create_token/)


```
https://api.etherscan.io/api?module=stats&action=tokensupply&contractaddress=0x57d90b64a1a57749b0f932f1a3395792e12e7055&apikey=YourApiKeyToken
```

[**弃用**]Get Token TotalSupply by TokenName (Supported TokenNames: DGD, MKR, FirstBlood, HackerGold, ICONOMI, Pluton, REP, SNGLS). This has feature been deprecated, instead use the Api above to look up any ERC20 token supply by its contract address

https://api.etherscan.io/api?module=stats&action=tokensupply&tokenname=DGD&apikey=YourApiKeyToken

## 获取ERC20代币余额


```
https://api.etherscan.io/api?module=account&action=tokenbalance&contractaddress=0x57d90b64a1a57749b0f932f1a3395792e12e7055&address=0xe04f27eb70e025b78871a2ad7eabe85e61212761&tag=latest&apikey=YourApiKeyToken
```

[**弃用**]Get Token Account Balance by known TokenName (Supported TokenNames: DGD, MKR, FirstBlood, ICONOMI, Pluton, REP, SNGLS). This feature has been deprecated, instead use the Api above to look up any ERC20 token balance by its contract address

https://api.etherscan.io/api?module=account&action=tokenbalance&tokenname=DGD&address=0x4366ddc115d8cf213c564da36e64c8ebaa30cdbd&tag=latest&apikey=YourApiKeyToken
