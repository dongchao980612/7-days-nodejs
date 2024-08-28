# NodeJS基础

## 什么是NodeJS

JS是脚本语言，脚本语言都需要一个解析器才能运行。对于写在HTML页面里的JS，浏览器充当了解析器的角色。而对于需要独立运行的JS，NodeJS就是一个解析器。

每一种解析器都是一个运行环境，不但允许JS定义各种数据结构，进行各种计算，还允许JS使用运行环境提供的内置对象和方法做一些事情。例如运行在浏览器中的JS的用途是操作DOM，浏览器就提供了document之类的内置对象。而运行在NodeJS中的JS的用途是操作磁盘文件或搭建HTTP服务器，NodeJS就相应提供了fs、http等内置对象。

## 有啥用处

尽管存在一听说可以直接运行JS文件就觉得很酷的同学，但大多数同学在接触新东西时首先关心的是有啥用处，以及能带来啥价值。

NodeJS的作者说，他创造NodeJS的目的是为了实现高性能Web服务器，他首先看重的是事件机制和异步IO模型的优越性，而不是JS。但是他需要选择一种编程语言实现他的想法，这种编程语言不能自带IO功能，并且需要能良好支持事件机制。JS没有自带IO功能，天生就用于处理浏览器中的DOM事件，并且拥有一大群程序员，因此就成为了天然的选择。

如他所愿，NodeJS在服务端活跃起来，出现了大批基于NodeJS的Web服务。而另一方面，NodeJS让前端众如获神器，终于可以让自己的能力覆盖范围跳出浏览器窗口，更大批的前端工具如雨后春笋。

因此，对于前端而言，虽然不是人人都要拿NodeJS写一个服务器程序，但简单可至使用命令交互模式调试JS代码片段，复杂可至编写工具提升工作效率。

NodeJS生态圈正欣欣向荣。

## 如何安装

### 安装程序

NodeJS提供了一些安装程序，都可以在nodejs.org这里下载并安装。

Windows系统下，选择和系统版本匹配的.msi后缀的安装文件。Mac OS X系统下，选择.pkg后缀的安装文件。

### 编译安装

Linux系统下没有现成的安装程序可用，虽然一些发行版可以使用apt-get之类的方式安装，但不一定能安装到最新版。因此Linux系统下一般使用以下方式编译方式安装NodeJS。

确保系统下g++版本在4.6以上，python版本在2.6以上。

从[nodejs.org](https://nodejs.org/zh-cn)下载tar.gz后缀的NodeJS最新版源代码包并解压到某个位置。

进入解压到的目录，使用以下命令编译和安装。

```sh
./configure
make
make install $ ./configure
make
sudo make install
```

## 如何运行

打开终端，键入node进入命令交互模式，可以输入一条代码语句后立即执行并显示结果，例如：

```js
node
console.log('Hello World!');
Hello World!
```

如果要运行一大段代码的话，可以先写一个JS文件再运行。例如有以下`hello.js`。

```js
function hello() {
    console.log('Hello World!');
}
hello();
```

写好后在终端下键入`node hello.js`运行，结果如下：

```sh
$node hello.js
Hello World!
```

### 权限问题

在Linux系统下，使用NodeJS监听80或443端口提供HTTP(S)服务时需要root权限，有两种方式可以做到。

一种方式是使用`sudo`命令运行NodeJS。例如通过以下命令运行的`server.js`中有权限使用80和443端口。一般推荐这种方式，可以保证仅为有需要的JS脚本提供root权限。

```sh
sudo node server.js
```

另一种方式是使用`chmod +s`命令让NodeJS总是以root权限运行，具体做法如下。因为这种方式让任何JS脚本都有了root权限，不太安全，因此在需要很考虑安全的系统下不推荐使用。

``sh
sudo chown root /usr/local/bin/node
sudo chmod +s /usr/local/bin/node
```

