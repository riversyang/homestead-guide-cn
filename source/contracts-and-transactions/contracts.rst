.. _Contracts:

********************************************************************************
合约
********************************************************************************

什么是合约？
================================================================================

一个合约是一个在以太坊区块链上的某个特定地址存在的代码（它的功能）和数据（它的状态）的集合。合约账户可以进行图灵完备的运算，并且可以在账户间发送消息。合约以一个叫做以太坊虚拟机字节码的以太坊所特定的二进制格式保存在区块链上。

合约一般是由某种高级语言，比如 `Solidity <https://solidity.readthedocs.org/en/latest/>`_ 写成，然后被编译为字节码上传到区块链上的。

.. seealso:: 其他语言也是存在的，尤其是Serpent和LLL，关于它们的介绍可以在 :ref:`ethereum-high-level-languages` 找到。

:ref:`IDE-or-development-framework` 列出了集成开发环境和开发工具可以帮助你使用这些语言进行开发和测试的支持，并提供了一些其他特性。

.. _ethereum-high-level-languages:

以太坊高级语言
===========================================================================

以以太坊特定的二进制格式（EVM字节码）在区块链上存在的合约是由以太坊虚拟机（EVM）执行的。然而合约一般是由高级语言写成，再编译成为字节码发布到区块链上的。

下边是一些开发者可以用来书写以太坊智能合约的几种高级语言。

Solidity
--------------------------------------------------------------------------------

Solidity是一种类似于Javascript的语言，可以用来开发合约并编译为EVM字节码。它也是以太坊开发中最受欢迎的标志性语言。

* `Solidity Documentation <http://solidity.readthedocs.org/en/latest/>`_ - Solidity is the flagship Ethereum high level language that is used to write contracts.
* `Solidity online realtime compiler <http://ethereum.github.io/browser-solidity/>`_
* `Standardized Contract APIs <https://github.com/ethereum/wiki/wiki/Standardized_Contract_APIs>`__
* `Useful Ðapp Patterns <https://github.com/ethereum/wiki/wiki/Useful-Ðapp-Patterns>`__ - Code snippets which are useful for Ðapp development.

Serpent
--------------------------------------------------------------------------------

Serpent是一个类似于Python的语言，可以用来开发合约并编译为EVM字节码。它最求最大化的简洁，融合了很多低级语言的优点，采用简单易用的编程风格。同时添加了为合约编程定制的一些特性。Serpent是用 _`LLL` 编译的。

* `Serpent on the ethereum wiki <https://github.com/ethereum/wiki/wiki/Serpent>`_
* `Serpent EVM compiler <https://github.com/ethereum/serpent>`_

LLL
--------------------------------------------------------------------------------

`Lisp Like Language (LLL) <https://github.com/ethereum/libethereum/tree/develop/liblll>`_ 是一种类似于汇编语言的低级语言，极其简单和抽象化，本质上就是直接在EVM上书写代码的极小包装。

* `LIBLLL in GitHub <https://github.com/ethereum/libethereum/tree/develop/liblll>`_
* `Examples of LLL <https://www.reddit.com/r/ethereum/comments/3secu1/anyone_have_a_copy_of_the_old_lll_tutorials/>`_

Mutan（不推荐）
--------------------------------------------------------------------------------

`Mutan <https://github.com/obscuren/mutan>`_ 是一个由Jeffrey Wilcke设计开发的，静态类型的，类似于C语言的开发语言。现在已经不再维护。

书写一个合约
================================================================================

没有哪个语言能躲开写一个Hello World程序。在以太坊环境中，Solidity没有一个明确的方法可以“输出”字符串。最相近的方式就是使用 *log event* 来将一个字符串放到区块链上：

.. code:: js

	contract HelloWorld {
		event Print(string out);
		function() { Print("Hello, World!"); }
	}

这个合约会在区块链上创建一个日志项，在它每次被执行时在其中打印一个“Hello World!”。

