Etherscan 文档简介
================================

Etherscan 是以太坊上应用最广泛的区块链浏览器，也提供 `API 服务 <https://etherscan.io/apis>`_。

本翻译由 `深入浅出区块链  <https://learnblockchain.cn/>`_ 社区成员翻译、整理、校队。需转载请联系微信：xlbxiong 获取授权。
如您在阅读时发现不准确或错误的地方，欢迎到 `GitHub 提Issues  <https://github.com/lbc-team/etherscan-docs>`_ 指正。


简介
==================

我们知道以太坊节点提供的API功能有限，尤其是需要一些多个区块相关的数据时，必须要依靠Etherscan API这样的服务。

Etherscan API是社区提供的服务，仅支持每秒 5 个GET或POST请求，可以在这个地址 `API-Keys <https://etherscan.io/myapikey>`_ 申请一个Key。

如果在商业或站点中使用，应该表明服务由 Etherscan.io API 提供支持。



.. toctree::
   :maxdepth: 2
   :caption: Etherscan APIs 手册

   Introduction.md
   Accounts.md
   Contracts.md
   Transactions.md
   Blocks.md
   EventLogs.md
   GethParityProxy.md
   Tokens.md
   Stats.md
   MiscToolsUtilities.md
   sphinx.md


Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
