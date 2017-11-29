********************************************************************************
术语表
********************************************************************************

.. glossary::
   :sorted:

.. _geth-letter:

   Đ
      Đ， `加了横线的D <https://en.wikipedia.org/wiki/D_with_stroke>`_ 是在古英语、中世纪英语以及冰岛语、法罗斯群岛语中的一个大写字母"Eth"。它被用在像ĐEV或Đapp（去中心化应用）这样的词中，在这里，Đ是一个斯堪的纳维亚语的字母"eth"。大写的eth（Đ）也被用来做加密货币Dogecoin（Doge币）的象征。

.. _dec-app:

   去中心化应用 (= dapp_)
      脱离中心化的信任机构而运作的服务。一种允许脱离中间人而使最终用户/资源可以直接进行互动、达成协议或交换信息的应用程序。参考 :ref:`dapps` 。

   DAO
      去中心化自治组织。DAO是区块链上的一种类型的合约（或者一套合约），它可以制定规则、强制执行或自动化包括组织管理、资金筹措、实操、开销和扩张在内的一些组织级的工作。

   身份（identity）
      由同一个人创建的一组可以通过某种方式进行验证的交互。

   数字身份（digital identity）
      一组使用相同公钥签名的、可以进行验证的交易，定义了数字身份的行为。在很多真实场景（比如投票）会希望数字身份可以和真实身份相符。如何非暴力地确保这一点，是个仍然未被解决的问题。

   唯一身份（unique identity）
      由同一个人创建的一组可以通过某种方式进行验证的交互，外加一个限定：一个人不会同时具有多个身份。

   名声（reputation）
      一个被其他实体所相信 (1) 有能力完成某项任务， (2) 在某些情况下值得信任（例如即使有短期获益的可能，也不会背叛其他人）的身份所拥有的财产（所有物）。

   第三方监管（escrow）
      如果两个互不信任的实体有意进行交易，他们也许会希望通过一个他们分别信任的第三方来处理资金转移；只有当产品交付的证明确认之后，资金才会被划转给收款方。这降低了付款方或者收款方进行欺诈的风险。这个过程和这个第三方就被叫做escrow。

   保证金（deposit）
      一些数字资产可以被加入一个合约，并在合约中包含另一方；当一个特定的条件无法达成时，这些数字资产会自动丧失，被奖励给认定这个条件的另一方，或者销毁掉（= 消费掉 = 被分发出去），或者被捐赠给一些信托基金。这些数字资产就是所谓的押金。

   信任网络（web of trust）
      这是一种设想：如果A高度认可B，并且B高度认可C，那么A可以信任C。基于这种原理，从理论上讲，判断特定概念中的特定个体间的可靠性的更复杂、更有效的算法，是可以被设计出来的。

   激励相融（incentive compatibility）
      这是一种协议，如果任何人想要“不遵守规则”来尝试欺诈，那么除非大多数人都在同时同意这种欺诈（共谋），否则无法达成。

   共谋（collusion）
      指在一种激励性的协议下，一部分参与者 *一起假扮* （密谋）基于规则为他们自己牟利。

   代币系统（token system）
      一种可以被交易的不可替换的虚拟货物。更正规的讲，一个代币系统就是一个将许多资产映射为地址的数据库。其中所允许的主要操作就是N个代币由A转移到B，N不能为负数，N不大于A的余额，并有一份文档记录这个由A签名的转移授权。此外，类似于“保险”和“消费”的操作也是可以存在的，交易费会被收取，多个实体间同时发生的多重交易也是可能的。典型的使用场景包含货币、网络中的加密代币、企业股份和数字礼品卡。

   区块（block）
      一个区块就是一个数据包。包含了若干交易、前一区块（父区块）的哈希和其他可选数据。所有区块的总和就叫做区块链，包含了网络中所有交易的历史；除了最开始的“创世区块（genesis block）”以外，每个区块都包含一个它父区块的哈希。一些基于区块链的加密货币使用“账本（ledger）”一词，而不是区块链；但他们大体上是等价的。不过，在那些使用”账本“术语的系统中，每个区块一般会包含一个所有账户当前状态的完整拷贝（比如货币余额、部分满足的合约、登记项目等），来允许用户丢弃过时的历史数据。

