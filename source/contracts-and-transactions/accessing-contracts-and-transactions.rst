.. _Accessing Contracts and Transactions:

********************************************************************************
访问合约和交易
********************************************************************************

RPC
================================================================================

前边几节我们已经看到合约是如何写成、发布和交互的，现在该深入一些关于以太坊网络和智能合约间通信的细节了。

一个以太坊节点提供一个 `RPC <https://wikipedia.org/wiki/Remote_procedure_call>`_ 接口。这个接口允许Ðapp访问以太坊网络和节点提供的功能，比如编译智能合约代码。它使用 `JSON-RPC 2.0 <http://www.jsonrpc.org/specification>`_ 规范的一个子集（不支持通知或命名参数）作为序列化协议，通过HTTP和IPC协议（在Linux/OSX上是unix domain socket，在Windows上是named pipes）实现。

如果你对细节不感兴趣，但在寻找一种简单的使用javascript的库，那你可以跳过下边的内容，直接参考 :ref:`使用Web3 <using_web3.js>` 。

公约
================================================================================

PRC接口使用了一些不在JSON-RPC 2.0规范中的公约：

* 数字需要使用16进制。做这个决定是因为一些语言没有、或者缺乏操作非常大的数字的支持。为了避免这种类型的错误，开发者需要对数字做出正确的处理。请以wiki上的 `16进制编码 <https://github.com/ethereum/wiki/wiki/JSON-RPC#output-hex-values>`_ 为参考。
* 默认的区块号。很多RPC方法可以接受区块号。但某些情况下，区块号无法被确定或者不容易被确定。在这些情况下，默认的区块号可以是以下几个字符串之一【“earliest”、“latest”、“pending”】。请参考 `wiki页 <https://github.com/ethereum/wiki/wiki/JSON-RPC#the-default-block-parameter>`_ 获知使用了默认区块号参数的RPC方法。

发布合约
================================================================================

我们来看一下仅使用RPC接口来发布下述合约的步骤。

.. code:: js

   contract Multiply7 {
      event Print(uint);
      function multiply(uint input) returns (uint) {
         Print(input * 7);
         return input * 7;
      }
   }

首先需要确认HTTP RPC接口是有效的。就是说我们用 ``--rpc`` 参数启动geth，或者用 ``-j`` 参数启动eth。在这个例子里，我们在一个私有开发链上使用geth节点，用这种方式，我们不需要真实的以太币。

.. code:: bash

    > geth --rpc --dev --mine --minerthreads 1 --unlock 0 console 2>>geth.log

这会在 ``http://localhost:8545`` 启动一个HTTP RPC接口。

.. note:: geth是支持 `CORS <https://en.wikipedia.org/wiki/Cross-origin_resource_sharing>`_ 的。请参考 ``--rpccorsdomain`` 参数。

我们可以通过使用 `curl <https://curl.haxx.se/download.html>`_ 获取coinbase地址来验证接口是否在运行。请注意这里使用的数据会与你本地节点有所不同，如果你想尝试这些命令，请相应修改请求参数。

.. code:: bash

    > curl --data '{"jsonrpc":"2.0","method":"eth_coinbase", "id":1}' localhost:8545
    {"id":1,"jsonrpc":"2.0","result":["0xeb85a5557e5bdc18ee1934a89d8bb402398ee26a"]}

    > curl --data '{"jsonrpc":"2.0","method":"eth_getBalance", "params": ["0xeb85a5557e5bdc18ee1934a89d8bb402398ee26a"], "id":2}' localhost:8545
    {"id":2,"jsonrpc":"2.0","result":"0x1639e49bba16280000"}

记得我们已经说过数字需要被变换为16进制吧？在这里返回的余额是由16进制表示的wei的数量。如果我们希望获得以太币单位的余额，我们可以在geth控制台使用web3。

.. code:: js

    > web3.fromWei("0x1639e49bba16280000", "ether")
    "410"

现在我们在私有开发链上有了一些以太币，我们可以发布合约了。第一步是验证Solidity编译器可用。我们可以使用 ``eth_getCompilers`` 这个RPC方法查询可用的编译器。

.. code:: bash

   > curl --data '{"jsonrpc":"2.0","method": "eth_getCompilers", "id": 3}' localhost:8545
   {"id":3,"jsonrpc":"2.0","result":["Solidity"]}

我们看到Solidity编译器是可用的。如果它不可用，请参考 `安装Solidity <http://solidity.readthedocs.org/en/latest/installing-solidity.html>`_ 。

