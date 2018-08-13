#Hyperledger Fabric 模型

这个章节主要简述了Hyperledger Fabric履行其全面的、可定制的企业区块链解决方案的承诺的关键设计功能:

- Assets —— 资产是指可以通过网络使用货币来交易几乎所有的东西，从全食超市到古董车到货币期货。
- Chaincode —— chaincode执行是由交易顺序划分的，限制需求的信任等级和验证通过的节点类型，并有最佳的网络伸缩性和性能。
- Ledger Features —— 不可变的，共享的ledger对每个通道的整个交易历史进行编码，并包含类似sql的查询功能，用于有效的审计和纠纷解决。
- Privacy —— 通道和隐私数据集合云溪私有的和独立的多方向的事物来通常允许有竞争性的企业和在公共网络上交换资产的受监管行业。
- Security & Membership Service —— 共有的身份验证提供一个可信的区块链网络，网络中的参与者可以知道所有的交易都可以被授权监管机构和审计机关追踪。
- Consensus —— 一个唯一的方式达成共识支持企业所需的灵活性和可伸缩性。

## Assets

Assets可以包括真实的（资产或者硬件）到虚拟的（合同和知识产权）。Hyperledger Fabric提供一个能力使用chaincode transaction来重定义资产.

Assets在Hyperledger Fabric代表为一个key-value对的集合,并且状态改变记录为交易存放在一个Channel ledger。Asset可以用为二进制或者JSON表示。

可以在Hyperledger Fabric使用Hyperledger Composer tool应用来特制和使用资产。

## Chaincode

chaincode是定义一个资产(asset)或者多个资产的软件，以及修改资产的交易指令；换句话说，chaincode就是业务逻辑。chaincode强制执行读取或者修改键值对或者其它状态数据库信息的规则。chaincode方法执行针对ledger当前状态数据库并且通过一个交易提案发起。Chaincode执行结果在一个键值对的写（写集合），它可以提交到网络并被所有的对等点的ledger所接受。

## Ledger 功能