.. seealso:: `Solidity docs <https://solidity.readthedocs.org/en/latest/>`_ 有更多样例和指引来书写Solidity代码。

编译一个合约
================================================================================

编译Solidity合约可以通过以下几种途径完成。

* 在命令行使用 ``solc`` 编译器。
* 在 ``geth`` or ``eth`` 提供的javascript控制台使用 ``web3.eth.compile.solidity`` （这也需要安装 ``solc`` 编译器）。
* 使用 `Solidity的在线实时编译器 <https://ethereum.github.io/browser-solidity/>`_.
* 使用 `Meteor dapp Cosmo来创建Solidity合约 <https://github.com/SilentCicero/meteor-dapp-cosmo>`_.
* 使用 `Mix IDE <https://github.com/ethereum/wiki/wiki/Mix:-The-DApp-IDE>`_.
* 使用 `以太坊钱包 <https://github.com/ethereum/mist/releases>`_.

.. note:: 更多关于使用solc编译Solidity合约的信息可以在 `这里 <https://solidity.readthedocs.org/en/latest/frequently-asked-questions.html#how-do-i-compile-contracts>`_ 找到。

在Geth中设置Solidity编译器
--------------------------------------------------------------------------------

如果你已经启动 ``geth`` 你可以检查哪种编译器是可用的。

.. code:: bash

    > web3.eth.getCompilers();
    ["lll", "solidity", "serpent"]

这个命令会返回一个数组指出当前可用的编译器。

.. note::
     ``solc`` 编译器是随着 ``cpp-ethereum`` 一起安装的，或者你可以 `自己构建它 <https://github.com/ethereum/go-ethereum/wiki/Building-Ethereum>`_ 

如果你的 ``solc`` 程序在一个不标准的位置，你可以使用 ``--solc`` 参数来指定其执行目录。

.. code:: bash

    $ geth --solc /usr/local/bin/solc

或者，你可以在控制台运行时设置这个选项：

.. code:: bash

    > admin.setSolc("/usr/local/bin/solc")
    solc, the solidity compiler commandline interface
    Version: 0.2.2-02bb315d/.-Darwin/appleclang/JIT linked to libethereum-1.2.0-8007cef0/.-Darwin/appleclang/JIT
    path: /usr/local/bin/solc

.. _compile_a_simple_contract:

编译一个简单的合约
--------------------------------------------------------------------------------

让我们编译一个简单的合约代码：

.. code:: bash

    > source = "contract test { function multiply(uint a) returns(uint d) { return a * 7; } }"

这个合约提供了一个方法 **multiply** ，可以用一个正整数 ``a`` 做参数，返回 ``a * 7`` 。

你可以使用 `eth\.compile\.solidity\(\) <https://github.com/ethereum/wiki/wiki/JavaScript-API#web3ethcompilesolidity>`_ 在 ``geth`` 的JS控制台编译Solidity代码：

.. code:: bash

    > contract = eth.compile.solidity(source).test
    {
      code: '605280600c6000396000f3006000357c010000000000000000000000000000000000000000000000000000000090048063c6888fa114602e57005b60376004356041565b8060005260206000f35b6000600782029050604d565b91905056',
      info: {
        language: 'Solidity',
        languageVersion: '0',
        compilerVersion: '0.9.13',
        abiDefinition: [{
          constant: false,
          inputs: [{
            name: 'a',
            type: 'uint256'
          } ],
          name: 'multiply',
          outputs: [{
            name: 'd',
            type: 'uint256'
          } ],
          type: 'function'
        } ],
        userDoc: {
          methods: {
          }
        },
        developerDoc: {
          methods: {
          }
        },
        source: 'contract test { function multiply(uint a) returns(uint d) { return a * 7; } }'
      }
    }

