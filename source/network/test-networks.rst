.. _test-networks:

********************************************************************************
测试网络
********************************************************************************

Morden测试网络
================================================================================
Morden是一个公开的以太坊备选测试网络。它将在以太坊的Frontier到Homestead里程碑期间一直存在。

使用方法
--------------------------------------------------------------------------------

eth（C++客户端）
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

从0.9.93及以上版本支持，可以在启动客户端时使用 ``--morden`` 以选择测试网络。例如：

.. code:: Console

   > eth --morden

PyEthApp（Python客户端）
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

PyEthApp从1.0.5版本开始支持Morden网络：

.. code:: Console

   > pyethapp --profile morden run

geth（Go客户端）
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code:: Console

   > geth --testnet

详情
--------------------------------------------------------------------------------
除了以下参数外，所有参数都与以太坊主网络相同：
All parameters are the same as the main Ethereum network except:

-  网络名称： **Morden**
-  网络标识： 2
-  genesis.json （下边会给出）
-  初始账户Nonce（ ``IAN`` ）为2^20（而不是像之前的网络那样为0）

   -  在状态前缀树中的所有账户Nonce均 >= ``IAN`` 。
   -  每当一个账户被加入状态前缀树时，Nonce都会被初始化为 = ``IAN`` 。

-  初始区块哈希：
   ``0cd786a2425d16f152c658316c423e6ce1181e15c3295826d7c9904cba9ce303``
-  初始状态前缀树根：
   ``f3f4696bbf3b3b07775128eb7a3763279a394e382130f27c21e70233e04946a9``

Morden的genesis.json
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code:: JSON

	{
			"nonce": "0x00006d6f7264656e",
			"difficulty": "0x20000",
			"mixhash": "0x00000000000000000000000000000000000000647572616c65787365646c6578",
			"coinbase": "0x0000000000000000000000000000000000000000",
			"timestamp": "0x00",
			"parentHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
			"extraData": "0x",
			"gasLimit": "0x2FEFD8",
			"alloc": {
					"0000000000000000000000000000000000000001": { "balance": "1" },
					"0000000000000000000000000000000000000002": { "balance": "1" },
					"0000000000000000000000000000000000000003": { "balance": "1" },
					"0000000000000000000000000000000000000004": { "balance": "1" },
					"102e61f5d8f9bc71d0ad4a084df4e65e05ce0e1c": { "balance": "1606938044258990275541962092341162602522202993782792835301376" }
			}
	}

获得Morden测试网络的以太币
--------------------------------------------------------------------------------

有两种途径可以获得Morden测试网络的以太币：

- 用你的CPU/GPU来挖矿。（参考 :ref:`mining` ）
- 使用 `Ethereum wei faucet <https://zerogox.com/ethereum/wei_faucet>`__ 。


********************************************************************************
配置一个本地的测试网络
********************************************************************************

.. _custom-networks-eth:

eth（C++客户端）
================================================================================

可以使用 --genesis 和 --config 参数来连接或创建一个新的网络。

.. code:: Console

  > eth --private "customChain" --config config.json --genesis genesis.json

也可以同时使用 --config 和 --genesis 。在这种情况下，由 --config 提供的初始区块描述会被 --genesis 选项的设定所覆盖。

.. code:: Console

  --private //defines the name of the custom chain (optional).

.. code:: Console

  --config <filename>

.. note:: <filename> 包含了一个网络信息的JSON描述：

	- sealEngine （挖矿引擎）

		"Ethash" 是以太坊工作量证明引擎（被当前网络使用）。

		"NoProof" 挖矿时不需要工作量证明。

	- params （网络的一般信息，比如minGasLimit、minimumDifficulty、blockReward、networkID）

	- genesis （初始区块描述）

	- accounts （设置账户/合约的初始状态）

这里是个Config样例（使用Olympic网络）：

