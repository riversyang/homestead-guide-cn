.. _ether:

********************************************************************************
以太币
********************************************************************************

以太币是什么？
================================================================================

以太币（Ether）就是以太坊中使用的虚拟货币的名字，它被用来为EVM中的计算付费。这是在为购买以太币的气（gas）时间接完成的，就像在 _`gas` 那节中所解释的那样。

单位面额
--------------------------------------------------------

为了使用以太币，以太坊有个面额计量体系。每个计量单位都有个唯一的名称（其中一些是在计算机科学及加密经济学领域中的标志性人物的姓氏）。其中，最小的计量单位，也就是以太币的 *基础单位* 叫做Wei。以下是已命名的面额单位以及它们与Wei的兑换关系。请注意，尽管有很多误解，但以太坊并不是个货币名称或者计量单位。


+-------------------------+-----------+-------------------------------------------+
| Unit                    | Wei Value | Wei                                       |
+=========================+===========+===========================================+
| **wei**                 | 1 wei     | 1                                         |
+-------------------------+-----------+-------------------------------------------+
| **Kwei (babbage)**      | 1e3 wei   | 1,000                                     |
+-------------------------+-----------+-------------------------------------------+
| **Mwei (lovelace)**     | 1e6 wei   | 1,000,000                                 |
+-------------------------+-----------+-------------------------------------------+
| **Gwei (shannon)**      | 1e9 wei   | 1,000,000,000                             |
+-------------------------+-----------+-------------------------------------------+
| **microether (szabo)**  | 1e12 wei  | 1,000,000,000,000                         |
+-------------------------+-----------+-------------------------------------------+
| **milliether (finney)** | 1e15 wei  | 1,000,000,000,000,000                     |
+-------------------------+-----------+-------------------------------------------+
| **ether**               | 1e18 wei  | 1,000,000,000,000,000,000                 |
+-------------------------+-----------+-------------------------------------------+


以太币的供给
=========================

* https://blog.ethereum.org/2014/04/10/the-issuance-model-in-ethereum/
* https://www.reddit.com/r/ethereum/comments/44zy88/clarification_on_ether_supply_and_cost_of_gas/
* https://www.reddit.com/r/ethereum/comments/45vj4g/question_about_scarcity_of_ethereum_and_its/
* https://www.reddit.com/r/ethtrader/comments/48yqg6/is_there_a_cap_like_with_btc_with_how_many_ether/


得到以太币
================================================================================

为了获得以太币，你需要

* 成为一个以太坊矿工（参考 :ref:`mining` ），或者
* 用一个中心化的或者去信任的服务用其他货币买进以太币
* 在有友好界面的 `Mist以太坊钱包 <https://github.com/ethereum/mist/releases>`_ 中使用http://shapeshift.io/ API来购买以太币

去信任的服务
--------------------------------------------------------------------------------

请注意，有了以太坊平台，基于智能合约的去信任服务，消除了对可信的第三方货币交换机构的需求，比如非居间投资的货币兑换业务。

这样的项目有：

* `BTCrelay <http://btcrelay.org/>`_
   * `More information <https://medium.com/@ConsenSys/taking-stock-bitcoin-and-ethereum-4382f0a2f17>`_ (about ETH/BTC 2-way peg without modifying bitcoin code).
   * `BTCrelay audit <http://martin.swende.se/blog/BTCRelay-Auditing.html>`_
* `EtherEx decentralised exchange <https://etherex.org>`_.

中心化的交易市场
--------------------------------------------------------------------------------

========================== ============================
Exchange                   Currencies
========================== ============================
Poloniex                   BTC
Kraken                     BTC, USD, EUR, CAD, GBP
Gatecoin                   BTC, EUR
Bitfinex                   BTC, USD
Bittrex                    BTC
Bluetrade                  BTC, LTC, DOGE
HitBTC                     BTC
Livecoin                   BTC
Coinsquare                 BTC
Bittylicious               GBP
BTER                       CNY
Yunbi                      CNY
Metaexchange               BTC
========================== ============================

中心化的固定比率兑换
-----------------------------------

========================== ============================
Exchange                   Currencies
========================== ============================
`Shapeshift`_              BTC, LTC, DOGE, Other
`Bity`_                    BTC, USD, EUR, CHF
========================== ============================

.. _Bity: https://bity.com
.. _Shapeshift: shapeshift.io


交易和价格分析
--------------------------------------------------------------------------------

* `ETH markets exhaustive listing by volume on coinmarketcap <https://coinmarketcap.com/currencies/ethereum/#markets>`_
* Aggregating realtime stats of major ETH markets:

  * `Tradeblock <https://tradeblock.com/ethereum>`_
  * `EthereumWisdom <http://ethereumwisdom.com>`_
  * `Cryptocompare <https://www.cryptocompare.com/coins/eth/overview>`_
  * `Coinmarketcap <https://coinmarketcap.com/currencies/ethereum/>`_


.. _online-wallets-and-storage-solutions:

在线钱包、纸质钱包和冷库
================================================================================

.. todo::
  这里只是一个包含链接和便签的临时区域，之后会由生态系统中的具体列表来覆盖。

* Mist Ethereum Wallet
    * `Releases to download <https://github.com/ethereum/mist/releases>`_
    * `Mist Ethereum Wallet developer preview <https://blog.ethereum.org/2015/09/16/ethereum-wallet-developer-preview/>`_ - foundation blog post
    * `How to easily set up the Ethereum Mist wallet! <https://www.youtube.com/watch?v=Z6lE0Ctaeqs>`_ - Tutorial by Tommy Economics
