.. _dapps:

********************************************************************************
Dapps
********************************************************************************

一个Dapp是一个使最终用户和服务提供者可以直接交互的服务（比如某些市场中的买家和卖家，文件存储服务中的所有者和保存者）。以太坊Dapp一般会允许用户通过一个使用javascript API的HTML/Javascript web应用程序来与区块链进行交流。Dapp一般会在区块链上保有它们自己的一些合约，作为它们的业务逻辑和业务状态的持久化存储的载体。由于以太坊网络中的冗余计算要求，实际运行所消耗的气总是会高于在私有链上执行时的消耗。这就使Dapp的开发者需要限制他们需要保存到区块链上的的代码量和数据存储量。

Dapp名录
====================================

使用以太坊的Dapp被编制到下边的名单中。其中列出了它们的开发状态（概念、原型、活跃/已发布）。如果你正在开发Dapp，请考虑将其加入这些名单中：

* `Ethercasts State of the Ðapps <http://dapps.ethercasts.com/>`_

这里列出的去中性化服务涵盖了非常广泛的领域，包括：金融、保险、预测市场（prediction markets）、社交网络、分布式计算和存储、赌博、集市、物联网、政府、协作、开发以及游戏。

* 我们最终会希望得到什么样的应用？ https://www.reddit.com/r/ethereum/comments/2mnl7f/the_top_10_ether_dapps_of_2015/cm63nsf

未来，Dapp将会由集成到Dapp浏览器的Dapp市场来进行罗列和分发。

Dapp浏览器
===========================

* `Mist <https://github.com/ethereum/mist>`_ - official GUI dapp browser developed by the foundation, alpha stage. Mist as Wallet dapp is in beta.
* `Status <https://status.im/>`_ - Mobile Ethereum browser (alpha)
* `MetaMask <https://metamask.io/>`_ - Aaron Kumavis Davis's in-browser GUI. `Epicenter Bitcoin interview on github <https://www.reddit.com/r/ethereum/comments/3x97rg/aaron_davis_explains_the_differences_between/>`_ - supported by DEVgrants
* `AlethZero <https://github.com/ethereum/alethzero>`_ - C++ eth client GUI, (discontinued).
* `Supernova <http://www.supernove.cc>`_ - (discontinued).

********************************************************************************
开发工具
********************************************************************************

Dapp开发需要对Web3 Javascript API、JSON RPC API以及Solidity开发语言的相关理解。

.. note:: 这里有一些可以帮助你自动化地利用相关资源来开发、测试和发布Dapp的工具。

* `Web3 JavaScript API <https://github.com/ethereum/wiki/wiki/JavaScript-API>`__ - 这是你想要和以太坊节点进行交互时会用到的主要的javascript SDK。
* `JSON RPC API <https://github.com/ethereum/wiki/wiki/JSON-RPC>`__ - 这是 `Web3 JavaScript API <https://github.com/ethereum/wiki/wiki/JavaScript-API>`__ 用到的底层JSON RPC 2.0接口。
* `Solidity Docs <https://solidity.readthedocs.org/en/latest/>`__ - Solidity是开发以太坊智能合约所需的语言，可以被编译为EVM操作码。
* `Solium <https://github.com/duaraghav8/Solium/>`__ - 一个遵从官方的 `Solidity风格指引 <http://solidity.readthedocs.io/en/latest/style-guide.html>`__ 的Solidity语法检查工具。
* :ref:`test-networks` - 测试网络帮助开发者开发和测试以太坊代码和网络交互，而不需要它们在主网络上花费自己的以太币。后边会列出一些测试网络选项。
* :ref:`IDE-or-development-framework` 这可以协助你开发、调试和发布以太坊应用程序。

.. _IDE-or-development-framework:

Dapp开发资源
=====================================================

* `Smart contracts ELI5 <https://www.reddit.com/r/ethereum/comments/2cbwak/ethereum_contracts_please_eli5/>`_
* https://blog.slock.it/a-primer-to-the-decentralized-autonomous-organization-dao-69fb125bd3cd
* `A 101 noob's intro to programming smart contracts <https://www.reddit.com/r/ethereum/comments/44vs8b/a_101_noob_intro_to_programming_smart_contracts/>`_
* `Standardised contract APIs listing <https://www.reddit.com/r/ethereum/comments/3k3jha/reminder_standardized_contract_apis_listing/>`_

一些样例
----------------------

* `example use of pricefeed - web3 script printing all account balances <https://gist.github.com/larspensjo/ffd2e4d41f739dc5af54>`_
* `Example Ethereum contracts <https://github.com/drupalnomad/ethereum-contracts>`_

