# 介绍

Hyperledger Fabric是一个用于分布式账本解决方案的平台，其基础是提供高度机密性、弹性、灵活性和可伸缩性的模块化架构。设计支持不同组件插入式的实现和适应经济生态系统中存在的复杂性。

我们建议初次用户从下面的介绍开始，以便熟悉区块链是如何工作的，以及Hyperledger Fabric的特定特性和组件。

如果你已经熟悉了区块链和Hyperledger Fabric 去看 Getting Started并且从那里探索演示、技术规范、api等。

## 什么是区块链？

### 一个分布式账本

在区块链网络中心是一个分布式账本来记录所有在网络上发生的交易。

一个区块链账本通常是分散管理的因为它的复制是通过大量网络参与者，每个参与者都在维护工作中相互配合。我们将会看到分散管理和合作是有力量的属性，它反映了企业在现实世界中交换商品和服务的方式。

![](https://i.imgur.com/uZgk9Qd.png)

除了是分散管理和相互配置之外，信息记录到一个blockchain是只追加的，使用密码技术来确保一旦事务被添加到分类帐中，它就不能被修改。这个“不可变”属性使得确定信息的来源变得很简单，因为参与者可以确定信息在事后没有被更改。这就是为什么区块链有时候描述为证明系统。

### Smart Contracts

为了支持信息的一致更新 —— 并支持所有分类函数(事务处理、查询等) —— 一个区块链网络使用 smart contracts 来提供控制访问账本。

![](https://hyperledger-fabric.readthedocs.io/en/release-1.2/_images/Smart_Contract.png)

智能合约(smart contract)不仅仅是一个关键因素来封装信息并且在整个网络中保持单一，它们也可以被编写成允许参与者自动执行交易的某些方面。

比如，一份smart contract可以规定货物的运输成本，运费取决于货物到达的速度。根据双方同意并记入分类帐的条款，当物品收到时，相应的资金自动易手。

### 共识

通过网络保持账本交易同步的处理 —— 确保账本仅在交易被合适的参与者认可时被接受，并且当账本执行更新，他们以相同的交易和相同的顺序进行更新 —— 这个称为共识。

![](https://hyperledger-fabric.readthedocs.io/en/release-1.2/_images/consensus.png)

在接下来你将学到更多关于账本，智能合约和共识。现在，可以认为区块链是作为一个共享的，复制的通过智能合约和通过一种称为共识的协作方式保持一致性同步进行更新的交易系统。

## 为什么区块链有用？

### 当今系统记录 Today’s Systems of Record

当今交易型网络不过是自保留业务记录以来已经存在的网络的略微更新的版本。业务网络的每个成员互相交易，但是他们保持各自的交易记录。他们交易的物品——无论是16世纪的佛兰德挂毯还是今天的证券——每次出售时都必须确定其出处，以确保出售物品的企业拥有一系列产权，以证明其所有权。

以下就是这样的一个网络:

![](https://hyperledger-fabric.readthedocs.io/en/release-1.2/_images/current_network.png)

现代科技已经将这一过程从平板电脑和纸质文件夹发展到硬盘和云平台，但是底层的结构是一样的。不存在统一的管理网络参与者身份的系统，建立出处是如此的费力，以至于需要几天的时间才能完成证券交易(全球交易量以数万亿美元计)，合同必须收工签署和执行，并且系统中的每个数据库都包含唯一的信息，因此会有单点故障。

如今，信息和流程共享的方式支离破碎，要建立一个跨越业务网络的记录系统是不可能的，尽管可见性和信任的需求是明确的。

### 区块链则不同

如果业务网络不再是“现代”事务系统所代表的低效之巢，而是拥有在网络上建立身份、执行事务和存储数据的标准方法，那该怎么办?如果可以通过查看一组事务来确定资产的来源，这些事务一旦被写入，就不能更改，因此可以信任，那么该怎么办呢?

这个业务网络看起来更像这样:

![](https://hyperledger-fabric.readthedocs.io/en/release-1.2/_images/future_net.png)

这个是一个区块链网络，在这儿每个参与者都拥有他们自己的一份账本备份。除了账本信息共享，处理更新账本也会共享。不像现代系统，他们的参与者的私有程序被用来更新他们私有的账本，一个区块链系统是共享程序更新账本的。

借助通过共享分类帐协调业务网络的能力，区块链网络可以减少与私有信息和处理相关的时间、成本和风险，同时提高信任和可见性。

你现在可以知道区块链是什么还有为什么他有用了吧。还有很多其他重要的细节，但它们都与共享信息和流程的基本思想有关。

## 什么是Hyperledger Fabric?

Linux基金会在2015年建立Hyperledger项目来推行跨行业区块链技术。它不是宣布一个单一的区块链标准，而是鼓励通过社区过程协作开发区块链技术，并拥有鼓励开放开发和随着时间推移采用关键标准的知识产权。

Hyperledger Fabric 是Hyperledger的其中一个区块链项目。和其他区块链技术一样，它有一个账本，使用智能合约，并且是一个参与者管理自己的交易的系统。

Hyperledger Fabric 区别于其他区块链在于它是private 和 permissioned。而不是一个开放的非许可的系统允许未知身份在网络中参与（需要“工作证明”之类的协议来验证事务并保护网络），超分类帐织物网络的成员通过可信的会员服务提供商(MSP)注册。

Hyperledger Fabric同样提供几个可插入选项。Ledger数据可以被存储在多个标准化，协商一致的机制可以交换进来和出去，并且支持不同的MSP。

Hyperledger Fabric 也提供创建channel的功能来允许一组参与者来分开创建ledger的交易。这是一个尤其重要的关于在网络一些参与者可能是竞争者或者不想任何的它们造成的交易——一个特别的价钱指定给一些参与者，例如——知道每个参与者。如果两个参与者来自同一个channel，那么其他的参与者没人能copy关于这个channel的ledger。

### 共享的Ledger

Hyperledger Fabric有一个ledger子系统包括两个部分：world state和transaction log.每个参与者都有一个它们所属的Hyperledger Fabric网络的ledger拷贝。

world state组件描述ledger的状态在给定一个时间点。这是ledger的数据库。transaction log组件记录所有的导致world state产生作用的交易。

ledger有一个可代替的关于world状态的数据存储。默认，这是一个LevelDB键值存储数据。交易日志不需要是插件式的。它只记录区块链网络使用的分类数据库的前后值。

### 智能合约

Hyperledger Fabric智能合约是由chaincode编写并且通过区块链外部程序调用当这个应用需要和ledger交互。在大多数情况下,chaincode仅和分账数据库,world状态(例如查询它)交互，不和transaction log.

Chaincode可以通过多种编程语言来实现。现阶段,Go和Node都支持了。

### 隐私

根据网关的需要，企业对企业(B2B)网络的参与者可能对他们共享的信息非常敏感。对于其他网络来说，隐私可能不是首要问题。

Hyperledger Fabric支持网络隐私(使用通道)是一个关键的操作需求，以及相对开放的网络。

### 共识

交易必须被写到ledger中以他们发生的顺序，甚至他们可能在多个网络中不同的参与者之中。为了实现这个目标，交易的顺序必须是既定的并且必须采用一种方法来拒绝错误地(或恶意地)插入到分类账中的不良交易。

这是一个深入研究计算机科学的领域，并且有很多种方式来实现它，每种都有不同的权衡。例如，PBFT(Practical Byzantine Fault Tolerance实际拜占庭容错)可以提供一种机制，让文件副本相互通信，以保持每个副本的一致性。或者，在比特币中，排序是通过一种被称为“挖掘”的过程进行的，在这种过程中，相互竞争的计算机竞相解决一个密码难题，这个难题定义了所有进程随后所建立的顺序。

Hyperledger Fabric已经被设计来允许网络初学者选择一个最能代表参与者之间存在关系的共识机制。和隐私一样，这里也有不同的需求；从关系高度结构化的网络到更对等的网络。

