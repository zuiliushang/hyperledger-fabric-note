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

>> 注意：必须设置GOPATH变量。
>> 在linux中 ，Go的GOPATH变量可以是一个冒号分隔的目录列表，如果未设置，则使用默认值$HOME/ Go，当前Fabric构建框架仍然需要设置并导出该变量，它必须包含Go工作空间的单个目录名。（这个限制可能在将来的版本中被删除。）

第二步，你需要(同样，可以设置在变量启动文件中)扩展命令搜索路径，以包含Go的bin目录。例如下面在linux中使用```bash```的例子:
<pre>
export PATH=$PATH:$GOPATH/bin
</pre>

虽然这个目录可能在新安装的GO工作目录下不存在，但是后面Fabric构建系统的时候会使用一些Go可执行文件来填充（这些文件提供其他构建系统使用）。因此，即使目前还没有这样的目录，也可以像上面那样扩展shell搜索路径。

## Node.js 运行和NPM

如果你要开发Hyperledge Fabric应用通过使用 Hyperledger Fabric SDK for Node.js,你需要有version 8.9.x的Node.js。

>> 注意： Node.js 9.x版本目前不支持<br> - Node.js version 8.9.x或者更好。

>> 注意：安装Node.js也要安装NPM，得检查下要求的NPM版本是否安装，可以根据下面命令来更新```npm```工具:

<pre>
npm install npm@5.6.0 -g
</pre>

## Python

>> 注意: 下面命令是在Ubuntu 16.04的用户,其他系统自行更新

默认Ubuntu 16.04有安装Python 3.5.1作为```python3```二进制执行文件。Fabric Node.js SDK需要Python2.7跌倒并需要```npm install```操作来完成。用下面命令恢复到2.7版本:

<pre>
sudo apt-get install python
</pre>

检查你的版本:

<pre>
python --version
</pre>

## Windows

略