.. note::
    也可以通过 `RPC <https://github.com/ethereum/wiki/wiki/JSON-RPC>`__ 使用编译器，或者通过RPC/IPC的方式，基于 `web3\.js <https://github.com/ethereum/wiki/wiki/JavaScript-API#web3ethcompilesolidity>`__ 来是任意基于浏览器的Ðapp连接到 ``geth`` 来使用编译器。

下面的样例会演示通过JSON-RPC来访问 ``geth`` 以使用编译器。

.. code:: bash

    $ geth --datadir ~/eth/ --loglevel 6 --logtostderr=true --rpc --rpcport 8100 --rpccorsdomain '*' --mine console  2>> ~/eth/eth.log
    $ curl -X POST --data '{"jsonrpc":"2.0","method":"eth_compileSolidity","params":["contract test { function multiply(uint a) returns(uint d) { return a * 7; } }"],"id":1}' http://127.0.0.1:8100

编译器输出的代码中的每个合约对象代表了一个单独的合约。 ``eth.compile.solidity`` 实际的返回值是一个合约名字和合约对象的映射对。由于我们的合约名字是 ``test`` ， ``eth.compile.solidity(source).test`` 会返回给你test合约的合约对象，包含以下字段：

.. glossary::

    ``code``
        编译好的EVM字节码

    ``info``
        编译器输出的额外的元数据

    ``source``
        源代码

    ``language``
        合约的语言（Solidity、Serpent或LLL）

    ``languageVersion``
        合约语言的版本

    ``compilerVersion``
        编译这个合约的编译器的版本

    ``abiDefinition``
         `Application Binary Interface Definition（应用程序二进制接口定义） <https://github.com/ethereum/wiki/wiki/Ethereum-Contract-ABI>`__

    ``userDoc``
        用户的 `NatSpec Doc <https://github.com/ethereum/wiki/wiki/Ethereum-Natural-Specification-Format>`__ 。

    ``developerDoc``
        开发者的 `NatSpec Doc <https://github.com/ethereum/wiki/wiki/Ethereum-Natural-Specification-Format>`__ 。

编译器输出内容的结构化（分为 ``code`` 和 ``info`` ）反映了两种截然不同的 **发布路径** 。一套EVM代码由一个创建合约的交易发送到区块链上，而其余（信息）则会适当的保存在去中心化的云端，作为在区块链上的可校验元数据使代码得以完整。

如果你的源码包含多个合约，输出则会包含每个合约的单独数据项，可以用合约名字作为属性名获得对应的合约信息对象。你可以通过检查当前的GlobalRegistrar代码来尝试。

.. code:: js

    contracts = eth.compile.solidity(globalRegistrarSrc)

创建并发布一个合约
================================================================================

在你开始这节之前，请确保你有一个已解锁的账户并有一些资金。

你可以用前一章节中的EVM代码作为数据，通过 `发送一个交易 <https://github.com/ethereum/wiki/wiki/JavaScript-API#web3ethsendtransaction>`__ 到一个空的地址来在区块链上创建一个合约。

.. note::
    使用 `Solidity的在线实时编译器 <https://ethereum.github.io/browser-solidity/>`_ 或者 `Mix IDE <https://github.com/ethereum/wiki/wiki/Mix:-The-DApp-IDE>`_ 可以很容易地实现。

.. code:: js

    var primaryAddress = eth.accounts[0]
    var abi = [{ constant: false, inputs: { name: 'a', type: 'uint256' } }]
    var MyContract = eth.contract(abi)
    var contract = MyContract.new(arg1, arg2, ..., {from: primaryAddress, data: evmByteCodeFromPreviousSection})

所有二进制数据都会被序列化为十六进制格式。十六进制字符串通常会以固定前缀 ``0x`` 开头。

.. note::
    注意， ``arg1, arg2, ...`` 是合约构造器的参数，可以接受任意数据。如果你的合约不需要构造参数，就可以省略它们。

