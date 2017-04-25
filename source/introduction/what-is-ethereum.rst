.. _what-is-ethereum:

################################################################################
以太坊是什么?
################################################################################

以太坊（Ethereum）是一个开放的区块链平台，可以让任何人都能够创建和使用基于区块链技术的去中心化应用程序。与比特币一样，没有人控制或拥有以太坊，它是一个由全世界的许多人所共通创建的开源项目。 不同于比特币的是，以太坊被设计成灵活的、可根据需求修改的模式。在以太坊平台上创建应用是很容易的，在Homestead发布版本之上，所有人使用这些应用程序都已经很安全了。

================================================================================
下一代的区块链
================================================================================

区块链技术是比特币的基础技术，在神秘的作者中本聪（Satoshi Nakamoto）于2008年发表的的白皮书"Bitcoin: A Peer-to-Peer Electronic Cash System"中被首次描述。尽管在这篇最初的论文中已经提及了区块链技术的泛用性，但区块链作为通用术语出现，还是在几年之后的事。区块链是一个分布式的计算架构，每个网络节点都执行和记录同样的交易流水，这些流水数据被组织到所谓区块之中。在同一时间，只有一个区块可以被添加到链中， 每个区块都包含一个数学证明，来证实它是在它之前的所有区块之后产生的。用这种方法，使区块链的“分布式数据库”在整个网络中达到共识。用户与账本（交易流水）的交互通过强大的加密方式保证其安全性。负责维持和校验整个网络状态的节点，将获得由编码到协议中的经济学奖励算法计算得出的奖励。

对于比特币而言，分布式数据库被设想成通过比特币代币在账户间的转移来使个人用户间的去信任金融变得可能的一种账户结算表、账本和交易流水的集合。但随着比特币吸引了越来越多的开发者和技术专家，一些新奇的项目开始用比特币网络来做一些代币价值转移以外的工作。其中一些项目采用了"alt coins"的模式，通过改进原始的比特币协议形成自己的加密货币，从而将区块链分离以增加新的特性和功能。在2013年底，以太坊（Ethereum）的发明人Vitalik Buterin正式提出了一个设想，这是一个具有再编程能力来执行任意复杂计算的单一区块链，可以将很多其他的项目纳入其内。 

在2014年，以太坊（Ethereum）的创始人Vitalik Buterin, Gavin Wood和Jeffrey Wilcke就开始致力于构建下一代的区块链技术的工作，以实现一个通用的、完全去信任的智能合约平台（smart contract platform）。

================================================================================
以太坊虚拟机
================================================================================

以太坊是一个可编程的区块链。以太坊允许用户根据自己的设想创建任意复杂的操作，而不是只给用户一些预设好的操作（例如比特币的交易操作）。用这种方法，它成为了一个支撑许多不同类型的去中心化区块链应用的平台，包含但不仅限于加密货币。

狭义上说，以太坊是定义了去中心化应用平台的一套协议。其核心就是可以运行任意的复杂算法代码的 :ref:`以太坊虚拟机("EVM") <the-EVM>`。用计算机科学术语来讲，以太坊是“图灵完备”的。开发者可以使用友好的编程语言在EVM上创建应用程序，比如使用JavaScript或Python。

与其他任何区块链一样，以太坊也包含一个P2P（peer-to-peer）网络协议。以太坊区块链数据库，由众多的连接到此网络的节点维护和更新。每个节点都会运行EVM并执行相同的操作序列。因此，以太坊有时也被形象的描述为“全球计算机”（“world computer”）。

这种跨越整个以太坊网络的超大规模并行计算，并不会使计算更加高效。事实上，这样的过程，使以太坊上的普通的计算远比使用传统的“计算机”来的更慢、更昂贵。但是，由于每个以太坊节点都会运行EVM来在区块链上达成共识，这种去中心化的共识，也给了以太坊极致的容错性（fault tolerance）、零宕机时间（zero downtime）、使存储在区块链上的数据永远无法更改（forever unchangeable）和抗审查（censorship-resistant）。