下一步就是把Multiply7合约编译为可以发动到EVM的字节码。

.. code:: bash

   > curl --data '{"jsonrpc":"2.0","method": "eth_compileSolidity", "params": ["contract Multiply7 { event Print(uint); function multiply(uint input) returns (uint) { Print(input * 7); return input * 7; } }"], "id": 4}' localhost:8545
   {"id":4,"jsonrpc":"2.0","result":{"Multiply7":{"code":"0x6060604052605f8060106000396000f3606060405260e060020a6000350463c6888fa18114601a575b005b60586004356007810260609081526000907f24abdb5865df5079dcc5ac590ff6f01d5c16edbc5fab4e195d9febd1114503da90602090a15060070290565b5060206060f3","info":{"source":"contract Multiply7 { event Print(uint); function multiply(uint input) returns (uint) { Print(input * 7); return input * 7; } }","language":"Solidity","languageVersion":"0.2.2","compilerVersion":"0.2.2","compilerOptions":"--bin --abi --userdoc --devdoc --add-std --optimize -o /tmp/solc205309041","abiDefinition":[{"constant":false,"inputs":[{"name":"input","type":"uint256"}],"name":"multiply","outputs":[{"name":"","type":"uint256"}],"type":"function"},{"anonymous":false,"inputs":[{"indexed":false,"name":"","type":"uint256"}],"name":"Print","type":"event"}],"userDoc":{"methods":{}},"developerDoc":{"methods":{}}}}}}

现在我们有了编译好的代码，我们需要确定发布它要消耗多少气。RPC接口 ``eth_estimateGas`` 可以给我们一个估算。

.. code:: bash

   > curl --data '{"jsonrpc":"2.0","method": "eth_estimateGas", "params": [{"from": "0xeb85a5557e5bdc18ee1934a89d8bb402398ee26a", "data": "0x6060604052605f8060106000396000f3606060405260e060020a6000350463c6888fa18114601a575b005b60586004356007810260609081526000907f24abdb5865df5079dcc5ac590ff6f01d5c16edbc5fab4e195d9febd1114503da90602090a15060070290565b5060206060f3"}], "id": 5}' localhost:8545
   {"id":5,"jsonrpc":"2.0","result":"0xb8a9"}

最后发布合约。

.. code:: bash

   > curl --data '{"jsonrpc":"2.0","method": "eth_sendTransaction", "params": [{"from": "0xeb85a5557e5bdc18ee1934a89d8bb402398ee26a", "gas": "0xb8a9", "data": "0x6060604052605f8060106000396000f3606060405260e060020a6000350463c6888fa18114601a575b005b60586004356007810260609081526000907f24abdb5865df5079dcc5ac590ff6f01d5c16edbc5fab4e195d9febd1114503da90602090a15060070290565b5060206060f3"}], "id": 6}' localhost:8545
   {"id":6,"jsonrpc":"2.0","result":"0x3a90b5face52c4c5f30d507ccf51b0209ca628c6824d0532bcd6283df7c08a7c"}

交易被节点接受，交易的哈希被返回。我们可以用这个哈希来追踪交易。

接下来是确定我们的合约的发布地址。每个交易被执行后都会有个收据。这个收据包含了一些交易信息，比如交易被包含在哪个区块、EVM消耗了多少气。如果一个交易创建了一个合约，它还会包含合约的地址。我们可以使用 ``eth_getTransactionReceipt`` 这个RPC方法取得收据信息。

.. code:: bash

   > curl --data '{"jsonrpc":"2.0","method": "eth_getTransactionReceipt", "params": ["0x3a90b5face52c4c5f30d507ccf51b0209ca628c6824d0532bcd6283df7c08a7c"], "id": 7}' localhost:8545
   {"id":7,"jsonrpc":"2.0","result":{"transactionHash":"0x3a90b5face52c4c5f30d507ccf51b0209ca628c6824d0532bcd6283df7c08a7c","transactionIndex":"0x0","blockNumber":"0x4c","blockHash":"0xe286656e478a1b99030e318d0f5c3a61a644f25e63deaa8be52e80da1e7b0c47","cumulativeGasUsed":"0xb8a9","gasUsed":"0xb8a9","contractAddress":"0x6ff93b4b46b41c0c3c9baee01c255d3b4675963d","logs":[]}}

