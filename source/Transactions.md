# 交易（Transaction）

交易相关的 API，接口的参数说明请参考[Etherscan API 约定](Introduction.md), 文档中不单独说明。

## [BETA] 检查合约执行状态 

(if there was an error during contract execution)

Note: isError":"0" = Pass , isError":"1" = Error during Contract Execution

```
https://api.etherscan.io/api?module=transaction&action=getstatus&txhash=0x15f8e5ea1079d9a0bb04a4c58ae5fe7654b5b2b4463375ff7ffb490aa0032f3a&apikey=YourApiKeyToken
```

## [BETA] 检查交易收据状态

(Only applicable for Post Byzantium fork transactions)

Note: status: 0 = Fail, 1 = Pass. Will return null/empty value for pre-byzantium fork

```
https://api.etherscan.io/api?module=transaction&action=gettxreceiptstatus&txhash=0x513c1ba0bebf66436b5fed86ab668452b7805593c05073eb2d51d3a52f480a76&apikey=YourApiKeyToken
```


