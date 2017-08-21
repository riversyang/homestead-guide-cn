.. _sec:connecting-to-the-network:

********************************************************************************
连接到网络
********************************************************************************

以太坊网络
================================================================================

保持和保护区块链的相互协作的节点所组成的P2P（peer-to-peer）网络，是去中心化一致性的基础。参见  :ref:`mining` 。

以太坊网络状态
--------------------------------------------------

`EthStats\.net <https://ethstats.net/>`_ 是以太坊网络实时统计数据的仪表盘。它显示了一些重要的信息，比如当前区块、哈希难度、气的价格以及气的消耗。在这个页面显示的节点，仅是网络中实际节点的一部分。任何人都可以将他们的节点添加到这个仪表盘。 `Eth\-Netstats README on Github <https://github.com/cubedro/eth-netstats>`_ 记述了如何进行连接。

`EtherNodes\.com <https://www.ethernodes.org/>`_ 显示以太坊主网络和最新测试网络中当前及历史节点统计以及一些其他信息。

`当前活动网络的一些统计信息 <https://etherchain.org>`_ - EtherChain上的实时状态信息。

公链、私有链和联盟链
------------------------------------------------

目前，大多数以太坊项目都将以太坊作为一个提供了大量用户接入、网络节点、货币和市场的公共的区块链。然而，也通常会有些特定的原因，使人们也倾向于使用一个私有链或联盟链（某些内部相互信任的团体）。例如一些垂直领域的公司团体，像银行，正把以太坊视为他们自己的私有链的基础平台。

以下是一位发表了 `On Public and Private Blockchains <https://blog.ethereum.org/2015/08/07/on-public-and-private-blockchains/>`_ 的专家，根据访问权限的不同所给出的以上三种区块链的区别。

- **公链（Public blockchains）**：公链，是一个世界上的任何人都可以读取的，任何人都可以向它发送交易，并在交易合法之后就能被记录的区块链；并且世界上的任何人都可以参与到共识过程（一个决定哪个区块会被加到链上并反映当前数据状态的过程）。作为中心化/准中心化信任体系的替代，公链基于加密经济学原理确保其安全可信，即将经济学原理与加密校验相结合，使用工作量证明或权益证明算法，并基于一个抽象概念：一个人能对共识过程施加的影响的程度，是与他可以运用的经济资源的数量相称的。这些区块链通常被认为是“完全去中心化”的。

- **联盟链（Consortium blockchains）**：联盟链，是一个共识过程由预先确定好的若干节点来控制的区块链。例如，我们可以想象一个由15个金融机构所组成的联盟链，需要其中10个以上机构控制的节点签名承认某个区块才能使该区块有效。读取这个区块链的权限可以是公开的，或者限制为仅联盟成员，并且还可能有混合路由来访问。这种混合路由是指联盟链上节点的根哈希与特定的API一起公开，以使公共成员可以做某些特定的查询，取得关于区块链状态的某些数据。这些区块链可以被认为是“部分去中心化”的。

- **私有链（Private blockchains）**：私有链，是一个写入权限由中心化的某一个组织所控制的区块链。而读取权限可以是公开的或者任意扩展的。就像现在的大多数应用程序一样，数据库的维护和审计等等工作由一个单独的公司负责。这样，在很多情况下，公开的数据读取就完全没必要了，尽管也有一些情况会希望可以有公开的审计能力。

尽管这些私有链/联盟链也许没有到公链的连接，但他们依然可以通过资助以太坊软件的开发来共建以太坊生态系统。随着时间的推移，这些终将变为软件的改进、知识的分享以及相应的工作机会。


How to connect
================================================================================

Geth continuously attempts to connect to other nodes on the network until it has peers. If you have UPnP enabled on your router or run Ethereum on an Internet-facing server, it will also accept connections from other nodes.

Geth finds peers through something called the *discovery protocol*. In the discovery protocol, nodes are gossipping with each other to find out about other nodes on the network. In order to get going initially, geth uses a set of bootstrap nodes whose endpoints are recorded in the source code.

Checking connectivity and ENODE IDs
--------------------------------------------------------------------------------

To check how many peers the client is connected to in the interactive console, the ``net`` module has two attributes that give you info about the number of peers and whether you are a listening node.

.. code-block:: Javascript

  > net.listening
  true

  > net.peerCount
  4

To get more information about the connected peers, such as IP address and port number, supported protocols, use the ``peers()`` function of the ``admin`` object. ``admin.peers()`` returns the list of currently connected peers.

.. code-block:: Javascript

  > admin.peers
  [{
  	ID: 'a4de274d3a159e10c2c9a68c326511236381b84c9ec52e72ad732eb0b2b1a2277938f78593cdbe734e6002bf23114d434a085d260514ab336d4acdc312db671b',
  	Name: 'Geth/v0.9.14/linux/go1.4.2',
  	Caps: 'eth/60',
  	RemoteAddress: '5.9.150.40:30301',
  	LocalAddress: '192.168.0.28:39219'
   }, {
  	ID: 'a979fb575495b8d6db44f750317d0f4622bf4c2aa3365d6af7c284339968eef29b69ad0dce72a4d8db5ebb4968de0e3bec910127f134779fbcb0cb6d3331163c',
  	Name: 'Geth/v0.9.15/linux/go1.4.2',
  	Caps: 'eth/60',
  	RemoteAddress: '52.16.188.185:30303',
  	LocalAddress: '192.168.0.28:50995'
   }, {
  	ID: 'f6ba1f1d9241d48138136ccf5baa6c2c8b008435a1c2bd009ca52fb8edbbc991eba36376beaee9d45f16d5dcbf2ed0bc23006c505d57ffcf70921bd94aa7a172',
  	Name: 'pyethapp_dd52/v0.9.13/linux2/py2.7.9',
  	Caps: 'eth/60, p2p/3',
  	RemoteAddress: '144.76.62.101:30303',
  	LocalAddress: '192.168.0.28:40454'
   }, {
    ID: 'f4642fa65af50cfdea8fa7414a5def7bb7991478b768e296f5e4a54e8b995de102e0ceae2e826f293c481b5325f89be6d207b003382e18a8ecba66fbaf6416c0',
    Name: '++eth/Zeppelin/Rascal/v0.9.14/Release/Darwin/clang/int',
    Caps: 'eth/60, shh/2',
    RemoteAddress: '129.16.191.64:30303',
    LocalAddress: '192.168.0.28:39705'
   } ]


