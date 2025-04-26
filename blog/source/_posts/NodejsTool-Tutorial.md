---
title: 记录这一段时间了解的node.js工具,做一个总结
categories:
  - 前端开发
tags:
  - node.js
---
Ciallo～(∠・ω < )⌒★众所周知,Node.js 是一个开源的、跨平台的 JavaScript 运行时环境,简单来讲就是一个js运行环境，一个软件，本文将对node.js工具进行相关介绍与使用,帮助你更好的使用node.js
## 工具概述:
- [nrm](#nrm)
- [nvm](#nvm)
- [volta](#volta)
## 工具的安装与使用

### nrm
**介绍：nrm 的全称是 npm registry manager ，是一个 npm 的镜像源管理工具**
#### 安装
**前提是你已经安装了node.js,如果没有安装那就看[nvm](#nvm)这节,[volta](#volta)这节也行,更傻瓜式,安装完之后再来安装nrm**
___
##### 安装nvm 
首先按快捷键Win+R打开运行窗口，再输入cmd回车
然后我们全局安装一下nrm
``` bash
npm i nrm -g
```
接着查看一下版本号，看是否安装成功，如果输出版本号代表安装成功
``` bash
nrm -V
```
#### 使用
##### 查看镜像源
**查看所有可用镜像源**
```bash
nrm ls
```
结果如下:
```md
* npm ---------- https://registry.npmjs.org/
  yarn --------- https://registry.yarnpkg.com/
  tencent ------ https://mirrors.tencent.com/npm/
  cnpm --------- https://r.cnpmjs.org/
  taobao ------- https://registry.npmmirror.com/
  npmMirror ---- https://skimdb.npmjs.com/registry/
  huawei ------- https://repo.huaweicloud.com/repository/npm/
```
##### 切换镜像源
这里就比如说我要切换淘宝的镜像源，就是这样,其余同理
```bash
nrm use taobao
```
### nvm
**介绍：nvm 允许您通过命令行快速安装和使用不同版本的 node**

#### 安装
**前提是你电脑没有安装node.js,如果有那就把node.js卸载再安装nvm,这里我推荐一个工具:[点击下载工具](/downloads/GeekUninstaller_v1.5.1.162单文件版.exe)   
如果已经卸载了，但没有卸载干净可以看看以下文件夹及文件是否存在，如果存在就删除这些文件夹及文件，还有环境变量里面关于node和npm的都删掉**
* C:\Program Files (x86)\Nodejs
* C:\Program Files\Nodejs
* C:\Users\用户名\AppData\Roaming\npm
* C:\Users\用户名\AppData\Roaming\npm-cache
* 删除C:\Users\用户名 下的 .npmrc文件以及 .yarnrc 文件
___
**下面是手动安装配置的教程，如果嫌麻烦可以用客户端进行可视化操作，客户端下载地址:[nvm-desktop](https://github.com/1111mp/nvm-desktop/releases/tag/v4.0.7)，直接无脑安装即可,
如果是国内再把镜像地址换成淘宝镜像进行加速，如果安装了node.js没生效可以重启一下**
```md
https://npmmirror.com/mirrors/node/
```
![](/images/nvm17.png)
___
**手动安装配置教程如下:**
##### 下载nvm包
首先到github下载nvm,地址：[nvm下载](https://github.com/coreybutler/nvm-windows/releases/tag/1.2.2)
然后这两个二选一
![](/images/nvm.png)
##### 安装nvm
下载下来接着进行安装,(注：这里不建议放在c盘，D盘或者E盘都可以的且路径不能有中文或空格)
![](/images/nvm2.png)
这里是`nvm安装路径`，配置好了之后直接点Next
![](/images/nvm3.png)
这里是`node.js安装路径`,配置好了之后直接点Next
![](/images/nvm4.png)
全部下一步即可,然后我们就完成安装了，接下来配置下载镜像
![](/images/nvm5.png)
![](/images/nvm6.png)
![](/images/nvm7.png)
##### 配置下载镜像
找到你nvm的安装目录，然后找到`settings.txt`这个文件
接着填写两段代码即可
```md
node_mirror: https://npmmirror.com/mirrors/node/
npm_mirror: https://npmmirror.com/mirrors/npm/
```
![](/images/nvm8.png)
![](/images/nvm9.png)
##### 指定全局安装目录和缓存目录
为了让全局安装的包在切换版本之后依旧能够使用，我们得指定一下`全局安装目录`和`缓存目录`，让所有node.js版本都能使用这些包
 **一定要先看[使用](#使用-1),用nvm安装一个node.js,再来配置环境变量**
___                
首先找到你nodejs的安装目录,然后在nodejs文件夹里新建`node_global`和`node_cache`这两个文件夹
![](/images/nvm11.png)
接着按快捷键Win+R打开运行窗口，再输入cmd回车
* 输入你的node安装目录\node_global
```bash
npm config set prefix "E:\nvm\nodejs\node_global"
```
* 输入你的node安装目录\node_cache
```bash
npm config set cache "E:\nvm\nodejs\node_cache"
```
再输入这两行命令,如果输出了路径代表配置成功
```bash
npm config get prefix
npm config get cache
```
#### 使用
##### 查看可安装的node版本
``` bash
nvm list available
```
![](/images/nvm12.png)
##### 安装node.js
首先按快捷键Win+R打开运行窗口，再输入cmd回车
这里就比如说我要安装20.19.0的node.js(默认推荐`lts`版本的)，就是这样,其余同理
``` bash
nvm install 20.19.0
```
![](/images/nvm13.png)
然后你就可以使用你下载下来的node.js
``` bash
nvm use 20.19.0
```
![](/images/nvm14.png)
接着查看node版本号和npm版本号,如果输出版本号代表安装成功
``` bash
node -v #查看node版本
npm -v #查看npm版本
```
![](/images/nvm15.png)
##### 查看已安装的node版本
`*`代表正在使用
```bash
nvm ls
```
![](/images/nvm16.png)
##### 卸载已安装的node版本
这里就比如说我要卸载20.19.0的node版本，就是这样,其余同理
```bash
nvm uninstall 20.19.0
```
### volta
**介绍：volta可以轻松切换项目，无需手动切换 Node，更傻瓜式**
* **`volta`和`nvm`的对比表**
![](/images/volta.png)
#### 安装
首先按快捷键Win+R打开运行窗口，再输入cmd回车
```bash
winget install Volta.Volta
```
![](/images/volta2.png)
如果安装不下来，也有msi安装包可以安装,地址：[volta下载](https://github.com/volta-cli/volta/releases/tag/v2.0.2)
![](/images/volta3.png)
#### 使用
##### 安装node.js
比如说我要下载20.19.0版本的node就是这样
```bash
 volta install node@20.19.0
```
* 安装最新`lts`版本的node
```bash
 volta install node
```
* 安装最新版本的node
```bash
 volta install node@latest
```
##### 项目固定node版本和包管理器版本
* 固定node版本
```bash
 volta pin node@20.19.0
```
* 固定包管理器版本，这里我举例的是npm
```bash
 volta pin npm@10.8.2
```
![](/images/volta4.png)
然后就会自动在package.json创建配置项，它就会自动切换版本了
![](/images/volta5.png)
##### 查看所有已安装工具版本
首先按快捷键Win+R打开运行窗口，再输入cmd回车
输入这行命令
```bash
volta list all
```
![](/images/volta6.png)
* 查看已安装node版本
如果你只想查看已安装的node版本就是这样
`default`代表默认node版本
```bash
volta list node
```
![](/images/volta7.png)
##### 卸载已安装node版本
卸载已安装node版本,volta只支持卸载默认node版本，如果你想卸载的版本不是默认版本，可以把node版本切换为默认版本之后再卸载
* 切换默认node版本
这里就比如说我要切换20.19.0版本为默认版本，就是这样
```bash
volta pin node@20.19.0 --global
```
然后就可以卸载了
* 卸载node版本
这里就比如说我要卸载20.19.0的node版本，就是这样
```bash
volta uninstall node@20.19.0
```

