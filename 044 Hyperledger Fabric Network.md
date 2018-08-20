# Hyperledger Fabric Network

## Fabric网络是什么?

一个Fabric公有链网络是一个技术架构来为应用程序的使用者和管理员提供ledger服务。大部分情况下，多数组织呆一起作为一个集团来形成一个网络并且他们的权限通过一系列的规则决定。（这些规则在最初配置网络时，由联合体同意。）。还有，网络策略可以在联合体的组织同意下随着时间改变。

文档将了解组织需要作出的配置和发布一个Hyperledger Fabric网络的策略，在网络中形成交易渠道，并如何更新这些决定在整个网络生命周期中。也可以学到这些策略如何嵌入架构和Hyperledger Fabric组件。

## 谁需要阅读?

这个主题，集中在网络中的重要组件，为什么他们存在并说明时候使用他们。主题专门为区块链设计和区块链网络管理员准备的。开发者有兴趣也可以看。由于这是一个概念性的文档，如果想深入了解技术细节，我们鼓励查看这个站点上可用的技术文档。

## 区块链网络业务需求例子

有组织 RA,RB,RC和RD共同投资加入一个Fabric区块链网络。组织RA贡献3个peer并且RA的2个客户端应用程序将会消费区块链网络的服务。组织RB贡献4个peer并且有1个客户端程序。RC有3个peer，2个客户端程序。RD4个orderer。RA和RB决组成一个联盟，在他们之间开发一个单独的应用渠道。RB和RC决定组成另外的联盟并在它们2个钟同样来开发一个独立的应用通道。每个应用通道有他们的规则。

## 网路中的组件

一个网路组成由:

- Ledgers(每个通道一个——由区块链和状态数据库组成)
- 智能合约(又称为chaincode)
- peer节点
- Ordering service
- Channel
- Fabric Certificate Authorities

### 网络服务中的消费者

- 组织中拥有的客户端应用程序
- 区块链管理员的客户端

### 网络规则和身份

Fabric证书认证(CA)颁发证书给组织，让组织在网络中进行身份认证。在网络中可以有一个或者多个CA并且组织可以选择使用他们自己的CA。此外，组织拥有的客户端应用程序在联盟中使用证书来认证交易提案，并且peer使用他们来批准提案，如果交易有效，就把它们提交到ledger上。

解释如下图：有一个Fabric网络N有一个网络策略NP1和排序服务O。通道C1被通道策略CP1管理。通道C1由RARB联盟建立。通道C1通过ordering service O管理并且peer P1和 P2还有客户端应用程序A1 A2已经在C1中被认证允许交易。客户端A1由组织RA拥有。证书认证CA1服务于组织RA。peer P2的目标ledger L1与通道C1相关联，L2的是C2。Peer P2利用chaincode S4和S5。ordering service O中的orderer节点属于组织RD。

![](https://hyperledger-fabric.readthedocs.io/en/release-1.2/_images/network.diagram.1_1.png)

## 创建网络

网络是由联盟定义创建的包括它的客户端，peer，通道和ordering service。ordering service是网络的管理端点因为它包括网络中间通道的配置。每个通道的配置包括通道的政策和每个通道中的用户的会员信息(在这个例子 X509 是根证书)。

![](https://hyperledger-fabric.readthedocs.io/en/release-1.2/_images/network.diagram.2.png)

## 定义一个联盟

一个联盟由两个或者更多的网络中的组织组成。联盟通过相互进行业务交易的组织定义的，它们必须同意管理网络的策略。

![](https://hyperledger-fabric.readthedocs.io/en/release-1.2/_images/network.diagram.3.png)

## 创建一个联盟上的通道

一个通道是一个交流的地方用来连接网络中的组件和/或用户客户端应用程序。通道通过排序服务来生成配置区块生成(通过评估通道配置的有效性)。通道很有用因为他们允许数据隔离和保密。交易组织必须通过身份验证才能与通道进行交互。通道被他们所配置的策略所管理。
![](https://hyperledger-fabric.readthedocs.io/en/release-1.2/_images/network.diagram.4.png)

## Peer和Channel

Peer加入通道并属于拥有它们的组织。并且在网络中可以有大量的peer节点在通道中。Peer可以承担多种角色:

- Endorsing peer - 通过策略定义作为一种特别的节点来模仿执行职能合约交易并返回给客户端应用一个提案响应(endorsement)。
- Committing peer -验证顺序区块交易和提交(写/拼接)区块到ledger的拷贝中。

因为每个通道中所有的peer目的是他们加入的ledger的拷贝，所有的peer都是committing peer。然而，仅通过只能合约的背书策略指定的peer才能是endorsing peer。一个peer可以由一下规则进一步定义:

- Anchor peer - 在通道配置中定义并且是最先字网络中被其他加入同一个通道的组织发现的peer.
- Leading peer - 存在于网络上，代表具有多个peer的组织与订购服务进行通信。

![](https://hyperledger-fabric.readthedocs.io/en/release-1.2/_images/network.diagram.5.png)

## 应用程序和智能合约

为了让客户机应用程序能够调用智能契约，智能合约chaincode必须在一个peer被安装和实例化。客户端应用程序是网络外面唯一生成交易提案的地方。当一个交易通过一个客户端程序被提案，智能合约会在endorsing peer中调用，这些peer模仿智能合约对齐ledger的备份执行并发送提案响应(endorsement)给客户端应用程序。客户端应用程序组装这些响应到一个交易并且广播到ordering service。

![](https://hyperledger-fabric.readthedocs.io/en/release-1.2/_images/network.diagram.6.png)

## 网络增长(growing the network)

虽然对于网络能够达到的大小没有理论上的限制，但是随着网络的增长，考虑有助于优化网络吞吐量、稳定性和弹性的设计选择是很重要的。
![](https://hyperledger-fabric.readthedocs.io/en/release-1.2/_images/network.diagram.7.png)

## 简约图如下

在下图我们可以看到有2个客户端应用程序连接2个peer节点还有一个ordering service在一个通道里。因为只有一个通道，所以在例子这里只有一个逻辑上的ledger。就像这个单一通道的情况一样，P1 和 P2有一个ledger的拷贝(L1)和一个智能合约 —— 又名 chaincode(S4).

![](https://hyperledger-fabric.readthedocs.io/en/release-1.2/_images/network.diagram.8.png)

## 添加另外一个联盟定义

当一个联盟被定义和添加到存在的通道时，我们必须更新通道配置通过发送一个通道配置更新交易到ordering service。如果交易是验证的，ordering service将会生成一个新的配置区块。网络中的peer下一步会验证ordering service所生成的新的通道配置区块并更新他们的通道配置如果他们验证新的区块的话。重点要注意通道配置更新交易(channel configuration update transaction)是被区块链网络管理员调用的system chaincode处理，并且它不能被客户端应用程序交易提案所执行(client application transaction proposals)。

![](https://hyperledger-fabric.readthedocs.io/en/release-1.2/_images/network.diagram.9.png)

## 添加一个新通道

组织是什么形式和连接渠道，渠道配置可以修改，以添加组织随着网络的增长。