我们可以看到合约被创建在 ``0x6ff93b4b46b41c0c3c9baee01c255d3b4675963d`` 上。如果你获得了null，说明交易还没有被包含到区块上。稍等一下，检查你的矿工是否在运行，然后重试这个命令。

与智能合约交互
================================================================================

现在我们的合约已经发布完成，我们可以与它开始交互了。这里有两种方法，发送一个交易，或者 :ref:`像先前提到的那样call <interacting_with_a_contract>` 。在此我们会向合约的multiply方法发送一个交易。

如果我们查看 `eth_sendTransaction <https://github.com/ethereum/wiki/wiki/JSON-RPC#eth_sendtransaction>`_ 这个文档，我们需要提供多个参数。我们需要指定 ``from`` 、 ``to`` 和 ``data`` 参数。``from`` 是我们的账号的公共地址， ``to`` 是合约地址。 ``data`` 参数有点儿麻烦。它包含了哪些方法需要用哪些参数进行调用这样的有效信息。这里就需要ABI（Application Binary Interface）出场了。ABI是如何为EVM编码的定义。请参考 `ABI的所有细节 <https://github.com/ethereum/wiki/wiki/Ethereum-Contract-ABI>`_ 。

这里的有效信息字节就是函数选择器，它将指定哪些方法会被调用。这是通过把对函数名称和他的参数类型的Keccak哈希值的首4字节转换为16进制达成的。 `multiply` 函数接受一个 `等价于 <http://solidity.readthedocs.org/en/latest/types.html#integers>`_ `uint256` 的 `uint` 参数。我们可以获得：

.. code:: js

   > web3.sha3("multiply(uint256)").substring(0, 8)
   "c6888fa1"

更多细节请参考 `函数选择器 <https://github.com/ethereum/wiki/wiki/Ethereum-Contract-ABI#function-selector>`__ 。

下一个步骤就是对参数进行编码，我们只有一个uint256，让我们假定以6作为参数值。这个ABI文档 `章节 <https://github.com/ethereum/wiki/wiki/Ethereum-Contract-ABI#argument-encoding>`_ 具体说明了如何编码成uint256类型。

   `int<M>: enc(X) is the big-endian two's complement encoding of X, padded on the higher-oder (left) side with 0xff for negative X and with zero bytes
   for positive X such that the length is a multiple of 32 bytes.`

这样，6就应该编码为 ``0000000000000000000000000000000000000000000000000000000000000006`` 。

结合函数选择器和参数编码，我们的 ``data`` 应该就是 ``0xc6888fa10000000000000000000000000000000000000000000000000000000000000006`` 。

我们试一下：

.. code:: bash

   > curl --data '{"jsonrpc":"2.0","method": "eth_sendTransaction", "params": [{"from": "0xeb85a5557e5bdc18ee1934a89d8bb402398ee26a", "to": "0x6ff93b4b46b41c0c3c9baee01c255d3b4675963d", "data": "0xc6888fa10000000000000000000000000000000000000000000000000000000000000006"}], "id": 8}' localhost:8545
   {"id":8,"jsonrpc":"2.0","result":"0x759cf065cbc22e9d779748dc53763854e5376eea07409e590c990eafc0869d74"}

由于我们发送了一个交易，我们获得了交易的哈希。如果我们来获取收据，会看到一些新东西：

.. code-block:: js
   :emphasize-lines: 7

   {
      blockHash: "0xbf0a347307b8c63dd8c1d3d7cbdc0b463e6e7c9bf0a35be40393588242f01d55",
      blockNumber: 268,
      contractAddress: null,
      cumulativeGasUsed: 22631,
      gasUsed: 22631,
      logs: [{
         address: "0x6ff93b4b46b41c0c3c9baee01c255d3b4675963d",
         blockHash: "0xbf0a347307b8c63dd8c1d3d7cbdc0b463e6e7c9bf0a35be40393588242f01d55",
         blockNumber: 268,
         data: "0x000000000000000000000000000000000000000000000000000000000000002a",
         logIndex: 0,
         topics: ["0x24abdb5865df5079dcc5ac590ff6f01d5c16edbc5fab4e195d9febd1114503da"],
         transactionHash: "0x759cf065cbc22e9d779748dc53763854e5376eea07409e590c990eafc0869d74",
         transactionIndex: 0
     }],
     transactionHash: "0x759cf065cbc22e9d779748dc53763854e5376eea07409e590c990eafc0869d74",
     transactionIndex: 0
   }

