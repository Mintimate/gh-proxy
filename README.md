# gh-proxy

## 简介
基于项目：
- [https://github.com/hunshcn/gh-proxy](https://github.com/hunshcn/gh-proxy)

> 基于的是早期版本，可能和源项目有些不一样。

更改内容：
- 移除Docker部署、Python部署，只保留Cloudfare Worker部署
- 修改为可自定义镜像地址，方便自定义


## 演示

[https://tool.mintimate.cn/gh](https://tool.mintimate.cn/gh)

演示站为公共服务，如有大规模使用需求请自行部署，演示站有点不堪重负

![imagea272c95887343279.png](https://img.maocdn.cn/img/2021/04/24/imagea272c95887343279.png)


## 使用

直接在copy出来的url前加`https://tool.mintimate.cn/gh/`即可。

如果是自己搭建的，一般为`https://**.workers.dev/`，将这个追加到需要加速的GitHub连接前即可。


以下都是合法输入（仅示例，文件不存在）：

- 分支源码：https://github.com/Mintimate/project/archive/master.zip

- release源码：https://github.com/Mintimate/project/archive/v0.1.0.tar.gz

- release文件：https://github.com/Mintimate/project/releases/download/v0.1.0/example.zip

- 分支文件：https://github.com/Mintimate/project/blob/master/filename

- commit文件：https://github.com/Mintimate/project/blob/1111111111111111111111111111/filename

- gist：https://gist.githubusercontent.com/Mintimate/351557e6e465c12986419ac5a4dd2568/raw/cmd.py

## 部署

首页：https://workers.cloudflare.com

注册，登陆，`Start building`，取一个子域名，`Create a Worker`。

复制 [index.js](https://cdn.jsdelivr.net/gh/hunshcn/gh-proxy@master/index.js)  到左侧代码框，`Save and deploy`。如果正常，右侧应显示首页。

`index.js`默认配置下项目文件会走jsDelivr，如需走worker，修改Config变量即可

`ASSET_URL`是静态资源的url（实际上就是现在显示出来的那个输入框单页面）

`PREFIX`是前缀，默认（根路径情况为"/"），如果自定义路由为example.com/gh/*，请将PREFIX改为 '/gh/'，注意，少一个杠都会错！


## 注意

python版本的机器如果无法正常访问github.io会启动报错，请自行修改静态文件url

workers版本默认配置下项目文件会走jsDelivr，如需走服务器，修改配置即可


## Cloudflare Workers计费

到 `overview` 页面可参看使用情况。免费版每天有 10 万次免费请求，并且有每分钟1000次请求的限制。

如果不够用，可升级到 $5 的高级版本，每月可用 1000 万次请求（超出部分 $0.5/百万次请求）。

## Changelog

* 2020.04.10 增加对`raw.githubusercontent.com`文件的支持
* 2020.04.09 增加Python版本（使用Flask）
* 2020.03.23 新增了clone的支持
* 2020.03.22 初始版本