以太坊平台本身是无特性（featureless）或价值未知（value-agnostic）的。与编程语言一样，是企业家和开发者决定它应该用来做什么。然而根据以太坊本身的能力，某些特定的应用显然要比其他类型更能受益。具体来讲，以太坊 **适合于那些旨在解决点到点之间直接交互，或者跨网络的团体协作问题的应用程序**。 例如特定的点到点（peer-to-peer）交易市场应用，或者自动化的复杂金融合约应用等等。 比特币，允许个人在不引入任何中介，像金融机构、银行或政府的情况下进行货币交易。而以太坊的影响会更加深远。从理论上讲，任意复杂度的金融交互或交易（financial interactions or exchanges）都可以自动化的、可靠的使用以太坊上的代码来实现。而除金融应用以外，任何注重信任、安全、持久性的场合，比如资产注册、投票、管辖和物联网，都可以大范围的嵌入以太坊平台。

================================================================================
以太坊是如何运作的？
================================================================================

Ethereum incorporates many features and technologies that will be familiar to users of Bitcoin, while also introducing many modifications and innovations of its own.

Whereas the Bitcoin blockchain was purely a list of transactions, :ref:`Ethereum's basic unit is the account <Accounts>`. The Ethereum blockchain tracks the state of every account, and all state transitions on the Ethereum blockchain are transfers of value and information between accounts. There are two types of accounts:

- Externally Owned Accounts (EOAs), which are controlled by private keys
- Contract Accounts, which are controlled by their contract code and can only be "activated" by an EOA

For most users, the basic difference between these is that human users control EOAs - because they can control the private keys which give control over an EOA. Contract accounts, on the other hand, are governed by their internal code. If they are "controlled" by a human user, it is because they are *programmed* to be controlled by an EOA with a certain address, which is in turn controlled by whoever holds the private keys that control that EOA. The popular term "smart contracts" refers to code in a Contract Account – programs that execute when a transaction is sent to that account. Users can create new contracts by deploying code to the blockchain.

Contract accounts only perform an operation when instructed to do so by an EOA. So it is not possible for a Contract account to be performing native operations like random number generation or API calls – it can do these things only if prompted by an EOA. This is because Ethereum requires nodes to be able to agree on the outcome of computation, which requires a guarantee of strictly deterministic execution.

Like in Bitcoin, users must pay small transaction fees to the network. This protects the Ethereum blockchain from frivolous or malicious computational tasks, like DDoS attacks or infinite loops. The sender of a transaction must pay for each step of the "program" they activated, including computation and memory storage.  These fees are paid in amounts of Ethereum's native value-token, ether.

These transaction fees are collected by the nodes that validate the network. These "miners" are nodes in the Ethereum network that receive, propagate, verify, and execute transactions. The miners then group the transactions – which include many updates to the "state" of accounts in the Ethereum blockchain – into what are called "blocks", and miners then compete with one another for *their* block to be the next one to be added to the blockchain. Miners are rewarded with ether for each successful block they mine. This provides the economic incentive for people to dedicate hardware and electricity to the Ethereum network.

Just as in the Bitcoin network, miners are tasked with solving a complex mathematical problem in order to successfully "mine" a block. This is known as a "Proof of Work". Any computational problem that requires orders of magnitude more resources to solve algorithmically than it takes to verify the solution is a good candidate for proof of work. In order to discourage centralisation due to the use of specialised hardware (e.g. ASICs), as has occurred in the Bitcoin network, Ethereum chose a memory-hard computational problem. If the problem requires memory as well as CPU, the ideal hardware is in fact the general computer. This makes Ethereum's Proof of Work ASIC-resistant, allowing a more decentralized distribution of security than blockchains whose mining is dominated by specialized hardware, like Bitcoin.


学习以太坊
==============================

[待续]

PR videos with some pathos:
---------------------------------

* `Ethereum: the World Computer <https://www.youtube.com/watch?v=j23HnORQXvs>`_
* `Ethereum -- your turn <https://vimeo.com/88959651>`_