.. _dapp:

   dapp
      即Đapp，就是“去中心化应用程序”。因为使用了 `大写的eth字母Ð <geth-letter_>`_ ，也可以把它读作Ethapp。

   地址（address）
      一个以太坊地址代表了一个账户。对于 EOA_ ，地址是由控制账户的公钥的最后20字节获得的，例如 ``cd2a3d9f938e13cd947ec05abc7fe734df8dd826`` 。这是个 `16进制 <hexadecimal_>`_ 格式，一般更明确地以 ``0x`` 作为前缀。在Web3.js和控制台函数中使用地址时可以不加前缀，但我们推荐使用它们。由于每字节地址由两个16进制字符标示，所以加上前缀的地址长度就是42字节。很多应用和API都实现了从Mist以太坊钱包0.5.0版本开始引入的新的 `可校验地址规则（checksum-enabled address scheme） <https://github.com/ethereum/EIPs/issues/55>`_ 。

.. _hexadecimal:

   16进制（hexadecimal）
      表示字节序列的一般格式。它的优点是可以使用两个字符（字符 ``[0-9][a-f]`` ）来简洁地表示一字节数据的值。

   以太币（ether）
      以太币是以太坊中所使用的货币的名称。它用来支付EVM中的计算费用。此外略有歧义的，它也是系统中一个计量单位的名称。

.. _EOA:

   外部账户（EOA）
      即Externally Owned Account，一个由唯一私钥控制的账户。如果你拥有一个EOA的私钥，你就可以使用它来发送以太币和消息。合约账户也有一个地址，参考 :ref:`Accounts` 。从Serenity版本开始，EOA和合约账户可以组合到同一个账户中。

.. _gas:

   气（gas）
      即所谓 `加密燃油（cryptofuel）` 的名称，由EVM在执行代码时所消耗。气被用来支付以太坊区块链上的每个执行所需的费用。

.. _gas limit:

   气的上限（gas limit）
      气的上限可以被应用到单独的交易中，参考 `气价 <transaction-gas-limit_>`_ ，也可以被用在区块中 `block-gas-limit` 。对于单独的交易，气的上限表示了你希望为执行合约的交易所支付的最大的气的数量。它是为了保护用户，使他们的以太币不会在尝试执行一个大任务或者恶意合约时被花光。区块的气上限，代表了区块中所有交易的气的累积。随着Homestead的发布，区块的气上限从3,141,592提高到4,712,388（大约增加了50%）。