值得指出的是，这个步骤需要你为执行付费。一旦你的交易进入某个区块，你的账户余额（就是你作为发送方在 ``from`` 指定的账户）会根据EVM中气的用量的规则相应减少。一段时间之后，你的交易可能会出现在某个区块中，即它所带来的状态的共识得到确认。你的合约就在区块链上生效了。

用异步方式做同样的事，应该是像这样：

.. code-block:: js

    MyContract.new([arg1, arg2, ...,]{from: primaryAccount, data: evmCode}, function(err, contract) {
      if (!err && contract.address)
        console.log(contract.address);
    });

.. _interacting_with_a_contract:

与一个合约进行交互
================================================================================

与合约的交互一般可以通过一个类似 `eth.contract\(\) <https://github.com/ethereum/wiki/wiki/JavaScript-API#web3ethcontract>`_ 的抽象层函数来实现，它会返回一个javascript对象，带有目标合约的所有可调用函数。

描述一个合约的有效函数的标准方式是 `ABI definition <https://github.com/ethereum/wiki/wiki/Ethereum-Contract-ABI>`_ 。这个对象是一个数组，描述了每个有效的合约函数的调用方法和返回值。

.. code-block:: js

    var Multiply7 = eth.contract(contract.info.abiDefinition);
    var myMultiply7 = Multiply7.at(address);

现在所有在ABI中说明的函数调用都在合约实例上可用了，你可以选择两种调用方式之一在合约实例上实际调用。

.. code-block:: js

    > myMultiply7.multiply.sendTransaction(3, {from: address})
    "0x12345"
    > myMultiply7.multiply.call(3)
    21

当使用 ``sendTransaction`` 这个函数来通过发送交易来调用合约函数时，它会消耗以太币来执行发送，并被永久的记录到区块链上。这种方式调用的返回值是交易的哈希值。

当使用 ``call`` 这个函数来调用合约函数时，执行实在本地EVM中进行的，返回值将是合约函数的实际返回值。这种方式的调用不会被记录到区块链上，但也不能更改合约的内部状态。这种方式也就是一种 **不变的** 函数调用，当然也不会花费以太币。

你应该在只关心返回值的时候使用 ``call`` ，而在只关心合约状态的 *边界效应（side effects，即副作用、额外的影响，译者注）* 时使用 ``sendTransaction`` 。

在以上的例子中并没有边界效应，所以 ``sendTransaction`` 仅仅消耗了气，增加了宇宙里的总熵。

合约元数据
================================================================================

在上面的章节里我们解释了你如何创建在区块链上创建一个合约。现在我们来看一下编译器余下的输出， **合约元数据** 或者叫合约信息。

当与一个不是你自己创建的合约进行交互的时候，你也许会希望看到它的文档或者源码。合约作者被鼓励来在区块链上注册这样的信息或者通过一个类似于 `EtherChain <https://www.etherchain.org/contracts>`_ 的第三方服务来进行发布。 ``admin`` API提供了方便的方法来获取选择了注册的任何合约的具体信息。

.. code:: js

    // get the contract info for contract address to do manual verification
    var info = admin.getContractInfo(address) // lookup, fetch, decode
    var source = info.source;
    var abiDef = info.abiDefinition

确保这种方法可以运作的底层机制是：

*  合约信息被上传到某处，由一个 *URI* 标示为可以公开访问
*  任何仅知道合约地址的人都可以知道这个 *URI* 

这些需求是通过两步区块链注册实现的。第一步注册是通过一个叫做 ``HashReg`` 的合约对要做注册的合约代码进行内容哈希。第二步则是用第一步中生成的内容哈希，通过 ``UrlHint`` 这个合约来注册一个URL。这种 `合约注册机制 <https://github.com/ethereum/go-ethereum/blob/develop/common/registrar/contracts.go>`__ 是Frontier版本的一部分，被拿到了Homestead版本中。

基于这种方案，我们就可以通过已知的合约地址来查询url，从而获得实际的合约元数据信息包。

至此我们可以小结下合约创建的步骤：