Blockchain and Ethereum 101
----------------------------------

* `Explain bitcoin like I'm five <https://medium.com/@nik5ter/explain-bitcoin-like-im-five-73b4257ac833>`_ - an excellent introduction to blockchain technology and bitcoin to the mildly techsavvy layperson.
* https://medium.com/@creole/7-a-simple-view-of-ethereum-e276f76c980b
* http://blog.chain.com/post/92660909216/explaining-ethereum

* `Explain Ethereum to non-technical people Q&A on stackexchange <http://ethereum.stackexchange.com/questions/45/how-would-i-explain-ethereum-to-a-non-technical-friend>`_
* Reddit threads on ELI5-ing Ethereum:

`[1] <https://www.reddit.com/r/ethereum/comments/43brik/explaining_ethereum_to_friends/>`_
`[2] <https://www.reddit.com/r/ethereum/comments/3c132d/eli5_what_you_guys_do_here/>`_
`[3] <https://www.reddit.com/r/ethereum/comments/1vvz13/eli5_ethereum/>`_
`[4] <https://www.reddit.com/r/ethereum/comments/1vb1gc/is_ethereum_an_alt_coin_can_anyone_eli5/>`_
`[5] <https://www.reddit.com/r/ethereum/comments/4279dh/eli5_what_exactly_is_ethereum/>`_
`[6] <https://www.reddit.com/r/ethereum/comments/2hl10p/eli5_ethereum/>`_
`[7] <https://www.reddit.com/r/ethereum/comments/41y8by/the_best_way_i_can_eli5_ethereum_to_someone/>`_
`[8] <https://www.reddit.com/r/ethereum/comments/44b69e/i_dont_understand_the_technology/>`_
`[9] <https://medium.com/@nik5ter/explain-bitcoin-like-im-five-73b4257ac833>`_
`[10] <https://www.reddit.com/r/ethereum/comments/1vb1gc/is_ethereum_an_alt_coin_can_anyone_eli5/>`_
`[11] <https://www.reddit.com/r/ethereum/comments/2dpgwy/eli5_ethereum/>`_
`[12] <https://www.reddit.com/r/ethereum/comments/47u5y9/explain_what_ethereum_is_to_a_bitcoin_trader/>`_
`[13] <https://www.reddit.com/r/ethereum/comments/27wsgq/eli5_ethereum_its_uses_its_features_its_future/>`_
`[14] <https://www.reddit.com/r/ethereum/comments/4936d3/are_you_new_to_ethereum_here_are_many/>`_
`[15] <https://www.reddit.com/r/ethereum/comments/4279dh/eli5_what_exactly_is_ethereum/>`_
`[16] <https://www.reddit.com/r/ethereum/comments/3n37dp/explaining_ethereum_ecosystem_for_normal/>`_
`[17] <https://www.reddit.com/r/ethereum/comments/271qdz/can_someone_explain_the_concept_of_gas_in_ethereum/>`_
`[18] <https://www.reddit.com/r/ethereum/comments/3hg7id/why_should_the_average_person_care_about_ethereum/>`_
`[19] <https://www.reddit.com/r/ethereum/comments/43exre/what_are_the_advantages_of_ethereum_over_other/>`_


Videos
----------------------

* http://change.is/video/ethereum-the-world-computer-featuring-dr-gavin-wood

Infographics
--------------------------------

* `Ethereum explained...[to your mother] <https://blog.ethereum.org/wp-content/uploads/2015/06/Ethereum-image-infographic-beginners-guide.png>`_
* http://decentral.ca/wp-content/uploads/2016/03/infographic.jpg
* https://medium.com/@angelomilan/ethereum-explained-to-my-mom-infographic-673e32054c1c#.n9kzhme6v


Comparison to alternatives
---------------------------------

* `NXT <https://www.reddit.com/r/ethereum/comments/23aejv/eli5_what_is_the_qnce_between_ethereum_and/>`_
* `MaidSafe <https://www.reddit.com/r/ethereum/comments/22r49u/how_is_maidsafe_different_then_etherium/>`_