https://dappsforbeginners.wordpress.com/tutorials/your-first-dapp/

https://github.com/ethereum/wiki/wiki/Dapp-Developer-Resources

一些指导
--------------

* `Dapp tutorials on ethereum.org <https://ethereum.org>`_
* `Dapps for beginners tutorial series <https://dappsforbeginners.wordpress.com/>`_
* `Eris' Solidity Tutorial Series <https://docs.erisindustries.com/tutorials/solidity/>`_
* `Tutorials on advanced Solidity <https://github.com/androlo/solidity-workshop>`_
* http://ethereumj.io/blog/2015/09/09/friendly-ether-bot/
* https://github.com/ConsenSys/ether-pudding

Mix-IDE
================================================================================

Mix是官方的以太坊IDE，让开发者可以在以太坊区块链上创建、发布合约和去中性化应用。它包含了一个Solidity源码的调试器。 :ref:`sec:mix` （已终止）

IDEs/Frameworks
================================================================================

以下使一些开发框架和IDE，可以用来书写以太坊Dapp。

* `Truffle <https://github.com/ConsenSys/truffle>`__ - Truffle是一个以太坊的开发环境、测试框架和资产渠道。
* `Dapple <https://github.com/nexusdev/dapple>`__ - Dapple是一个Solidity开发者工具，有助于在类似于以太坊的区块链上构建和管理复杂的合约系统。
* `Populus <http://populus.readthedocs.org/en/latest/>`__ - Populus是一个用Python写的智能合约开发框架。
* `Eris-PM <https://docs.erisindustries.com/documentation/eris-package-manager/>`__ - Eris包管理器可以在私有链和公有链上发布和测试智能合约系统。
* `Embark <https://iurimatias.github.io/embark-framework/>`__ - Embark是一个用javascript写的Dapp开发框架。
* `EtherScripter \(obsolete, discontinued\) <http://etherscripter.com/0-5-1/>`_
* `Resilience Raw Transaction Broadcaster <https://github.com/resilience-me/broadcaster/>`_

Ethereum控制台
================================================================================

以太坊节点的命令行控制台。

`Ethconsole <https://github.com/ethereum/ethereum-console>`_ 可以通过IPC连接到以太坊节点并后台运行，它可以提供一个包含了web3对象和admin功能的javascript控制台。

这里你可以找到一个有效命令的列表 `以太坊节点控制命令 <https://github.com/ethereum/ethereum-console/blob/master/web3Admin.js>`_ 。

要是用控制台，你需要启动一个本地以太坊节点，并允许IPC socket通信（在数据目录中的 ``geth.ipc`` 文件）。你启动一个节点之后，可以在本地的主目录 .ethereum 下找到IPC socket文件。你可以设置 ``--test`` 选项来使用特定的节点测试命令。

.. code:: Console

   > eth --test
   > ethconsole ipc://path/to/geth.ipc

在控制台输入：

.. code:: Console

   > web3.eth.<command name> (arguments, function(){})

这里是 ``--test`` 模式的节点命令：

.. code:: Console

   > web3.test.addBlock("[RLP]", function(){}) - Add a block from a string containing its hex RLP
   > web3.test.rewindToBlock:("[int]", function(){}) - Reset the blockchain to specified block number
   > web3.test.mineBlocks:("[int]", function(){}) - Mine a certain amount of NoProof blocks into chain
   > web3.test.modifyTimestamp:("[int]", function(){}) - Set current block timestamp
   > web3.test.setChainParams:("[json]", function(){}) - Reset the blockchain with given node configuration file

更多信息请参考 `节点配置 <../network/test-networks.html#custom-networks-eth>`_ 。

基础层服务
=================================================

Whisper
--------------------------

.. * TODO - Add Whisper documentation here!
.. `Whisper: the Multi DHT Messaging System with Routing Privacy. Vision & Roadmap.` - DEVCON-0 talk youtube video

* `What is Whisper and what is it used for <http://ethereum.stackexchange.com/questions/127/what-is-whisper-and-what-is-it-used-for>`_ - stackexchange Q&A
* `Gavin Wood: Shh! Whisper <https://www.youtube.com/watch?v=U_nPoBVLPiw>`_ - DEVCON-1 talk youtube video
* `Whisper overview and dream API usage <https://github.com/ethereum/wiki/wiki/Whisper-Overview>`_ -
* `ELI5 <https://www.reddit.com/r/ethereum/comments/2xzm5w/whisper_explain_to_me_like_im_5/>`_

Swarm
---------------------------