.. code:: JSON

    {
    	"sealEngine": "Ethash",
    	"params": {
    		"accountStartNonce": "0x00",
    		"frontierCompatibilityModeLimit": "0xffffffff",
    		"maximumExtraDataSize": "0x0400",
    		"tieBreakingGas": false,
    		"minGasLimit": "125000",
    		"gasLimitBoundDivisor": "0x0400",
    		"minimumDifficulty": "0x020000",
    		"difficultyBoundDivisor": "0x0800",
    		"durationLimit": "0x08",
    		"blockReward": "0x14D1120D7B160000",
    		"registrar": "5e70c0bbcd5636e0f9f9316e9f8633feb64d4050",
    		"networkID" : "0x0"
    	},
    	"genesis": {
    		"nonce": "0x000000000000002a",
    		"difficulty": "0x20000",
    		"mixHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
    		"author": "0x0000000000000000000000000000000000000000",
    		"timestamp": "0x00",
    		"parentHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
    		"extraData": "0x",
    		"gasLimit": "0x2fefd8"
    	},
    	"accounts": {
    		"0000000000000000000000000000000000000001": { "wei": "1", "precompiled": { "name": "ecrecover", "linear": { "base": 3000, "word": 0 } } },
    		"0000000000000000000000000000000000000002": { "wei": "1", "precompiled": { "name": "sha256", "linear": { "base": 60, "word": 12 } } },
    		"0000000000000000000000000000000000000003": { "wei": "1", "precompiled": { "name": "ripemd160", "linear": { "base": 600, "word": 120 } } },
    		"0000000000000000000000000000000000000004": { "wei": "1", "precompiled": { "name": "identity", "linear": { "base": 15, "word": 3 } } },
    		"dbdbdb2cbd23b783741e8d7fcf51e459b497e4a6": { "wei": "1606938044258990275541962092341162602522202993782792835301376" },
    		"e6716f9544a56c530d868e4bfbacb172315bdead": { "wei": "1606938044258990275541962092341162602522202993782792835301376" },
    		"b9c015918bdaba24b4ff057a92a3873d6eb201be": { "wei": "1606938044258990275541962092341162602522202993782792835301376" },
    		"1a26338f0d905e295fccb71fa9ea849ffa12aaf4": { "wei": "1606938044258990275541962092341162602522202993782792835301376" },
    		"2ef47100e0787b915105fd5e3f4ff6752079d5cb": { "wei": "1606938044258990275541962092341162602522202993782792835301376" },
    		"cd2a3d9f938e13cd947ec05abc7fe734df8dd826": { "wei": "1606938044258990275541962092341162602522202993782792835301376" },
    		"6c386a4b26f73c802f34673f7248bb118f97424a": { "wei": "1606938044258990275541962092341162602522202993782792835301376" },
    		"e4157b34ea9615cfbde6b4fda419828124b70c78": { "wei": "1606938044258990275541962092341162602522202993782792835301376" }
    	}
    }


.. code:: Console

  --genesis <filename> (optional if the config option is provided and contains the genesis description).

.. note:: <filename> 包含了一个初始区块的JSON描述，内容与‘config’参数提供的genesis字段相同：

.. code:: JavaScript

  {
		"nonce": "0x000000000000002a",
		"difficulty": "0x20000",
		"mixHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
		"author": "0x0000000000000000000000000000000000000000",
		"timestamp": "0x00",
		"parentHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
		"extraData": "0x",
		"gasLimit": "0x2fefd8"
  }


geth（Go客户端）
================================================================================

在一个私有测试网络中，你可以通过预生成或者自己挖矿的方式获得以太币。这是个尝试以太坊的性价比最高的方式，因为你不必自己在最新的测试网络中挖矿或者去寻找以太币来源。

需要在私有链中指定的主要配置是：
 - 自定义Genesis文件（即初始区块信息，译者注）
 - 自定义数据目录
 - 自定义网络ID
 - （推荐）禁止节点发现

Genesis文件
--------------------------------------------------------------------------------

初始区块（创世区块）是区块链的开始 - 即第一个区块，区块0，并且是唯一一个没有前导区块的区块。基于协议，不会有其他节点批准你的区块链版本，除非它们也拥有同样的初始区块。所以你想创建多少私有测试网络就可以创建多少。

:file:`CustomGenesis.json`

.. code-block:: JSON

  {
      "nonce": "0x0000000000000042",     "timestamp": "0x0",
      "parentHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
      "extraData": "0x0",     "gasLimit": "0x8000000",     "difficulty": "0x400",
      "mixhash": "0x0000000000000000000000000000000000000000000000000000000000000000",
      "coinbase": "0x3333333333333333333333333333333333333333",     "alloc": {     }
  }

保存一个文件叫做 :file:`CustomGenesis.json` ，它将用来初始化你的geth节点，通过以下命令：

``geth init /path/to/CustomGenesis.json``

.. note:: geth默认会使用与公链主网络相同的目录。所以你需要使用 ``--datadir`` 来给测试网络指定一个单独的目录以避免公链数据被重置。

针对私有网络的命令行参数
--------------------------------------------------------------------------------

有一些命令行选项（也可以叫做“标志”）是用来确保你的网络保持私有状态的。我们已经看过了genesis标志，但我们还需要一些。请注意，以下命令适用于geth以太坊客户端。

``--nodiscover``

使用这个选项以确保除非其他人手工添加你的节点，否则你的节点不会被自动发现。如果其它某个陌生人恰好使用了跟你同样的genesis文件和网络id，不使用这个选项，你的节点可能会被无端加入他们创建的区块链网络中。

``--maxpeers 0``

如果你不希望其他人连接到你的区块链，请使用这个选项。当然，如果你知道有多少节点会连接到你的网络，你也可以调整这个数字。

``--rpc``

这个选项会在你的节点上打开RPC接口。在Geth中这个选项是缺省打开的。

``--rpcapi "db,eth,net,web3"``

这个选项指定了哪些API可以通过RPC方式使用。缺省情况下，Geth允许web3接口。

**重要：请注意，通过RPC/IPC方式提供API接口，将允许能访问到接口的所有人使用相应API（比如dapp's，即去中心化应用）。请慎重地打开API。缺省地，Geth客户端允许通过IPC使用所有API，而通过RPC则只能使用db、eth、net和web3的API。**

``--rpcport "8080"``

