.. _about:

***************************************
Homestead文档计划
***************************************

|Gitter|

.. |Gitter| image:: img/homestead-guide.svg
   :target: https://gitter.im/ethereum/homestead-guide?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge

目的和受众
===============================================================================

这份手册是为所有以太坊用户和开发者提供的入门级的资料。

这份手册的目标是为使用以太坊与去中心化应用（dapp）进行交互或开发一个去中心化应用提供初级和中级功能的简短流程向导和样例。

任何对于上述目标而言过于具体、技术或不必要的内容都被保留在以太坊的Github Wiki上。如有必要，会在这份手册中保留链接。

虽然很多内容在Frontier和Homestead手册里是很接近的，但还是需要很多精力去确认这里记述的内容是精确的。这份文档不是针对特定客户端的，样例和流程向导可能会涉及各个客户端，作者会根据样例/流程向导指明其所使用的客户端。

尽管过于具体和技术性的文档不会被包含在这份手册的首次迭代中，但这份手册的受欢迎程度和其社区内的使用，会在未来决定是否将Github Wiki中的文档迁移过来。

过于具体和技术型的文档包括：

* ETHash、CASPER、ABI、RLP或其他技术说明。
* 针对协议的完整的API说明。警告：如果一个样例、信息或流程指引需要参考某个客户端的API调用或者界面来完成，那么这种参考是可以接受的。但请确保你保留了链接，以便让用户可以找到可能在Github Wiki上的具体文档。

范例文档资源
===============================================================================

这里是一些先前的以太坊文档和一些范例文档。

* Solidity Docs - https://ethereum.github.io/solidity/docs/home/
* Frontier Guide - https://ethereum.gitbooks.io/frontier-guide/content/
* Gav’s TurboEthereum Guide - https://gavofyork.gitbooks.io/turboethereum/content/
* Ancient EthereumBuilder’s Guide - https://ethereumbuilders.gitbooks.io/guide/content/en/index.html
* Other Ethereum Links: https://souptacular.gitbooks.io/ethereum-tutorials-and-tips-by-hudson/content/giant_ethereum_resource_list.html
* Django Docs - https://docs.djangoproject.com/en/1.9/

文本整理标记工具 - Sphinx
=======================================

* Best Cheat Sheet - https://github.com/ralsina/rst-cheatsheet/blob/master/rst-cheatsheet.rst
* Quick Reference - http://docutils.sourceforge.net/docs/user/rst/quickref.html
* Official Cheat Sheet - http://docutils.sourceforge.net/docs/user/rst/cheatsheet.txt -> http://docutils.sourceforge.net/docs/user/rst/cheatsheet.html
* RST Primer http://sphinx-doc.org/rest.html
* http://sphinx-doc.org/markup/inline.html

编译和发布
===============================================================================

我们使用 `make` 命令的 `Makefile` 来自动生成文档结构。

.. code-block:: bash

    git clone https://github.com/ethereum/homestead-guide
    cd homestead-guide
    make html

处理技巧
===============================================================================

固定的章节换行（每行总是使用80字符长度，除了那些超过80字符的标题以外）

.. code-block:: bash

    for f in `ls source/*/*.rst`; do cat $f|perl -pe 's/\=+$/================================================================================/' > $f.o; mv $f.o $f; done; done
    for f in `ls source/*/*.rst`; do cat $f|perl -pe 's/\*+$/********************************************************************************/' > $f.o; mv $f.o $f; done
    for f in `ls source/*/*.rst`; do cat $f|perl -pe 's/\-+$/--------------------------------------------------------------------------------/' > $f.o; mv $f.o $f; done
    for f in `ls source/*/*.rst`; do cat $f|perl -pe 's/\++$/++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++/' > $f.o; mv $f.o $f; done
    for f in `ls source/*/*.rst`; do cat $f|perl -pe 's/\#+$/################################################################################/' > $f.o; mv $f.o $f; done

Referencing Old Documentation
===============================================================================

old-docs-for-reference folder has all of the Frontier Gitbook and Ethereum Wiki doc. Feel free to copy/paste information from those documents that is still relevant.

Migrate and Convert Old Wiki Content Using Pandoc
===============================================================================

If you still want to clone the absolute latest Ethereum Wiki and Frontier Guide docs:

.. code-block:: bash

    git clone git@github.com:ethereum/go-ethereum.wiki.git
    git clone git@github.com:ethereum/wiki.wiki.git

    mkdir main-wiki.rst
    mkdir go-ethereum-wiki.rst

    for f in `ls wiki.wiki/*.md`; do pandoc $f -o main-wiki.rst/`basename $f .md`.rst; done
    for f in `ls go-ethereum.wiki/*.md`; do pandoc $f -o go-ethereum-wiki.rst/`basename $f .md`.rst; done
