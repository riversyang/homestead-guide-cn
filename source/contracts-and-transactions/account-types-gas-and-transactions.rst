.. _account-types-gas-and-transactions:

********************************************************************************
账户类型、气和交易
********************************************************************************

外部账户（EOA）和合约账户
================================================================================

以太坊中有两种类型的账户
  - 外部账户（Externally Owned Accounts）
  - 合约账户（Contracts Accounts）

外部账户（由外部角色拥有的账户）
--------------------------------------------------------------------------------

一个外部账户

- 有一个以太币余额
- 可以发送交易（以太币的转移或触发合约代码）
- 由一个私钥所控制
- 没有关联代码

合约账户
--------------------------------------------------------------------------------

一个合约

- 有一个以太币余额
- 有关联代码
- 由交易或从其他合约收到的消息所触发执行
- 代码执行
  - 可以处理任意复杂度的操作（图灵完备）
  - 可以操作它自己的持久化存储，比如可以有它自己的永久状态
  - 可以调用其他合约

以太坊区块链上的所有动作，都被设定为由外部账户所发出的交易所触发。每当合约账户接收到交易，它的代码会根据作为交易的一部分传入的参数来具体执行。将在网络中每个节点上的以太坊虚拟机中被执行，并被作为它们对新区块的验证结果的一部分。

这种执行需要是完全可预测的，它仅有的上下文就是区块在区块链中的位置及所有可用数据。区块链上的区块相当于时间的单元，区块链自己即以时间维度记录着链上所有区块的状态变动历史。

所有以太币余额都被以wei为单位所记录：1以太币即是1e18wei（10的18次方Wei）。

.. note:: 以太坊里的“合约”不该被认为是应该“实现”或“编译”，他们更像是以太坊运行环境中的“自治化的代理”，当被消息或交易所“插入”时会执行特定的代码，并且由它们自己的以太币余额所控制、由它们自己的键/值存储永久的状态。

什么是交易？
================================================================================

在以太坊中，所谓“交易”，是指存储了消息的签名数据包，在区块链上从一个外部账户发送到另外一个外部账户。

交易包含：
 - 消息的接收方
 - 一个用以标示发送方的签名，来证明他们通过区块链发送消息给接收方的意图
 - ``VALUE`` 字段 - 由发送方向接收方转移的wei的数量
 - 一个可选数据字段，可以包含发送到某个合约的消息
 - ``STARTGAS`` 值，代表交易执行所允许花费的最大可计算步骤（气）的数量
 - ``GASPRICE`` 值，代表发送方愿意为了气（gas）的消耗所支付的费用。一单位的气与执行一个原子操作对等，比如一个可计算步骤。

什么是消息？
================================================================================

合约可以发送“消息”给其他合约。消息是一些虚拟对象，他们不会被序列化，且仅存在于以太坊的执行环境中，他们可以被理解为函数调用。

一个消息包括：
 - 消息的发送方（内置的）
 - 消息的接收方
 - ``VALUE`` 字段 - 伴随消息一起转移到合约地址的wei的数量
 - 一个可选数据字段，这是实际输入给合约的数据
 - ``STARTGAS`` 字段，由消息所触发的代码执行所能引起的气的最大消耗数量

大体上讲，消息就像交易，除了它是由合约产生的，而不是外部用户。当合约代码执行 ``CALL`` 或 ``DELEGATECALL`` 操作码时会产生并执行一个消息。像交易一样，消息会导致接收者账号执行它的代码。这样，合约就可以与其他合约建立联系，就像外部用户之间用交易建立联系那样。

什么是气？
================================================================================

以太坊在区块链上实现了一个被称为以太坊虚拟机（EVM）的执行环境。网络中的每个节点都会将EVM作为区块校验协议的一部分来运行。它们会逐个检查正在验证的区块中的所有交易，并在EVM中执行这些交易所触发的代码。网络中的每个全节点都会进行相同的计算并保存相同的结果。显然，以太坊并不是在做计算效率的优化，它这种并行计算是无必要的；这是为了提供一种无需第三方、权威机构或垄断组织的方式来达到系统状态的共识。这当然不是为了优化计算，事实上，合约是在各个节点之上无必要的重复执行的，这使合约变得很昂贵。所以总体上说，并不鼓励在链上运行那些可以脱离区块链完成的计算。

当你在运行一个去中心化应用（dapp）的时候，它会使用区块链来读取和修改它的状态。但这些应用仅在区块链上存放那些对达成共识最为重要的业务逻辑和状态。

当一个合约被一个消息或交易触发而执行的时候，每个预设指令都会被在网络中的所有节点上执行。这会导致一个结果：每个被执行的操作都会有一个用气的数量来衡量的特定花销。