8080可以改为任何你网络中允许的端口。Geth的缺省端口是8080。

``--rpccorsdomain "http://chriseth.github.io/browser-solidity/"``

这个选项指定了哪些URL可以连接到你的节点来执行RPC客户端任务。请谨慎使用这个选项，指定一个特定的URL，而不是使用通配符（*）来允许所有URL连接到你的RPC实例。

``--datadir "/home/TestChain1"``

这个选项是指定你的私有链数据的存储目录。请选择你的以太坊客户端主目录以外的目录。

``--port "30303"``

这是“网络监听端口”，你可以用它来手工连接其他节点。

``--identity "TestnetMainNode"``

这将会给你节点加一个标识，以使它更容易的被标识在节点列表中。

以下是一个这些标识如何在网络中显示的例子。

启动 ``geth``
--------------------------------------------------------------------------------

当你创建了自定义初始区块的JSON文件，并为你的区块链创建了数据目录之后，就可以使用以下命令访问geth：

.. code-block:: Console

  geth --identity "MyNodeName" --rpc --rpcport "8080" --rpccorsdomain "*" --datadir "C:\chains\TestChain1" --port "30303" --nodiscover --rpcapi "db,eth,net,web3" --networkid 1999 init /path/to/CustomGenesis.json

.. note:: 请把相关参数修改为适合你自己的配置。

它将会初始化你的初始区块。键入以下命令，就可以与geth进行交互了：

.. code-block:: Console

  geth --identity "MyNodeName" --rpc --rpcport "8080" --rpccorsdomain "*" --datadir "C:\chains\TestChain1" --port "30303" --nodiscover --rpcapi "db,eth,net,web3" --networkid 1999 console

你每次要访问你的自定义链之前，你都需要使用自定义命令启动geth实例。如果你只用“geth”命令启动，它不会记住你的所有自定义选项。

javascript命令行中可使用的完整方法一览，请参考 `the geth wiki on github <https://github.com/ethereum/go-ethereum/wiki/JavaScript-Console>`_ 。

如果你已经运行了一个geth节点，你可以将其他geth实例与它联结在一起：

.. code-block:: Console

  geth attach

现在你需要在测试网路中初始化一个新账户，并把它作为你的etherbase（接收挖矿奖励的地址）。

在javascript控制台输入：

.. code-block:: Console

  personal.newAccount("password")

.. note:: 把password替换为你的密码。

现在将它设定为etherbase：

.. code-block:: Console

  miner.setEtherbase(personal.listAccounts[0])

如果成功，命令行会打印“true”。

最终你就可以开始挖矿了：

.. code-block:: Console

  miner.start()

给你的账户预分配以太币
--------------------------------------------------------------------------------

一个“0x400”的难度将允许你在你的私有测试链上快速挖出以太币。在你创建了你的链并开始挖矿之后，你会在数分钟内就拥有几百以太币，这将足够你在测试网络中执行交易了。如果你仍想给你的账户预分配以太币，你可以这样做：

1、在创建私有链之后创建一个新的账户
2、拷贝新账户的地址
3、将以下命令加到你的自定义初始区块文件中

.. code-block:: Javascript

  "alloc":
  {
	  "<your account address e.g. 0x1fb891f92eb557f4d688463d0d7c560552263b5a>":
	  { "balance": "20000000000000000000" }
  }

.. note:: 将 ``0x1fb891f92eb557f4d688463d0d7c560552263b5a`` 替换为你的账户地址。

保存新的初始区块文件，重新运行你的私有链。一旦geth加载完毕，使用 . 关闭它。

我们要把一个地址分配到变量 ``primary`` 中，并检查它余额。

在你的终端上执行 ``geth account list`` 以确认你的新地址被分配到哪个账户上。

.. code-block:: Console

   > geth account list
   Account #0: {d1ade25ccd3d550a7eb532ac759cac7be09c2719}
   Account #1: {da65665fc30803cb1fb7e6d86691e20b1826dee0}
   Account #2: {e470b1a7d2c9c5c6f03bbaa8fa20db6d404a0c32}
   Account #3: {f4dd5c3794f1fd0cdc0327a83aa472609c806e99}

确认哪个账户是你预分配了以太币的。
Take note of which account # is the one that you pre-allocated ether to.
或者你可以用 ``geth console`` 启动控制台（使用与开始启动 ``geth`` 时相同的参数）。提示符出现之后，输入：

.. code-block:: Console

  > eth.accounts

它将返回你现在掌握的账户地址。

.. code-block:: Console

  > primary = eth.accounts[0]

.. note:: 把 ``0`` 替换为你的账户索引。这个命令将返回你的主以太坊地址。

输入以下命令：

.. code-block:: Console

  > balance = web3.fromWei(eth.getBalance(primary), "ether");

这将会返回 ``7.5`` ，表明你的账户有很多以太币。我们在初始区块文件中指定了那么大数字的原因是余额字段使用的单位是wei，是以太坊货币维度中最小的单位（参见 :ref:`ether` ）。

* https://www.reddit.com/r/ethereum/comments/3kdnus/question_about_private_chain_mining_dont_upvote/

