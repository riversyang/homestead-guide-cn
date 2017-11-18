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

What is gas?
================================================================================

Ethereum implements an execution environment on the blockchain called 
the Ethereum Virtual Machine (EVM). Every node participating in the 
network runs the EVM as part of the block verification protocol. They go 
through the transactions listed in the block they are verifying and run 
the code as triggered by the transaction within the EVM. Each and every 
full node in the network does the same calculations and stores the same 
values. Clearly Ethereum is not about optimising efficiency of computation. 
Its parallel processing is redundantly parallel. This is to offer an 
efficient way to reach consensus on the system state without needing 
trusted third parties, oracles or violence monopolies. But importantly 
they are not there for optimal computation. The fact that contract 
executions are redundantly replicated across nodes, naturally makes them 
expensive, which generally creates an incentive not to use the blockchain 
for computation that can be done offchain.

When you are running a decentralized application (dapp), it interacts 
with the blockchain to read and modify its state, but dapps will typically 
only put the business logic and state that are crucial for consensus on 
the blockchain.

When a contract is executed as a result of being triggered by a message 
or transaction, every instruction is executed on every node of the 
network. This has a cost: for every executed operation there is a 
specified cost, expressed in a number of gas units.

Gas is the name for the execution fee that senders of transactions need 
to pay for every operation made on an Ethereum blockchain. The name gas 
is inspired by the view that this fee acts as cryptofuel, driving the 
motion of smart contracts. Gas is purchased for ether from the miners 
that execute the code. Gas and ether are decoupled deliberately since 
units of gas align with computation units having a natural cost, while 
the price of ether generally fluctuates as a result of market forces. 
The two are mediated by a free market: the price of gas is actually 
decided by the miners, who can refuse to process a transaction with a 
lower gas price than their minimum limit. To get gas you simply need to 
add ether to your account. The Ethereum clients automatically purchase 
gas for your ether in the amount you specify as your maximum expenditure 
for the transaction.

The Ethereum protocol charges a fee per computational step that is 
executed in a contract or transaction to prevent deliberate attacks and 
abuse on the Ethereum network. Every transaction is required to include 
a gas limit and a fee that it is willing to pay per gas. Miners have the 
choice of including the transaction and collecting the fee or not. If the 
total amount of gas used by the computational steps spawned by the 
transaction, including the original message and any sub-messages that may 
be triggered, is less than or equal to the gas limit, then the transaction 
is processed. If the total gas exceeds the gas limit, then all changes are 
reverted, except that the transaction is still valid and the fee can still 
be collected by the miner. All excess gas not used by the transaction 
execution is reimbursed to the sender as Ether. You do not need to worry 
about overspending, since you are only charged for the gas you consume. 
This means that it is useful as well as safe to send transactions with a 
gas limit well above the estimates.

Estimating transaction costs
================================================================================

The total ether cost of a transaction is based on 2 factors:

``gasUsed`` is the total gas that is consumed by the transaction

``gasPrice`` price (in ether) of one unit of gas specified in the 
transaction

**Total cost = gasUsed * gasPrice**

gasUsed
--------------------------------------------------------------------------------

Each operation in the EVM was assigned a number of how much gas it 
consumes. ``gasUsed`` is the sum of all the gas for all the operations 
executed. There is a `spreadsheet <http://ethereum.stackexchange.com/q/52/42>`_ 
which offers a glimpse to some of the analysis behind this.

For estimating ``gasUsed``, there is an `estimateGas API <http://ethereum.stackexchange.com/q/266/42>`_ 
that can be used but has some caveats.

gasPrice
--------------------------------------------------------------------------------

A user constructs and signs a transaction, and each user may specify 
whatever ``gasPrice`` they desire, which can be zero. However, the 
Ethereum clients launched at Frontier had a default gasPrice of 0.05e12 
wei. As miners optimize for their revenue, if most transactions are being 
submitted with a gasPrice of 0.05e12 wei, it would be difficult to 
convince a miner to accept a transaction that specified a lower, or zero, 
gasPrice.

Example transaction cost
--------------------------------------------------------------------------------

Let’s take a contract that just adds 2 numbers. The EVM OPCODE ``ADD`` 
consumes 3 gas.

The approximate cost, using the default gas price (as of January 2016), 
would be:

3 \* 0.05e12 = 1.5e11 wei

Since 1 ether is 1e18 wei, the total cost would be 0.00000015 Ether.

This is a simplification since it ignores some costs, such as the cost of 
passing the 2 numbers to contract, before they can even be added.

* `question <http://ethereum.stackexchange.com/q/324/42>`_
* `gas fees <http://ether.fund/tool/gas-fees>`_
* `gas cost calculator <http://ether.fund/tool/calculator>`_
* `Ethereum Gas Prices <https://docs.google.com/spreadsheets/d/1m89CVujrQe5LAFJ8-YAUCcNK950dUzMQPMJBxRtGCqs>`_

=================  =========    =============================
Operation Name     Gas Cost     Remark
=================  =========    =============================
step               1            default amount per execution cycle
stop               0            free
suicide            0            free
sha3               20
sload              20           get from permanent storage
sstore             100          put into permanent storage
balance            20
create             100          contract creation
call               20           initiating a read-only call
memory             1            every additional word when expanding memory
txdata             5            every byte of data or code for a transaction
transaction        500          base fee transaction
contract creation  53000        changed in homestead from 21000
=================  =========    =============================

Account interactions example - betting contract
================================================================================

As previously mentioned, there are two types of accounts:

* **Externally owned account (EOAs)**: an account controlled by a private 
key, and if you own the private key associated with the EOA you have the 
ability to send ether and messages from it.
* **Contract**: an account that has its own code, and is controlled by 
code.

By default, the Ethereum execution environment is lifeless; nothing 
happens and the state of every account remains the same. However, any 
user can trigger an action by sending a transaction from an externally 
owned account, setting Ethereum's wheels in motion. If the destination of 
the transaction is another EOA, then the transaction may transfer some 
ether but otherwise does nothing. However, if the destination is a 
contract, then the contract in turn activates, and automatically runs 
its code.

The code has the ability to read/write to its own internal storage (a 
database mapping 32-byte keys to 32-byte values), read the storage of the 
received message, and send messages to other contracts, triggering their 
execution in turn. Once execution stops, and all sub-executions triggered 
by a message sent by a contract stop (this all happens in a deterministic 
and synchronous order, ie. a sub-call completes fully before the parent 
call goes any further), the execution environment halts once again, until 
woken by the next transaction.

Contracts generally serve four purposes:

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