气是交易的发送方需要为在以太坊区块链上执行每个操作而支付的执行费用的名称。这个费用可以想象为一种驱动智能合约执行的加密燃油，气这个名称的灵感就来源于此。气是从那些执行代码的矿工那里用以太币的形式购置的。气和以太币被故意作为不同的概念，是因为气相当于计算单位的自然消耗，而以太币的价格一般会因市场原因而波动。一个自由市场会调和两者的关系：气的价格实际上是由矿工们决定的，它们可以拒绝那些气的价格低于它们的最低限的交易。要获得气，你只需要为你的账户添加以太币即可。以太坊客户端会根据你为交易所指定的最大开支自动用你的以太币购置气。

为了阻止故意的攻击或对以太坊网络的滥用，以太坊协议规定执行合约或交易中的每个计算步骤都需要支付费用。每个交易都需要包含气的上限和希望为每个气所支付的费用。矿工们可以决定是否包含某个交易并获得相应的费用。如果交易所产生的所有计算步骤（包含原始消息和可能被触发的所有其他消息）所需要的气的总量小于等于交易中指定的气的上限，交易会被处理。如果实际消耗的气的总量超过交易中气的上限，所有的变动都会被回复原样，除了交易仍然有效，且费用仍可以被矿工收取。所有在交易执行过程中没有被消耗的多余的气，会被作为以太币返还给发送方。你不需要担心超支，因为你最多只会被收取你在交易中所充入的所有气（即你为交易指定的气的上限，译者注）。这意味着为你的交易指定一个超出预估的气的上限是有用并且安全的。

估算交易的费用
================================================================================

一个交易的总费用取决于两个因素：

``gasUsed`` 交易中所消耗的气的总量

``gasPrice`` 交易中所指定的气的价格（用以太币为单位）

**总费用 = gasUsed * gasPrice**

gasUsed
--------------------------------------------------------------------------------

EVM中的每个操作都会对应一个其消耗的气的数值。 ``gasUsed`` 即是所有操作所消耗的气的总和。 `这份表格 <http://ethereum.stackexchange.com/q/52/42>`_ 提供了相关的一些分析。

这里有份 `estimateGas API <http://ethereum.stackexchange.com/q/266/42>`_ 可以帮助你预估 ``gasUsed`` ，但其中也有些需要小心的地方。

gasPrice
--------------------------------------------------------------------------------

一个用户构造并签名了一个交易之后，每个用户都可以指定一个他们希望的 ``gasPrice`` ，这甚至可以设为0。然而，在Frontier版本的以太坊客户端中gasPrise会有一个默认值0.05e12 wei。由于矿工们会优化他们的收入，所以如果大多数交易的gasPrise都是0.05e12 wei的话，你就很难让矿工去接受一个低于这个数值甚至为0的gasPrise了。

交易费用示例
--------------------------------------------------------------------------------

让我们使用一个仅仅对两个数字做加法的合约。EVM操作码 ``ADD`` 会消耗3个气。

使用默认气价（2016年1月时）的大概的费用为：

3 \* 0.05e12 = 1.5e11 wei

由于1以太币等于1e18 wei，所以总费用等于0.00000015以太币。

这是一个简化，因为它忽略了一些费用，比如在两个数字被相加之前，它们需要先被发送给合约。

* `question <http://ethereum.stackexchange.com/q/324/42>`_
* `gas fees <http://ether.fund/tool/gas-fees>`_
* `gas cost calculator <http://ether.fund/tool/calculator>`_
* `Ethereum Gas Prices <https://docs.google.com/spreadsheets/d/1m89CVujrQe5LAFJ8-YAUCcNK950dUzMQPMJBxRtGCqs>`_

=================  =========    =============================
Operation Name     Gas Cost     Remark
=================  =========    =============================
step               1            每个执行循环的默认数额 
stop               0            免费
suicide            0            免费
sha3               20           哈希运算，译者注
sload              20           从永久存储获取数据
sstore             100          向永久存储保存数据
balance            20           获取余额，译者注
create             100          创建合约
call               20           开始只读调用
memory             1            扩大内存时每个额外的字
txdata             5            交易中的每字节数据或代码
transaction        500          基础交易费
contract creation  53000        在homestead版本中变更，从21000区块开始的创建合约费用
=================  =========    =============================

账户交互示例 - 对赌合约
================================================================================

如前文所述，有两种类型的合约：

* **外部账户（EOAs）** ：由私钥控制的账户，如果你拥有EOA的私钥，你就可以用它来发送以太币或者消息。
* **合约账户** ：拥有自己的代码，并由代码控制的账户。