* Kryptokit Jaxx
    * `Jaxx main site <http://jaxx.io/>`_
    * `Mobile release <http://favs.pw/first-ethereum-mobile-app-released/#.VsHn_PGPL5c>`_
* Etherwall
    * `Etherwall website <http://www.etherwall.com/>`_
    * `Etherwall source <https://github.com/almindor/etherwall>`_
* MyEtherWallet
    * `MyEtherWallet website <https://www.myetherwallet.com/>`_
    * `MyEtherWallet source <https://github.com/kvhnuke/etherwallet/>`_
    * `Chrome extension <http://sebfor.com/myetherwallet-chrome-extension-release/>`_
* Cold storage
    * `Icebox <https://github.com/ConsenSys/icebox>`_ by `ConsenSys <https://consensys.net/>`_ - Cold storage based on lightwallet with HD wallet library integrated.
    * `Reddit discussion 1 <https://www.reddit.com/r/ethereum/comments/45uvmy/offline_cold_storage_question/offline_cold_storage_question>`_
    * `How to setup a cold storage wallet <https://www.reddit.com/r/ethereum/comments/48wfbv/eli5_how_to_setup_a_cold_storage_wallet_as/>`_
* Hardware wallet
    * `reddit discussion 2 <https://www.reddit.com/r/ethereum/comments/45siaq/hardware_wallet/>`_
    * `reddit discussion 3 <https://www.reddit.com/r/ethereum/comments/4521o4/crowdfunding_ethereum_hardware_cold_storage_wallet/>`_
* Brain wallet
    * brain wallets are not safe, do not use them. https://www.reddit.com/r/ethereum/comments/45y8m7/brain_wallets_are_now_generally_shunned_by/
    * Extreme caution with brain wallets. Read the recent controversy: https://reddit.com/r/ethereum/comments/43fhb5/brainwallets vs http://blog.ether.camp/post/138376049438/why-brain-wallet-is-the-best
* Misc
    * `Kraken Wallet Sweeper Tool <https://www.kraken.com/ether>`_ - Pre-sale wallet import
    * `Recommended ways to safely store ether <http://ethereum.stackexchange.com/questions/1239/what-is-the-recommended-way-to-safely-store-ether>`_
    * `How to buy and store ether <http://sebfor.com/how-to-buy-and-store-ether/>`_
    * `A laymen's intro into brute forcing and why not to use brain wallets <http://www.fastcompany.com/3056651/researchers-find-a-crack-that-drains-supposedly-secure-bitcoin-wallets>`_
    * `Pyethsaletool <https://github.com/ethereum/pyethsaletool/blob/master/README.md>`_
    * `Account vs wallet <https://www.reddit.com/r/ethereum/comments/47j3r5/eli5_accounts_vs_wallet_contracts_on_mist/>`_

发送以太币
================================================================================

 `以太坊钱包 <https://github.com/ethereum/mist/releases>`_ 支持通过图形用户界面发送以太币。

你也可以使用 **geth控制台** 传送以太币。

.. code-block:: console

    > var sender = eth.accounts[0];
    > var receiver = eth.accounts[1];
    > var amount = web3.toWei(0.01, "ether")
    > eth.sendTransaction({from:sender, to:receiver, value: amount})

更多详情，请参考 :ref:`account-types-gas-and-transactions` 。

在加密货币领域，以太坊是唯一使用以太币作为价值媒介的，这通常也就是指的“气（gas）”。除了交易费以外，气是作为网络中的每个请求的核心部分有发送者提供，由实际计算方消费的。气的消费成本是基于请求的复杂度和当前气的价格来动态计算的。从整体来看，气的价值在于维持以太币和以太坊的稳定以及长期需求。更多信息，请参考 :ref:`account-types-gas-and-transactions` 。

气和以太币
=============================

* https://www.reddit.com/r/ethereum/comments/271qdz/can_someone_explain_the_concept_of_gas_in_ethereum/
* https://www.reddit.com/r/ethereum/comments/3fnpr1/can_someone_possibly_explain_the_concept_of/
* https://www.reddit.com/r/ethereum/comments/49gol3/can_ether_be_used_as_a_currency_eli5_ether_gas/

气被设计为网络资源/网络使用的固定成本。我们希望发送一个交易的实际成本都是一样的，所以我们不能期待发行的气，也就是一般意义上的货币，是不稳定的。

取而代之，我们发行价格可以浮动的以太币，同时也执行一个气与以太币的兑换价格。如果以太币的价格涨了，气和以太币的比价就将降低，以保证气的真实成本是一样。

气与多个概念相关联：气的价格、气的成本、气的上限和气费。气的本质是以太坊网络中交易或者计算成本的一种稳定的衡量。

* 气的成本是一个衡量计算成本的静态的数值，它的意图是使气的价值永远不变，所以其成本也就不随时间推移而变化。
* 气的价格是气相对于其他货币或代币的成本，比如以太币。为了稳定气的价值，气的价格是会随着代币或货币价格浮动而浮动的，以保持它的真实价值。气的价格会根据有多少用户希望消费以及有多少处理节点希望接收的平衡关系而计算出来。
* 气的上限是指每个区块中最多可以使用多少气，这也是一个区块的计算负载、交易数量或区块大小的最大值。矿工们可以随着时间推移修改缓慢地修改这个数值。
* 气费就是运行一个标准的交易或程序（也就是合约）所需要花费的气。一个区块的气费可以用来标识一个区块的计算负载、交易数量或区块大小。气费会被支付给矿工（或Pos中的绑定合约账户）。