To check the ports used by geth and also find your enode URI run:

.. code-block:: Javascript

  > admin.nodeInfo
  {
    Name: 'Geth/v0.9.14/darwin/go1.4.2',
    NodeUrl: 'enode://3414c01c19aa75a34f2dbd2f8d0898dc79d6b219ad77f8155abf1a287ce2ba60f14998a3a98c0cf14915eabfdacf914a92b27a01769de18fa2d049dbf4c17694@[::]:30303',
    NodeID: '3414c01c19aa75a34f2dbd2f8d0898dc79d6b219ad77f8155abf1a287ce2ba60f14998a3a98c0cf14915eabfdacf914a92b27a01769de18fa2d049dbf4c17694',
    IP: '::',
    DiscPort: 30303,
    TCPPort: 30303,
    Td: '2044952618444',
    ListenAddr: '[::]:30303'
  }

Download the blockchain faster
================================================================================

When you start an Ethereum client, the Ethereum blockchain is automatically downloaded. The time it takes to download the Ethereum blockchain can vary based on client, client settings, connection speed, and number of peers available. Below are some options for more quickly obtaining the Ethereum blockchain.

Using geth
--------------------------------------------------------------------------------

If you are using the geth client, there are some things you can do to speed up the time it takes to download the Ethereum blockchain. If you choose to use the ``--fast`` flag to perform an Ethereum fast sync, you will not retain past transaction data.

.. note:: You cannot use this flag after performing all or part of a normal sync operation, meaning you should not have any portion of the Ethereum blockchain downloaded before using this command. `See this Ethereum Stack\.Exchange answer for more information <http://ethereum.stackexchange.com/questions/1845/why-isnt-fast-sync-the-default>`_.

Below are some flags to use when you want to sync your client more quickly.

``--fast``

This flag enables fast syncing through state downloads rather than downloading the full block data. This will also reduce the size of your blockchain dramatically.
NOTE: ``--fast`` can only be run if you are syncing your blockchain from scratch and only the first time you download the blockchain for security reasons. `See this Reddit post for more information <https://www.reddit.com/r/ethereum/comments/3y9316/geth_fast_option_question/>`_.

``--cache=1024``

Megabytes of memory allocated to internal caching (min 16MB / database forced). Default is 16MB, so increasing this to 256, 512, 1024 (1GB), or 2048 (2GB) depending on how much RAM your computer has should make a difference.

``--jitvm``

This flag enables the JIT VM.

Full example command with console:

.. code-block:: Bash

  geth --fast --cache=1024 --jitvm console

For more discussion on fast syncing and blockchain download times, `see this Reddit post <https://www.reddit.com/r/ethereum/comments/46c4ga/lets_benchmark_the_clients/>`_.

Exporting/Importing the blockchain
--------------------------------------------------------------------------------

If you already have a full Ethereum node synced, you can export the blockchain data from the fully synced node and import it into your new node. You can accomplish this in geth by exporting your full node with the command ``geth export filename`` and importing the blockchain into your node using ``geth import filename``.
see `this link <staticnodes>`_

..  _cr-static-nodes:

Static Nodes, Trusted Nodes, and Boot Nodes
================================================================================

Geth supports a feature called static nodes if you have certain peers you always want to connect to. Static nodes are re-connected on disconnects. You can configure permanent static nodes by putting something like the following into ``<datadir>/static-nodes.json`` (this should be the same folder that your ``chaindata`` and ``keystore`` folders are in)

.. code-block:: Javascript

  [
  	"enode://f4642fa65af50cfdea8fa7414a5def7bb7991478b768e296f5e4a54e8b995de102e0ceae2e826f293c481b5325f89be6d207b003382e18a8ecba66fbaf6416c0@33.4.2.1:30303",
  	"enode://pubkey@ip:port"
  ]

You can also add static nodes at runtime via the Javascript console using ``admin.addPeer()``

.. code-block:: Console

  > admin.addPeer("enode://f4642fa65af50cfdea8fa7414a5def7bb7991478b768e296f5e4a54e8b995de102e0ceae2e826f293c481b5325f89be6d207b003382e18a8ecba66fbaf6416c0@33.4.2.1:30303")

Common problems with connectivity
--------------------------------------------------------------------------------

Sometimes you just can't get connected. The most common reasons are:

* Your local time might be incorrect. An accurate clock is required to participate in the Ethereum network. Check your OS for how to resync your clock (example ``sudo ntpdate -s time.nist.gov``) because even 12 seconds too fast can lead to 0 peers.
* Some firewall configurations can prevent UDP traffic from flowing. You can use the static nodes feature or ``admin.addPeer()`` on the console to configure connections by hand.

To start geth without the discovery protocol, you can use the ``--nodiscover`` parameter. You only want this if you are running a test node or an experimental test network with fixed nodes.