* 1、把合约本身发布到区块链上
* 2、取得合约信息json文件
* 3、把合约信息json文件发布到你选择的url上
* 4、注册 代码哈希 -> 内容哈希 -> url

JS API提供了助手使这个过程非常简单。调用 ``admin.register`` 可以从合约取得其合约信息，把这些json内容写入到一个文件，计算这个文件的内容哈希，最后用合约的代码哈希来注册内容哈希。当你把这个内容文件发布到某个url之后，你可以使用 ``admin.registerUrl`` 来用你的内容哈希把url注册到区块链上。（注意，如果以固定内容地址模式来存储文档，那就不需要再使用url-hint这个合约了。）

.. code-block:: js

    source = "contract test { function multiply(uint a) returns(uint d) { return a * 7; } }"
    // compile with solc
    contract = eth.compile.solidity(source).test
    // create contract object
    var MyContract = eth.contract(contract.info.abiDefinition)
    // extracts info from contract, save the json serialisation in the given file,
    contenthash = admin.saveInfo(contract.info, "~/dapps/shared/contracts/test/info.json")
    // send off the contract to the blockchain
    MyContract.new({from: primaryAccount, data: contract.code}, function(error, contract){
      if(!error && contract.address) {
        // calculates the content hash and registers it with the code hash in `HashReg`
        // it uses address to send the transaction.
        // returns the content hash that we use to register a url
        admin.register(primaryAccount, contract.address, contenthash)
        // here you deploy ~/dapps/shared/contracts/test/info.json to a url
        admin.registerUrl(primaryAccount, hash, url)
      }
    });

测试合约和交易
================================================================================

你一般需要用一些底层的策略来测试、调试合约和交易。这节会介绍一些调试工具。为了不涉及真实共识逻辑来测试合约和交易，最好的方式时使用私有区块链。这可以通过设置一个特殊的网络id（比如选一个特殊的整数）并禁止掉其他节点来做到。推荐的方式是使用独立的数据目录和网络端口，以免因为误操作影响到你正在使用的区块链网络（如果你使用默认设置的话）。推荐你使用带分析的最高日志等级的VM debug模式启动 ``geth`` 。

.. code:: bash

    geth --datadir ~/dapps/testing/00/ --port 30310 --rpcport 8110 --networkid 4567890 --nodiscover --maxpeers 0 --vmdebug --verbosity 6 --pprof --pprofport 6110 console 2>> ~/dapp/testint/00/00.log

在提交交易之前，你需要先设置好你的私有测试链。请参考 :ref:`test-networks` 。

.. code:: js

    // create account. will prompt for password
    personal.newAccount();
    // name your primary account, will often use it
    primary = eth.accounts[0];
    // check your balance (denominated in ether)
    balance = web3.fromWei(eth.getBalance(primary), "ether");

.. code:: js

    // assume an existing unlocked primary account
    primary = eth.accounts[0];

    // mine 10 blocks to generate ether

    // starting miner
    miner.start(4);
    // sleep for 10 blocks (this can take quite some time).
    admin.sleepBlocks(10);
    // then stop mining (just not to burn heat in vain)
    miner.stop();
    balance = web3.fromWei(eth.getBalance(primary), "ether");

创建交易之后，你可以用以下命令强制处理它们：

.. code:: js

    miner.start(1);
    admin.sleepBlocks(1);
    miner.stop();

你可以检查待处理的交易：

.. code:: js

    // shows transaction pool
    txpool.status
    // number of pending txs
    eth.getBlockTransactionCount("pending");
    // print all pending txs
    eth.getBlock("pending", true).transactions

如果你提交了创建合约的交易，你可以检查合约代码是否已经被加入当前的区块链：

.. code:: js

    txhash = eth.sendTansaction({from:primary, data: code})
    //... mining
    contractaddress = eth.getTransactionReceipt(txhash);
    eth.getCode(contractaddress)
