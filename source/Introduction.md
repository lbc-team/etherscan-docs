# Etherscan API 约定

当前翻译[Etherscan官方 API](https://etherscan.io/apis)时间为**2019年4月**，因官方API没有版本号，这里用时间做一个标注。

## 包含模块

Etherscan API 主要包含模块有：
* 账号地址相关接口
* 智能合约相关接口
* 交易相关接口
* 区块相关接口
* 事件日志相关接口
* Tokens代币相关接口
* 状态相关接口
* 一些相关工具相关接口

这些模块对应着左侧的一级菜单，在接口中使用`module`参数指定

## 参数

参数说明：

* module: 指明接口所属模块，即上面包含的模块
* action: API动作，如：txlist - 表示列出交易记录；
* address: 所查询交易的账号地址；
* contractaddress: 合约地址
* apikey: 用户API-key 根据key来统计请求限额；
* startblock: 起始查询块 id，可选，默认值为 0；
* endblock: 结束查询块 id，可选，默认值为最后一个区块；
* tag:  状态：pending 或 latest
* blocktype: 块类型：blocks（主链块） 或 uncles （叔块）
* page: 页码，可选；
* offset: 每页查询记录数，可选，默认是查询 10000 条记录；
* sort: 排序规则，支持正序asc和倒序desc。


module、action、apikey是每个 API 都有的参数，其他的参数则因不同 API 而不同，这里做一个统一的介绍，后面介绍接口时不再单独说明。

## 测试网络接口Host

主网的Host是 **api.etherscan.io**，其实Etherscan API 所有接口在测试网络下也使用，只是所使用的域名不同，目前支持的三个网络的Host为：

* api-ropsten.etherscan.io
* api-kovan.etherscan.io
* api-rinkeby.etherscan.io
