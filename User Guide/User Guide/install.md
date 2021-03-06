# 安装手册

<!-- TOC -->

- [安装手册](#安装手册)
    - [MySQL安装及配置](#mysql安装及配置)
    - [AutoLine依赖包安装](#autoline依赖包安装)
    - [初始化数据库](#初始化数据库)
    - [初始化数据](#初始化数据)
    - [运行](#运行)
    - [可能碰到的问题](#可能碰到的问题)

<!-- /TOC -->

## MySQL安装及配置

下载最新版的Mysql安装，具体安装方法，请自行参照相关文档。

1. 使用utf-8编码创建一个名为autoline的数据库

2. 修改.env配置文件中的数据库连接字符串，如下：

> 
>DATABASE_URL=mysql+pymysql://root:123456@127.0.0.1/autoline
>
>TRIGGER_DATABASE_URL=mysql+pymysql://root:123456@127.0.0.1/autoline
> 

注：  
1. root:123456 改为你的MySQL账号和密码

2. 127.0.0.1 改为你的MySQL服务器的IP地址

## AutoLine依赖包安装

如何安装AutoLine相关依赖包？
1. 直接在 https://github.com/small99/AutoLine 下载

2. 或通过git命令clone：
> git clone https://github.com/small99/AutoLine

等待下载完成， 在AutoLine根目录下的requirements.txt即为相关依赖包文件，使用下面的命令安装依赖

1. 需要先安装好Python3，最好将pip升级到最新的版本（python）,先升级pip

> python -m pip install --upgrade pip

2. 安装AutoLine依赖包：

> pip install -r requirements.txt

## 初始化数据库

首次启动时，需要初始化数据库建表和数据信息：

使用下面命令初始化建表

1. 初始化
> python manage.py db init
2. migrate
> python manange.py db migrate
3. upgrade
> python manage.py db upgrade

如果你修改了数据库模型,即修改了models.py中的表字段，运行上述的2和3即可修改表结构

## 初始化数据
第一次运行时，需要初始化数据，使用下面的命令即可：

> python manage.py deploy

## 运行

运行方式分为两种
1. 默认方式，只能在本机访问
> python manage.py runserver
此时只能通过http://127.0.0.1:5000来访问

2. 外网访问模式
> python manage.py runserver -h 0.0.0.0 -p 8080

-h 用于绑定本机IP

-p 用于指定端口

这是你可以通过http://ip:端口 来访问平台了，只要能ping到你IP地址的机器均可访问平台

## 可能碰到的问题

1. 提示pip不是最新版，请根据上面的提示先更新你的pip版本

2. 提示缺依赖包，请根据提示信息，手动pip install xxx 来安装缺的依赖包

3. 发现任何问题，请优先重新到github拉取最新的代码

公众号,扫一扫关注我，收获第一手信息：

![开源优测](../../app/static/images/deeptest.jpg)
