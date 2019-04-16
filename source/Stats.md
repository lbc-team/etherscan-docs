# 常规状态数据(General Stats)

常规状态数据API，接口的参数说明请参考[Etherscan API 约定](Introduction.md), 文档中不单独说明。

## Get Total Supply of Ether


```
https://api.etherscan.io/api?module=stats&action=ethsupply&apikey=YourApiKeyToken
```

(Result returned in Wei, to get value in Ether divide resultAbove/1000000000000000000)

## Get ETHER Last Price


```
https://api.etherscan.io/api?module=stats&action=ethprice&apikey=YourApiKeyToken
```

## Get Ethereum Nodes Size

[Parameters] startdate and enddate format 'yyyy-MM-dd', clienttype value is 'geth' or 'parity', syncmode value is 'default' or 'archive'


```
https://api.etherscan.io/api?module=stats&action=chainsize&startdate=2019-02-01&enddate=2019-02-28&clienttype=geth&syncmode=default&sort=asc&apikey=YourApiKeyToken
```

(The chainsize return in bytes.)


