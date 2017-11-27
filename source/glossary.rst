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

   balance
      The amount of cryptocurrency (in this case) belonging to an account.

   solidity
      Solidity is a high-level language whose syntax is similar to that 
      of JavaScript and it is designed to compile to code for the 
      Ethereum Virtual Machine.

   serpent
      Serpent is a high-level language whose syntax is similar to that of 
      Python and it is designed to compile to code for the Ethereum 
      Virtual Machine.

   EVM
      Ethereum Virtual Machine, the decentralized computing platform 
      which forms the core of the Ethereum platform.

   virtual machine
      In computing, it refers to an emulation of a particular computer 
      system.

   peer to peer network
      A network of computers that are collectively able to perform 
      functionalities normally only possible with centralized, 
      server-based services.

   decentralization
      The concept of moving the control and execution of computational 
      processes away from a central entity.

   distributed hash table
      A distributed hash table (DHT) is a class of a decentralized 
      distributed system that provides a lookup service similar to a 
      hash table: (key, value) pairs are stored in a DHT, and any 
      participating node can efficiently retrieve the value associated 
      with a given key.

   NAT
      Network address translation (NAT) is a methodology of remapping 
      one IP address space into another by modifying network address 
      information in Internet Protocol (IP) datagram packet headers 
      while they are in transit across a traffic routing device.

   nonce
      Number Used Once or Number Once. A nonce, in information technology, 
      is a number generated for a specific use, such as session 
      authentication. Typically, a nonce is some value that varies with 
      time, although a very large random number is sometimes used. 
      In general usage, nonce means “for the immediate occasion” or “for 
      now.”
      In the case of Blockchain Proof of Work scenarios, the hash value, 
      found by a Miner, matching the network's Difficulty thus proving 
      the Block Validity is called Nonce as well.

   proof-of-work
      Often seen in its abbreviated form "PoW", it refers to a 
      mathematical value that can act as the proof of having solved a 
      resource and time consuming computational problem.

   proof-of-stake
      An alternative method of mining blocks that require miners to 
      demonstrate their possession of a certain amount of the currency of 
      the network in question. This works on the principle that miners 
      will be disincentivized to try to undermine a network in which 
      they have a stake. PoS is less wasteful than PoW, but is still 
      often used together with it to provide added security to the 
      network.

   CASPER
      Casper is a security-deposit based economic consensus protocol. 
      This means that nodes, so called “bonded validators”, have to place 
      a security deposit (an action we call “bonding”) in order to serve 
      the consensus by producing blocks. If a validator produces anything 
      that Casper considers “invalid”, the deposit is forfeited along 
      with the privilege of participating in the consensus process.

   consensus
      The agreement among all nodes in the network about the state of 
      the Ethereum network.

   homestead
      Homestead is the second major version release of the Ethereum 
      platform. Homestead includes several protocol changes and a 
      networking change that makes possible further network upgrades: 
      `EIP\-2 Main homestead hardfork changes <https://github.com/ethereum/EIPs/blob/master/EIPS/eip-2.mediawiki>`_; 
      `EIP\-7 Hardfork EVM update (DELEGATECALL) <https://github.com/ethereum/EIPs/blob/master/EIPS/eip-7.md>`_; 
      `EIP\-8 devp2p forward compatibility <https://github.com/ethereum/EIPs/blob/master/EIPS/eip-8.md>`_. 
      Homestead will launch when block 1,150,000 is reached on the 
      Mainnet. On the Testnet, Homestead will launch at block 494,000.

   metropolis
      The third stage of Ethereum's release. This is the stage when the 
      user interfaces come out (e.g. Mist), including a dapp store, and 
      non-technical users should feel comfortable joining at this point.

   serenity
      The fourth stage of Ethereum's release. This is when things are 
      going to get fancy: the network is going to change its mining 
      process from Proof-of-Work to Proof-of-Stake.

   frontier
      Ethereum was planned to be released in four major steps with 
      Frontier being the name for the first phase. The Frontier release 
      went live on July 30th, 2015. The command line Frontier phase was 
      mainly meant to get mining operations going with the full reward 
      of 5 ether per block and also to promote the emergence of ether 
      exchanges. Frontier surpassed earlier modest expectations and has 
      nurtured tremendous growth of the ecosystem.

   olympic
      The Frontier pre-release, which launched on May 9th 2015. It was 
      meant for developers to help test the limits of the Ethereum 
      blockchain.

   morden
      Morden is the first Ethereum alternative testnet. It is expected 
      to continue throughout the Frontier and Homestead era.

   testnet
      A mirror network of the production Ethereum network that is meant 
      for testing. See Morden.

   private chain
      A fully private blockchain is a blockchain where write permissions 
      are kept centralized to one organization.

   consortium chain
      A blockchain where the consensus process is controlled by a 
      pre-selected set of nodes.

   micropayment
      A micropayment is a financial transaction involving a very small 
      sum of money (<1 USD) and usually one that occurs online.

   sharding
      The splitting of the space of possible accounts (contracts are 
      accounts too) into subspaces, for example, based on first digits 
      of their numerical addresses. This allows for contract executions 
      to be executed within 'shards' instead of network wide, allowing 
      for faster transactions and greater scalability.

   hash
      A cryptographic function which takes an input (or 'message') and 
      returns a fixed-size alphanumeric string, which is called the 
      hash value (sometimes called a message digest, a digital fingerprint, 
      a digest or a checksum). A hash function (or hash algorithm) is a 
      process by which a document (i.e. a piece of data or file) is 
      processed into a small piece of data (usually 32 bytes) which 
      looks completely random, and from which no meaningful data can 
      be recovered about the document, but which has the important 
      property that the result of hashing one particular document is 
      always the same. Additionally, it is crucially important that it 
      is computationally infeasible to find two documents that have the 
      same hash. Generally, changing even one letter in a document will 
      completely randomize the hash; for example, the SHA3 hash of 
      "Saturday" is ``c38bbc8e93c09f6ed3fe39b5135da91ad1a99d397ef16948606cdcbd14929f9d``, 
      whereas the SHA3 hash of "Caturday" is ``b4013c0eed56d5a0b448b02ec1d10dd18c1b3832068fbbdc65b98fa9b14b6dbf``. 
      Hashes are usually used as a way of creating a globally agreed-upon 
      identifier for a particular document that cannot be forged.

   crypto-fuel
      Similar to 'gas', referring to the amount of cryptocurrency 
      required to power a transaction.

   cryptoeconomics
      The economics of cryptocurrencies.

   protocol
      A standard used to define a method of exchanging data over a 
      computer network.

   block validation
      The checking of the coherence of the cryptographic signature of 
      the block with the history stored in the entire blockchain.

   blocktime
      The average time interval between the mining of two blocks.

   network hashrate
      The number of hash calculations the network can make per second 
      collectively.

   hashrate
      The number of hash calculations made per second.

   serialization
      The process of converting a data structure into a sequence of 
      bytes. Ethereum internally uses an encoding format called 
      recursive-length prefix encoding (RLP), described in the 
      `RLP section of the wiki <https://github.com/ethereum/wiki/wiki/RLP>`_.

   double spend
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
