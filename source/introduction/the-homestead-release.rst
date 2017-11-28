********************************************************************************
Homestead版本
********************************************************************************

Homestead是以太坊平台的第二个主要版本，也是第一个产品级的发布。 它包含了很多协议和网络上的变动以支持未来的网络升级。以太坊的第一个版本，Frontier版本，本质上是一个beta版本，供开发者学习和体验并开始初步构建去中心化的应用和工具。 

以太坊开发路线图中的里程碑
-----------------------------------------------

在以太坊上线前发表的 `初始的开发路线图 <https://blog.ethereum.org/2015/03/03/ethereum-launch-process/>`_ 指出了以下几个里程碑：

* 预发布 步骤 0: Olympic测试网络 - 2015年5月
* 发布 步骤 １: Frontier - 2015年7月30日
* 发布 步骤 ２: Homestead - 2016年3月14日（圆周率日，Pi Day）
* 发布 步骤 ３: Metropolis - 待定
* 发布 步骤 ４: Serenity - 待定


尽管以上里程碑仍然有效，但它们的实质已经从某种程度上改变了。 `Olympic测试网络 <olympic-testnet>`_ 发现了很多重大改进点，于是 `Frontier版本 <history-of-ethereum.html#the-ethereum-frontier-launch>`_ 在其后很快就发布了。而Homestead则是由beta产品阶段退出进入稳定版本的标志。Homestead已经被于2016年3月14日（圆周率日）左右产生的1,150,000号区块所自动引入了。

如果你正在运行一个已连接到网络的节点，你需要尽快升级到兼容Homestead版本的客户端。这些客户端可以在 :ref:`Ethereum Clients` 找到。否则你将会在一个错误的分叉上终止，无法再与整个网络同步。

一旦以太坊区块链达到1,150,000号区块，以太坊网络将经历一次硬分叉来使以下几个重大变动生效。

.. _homestead-hard-fork-changes:

Homestead硬分叉变动
----------------------------------
以太坊从狭义上讲就是一组协议。Homestead包含几个向前兼容的协议变动，故而需要一次硬分叉。这些变动用它们特定的方式实现了 :ref:`以太坊改进建议 <Ethereum Improvement Proposals>` 包含以下几点：

* `EIP 2: <https://github.com/ethereum/EIPs/blob/master/EIPS/eip-2.mediawiki>`_

  * cost for creating contracts via a transaction is increased from 21000 to 53000. Contract creation from a contract using the ``CREATE`` opcode is unaffected.
  * transaction signatures whose s-value is greater than ``secp256k1n/2`` are now considered invalid
  * If contract creation does not have enough gas to pay for the final gas fee for adding the contract code to the state, the contract creation fails (ie. goes out-of-gas) rather than leaving an empty contract.
  * Change the difficulty adjustment algorithm
* `EIP 7: DELEGATECALL <https://github.com/ethereum/EIPs/blob/master/EIPS/eip-7.md>`_: Add a new opcode, ``DELEGATECALL`` at ``0xf4``, which is similar in idea to ``CALLCODE``, except that it propagates the sender and value from the parent scope to the child scope, ie. the call created has the same sender and value as the original call. This means contracts can store pass through information while following msg.sender and ``msg.value`` from its parent contract. Great for contracts which create contracts but don’t repeat additional information which saves gas. See `comments on EIP 7 <https://github.com/ethereum/EIPs/issues/23>`_
* `EIP 8: devp2p Forward Compatibility compliance with the Robustness Principle <https://github.com/ethereum/EIPs/blob/master/EIPS/eip-8.md>`_ Changes to the RLPx Discovery Protocol and RLPx TCP transfer protocol to ensure that all client software in use on the Ethereum network can cope with future network protocol upgrades. For older versions of an Ethereum client, updates to the network protocol weren’t being accepted by older clients and would refuse communication if the hello packets didn’t meet expectations. This update means all future versions of the client will accept incoming network upgrades and handshakes.

这些变动有如下一些优点：

* EIP-2/1 eliminates the excess incentive to create contracts via transactions, where the cost is 21000, rather than contracts, where the cost is 32000.
* EIP-2/1 also fixes the protocol "bug" that with the help of suicide refunds, it is currently possible to make a simple ether value transfer using only 11664 gas.
* EIP-2/2 fixes a transaction malleability concern (not a security flaw, but a UI incovenience).
* EIP-2/3 creates a more intuitive "success or fail" distinction in the result of a contract creation process, rather than the current "success, fail, or empty contract" trichotomy
* EIP-2/4 eliminates the excess incentive to set the timestamp difference to exactly 1 in order to create a block that has slightly higher difficulty and that will thus be guaranteed to beat out any possible forks. This guarantees to keep block time in the 10-20 range and according to simulations restores the target 15 second blocktime (instead of the current effective 17s).
* EIP-7 makes it much easier for a contract to store another address as a mutable source of code and ''pass through'' calls to it, as the child code would execute in essentially the same environment (except for reduced gas and increased callstack depth) as the parent.
* EIP-8 makes sure that all client software in use on the Ethereum network can cope with future network protocol upgrades.


参考资源：
- `Reddit discussion on Homestead Release <https://www.reddit.com/r/ethereum/comments/48arax/homestead_release_faq/>`_
- :ref:`Ethereum Improvement Proposals`
