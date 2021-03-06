---
layout: wikis
title:  B/S结构
description: B/S结构（Browser/Server，浏览器/服务器模式），是WEB兴起后的一种网络结构模式，WEB浏览器是客户端最主要的应用软件。
header-img: "img/about-bg.jpg"
catalog: true
---

> 摘自`百度百科`

# B/S结构

B/S结构（Browser/Server，浏览器/服务器模式），是WEB兴起后的一种网络结构模式，[WEB](https://baike.baidu.com/item/WEB/150564)浏览器是客户端最主要的应用软件。这种模式统一了客户端，将系统功能实现的核心部分集中到服务器上，简化了系统的开发、维护和使用。客户机上只要安装一个浏览器，如[Netscape Navigator](https://baike.baidu.com/item/Netscape Navigator/1014148)或[Internet Explorer](https://baike.baidu.com/item/Internet Explorer/1537769)，服务器安装[SQL Server](https://baike.baidu.com/item/SQL Server/245994)、[Oracle](https://baike.baidu.com/item/Oracle/301207)、[MYSQL](https://baike.baidu.com/item/MYSQL/471251)等数据库。浏览器通过[Web Server](https://baike.baidu.com/item/Web Server/9306055) 同数据库进行数据交互。



## 架构

随着Internet和WWW的流行，以往的主机/终端和[C/S](https://baike.baidu.com/item/C%2FS/826311)都无法满足当前的全球网络开放、互连、信息随处可见和信息共享的新要求，于是就出现了B/S型模式，即浏览器/服务器结构。它是C/S架构的一种改进，可以说属于三层C/S架构。主要是利用了不断成熟的WWW浏览器技术，用通用浏览器就实现了原来需要复杂专用软件才能实现的强大功能，并节约了开发成本，是一种全新的软件系统构造技术。

第一层是[浏览器](https://baike.baidu.com/item/浏览器/213911)，即[客户端](https://baike.baidu.com/item/客户端/101081)，只有简单的输入输出功能，处理极少部分的事务逻辑。由于客户不需要安装客户端，只要有浏览器就能上网浏览，所以它面向的是大范围的用户，所以界面设计得比较简单，通用。

第二层是WEB服务器，扮演着信息传送的角色。当用户想要访问[数据库](https://baike.baidu.com/item/数据库/103728)时，就会首先向WEB服务器发送请求，WEB服务器统一请求后会向数据库服务器发送访问数据库的请求，这个请求是以[SQL](https://baike.baidu.com/item/SQL/86007)语句实现的。

第三层是数据库服务器，他扮演着重要的角色，因为它存放着大量的数据。当数据库服务器收到了WEB服务器的请求后，会对SQL语句进行处理，并将返回的结果发送给WEB服务器，接下来，WEB服务器将收到的数据结果转换为[HTML](https://baike.baidu.com/item/HTML/97049)文本形式发送给浏览器，也就是我们打开浏览器看到的界面。



## 工作原理

B/S架构采取浏览器请求，服务器响应的工作模式。

用户可以通过浏览器去访问Internet上由Web服务器产生的文本、数据、图片、动画、视频点播和声音等信息；

而每一个Web服务器又可以通过各种方式与数据库服务器连接，大量的数据实际存放在数据库服务器中；

从[Web服务](https://baike.baidu.com/item/Web服务/2837593)器上下载程序到本地来执行，在下载过程中若遇到与数据库有关的指令，由Web服务器交给数据库服务器来解释执行，并返回给Web服务器，Web服务器又返回给用户。在这种结构中，将许许多多的网连接到一块，形成一个巨大的网，即全球网。而各个企业可以在此结构的基础上建立自己的Internet。

在 B/S 模式中，用户是通过浏览器针对许多分布于网络上的服务器进行请求访问的，浏览器的请求通过服务器进行处理，并将处理结果以及相应的信息返回给浏览器，其他的数据加工、请求全部都是由Web Server完成的。通过该框架结构以及植入于操作系统内部的浏览器，该结构已经成为了当今软件应用的主流结构模式。



## 优缺点

### 优点

B/S架构最大的优点是总体拥有成本低、维护方便、 分布性强、开发简单，可以不用安装任何专门的软件就能 实现在任何地方进行操作，客户端零维护，系统的扩展非常容易，只要有一台能上网的电脑就能使用。 [3] 

首先，维护和升级方式简单。

目前，软件系统的改进和升级越来越频繁，B/S架构的产品明显体现着更为方便的特性。对一个稍微大一点单位来说，系统管理人员如果需要在几百甚至上千部电脑之间来回奔跑，效率和工作量是可想而知的，但B/S架构的软件只需要管理服务器就行了，所有的客户端只是浏览器，根本不需要做任何的维护。无论用户的规模有多大，有多少分支机构都不会增加任何维护升级的工作量，所有的操作只需要针对服务器进行；如果是异地，只需要把服务器连接专网即可，实现远程维护、升级和共享。所以客户机越来越“瘦”，而服务器越来越“胖”是将来信息化发展的主流方向。今后，软件升级和维护会越来越容易，而使用起来会越来越简单，这对用户人力、物力、时间、费用的节省是显而易见的，惊人的。因此,维护和升级革命的方式是“瘦”客户机,“胖”服务器。

其次，成本降低，选择更多。

大家都知道[windows](https://baike.baidu.com/item/windows/165458)在桌面电脑上几乎一统天下，浏览器成为了标准配置，但在服务器操作系统上windows并不是处于绝对的统治地位。现在的趋势是凡使用B/S架构的应用管理软件，只需安装在[Linux](https://baike.baidu.com/item/Linux/27050)服务器上即可,而且安全性高。所以服务器操作系统的选择是很多的，不管选用那种操作系统都可以让大部分人使用windows作为桌面操作系统电脑不受影响，这使的最流行免费的Linux操作系统快速发展起来，Linux除了操作系统是免费的以外，连数据库也是免费的，这种选择非常盛行。比如说很多人每天上“新浪”网，只要安装了浏览器就可以了，并不需要了解“新浪”的服务器用的是什么操作系统，而事实上大部分网站确实没有使用windows操作系统,但用户的电脑本身安装的大部分是windows操作系统。

### 缺点

虽说B/S架构有很多优越性，但是也不可避免有些缺陷。不过，在理论上，既然B/S是C/S的改进版，缺点应该不是很多。在实际使用中存在问题。

最大的缺点就是通信开销大、系统和数据的安全性较难保障。 

由于B/S架构管理软件只安装在服务器端(Server)上，网络管理人员只需要管理服务器就行了，用户界面主要事务逻辑在服务器(Server)端完全通过WWW浏览器实现，极少部分事务逻辑在前端(Browser)实现，所有的客户端只有浏览器，网络管理人员只需要做硬件维护。但是，应用服务器运行数据负荷较重，一旦发生服务器“崩溃”等问题，后果不堪设想。因此，许多单位都备有数据库存储服务器，以防万一。

## C/S与B/S

B/S架构是从C/S架构改进而来，可以说是三层C/S架构，由此可见两者关系不一般。B/S从C/S中脱离而出，后来随着WEB技术的飞速发展以及人们对网络的依赖程度加深，B/S一举成为当今最流行的网络架构。两种架构都在各自岗位上虎虎生威，它们各有千秋，都是非常重要的网络架构。在响应速度，用户界面，数据安全等方面，C/S强于B/S，但是在业务扩展和适用www条件下，B/S明显胜过C/S。可以这么说，B/S的强项就是C/S的弱项，反之亦然。它们各有优缺点，相互无法取代。 [4] 

C/S结构与B/S结构两种模式各自拥有其特色优势，在不同的系统环境与操作平台下，选择较为接近或交叉进 行混合模式的使用，可以保证数据的敏感性、安全性和稳定发展，还可以加强对数据库的修改与新增记录的操作。 对客户端程序进行保护，提高资源数据的交互性能，实现系统维护成本较低、维护方式较简便、布局更合理、网络数据使用效率较高的目的，采用C/S与B/S混合模式才是最佳方案。