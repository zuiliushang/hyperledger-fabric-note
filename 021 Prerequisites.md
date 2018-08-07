# 021 Prerequisites

在开始之前，如果你已经完成了，你可能只是想要检查你的prerequisites是否已经安装在你操作Fabric来开发区块链应用的平台上。

## Install cURL

下载最新(latest)版本的```cURL```工具如果不存在或者运行文档中的curl命令时候出错。

>> 注意:如果你是用Windows要查看下特别的注意事项。

## Docker 和 Docker Compose

你需要根据下文来安装软件到你要操作或者开发Hyperledger Fabric的平台:

- MacOSX, *nix,or Windows 10: Docker version 17.06.2-ce 或者如果需要的话安装更好的.
- 更老的windows版本: Docker Toolbox , Docker version 17.06.2-ce或者需要的话安装更好的。

可以检查下你已经安装的Docker版本使用一下命令到一个终端提示：

<pre>
docker --version
</pre>

>> 注意: Mac或者Windows或者Docker Toolbox安装的Docker同样将会安装Docker Compose。如果你已经安装了Docker，你需要检查你已经安装的Docker Compose版本是否是1.14.0或者更新的。如果不是，建议安装更近的Docker版本.

可以使用一下命令在终端提示中检测安装的Docker Compose版本：

<pre>
docker-compose --version
</pre>

## Go编程语言

Hyperledger Fabric 使用Go变成语言来编写大量组件:

- 需要Go版本在1.10.x

鉴于我们想要使用Go来编写chaincode程序。这里有两种环境需要设置行；你可以把这些设置放在合适的启动文件中，比如你个人的```~/.bashrc```文件如果你使用```bash```脚本在linux之上。

首先，你需要设置环境变量```GOPATH```来标记Go的工作目录包括下载的Fabric代码，像这样:

<pre>
export GOPATH=$HOME/go
</pre>