Swarm是一个分布式存储平台和内容分发服务，是以太坊Web3技术栈的原生基础层服务。Swarm的主要目标是为以太坊的公共履历提供一个充分的去中心化的冗余存储，特别是可以像处理区块链数据那样保存和分发Dapp代码和数据。从经济学角度来看，它允许参与者把他们的存储和带宽资源充分的池化，来给所有参与者提供上述服务。

从最终用户的角度，Swarm和WWW没有多大不同，除了数据并不是上传到一个特定的服务器以外。其目标就是达成一个点到点（peer-to-peer）存储来提供DDOS抗性、零宕机时间、容错和抗审查的特性，就像因为内置的使用点到点账户并允许由支付来交易资源的激励机制所产生了自我维持特性那样。Swarm被设计为与以太坊的devp2p多重网络协议和以太坊区块链进行深度集成，为域名解析、服务支付和内容有效性保障所服务。

ÐΞVcon上关于Swarm的谈话
^^^^^^^^^^^^^^^^^^^^^^^^^^

* `Viktor Trón, Daniel A. Nagy: Swarm <https://www.youtube.com/watch?v=VOC45AgZG5Q>`_ - Ethereum ÐΞVcon-1 talk on youtube
* `Daniel A. Nagy: Keeping the Public Record Safe and Accessible <https://www.youtube.com/watch?v=QzYZQ03ON2o&list=PLJqWcTqh_zKEjpSej3ddtDOKPRGl_7MhS>`_ - Ethereum ÐΞVcon-0 talk on youtube

代码和状态
^^^^^^^^^^^^^^^^^^^^^^^^^^

* [source](https://github.com/ethereum/go-ethereum/tree/swarm)
* [issues on github](https://github.com/ethereum/go-ethereum/labels/swarm)
* [development roadmap]()

* `ethersphere on twitter <https://twitter.com/ethersphere>`_
* `swarm gitter room <https://gitter.im/ethereum/swarm>`_
* `swarm subreddit <https://reddit.com/r/bzz>`_

线上、线下的存储

* https://www.reddit.com/r/ethereum/comments/3hkv2f/eli5_storage_in_the_ethereum_blockchain/
* https://www.reddit.com/r/ethereum/comments/3npsoz/ethereum_ipfs_and_filecoin/
* `What is swarm and what is it used for? <https://ethereum.stackexchange.com/questions/375/what-is-swarm-and-what-is-it-used-for>`_  - stackexchange Q&A

以太坊闹钟
--------------------------------------------------------------------------------

* **Author:** Piper Merriam
* **Website:** `alarm_main_website`_.
* **Documentation:** `alarm_documentation`_.

一个可以调度交易在一段时间之后发生的集市。与unix中的 *crontab* 或javascript中的 *setTimeout* 扮演相似的角色。

* `Decentralized cron service in Ethereum proposal <https://gist.github.com/karalabe/0ab4d715a81b74dd257d>`_ - by Peter Szilagyi

以太坊计算市场
--------------------------------------------------------------------------------

* **Author:** Piper Merriam
* **Website:** `computation_market_main_website`_.
* **Documentation:** `computation_market_documentation`_.

一个可以使链下的可验证计算得以进行的集市。允许在EVM中进行非常昂贵的计算而不用支付在链上运行它们所需要的高额的气。

.. _alarm_main_website: http://www.ethereum-alarm-clock.com/
.. _alarm_documentation: http://docs.ethereum-alarm-clock.com/
.. _computation_market_main_website: http://www.ethereum-computation-market.com/
.. _computation_market_documentation: http://docs.ethereum-computation-market.com/

BTCRelay
-------------------------------------------------

`BTCrelay <http://btcrelay.org/>`_
   * `More information <https://medium.com/@ConsenSys/taking-stock-bitcoin-and-ethereum-4382f0a2f17>`_ (about ETH/BTC 2-way peg without modifying bitcoin code).
   * `BTCrelay audit <http://martin.swende.se/blog/BTCRelay-Auditing.html>`_

RANDAO
-----------------------------------------

随机数

* https://www.reddit.com/r/ethereum/comments/49yld7/eli5_how_does_a_service_like_szabodice_grab_a/

.. _the-EVM:

EVM
================================================================================

以太坊虚拟机（EVM）是以太坊上的智能合约运行环境。它不但是个沙箱，而且是完全独立的，就是说在EVM中运行的代码是不能访问任何网络、文件系统或其他进程的。智能合约甚至对其他智能合约也是有限访问的。

区块链上的合约是以以太坊特定的二进制格式（EMV字节码）保存的。然而，合约一般是由一种以太坊高级语言写成的，由EVM编译器编译为字节码，最终使用以太坊客户端上传到区块链上的。