.. _transaction-gas-limit:

   气价（gas price）
      即在交易中指定的每单位气所对应的以太币价格。随着Homestead的发布，默认的气价从50 shannon降低到20 shannon（大约降低了60%）。

   交易（transaction）
      一个由外部账户发出的签名数据包，其中保存一个消息。一个交易就是从一个外部账户到另一个外部账户或合约账户的信息转移。

   消息（message）
      合约与合约之间进行数据传输的一种机制。消息也可以被描述为一种虚拟对象，它不会被序列化，并且仅存在于以太坊执行环境中。

   Web3
      Web3的确切定义仍在被讨论，但它一般是指由日益增长的各种可连接设备、去中心化服务和应用程序、在线信息的逻辑存储和人工智能应用程序所组成的网络。

   epoch
      Epoch是DAG的生成周期，DAG是PoW算法Ethash所使用的种子。Epoch被指定为30000个区块。（即每隔30000个区块需要重新生成DAG，译者注。）

   椭圆曲线（elliptic curve，密码学）
      一个基于椭圆曲线代数结构的公钥密码学算法。参见 `椭圆曲线加密 <https://en.wikipedia.org/wiki/Elliptic_curve_cryptography>`_ 。

   钱包（wallet）
      一般意义上说，钱包就是任何可以保存以太币或其他加密货币的载体。在加密货币领域，钱包一般是指从可以保存单一公私钥对到管理多个密钥对的任何载体，比如Mist以太坊钱包。

   合约（contract）
      以太坊区块链上的一些持久化的代码，包含可执行函数的数据。当包含特定输入参数的以太坊交易发生时，这些函数可以运行。函数可以基于输入参数与合约内外的数据进行交互。

   自杀（suicide）
      参考自毁。依照 `EIP 6 \- Renaming SUICIDE OPCODE <https://github.com/ethereum/EIPs/blob/master/EIPS/eip-6.md>`_ ``自杀（suicide）`` 已不推荐使用。``自毁（selfdestruct）`` 是与其等价的术语。

   自毁（selfdestruct）
      Solidity语言中的一个全局变量，允许你`“销毁当前合约，把它的资金发送到给定的地址上” <https://solidity.readthedocs.org/en/latest/miscellaneous.html#global-variables>`_ ，是已不推荐使用的术语自杀（suicide）的同义词。它会释放在区块链上的空间，并防止合约再被执行。合约的地址仍然回存在，但发送到其上的以太币会永远丢失。合约的创建者可以使用Solidity的 ``selfdestruct`` 函数来删掉合约。

   交易费（transaction fee）
      也就是气费（gas cost），是为了执行你的交易所需要支付给矿工们的以太币的数量。

   挖矿（mining）
      在以太坊区块链上校验交易和合约的执行（挖到区块），以此来交换一个以以太币为单位的奖励的过程。

   矿池（mining pool）
      一个由矿工所组成的资源池，它们通过一个网络共享处理能力，依照解决一个区块所贡献的工作量分配收到的奖励。

   挖矿奖励（mining reward）
      挖到一个新区块的矿工会被给予的加密货币（在这里是以太币）奖励。

   状态（state）
      区块链上所有余额和数据在某个时间点的快照，一般指某个特定区块的状况。

   区块链（blockchain）
      一个永远增长的数据区块序列。当一个新交易被作为一个新区块的一部分被确认的时候，它会得以增长。每个新区块都会基于一个密码学的工作量证明（PoW）而添加到当前区块链的尾部。

   端点（peer）
      网络上其他也在运行以太坊节点（Geth）的计算机，和你一样，它们也都有一个准确的区块链拷贝。

   签名（signing）
      用你的私钥生成一些表示签名的数据，来证明数据的原始拥有者是你。

   发现（端点）
      与网络中的其他‘攀谈’的过程，以此来获取其他节点的状态。

   权威气价（gas price oracle）
      一个Geth客户端的辅助函数，在发送交易时可以找到一个合适的默认气价。

   轻客户端（light client）
      允许用户在一个低容量环境中执行和检查交易执行，而不用去运行一个以太坊全节点（Geth）的客户端程序。

   etherbase
      你的节点上的账户的默认名称，它会作为你的主账户。如果你进行挖矿，挖矿奖励会被存入这个账户。

   coinbase
      一个与etherbase类似的概念，但也是个所有加密货币平台所通用的术语。

   余额（balance）
      属于一个账户的加密货币（在现在这个事例里）的数量。

   solidity
      Solidity是一个高级开发语言，语法规则接近Javascript。它被设计用来编译以太坊虚拟机的代码。

   serpent
      Serpent是一种高级开发语言，语法规则接近Python。它被设计用来编译以太坊虚拟机的代码。

   EVM
      即以太坊虚拟机（Ethereum Virtual Machine），它是构成以太坊平台的去中心化核心计算平台。

   虚拟机（virtual machine）
      在计算机领域，它指一种对特定的计算机系统的模拟。

   端到端网络（peer to peer network，即P2P网络）
      一个由计算机组成的网络，可以完成那些仅可能由中心化的、基于服务器的服务所完成的功能。

   去中心化（decentralization）
      一种将控制和计算处理的执行从中心化的实体中移出的概念。

   分布式哈希表（Distributed Hash Table，DHT）
      分布式哈希表是一种去中心化的分布式系统，可以提供类似于哈希表功能的查找服务。DHT中保存的是键、值对，网络中的任何节点都可以通过特定键高效地取得相应的值。

   网络地址翻译（Network Address Translation，NAT）
      一种将一个IP地址重映射到其他地址的方法。这是通过在网络路由设备中传输数据包时修改数据包头数据中的网络协议（IP）信息而做到的。

   nonce
      即一次性数字。在信息技术里，nonce就是为了某个特定目的而生成的数字，比如会话验证（session authentication）。典型地，nonce应该是一些随时间而变化的数值，因而有时会使用一个很大的随机数。一般而言，nonce意味着“邻近的时刻”或者“临时”。在区块链的工作量证明场景中，适合当前网络难度来证明区块有效性的那些由矿工找到的哈希值，被称为Nonce。

   工作量证明（proof-of-work）
      指一个数学上的值，可以证明已经解决了一个消耗资源和时间的计算问题。一般以缩写形式“PoW”出现。

   权益证明（proof-of-stake）
      挖矿操作的一种替代方法，需要矿工通过回答问题的方式证明它们拥有一定量的网络货币。这基于一个原理，就是矿工们不应该会去尝试破坏一个它们拥有权益的网络。权益证明一般以缩写形式“PoS”出现。与PoW相比，PoS可以降低算力的浪费，但它同样也可以给网络提供额外的安全性。

   CASPER
      Casper是一个基于保证金的经济学共识协议。这意味着被称为“bonded validators”的节点，需要为了在通过产生区块而达成共识的时候缴纳一份保证金（我们称之为“bonding”的一种行为）。如果一个验证器（即某个节点）产生了一个被Casper认为“无效”的数据，它就会丧失这个保证金和继续参与共识过程的权力。

   共识（consensus）
      指网络中所有节点关于以太坊网络状态的一致认同。

   homestead
      Homestead是以太坊平台的第二个主版本。它包含了很多未来网络升级所需的协议改动和网络改动：`EIP\-2 Main homestead hardfork changes <https://github.com/ethereum/EIPs/blob/master/EIPS/eip-2.mediawiki>`_ ； `EIP\-7 Hardfork EVM update (DELEGATECALL) <https://github.com/ethereum/EIPs/blob/master/EIPS/eip-7.md>`_ ； `EIP\-8 devp2p forward compatibility <https://github.com/ethereum/EIPs/blob/master/EIPS/eip-8.md>`_ 。他已经在主网络到达1,150,000区块时被引入了。在测试网路中，它是在494,000区块时被引入的。

   metropolis
      以太坊的第三个发布版本。这是个用户界面出现的阶段（比如Mist），包括dapp商店。非技术背景的用户也可以在这个时候舒服的加入了。

   serenity
      以太坊的第四个发布阶段。这将是我们希望将网络中的挖矿过程由工作量证明迁移到权益证明的时候。

   frontier
      以太坊被计划为执行四个主要的阶段，Frontier是第一阶段的名称。Frontier版本已经在2015年7月30日发布。在这个命令行方式的Frontier阶段，每个区块奖励都被定为5以太币，并允许以太币的兑换。Frontier大大超过了早期的预料，使以太坊的生态系统得到了巨大的成长。

   olympic
      Frontier的先期发布版本，于2015年5月9日上线。它是为了使开发者可以测试以太坊区块链的各种边界限制。

   morden
      Morden是以太坊的第一个替代性测试网络。预计它会从Frontier到Homestead阶段一直持续存在。

   测试网络（testnet）
      A mirror network of the production Ethereum network that is meant 
      for testing. See Morden.
      为测试目的而存在的以太坊生产环境的镜像网络。参见morden。

   私链（private chain）
      私链就是一个写入权限中心化地由一个组织所掌握的区块链。

   联盟链（consortium chain）
      一个共识处理由预设的若干节点所控制的区块链。

   微支付（micropayment）
      微支付就是经常在线上活动发生的，交易额很小（小于1美元）的财务交易。

   分片（sharding）
      将可能的账户（合约也属于账户）空间切分为子空间的处理，比如基于它们的数字地址的首数字。这可以使合约在‘片’上执行，而不是在整个网络中，从而使交易更快速完成，并提供了一种更强的可扩展性。

   哈希（hash）
      一个密码学功能，它可以接受一个输入（或‘消息’），产生一个定长的字符串，被称为哈希值（有时也称为消息摘要、数字指纹、摘要或者检查计数）。哈希函数（或哈希算法）是一种将文档（比如一部分数据或文件）变换为一个较小数据（通常是32字节）的处理。哈希值看起来是完全随机的，并且与文档毫无关联的数据，但特定的文档经过哈希处理所得到的值总是一样的。此外最重要的是，要找到两个具有同样哈希值的文档是极为困难的计算处理。一般而言，即使两个文档中只有一个字母的不同，它们也会产生完全不同的哈希值。比如，“Saturday”的SHA3哈希值是 ``c38bbc8e93c09f6ed3fe39b5135da91ad1a99d397ef16948606cdcbd14929f9d`` ，而“Caturday”的SHA3哈希值则是 ``b4013c0eed56d5a0b448b02ec1d10dd18c1b3832068fbbdc65b98fa9b14b6dbf`` 。哈希总是被用做生成某个特定文档的不可伪造的全局唯一标示的方法。

   加密燃油（crypto-fuel）
      就是‘气’，指处理交易所需要的加密货币数量。

   加密经济学（cryptoeconomics）
      即加密货币的经济学。

   协议（protocol）
      A standard used to define a method of exchanging data over a 
      computer network.
      一个用来定义通过计算机网络交换数据的方法的标准。

   区块认可（block validation）
      The checking of the coherence of the cryptographic signature of 
      the block with the history stored in the entire blockchain.
      即通过存储在区块链上的历史数据对区块的密码学签名进行合法性校验。

   区块时间（blocktime）
      挖矿产生两个区块的平均时间间隔。

   网络哈希率（network hashrate）
      网络中节点每秒可以完成的哈希计算次数总和。

   哈希率（hashrate）
      每秒可以完成的哈希计算次数。

   序列化（serialization）
      把数据结构变换为字节序列的处理。以太坊内部使用一个被成为Recursive-Length Prefix（RLP）编码的格式，在 `wiki的RLP这一节 <https://github.com/ethereum/wiki/wiki/RLP>`_ 中有具体描述。

   双花（double spend）
      A deliberate blockchain fork, where a user with a large amount of 
      mining power sends a transaction to purchase some produce, then 
      after receiving the product creates another transaction sending 
      the same coins to themselves. The attacker then creates a block, 
      at the same level as the block containing the original transaction 
      but containing the second transaction instead, and starts mining 
      on the fork. If the attacker has more than 50% of all mining power, 
      the double spend is guaranteed to succeed eventually at any block 
      depth. Below 50%, there is some probability of success, but it is 
      usually only substantial at a depth up to about 2-5; for this 
      reason, most cryptocurrency exchanges, gambling sites and financial 
      services wait until six blocks have been produced ("six 
      confirmations") before accepting a payment.

   SPV client
      A client that downloads only a small part of the blockchain, 
      allowing users of low-power or low-storage hardware like 
      smartphones and laptops to maintain almost the same guarantee of 
      security by sometimes selectively downloading small parts of the 
      state without needing to spend megabytes of bandwidth and 
      gigabytes of storage on full blockchain validation and maintenance. 
      See light client.

   uncle
      Uncles are blockchain blocks found by a miner, when a different 
      miner has already found another block for the corresponding place 
      in the blockchain. They are called “stale blocks”. The parent of 
      an Uncle is an ancestor of the inserting block, located at the tip 
      of the blockchain. In contrast to the Bitcoin network, Ethereum 
      rewards stale blocks as well in order to avoid to penalize miners 
      with a bad connection to the network. This is less critical in the 
      Bitcoin network, because the Block Time there is much higher 
      (~10 minutes) than on the Ethereum network (aimed to ~15 seconds).

   GHOST
      Greedy Heaviest-Observed Sub-Tree is an alternative chain-selection 
      method that is designed to incentivize stale blocks (uncles) as well, 
      thus reducing the incentive for pool mining. In GHOST, even the 
      confirmation given by stale blocks to previous blocks are considered 
      valid, and the miners of the stale blocks are also rewarded with a 
      mining reward.

   merkle patricia tree
      Merkle Patricia trees provide a cryptographically authenticated 
      data structure that can be used to store all (key, value) bindings. 
      They are fully deterministic, meaning that a Patricia tree with 
      the same (key,value) bindings is guaranteed to be exactly the same 
      down to the last byte and therefore have the same root hash, 
      provide O(log(n)) efficiency for inserts, lookups and deletes, 
      and are much easier to understand and code than more complex 
      comparison-based alternatives like red-black trees.

   DAG
      DAG stands for Directed Acyclic Graph. It is a graph, a set of 
      nodes and links between nodes, that has very special properties. 
      Ethereum uses a DAG in Ethash, the Ethereum Proof of Work (POW) 
      algorithm.The Ethash DAG takes a long time to be generated, 
      which is done by a Miner node into a cache file for each Epoch. 
      The file data is then used when a value from this graph is 
      required by the algorithm.

   uncle rate
      The number of uncles produced per block.

   issuance
      The minting and granting of new cryptocurrency to a miner who has 
      found a new block.

   presale
      Sale of cryptocurrency before the actual launch of the network.

   static node
      A feature supported by Geth, the Golang Ethereum client, which 
      makes it possible to always connect to specific peers. Static 
      nodes are re-connected on disconnects. For details, see the 
      :ref:`section on static nodes <cr-static-nodes>`.

   bootnode
      The nodes which can be used to initiate the discovery process when 
      running a node. The endpoints of these nodes are recorded in the 
      Ethereum source code.

   exchange
      An online marketplace which facilitates the exchange of crypto or 
      fiat currencies based on the market exchange rate.

   compiler
      A program that translates pieces of code written in high level 
      languages into low level executable code.

   genesis block
      The first block in a blockchain.

   network id
      A number which identifies a particular version of the Ethereum 
      network.

   block header
      The data in a block which is unique to its content and the 
      circumstances in which it was created. It includes the hash of the 
      previous block's header, the version of the software the block is 
      mined with, the timestamp and the merkle root hash of the contents 
      of the block.

   pending transaction
      A transaction that is not yet confirmed by the Ethereum network.

   block propagation
      The process of transmitting a confirmed block to all other nodes 
      in the network.

   sidechain
      A blockchain that branches off a main blockchain and checks in 
      periodically with the main blockchain. Besides that it runs 
      independently from the main chain, and any security compromises 
      in the sidechain will not affect the main chain.

   pegging
      Locking down the exchange rate of the coins/tokens in two chains 
      (usually a main and a side chain) in a certain direction.

   2-way pegging
      Locking down the exchange rate of the coins/tokens in two chains 
      (usually a main and a side chain) in both directions.

   trustless
      Refers to the ability of a network to trustworthily mediate 
      transactions without any of the involved parties needing to trust 
      anyone else.

   faucet
      A website that dispenses (normally testnet) cryptocurrencies for 
      free.

   checksum
      A count of the number of bits in a transmission that is included 
      with the unit so that the receiving end can verify that the 
      entirety of the message has been transmitted.

   ICAP
      Interexchange Client Address Protocol, an IBAN-compatible system 
      for referencing and transacting to client accounts aimed to 
      streamline the process of transferring funds, worry-free between 
      exchanges and, ultimately, making KYC and AML concerns a thing of 
      the past.

   private key
      A private key is a string of characters known only to the owner, 
      that is paired with a public key to set off algorithms for text 
      encryption and decryption.

   public key
      A string of characters derived from a private key that can be made 
      public. The public key can be used to verify the authenticity of 
      any signature created using the private key.

   encryption
      Encryption is the conversion of electronic data into a form 
      unreadable by anyone except the owner of the correct decryption 
      key. It can further be described as a process by which a document 
      (plaintext) is combined with a shorter string of data, called a 
      key (e.g. ``c85ef7d79691fe79573b1a7064c19c1a9819ebdbd1faaab1a8ec92344438aaf4``), 
      to produce an output (ciphertext) which can be "decrypted" back into 
      the original plaintext by someone else who has the key, but which is 
      incomprehensible and computationally infeasible to decrypt for 
      anyone who does not have the key.

   digital signature
      A mathematical scheme for demonstrating the authenticity of a 
      digital message or documents.

   port
      A network port is a communication endpoint used by a one of the 
      existing standards of establishing a network conversation 
      (e.g. TCP, UDP).

   RPC
      Remote Procedure Call, a protocol that a program uses to request 
      a service from a program located in another computer in a network 
      without having to understand the network details.

   IPC
      Interprocess communication (IPC) is a set of programming interfaces 
      that allow a programmer to coordinate activities among different 
      program processes that can run concurrently in an operating system.

   attach
      The command used to initiate the Ethereum Javascript console.

   daemon
      A computer program that runs as a background process instead of 
      in direct control by an interactive user.

   system service
      See base layer service

   base layer service
      Services such as SWARM and Whisper which are built into the 
      Ethereum platform.

   js
      Javascript.

   syncing
      The process of downloading the entire blockchain.

   fast sync
      Instead of processing the entire block-chain one link at a time, 
      and replay all transactions that ever happened in history, fast 
      syncing downloads the transaction receipts along the blocks, and 
      pulls an entire recent state database.

   ASIC
      Application-specific integrated circuit, in this case referring 
      to an integrated circuit custom built for cryptocurrency mining.

   memory-hard
      Memory hard functions are processes that experience a drastic 
      decrease in speed or feasibility when the amount of available 
      memory even slightly decreases.

   keyfile
      Every account's private key/address pair exists as a single 
      keyfile. These are JSON text files which contains the encrypted 
      private key of the account, which can only be decrypted with the 
      password entered during account creation.

   ICAP format
      The format of the IBANs defined using the 
      `Inter-exchange Client Address Protocol <https://github.com/ethereumjs/ethereumjs-icap>`_.

   block(chain) explorer
      A website that allows easy searching and extraction of data from 
      the blockchain.

   geth
      Ethereum client implemented in the Golang programming language, 
      based on the protocol as defined in the Ethereum Yellow Paper.

   eth
      Ethereum client implemented in the C++ programming language, 
      based on the protocol as defined in the Ethereum Yellow Paper.

   ethereumjs
      Ethereum client implemented in the Javascript/Node programming 
      language, based on the protocol as defined in the Ethereum Yellow 
      Paper.

   pyethereum
      Ethereum client implemented in the Python programming language, 
      based on the protocol as defined in the Ethereum Yellow Paper.

   ethereumj
      Ethereum client implemented in the Java programming language, 
      based on the protocol as defined in the Ethereum Yellow Paper.

   ethereumh
      Ethereum client implemented in the Haskell programming language, 
      based on the protocol as defined in the Ethereum Yellow Paper.

   parity
      Ethereum client implemented in the Rust programming language, 
      based on the protocol as defined in the Ethereum Yellow Paper.

   difficulty
      In very general terms, the amount of effort required to mine a new 
      block. With the launch of Homestead, the 
      `difficulty adjustment algorithm will change <https://github.com/ethereum/EIPs/blob/master/EIPS/eip-2.mediawiki>`_.

   account
      Accounts are a central part of the Ethereum network and are an 
      essential part of any transaction or contract. In Ethereum, 
      there are two types of accounts: Externally Owned accounts (EOA) 
      and Contract accounts.

   HLL (obsolete)
      Acronym for Higher Level Language, which is what Serpent and 
      Solidity are. HLL is what early Ðapp developers called Ethereum 
      programming languages that did not touch the low level elements. 
      This phrase has been phased out.

   CLL (obsolete)
      Acronym for C Like Language, which Mutan was. This acronym has 
      been phased out.

   ES1, ES2, and ES3 (obsolete)
      "Ethereum Script" versions 1,2 and 3. There were early versions 
      of what would become the Ethereum Virtual Machine (EVM).

   log event
      Contracts are triggered by transactions executed as part of the 
      block verification. If conceived of as a function call, contract 
      execution is asynchronous, and therefore they have no return value. 
      Instead contracts communicate to the outside world with log events. 
      The log events are part of the transaction receipt which is 
      produced when the transaction is executed.
      The receipts are stored in the receipt trie, the integrity of 
      which is guaranteed by the fact that the current root of the 
      receipt trie is part of the block header alongside the roots of 
      state and state-trie. In a broad sense from the external 
      perspective receipts are part of the Ethereum system state except 
      that they are not readable contracts internally.

   .. hardware wallet
   .. brain wallet
   .. cold storage