收据包含了日志。这个日志是在交易执行的时候由EVM生成并包含到收据里的。我们可以看到在multiply函数中的Print事件被触发，打印了输入数值的7倍。由于Print事件的参数是uint256类型，我们可以基于ABI规则对其解码得到我们预期的十进制数值42。虽然脱离了data，topics字段就没有意义了，但它可以用来判断是哪个事件创建了这个日志：

.. code:: js

   > web3.sha3("Print(uint256)")
   "24abdb5865df5079dcc5ac590ff6f01d5c16edbc5fab4e195d9febd1114503da"

你可以从 `Solidity tutorial <http://solidity.readthedocs.org/en/latest/contracts.html#events>`_ 中得到更多关于events、topics和indexing相关的信息。

这里仅是个对最普通任务的简短介绍。请参阅 `RPC wiki page <https://github.com/ethereum/wiki/wiki/JSON-RPC#json-rpc-methods>`_ 获知全部的可用RPC方法。

.. _using_web3.js:

Web3.js
================================================================================

就像我们在先前的示例中看到的那样，使用JSON-RPC接口是单调的、容易犯错的，特别是当我们要处理ABI的时候。Web.js则是一个基于以太坊RPC接口之上的javascript库，它的目标是提供一个更友好的接口、减少出错的机会。

用web3发布Multiply7合约大致像这样：

.. code:: js

   var source = 'contract Multiply7 { event Print(uint); function multiply(uint input) returns (uint) { Print(input * 7); return input * 7; } }';
   var compiled = web3.eth.compile.solidity(source);
   var code = compiled.Multiply7.code;
   var abi = compiled.Multiply7.info.abiDefinition;

   web3.eth.contract(abi).new({from: "0xeb85a5557e5bdc18ee1934a89d8bb402398ee26a", data: code}, function (err, contract) {
      if (!err && contract.address)
         console.log("deployed on:", contract.address);
      }
   );

   deployed on: 0x0ab60714033847ad7f0677cc7514db48313976e2

加载发布的合约并发送一个交易：

.. code:: js

   var source = 'contract Multiply7 { event Print(uint); function multiply(uint input) returns (uint) { Print(input * 7); return input * 7; } }';
   var compiled = web3.eth.compile.solidity(source);
   var Multiply7 = web3.eth.contract(compiled.Multiply7.info.abiDefinition);
   var multi = Multiply7.at("0x0ab60714033847ad7f0677cc7514db48313976e2")
   multi.multiply.sendTransaction(6, {from: "0xeb85a5557e5bdc18ee1934a89d8bb402398ee26a"})

注册一个当 ``Print`` 事件创建日志之后会被调用的回调（callback）。

.. code:: js

   multi.Print(function(err, data) { console.log(JSON.stringify(data)) })
   {"address":"0x0ab60714033847ad7f0677cc7514db48313976e2","args": {"":"21"},"blockHash":"0x259c7dc07c99eed9dd884dcaf3e00a81b2a1c83df2d9855ce14c464b59f0c8b3","blockNumber":539,"event":"Print","logIndex":0, "transactionHash":"0x5c115aaa5418118457e96d3c44a3b66fe9f2bead630d79455d0ecd832dc88d48","transactionIndex":0}

更多信息请参考 `web3.js <https://github.com/ethereum/wiki/wiki/JavaScript-API>`_ wiki页。

控制台
================================================================================

geth `控制台 <https://github.com/ethereum/go-ethereum/wiki/JavaScript-Console>`_ 提供了一个javascript环境的命令行接口。它可以连接到一个本地或远程的geth或eth节点。它会加载web3.js库，使用户可以在控制台上使用web3.js与智能合约进行交互。 :ref:`Web3.js <using_web3.js>` 这节中的样例是可以直接在命令行执行的。

查看合约和交易
================================================================================

有很多在线的区块链浏览器可以使你查看以太坊区块链。请参考 :ref:`区块链浏览器 <blockchain_explorers>` 。

.. _blockchain_explorers:

托管的区块链浏览器
--------------------------------------------------------------------------------

-  `EtherChain <https://www.etherchain.org/>`_
-  `EtherCamp <https://live.ether.camp/>`_
-  `EtherScan <http://etherscan.io/>`_ (and for `Testnet <http://testnet.etherscan.io>`_)

其他资源
--------------------------------------------------------------------------------

* `EtherNodes <http://ethernodes.org/>`_ - Geographic distribution of nodes and split by client
* `EtherListen <http://www.etherlisten.com>`_ - Realtime Ethereum transaction visualizer and audializer