默认情况下，以太坊的执行环境是没有任何活动的，所有账户的状态都是一样的。然而，任何用户都可以从一个外部账户发送一个交易从而使以太坊开始运转。如果交易的发送目标是另一个外部账户，那么交易会转移一些以太币但没有任何其他事发生。而如果交易的发送目标是一个合约账户，那么合约就会被激活，其中的代码就会被运行。

这些代码可以从它所控制的内部存储（一个由32字节的键和32字节的值所构成的数据库）读写数据，可以读取接收到的消息，可以将消息发送给其他合约而触发它们的顺序执行。一旦合约执行结束，即所有由合约发送的消息所触发的执行（这是一个可预计的、同步的顺序，就是说父调用会等待子调用完全结束才会继续执行）都停止之时，执行环境会被再次挂起，直到下一个交易发生。

合约账户总体上说是为了4个目的而服务的：

* Maintain a data store representing something which is useful to either 
other contracts or to the outside world; one example of this is a contract 
that simulates a currency, and another is a contract that records 
membership in a particular organization.
* Serve as a sort of externally-owned account with a more complicated 
access policy; this is called a "forwarding contract" and typically 
involves simply resending incoming messages to some desired destination 
only if certain conditions are met; for example, one can have a forwarding 
contract that waits until two out of a given three private keys have 
confirmed a particular message before resending it (ie. multisig). More 
complex forwarding contracts have different conditions based on the 
nature of the message sent. The simplest use case for this functionality 
is a withdrawal limit that is overrideable via some more complicated 
access procedure. A wallet contract is a good example of this.
* Manage an ongoing contract or relationship between multiple users. 
Examples of this include a financial contract, an escrow with some 
particular set of mediators, or some kind of insurance. One can also 
have an open contract that one party leaves open for any other party to 
engage with at any time; one example of this is a contract that 
automatically pays a bounty to whoever submits a valid solution to some 
mathematical problem, or proves that it is providing some computational 
resource.
* Provide functions to other contracts, essentially serving as a software 
library.

Contracts interact with each other through an activity that is alternately 
called either "calling" or "sending messages". A "message" is an object 
containing some quantity of ether, a byte-array of data of any size, the 
addresses of a sender and a recipient. When a contract receives a message, 
it has the option of returning some data, which the original sender of 
the message can then immediately use. In this way, sending a message is 
exactly like calling a function.

Because contracts can play such different roles, we expect that contracts 
will be interacting with each other. As an example, consider a situation 
where Alice and Bob are betting 100 GavCoin that the temperature in San 
Francisco will not exceed 35ºC at any point in the next year. However, 
Alice is very security-conscious, and as her primary account uses a 
forwarding contract which only sends messages with the approval of two 
out of three private keys. Bob is paranoid about quantum cryptography, 
so he uses a forwarding contract which passes along only messages that 
have been signed with Lamport signatures alongside traditional ECDSA 
(but because he's old fashioned, he prefers to use a version of Lamport 
sigs based on SHA256, which is not supported in Ethereum directly).

The betting contract itself needs to fetch data about the San Francisco 
weather from some contract, and it also needs to talk to the GavCoin 
contract when it wants to actually send the GavCoin to either Alice or 
Bob (or, more precisely, Alice or Bob's forwarding contract). We can show 
the relationships between the accounts thus:

..  image:: ../img/contract_relationship.png
..
   :align: center

When Bob wants to finalize the bet, the following steps happen:

1. A transaction is sent, triggering a message from Bob's EOA to his 
forwarding contract.
2. Bob's forwarding contract sends the hash of the message and the 
Lamport signature to a contract which functions as a Lamport signature 
verification library.
3. The Lamport signature verification library sees that Bob wants a 
SHA256-based Lamport sig, so it calls the SHA256 library many times as 
needed to verify the signature.
4. Once the Lamport signature verification library returns 1, signifying 
that the signature has been verified, it sends a message to the contract 
representing the bet.
5. The bet contract checks the contract providing the San Francisco 
temperature to see what the temperature is.
6. The bet contract sees that the response to the messages shows that 
the temperature is above 35ºC, so it sends a message to the GavCoin 
contract to move the GavCoin from its account to Bob's forwarding contract.

Note that the GavCoin is all "stored" as entries in the GavCoin contract's 
database; the word "account" in the context of step 6 simply means that 
there is a data entry in the GavCoin contract storage with a key for the 
bet contract's address and a value for its balance. After receiving this 
message, the GavCoin contract decreases this value by some amount and 
increases the value in the entry corresponding to Bob's forwarding 
contract's address. We can see these steps in the following diagram:

..  image:: ../img/contract_relationship2.png
..
   :align: center

Signing transactions offline
================================================================================

[ Maybe add this to the FAQ and point to the ethkey section of 
turboethereum guide? ]

* `Resilience Raw Transaction Broadcaster <https://github.com/resilience-me/broadcaster/>`_
