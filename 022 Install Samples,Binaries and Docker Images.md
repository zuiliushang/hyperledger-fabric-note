# Install Samples, Binaries and Docker Images

我们在开发真正的Hyperledger Fabric二进制安装文件时，我们提供一个脚本来下载和安装示例和二进制文件在你的系统。我们认为，您会发现安装的示例应用程序对了解Hyperledger Fabric的功能和操作是有用的。

>> 注意:如果您在Windows上运行，您将希望使用Docker Quickstart终端来执行即将到来的终端命令。如果您之前没有安装，请访问先决条件。<br><br>如果在Windows7或者macOS中使用Docker Toolbox,需要使用```C:\Users```（Windows 7）或者```/Users```(macOS)的位置来安装和运行例子。<br><br>如果使用Mac下的Docker需要```/Users```，```/Volumes```,```/private```或者```/tmp```位置。要使用不同的位置，请参阅Docker文档以共享文件。

决定一个机器的位置来放置```fabric-samples```目录并使用这个目录在window终端中。下面的命令将执行以下步骤:

1. 如果需要,clone ```hyperledger/fabric-sample```仓库。
2. checkout到合适的分支。
3. 在Fabric -samples存储库的根目录中安装指定版本的Hyperledger Fabric平台专用二进制文件和配置文件。
4. 下载指定版本的 Hyperledger Fabric docker 镜像

如果准备好了，在这个目录安装Fabric Samples和二进制文件，执行下面命令:
<pre>
curl -sSL http://bit.ly/2ysbOFE | bash -s 1.2.0
</pre>

>> 注意: 如果想要下载Fabric,Fabric-ca和第三方的Docker镜像需要通过脚本的版本身份验证。

<pre>
curl -sSL http://bit.ly/2ysbOFE | bash -s fabric fabric-ca thirdparty
curl -sSL http://bit.ly/2ysbOFE | bash -s 1.2.0 1.2.0 0.4.10
</pre>

>>注意:如果使用上面curl命令报错了，说明你的curl版本太老不支持处理重定向或不支持环境。<br><br>
>查看```Prerequisites```关于版本的信息并且重新获取对的环境。或者，你可以用未缩短的URL来代替:https://github.com/hyperledger/fabric/blob/master/scripts/bootstrap.sh


>>注意：您可以对任何已发布版本的Hyperledger Fabric使用上面的命令。只需用希望安装的版本的版本标识符替换1.2.0即可。

上面命令下载和执行一个bash脚本将下载和提取所有平台指定的你需要建立你的网络并且替换他们到你clone的库中的二进制文件。它检索下列特定于平台的二进制文件：

- cryptogen
- configtxgen
- configtxlator
- peer
- orderer
- idemixgen
- fabric-ca-client

并替换它们到```bin```下的子目录要工作的目录中。

你可能想要添加他们到你的PATH环境变量来直接取得。例如:

```
export PATH=<path to download location>/bin:$PATH
```

最后，这个脚本会从Docker Hub中下载Hyperledger Fabric docker镜像到你本地的Docker registry并标记为'latest'。

脚本列出了在结束时安装的Docker镜像。

查看每个镜像的名字；这些组件最终构成我们的Hyperledger Fabric网络平台。可以注意到有两个实例的有相同的镜像ID一个tag为"amd64-1.x.x"另一个为"latest".最早为1.2.0，镜像会被下载并通过```uname =-m```来决定和表现为"x86_64-1.x.x"。

>> 注意：

>> 在不同的功能中，x86_64/amd64可能被标识体系结构的字符串替代。

>> 有问题 https://hyperledger-fabric.readthedocs.io/en/release-1.2/questions.html
