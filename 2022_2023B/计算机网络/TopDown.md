# 计算机网络-自顶向下方法

[toc]

## 第1章

### 一些概念

+ 主机 = 端系统
+ 端系统通过通信链路和分组交换机连接到一起。
+ 通信链路：

  + 光纤

  + 同轴电缆

  + 无线电 

  + 卫星
+ ISP：Internet Server Provider
+ 分布式应用程序：涉及多个相互交换数据的端系统
+ 套接字接口：规定了一个端系统上的程序向另一个端系统上的程序交付数据的方式
+ 协议：一种规范，用于在计算机网络中实现通信和数据传输。定义了数据格式、通信规则、错误检测和恢复机制、数据传输速率等方面的细节
+ 网络边缘：主机和服务器
+ 链路的速率：理解成打包分组并推出去的速率
+ 多宿：一个客户ISP（小ISP）连接两个提供商ISP（大ISP）
+ 信道带宽：信道带宽 = 链路的速率R
+ 因特网：因特网是由全球范围内互联的计算机网络构成的系统。它是一个开放的、分布式的、自治的网络系统，由众多网络组成，通过标准化的协议相互连接和通信。

### 物理媒体各自的优缺点

双绞铜线的优点包括：

1. 价格相对便宜；
2. 安装和维护容易；
3. 抗干扰性能相对较好。

双绞铜线的缺点包括：

1. 距离受限，信号传输距离较短；
2. 传输速率相对较低；
3. 受电磁干扰影响较大。

同轴电缆的优点包括：

1. 传输速率较高；
2. 抗干扰性能较好；
3. 传输距离较远。

同轴电缆的缺点包括：

1. 安装和维护较为复杂；
2. 价格相对较高。

光纤的优点包括：

1. 传输速率非常高；
2. 传输距离非常远；
3. 抗干扰性能非常好。

光纤的缺点包括：

1. 价格相对较高；
2. 安装和维护较为复杂。

陆地无线电信道的优点包括：

1. 适用范围广，可覆盖大范围；
2. 安装和维护容易。

陆地无线电信道的缺点包括：

1. 受地形和气候影响较大；
2. 受电磁干扰影响较大；
3. 容易被黑客攻击。

卫星无线电信道的优点包括：

1. 覆盖范围广，信号可覆盖全球；
2. 传输距离非常远。

卫星无线电信道的缺点包括：

1. 价格相对较高；
2. 信号传输延迟较大；
3. 受天气影响较大。

### 4种时延

[网络传输的四种时延](https://www.cnblogs.com/liushuailing/p/15916186.html)

P25

#### 处理时延

$d_{proc}$：检查分组并路由的时延

产生在路由器，交换机等等。

#### 排队时延

$d_{queue}$：分组进路由器并被检查和路由好后等待传输的时延

产生在路由器，交换机等等。

#### 传输/发送时延

$d_{trans}$：将分组**所有**比特推向链路的时延（P26加油站比喻）

经过t = $d_{trans}$后，分组最后一个比特刚刚离开主机到达信道。

产生在路由器，交换机等等。

#### 传播时延

$d_{prop}$：电磁波承载数据在信道传播的时延（很少，光速）

产生在电缆、光纤、无线电波。

### 时分复用和频分复用

都是围绕链路讲，将链路按频率划分......将链路传输的时间划分为固定的帧......

### 分组交换和电路交换

#### 分组交换

平时想的那种，一个包一个包地发。

#### 电路交换

P19

跟打电话一样的，提前预留好带宽。

一条链路里有多条电路。

一个时分复用算传输时间的例子P21顶

#### 二者的比较

P21

+ 电路交换

电路交换是一种建立点对点连接的通信方式。在电路交换中，通信双方需要先建立一条物理电路，然后在这条电路上进行通信。在通信过程中，整条电路都被占用，只有两端设备之间的数据才能在电路上传输，因此电路交换**需要占用大量的资源**。

电路交换的原理是**基于电路的连接**，通信双方需要占用一定的带宽和资源，因此在通信过程中可以保证传输的可靠性和实时性。

+ 分组交换

分组交换是一种将数据分成小块（数据包）进行传输的通信方式。在分组交换中，数据包在传输过程中需要经过多个网络设备（如路由器、交换机）的转发，每个设备只需要处理数据包的一部分，因此分组交换可以**更加高效地利用网络资源**。

分组交换的原理是**基于数据包的交换**，将数据分成小块进行传输，每个数据包都会携带目标地址和源地址等信息，网络设备根据这些信息来转发数据包。由于分组交换不需要占用整条电路，因此可以更加高效地利用网络资源，但也可能会出现数据丢失或延迟等问题。

### 网络分层

#### 每层各自的作用

物理层：负责网络**物理传输**介质的传输特性和传输规范。

链路层：负责定义数据在物理通信**链路上传输的格式和规范**，以及对**数据的差错控制**和流量控制等。

网络层：负责对数据进行**路由选择和转发**，实现**不同网络之间的数据传输**。

传输层：负责提供**数据传输**服务，包括**数据的分段**、传输控制和**错误恢复**等。

应用层：负责为用户提供各种**网络应用服务**，如电子邮件、文件传输、Web浏览等。

#### 分层的原因

将整个通信过程分解成一个个的子问题，并且每个子问题都有其特定的解决方案。这样可以**降低系统的复杂度**，提高系统的**可靠性**和**可维护性**。此外，网络分层还可以提高系统的**灵活性**和**可扩展性**，使得各层之间的协议和功能可以相互独立地进行开发和升级。

#### 分层是否越多越好/越少越好

分层并不是越多越好或者越少越好，网络分层的层数应该根据具体情况来决定。如果**层数过多，会增加系统的复杂度和开发难度**，而如果**层数过少，会导致功能不够完善、性能不够优秀**等问题。因此，在设计网络分层时，需要考虑到各种因素，如系统的规模、性能、可靠性和安全性等，来确定合适的层数。

### 流量强度

P27

L：一个分组的大小

a：分组到达队列的平均速率

R：传输速率

流量强度：La/R

当流量强度趋近于1时排队时延剧增，虽然感觉上还是可以一直吞吐，实际上类比一个车道上全是车，虽然在走，但是由于大家快慢不一，车流速度总是跟最慢的相等，而且一旦出事故就会堵车。



### 时延带宽积

分组的第一个比特到达终点时，发送端发出的比特数量

时延带宽积 = 传播时延\*信道带宽

### 比特宽度

信道上两个比特间的长度

比特宽度 = 传播速率/传输速率（单位：m）

## 第2章 应用层

### 应用层提供的服务和使用的协议

应用层是TCP/IP协议栈中的最高层，主要提供各种网络应用服务，如电子邮件、文件传输、Web浏览等。以下是应用层提供的一些常见服务及其使用的协议及应用：

web浏览：

1. HTTP：超文本传输协议，用于Web浏览，通过Web浏览器访问网站时使用。
2. DNS：域名系统，用于将域名转换为IP地址，通常在Web浏览器访问网站时使用。

文件传输：

1. FTP：文件传输协议，用于在网络上进行文件传输，通常使用FTP客户端软件进行操作。

电子邮件：

1. SMTP：简单邮件传输协议，用于电子邮件的发送，常用于邮件客户端软件和邮件服务器之间的通信。
2. POP3：邮局协议版本3，用于电子邮件的接收，通常用于邮件客户端软件和邮件服务器之间的通信。
3. IMAP：互联网消息访问协议，用于电子邮件的接收，与POP3类似，但提供更多的功能和灵活性。

### HTTP报文格式

#### HTTP请求报文

![image-20230612131533425](Pics\pic29.png) 

请求行和首部行：

第一行为请求行，有三个部分：方法，文件的URL，HTTP版本

第二行以后为首部行，内容在P68

#### HTTP响应报文

![image-20230612132207740](Pics\pic30.png) 

第一行为状态行，200 OK表示请求成功

接下来6行为首部行

后面data data为实体体

#### 为什么请求报文要标明浏览器类型

服务器需要浏览器类型信息将同⼀对象的不同版本发送到不同类型的浏览器。

### HTTP持续和非持续连接（后面删掉）

持续的好处：

1. 减少延迟：由于持续连接可以重用已经建立的连接，所以可以减少每次请求建立连接的时间，从而减少延迟。
2. 节省服务器带宽：由于持续连接可以重用已经建立的连接，所以可以减少网络带宽的消耗。

持续的坏处：

1. 需要一直维护连接，消耗大

非持续的好处：

1. 减少服务器资源占用：由于每个请求都需要建立新的连接，不需要连接的时候可以省出资源给服务器，所以可以减少服务器的资源占用。

非持续的坏处：

1. 必须为每一个请求维护一个连接，服务器消耗巨大

### get/post方法

GET和POST方法是HTTP协议中最常用的两种请求方法。GET方法用于获取资源，POST方法用于提交数据（提交表单）。GET请求将参数放在URL中，而POST请求将参数放在请求体中。GET请求适用于获取数据，POST请求适用于提交数据。

### Web缓存器

缓存器中存着局域网里主机的各种副本，命中以减少请求时延。

P73和P116中P9

![image-20230612134747210](Pics\pic31.png) 

注意局域网路由器到机构网络之间的时延由于流量强度太低，时延过低被省略了。

注意P116中P9的Q2流量强度也因为有了缓存器而会变化，所以平均接入时间不一样。详见笔记本。

### SMTP

P76

**推**协议

通过SMTP，邮件客户端可以将邮件发送到邮件服务器

### POP3

**拉**协议

用于接收电子邮件的协议

#### 下载并删除模式

![image-20230612140714517](Pics\pic32.png) 

每次访问邮箱

1. 列出邮件
2. 要求返回
3. 删除
4. 依次对每个邮件执行要求返回和删除直到quit

#### 下载并保留模式

就不删除，其它一样，这样方便在不同的地方看邮件。（不然取回本地就没了）

### 电子邮件整体框架

整体构架包括邮件客户端、邮件服务器和中间服务器。邮件客户端和邮件服务器之间通过SMTP和POP协议进行通信。中间服务器主要用于邮件转发、过滤和存储等功能。

存在中间服务器的原因有很多，其中包括：

1. 提高邮件传输效率：中间服务器可以对邮件进行过滤和优化，从而提高邮件传输效率。
2. 邮件**存储和备份**：中间服务器可以对邮件进行存储和备份，从而保证邮件的安全和可靠性。
3. 邮件转发和路由：中间服务器可以对邮件进行转发和路由，从而保证邮件能够正确地发送和接收。

如果没有服务器，电子邮件会有以下缺点：

1. 邮件存储不方便：如果没有服务器，邮件客户端需要将所有邮件保存在本地计算机中，这样会占用大量的存储空间。
2. 邮件备份困难：如果没有服务器，邮件备份和恢复会比较困难，容易发生数据丢失的情况。
3. 邮件传输效率低下：如果没有服务器，邮件客户端需要直接将邮件发送到目标邮件服务器，这样会导致邮件传输效率低下，并且容易出现传输错误的情况。

### DNS服务器

将主机名和IP互相映射解析。

P86

一般是逐层向上查询的，也可以有缓存。

### DNS记录和报文

P89

记录包含了4元组：（Name，Value，Type，TTL）

TTL是记录的生存周期

Name和Value取决于Type

DNS记录：

1. A记录：将域名映射到一个IPv4地址，它是最常用的DNS记录类型。
2. MX记录：指定处理邮件的服务器。
3. CNAME记录：将一个域名别名映射到另一个域名。（Value为别名是Name的主机对应的规范主机名）
4. NS记录：指定该域名的授权域名服务器。

### nslookup

在cmd中键入nslookup之后进入交互模式

此时输入任何的域名/ip可以向DNS服务器发送DNS查询

### DNS服务器的查询过程

**递归查询与迭代查询**

一、主机向本地域名服务器的查询一般都是采用递归查询。

所谓递归查询就是：如果主机所询问的本地域名服务器不知道被查询的域名的IP地址，那么本地域名服务器就以DNS客户的身份，

向其它根域名服务器继续发出查询请求报文(即替主机继续查询)，而不是让主机自己进行下一步查询。

因此，递归查询返回的查询结果或者是所要查询的IP地址，或者是报错，表示无法查询到所需的IP地址。

二、本地域名服务器向根域名服务器的查询的迭代查询。

迭代查询的特点：当根域名服务器收到本地域名服务器发出的迭代查询请求报文时，要么给出所要查询的IP地址，要么告诉本地服务器：“你下一步应当向哪一个域名服务器进行查询”。

然后让本地服务器进行后续的查询。根域名服务器通常是把自己知道的顶级域名服务器的IP地址告诉本地域名服务器，让本地域名服务器再向顶级域名服务器查询。

顶级域名服务器在收到本地域名服务器的查询请求后，要么给出所要查询的IP地址，要么告诉本地服务器下一步应当向哪一个权限域名服务器进行查询。

最后，知道了所要解析的IP地址或报错，然后把这个结果返回给发起查询的主机



递归查询：指使上一级服务器代替本地服务器去向上上一级服务器发查询指令

迭代查询：上一级服务器告诉本地服务器下一步应该去哪个服务器查询，然后下一步的这个服务器告诉下下一步该去哪里查询



P87实例

通常从请求主机道本地DNS服务器的查询是递归的，其余的都是迭代的



优化（就是在没有缓存的情况下考虑缓存，混合使用）**后面删**

### 新域名加入网络的步骤

1. 配置DNS服务器：在注册域名之后，需要配置DNS服务器，将该域名与IP地址进行关联。这一步需要将域名服务器的IP地址添加到DNS系统中，以便其他用户可以通过域名访问该服务器。
2. 发布网站内容：在DNS服务器配置完成之后，需要将网站内容上传到服务器上，并进行相关设置。这一步需要将网站配置文件、数据库等相关文件上传到服务器上，并配置服务器环境、网站目录等信息。
3. 测试域名解析：在网站内容上传完成之后，需要进行域名解析测试，以确保域名解析正常。这一步可以通过ping命令或者nslookup命令进行测试，验证域名解析是否正确。

### 内容分发网络 CDN

CDN的工作原理如下：

1. 用户向CDN请求某个资源，如图片、视频、网页等。
2. CDN系统根据用户的IP地址、地理位置等信息，**选择离用户最近的服务器**，将资源**从源服务器**中获取并**缓存**到**该服务器**上。
3. 当其他用户请求同一资源时，CDN系统可以直接从缓存服务器中返回资源，避免了重复的网络传输，提高了访问速度。
4. 如果缓存服务器中的资源过期或被删除，CDN系统会从源服务器中重新获取资源并更新缓存。

### 客户-服务器体系结构C/S

P93

传统的一个服务器给多个客户发

一个例题：

P118中P23

（边上传也就边在下载了）

C/S结构（Client/Server Structure）指的是客户端和服务器的结构，客户端向服务器发送请求，服务器处理请求并返回结果。这种结构通常用于需要处理大量数据以及复杂业务逻辑的应用程序，例如数据库管理系统。

### B/S

B/S结构（Browser/Server Structure）指的是浏览器和服务器的结构，用户通过浏览器向服务器发送请求，服务器处理请求并将结果发送回浏览器。这种结构通常用于Web应用程序。

### P2P

P93

一个服务器发给多个客户，客户之间也能互相发

一个例题：

P118中P24

P2P结构（Peer-to-Peer Structure）指的是点对点结构，每个节点都可以充当客户端和服务器。节点之间可以直接通信，而不需要经过中央服务器。这种结构通常用于文件共享、视频聊天等应用程序。

### 数据传输效率

长度为 **100** 字节的应用层数据交给运输层传送，需加上 **20** 字节的 **TCP** 首部。再交给网络层传送，需加上 **20** 字节的 **IP** 首部。最后交给数据链路层的以太网传送，加上首部和尾部共 **18** 字节。试求数据的传输效率。数据的传输效率是指发送的应用层数据除以所发送的总数据(即应用数据加上各种首部和尾部的额外开销)。 

  若应用层数据长度为 **1000** 字节，数据的传输效率是多少？

数据长度为100字节时 传输效率=100/（100+20+20+18）=63.3% 数据长度为1000字节时， 传输效率=1000/（1000+20+20+18）=94.5%

## 第3章 传输层

### 一些概念

#### 套接字

连接在传输层和应用层之间的**套接**首部**字**符串的工具。规定了一个端系统上的程序向另一个端系统上的程序交付数据的方式

#### 多路分解和多路复用

多路分解：从下往上的，将传输层的报文分解，然后交付到对应的套接字接口。

多路复用：从上往下的，从多个套接字接口中取得数据，复合成报文并封装上首部信息。

#### 端口

端口用于标识一条**数据**通路或进程间通信的**终点**。每个正在运行的网络应用程序都会开放一个或多个端口，用于接收来自网络上其他应用程序的数据。

端口号是一个16位的无符号整数，范围从0到65535。其中，0到1023的端口号被保留为被系统或应用程序使用，如HTTP默认使用的端口号为80，FTP默认使用的端口号为21。用户可以使用1024到65535的端口号，用于自己的应用程序。

当一个数据包到达计算机时，根据目的IP地址和端口号，操作系统会将该数据包发送给对应的应用程序。同样，当一个应用程序需要将数据包发送给其他计算机上的应用程序时，也需要指定目的IP地址和端口号。

### UDP

#### 报文结构

![image-20230612153426329](Pics\pic33.png) 

### UDP检验和

P133

### rdt 可靠数据传输协议

P135

#### 有限状态机 FSM

引起变迁的事件（如上层调用rdt_send(data)）写在横线上

事件发生后采取的动作写在横线下

虚线箭头指向一开始的状态

圆圈里面：当前状态

箭头：状态变迁

没有调用事件或事件没有动作，用反V表示



例题：P191中P17     注意：等待B的数据也应该有自环，比如在等待B的时候上层调用了，就去拒绝上层调用。

#### rdt 1.0

没有考虑比特受损的情况

#### rdt 2.0

接收方可以发NAK（否定确认）和ACK（肯定确认）来对上一个接受的分组进行回应，要求对方是否重传。

但是没有考虑NAK和ACK受损的情况。

#### rdt 2.1

对每个分组都加一个编号。收到损坏的分组发一个否定确认，要求重传。

#### rdt 2.2

对每个分组都加一个编号。当接收方需要重传是不发NAK，而是对上一个编号的包发一个ACK，要求重传。

#### rdt 3.0

设置一个倒计数定时器，当某个包的ACK到发送方的时间超过一定限制，发送方就重发这个包。

### 流水线可靠数据传输协议

发送方没必要硬等接收方ACK来了才发下一个，可以发一批再检查一批

#### 停等

发送窗口大小 = 1，接受窗口大小 = 1

#### 回退N步 GBN

P145

发送窗口大小 = N，接受窗口大小 = 1

也称滑动窗口协议。

特点：

+ 必须按序交付，收到没按序的直接丢弃，然后发一个上一个按序的ACK
+ 没有缓存

缺点：单个分组的误差可能引起整个窗口前半部分从丢失处起的重传。

猜想：接受到乱序ACK无所谓，只要填满前面到一定程度就移动窗口。某个ACK迟迟不来就从这个包开始重传。

#### 选择重传 SR

P148

发送窗口大小 = N，接受窗口大小 = N

发送方，接收方都有一个窗口。

发送方如果乱序收到ACK，则等待直到超时。按序则收到一个就将窗口后移一位。

接收方如果乱序收到包则缓存，直到之前差的包收到后一起沿协议栈上传。按序则直接上传，然后后移还没上传的包的个数那么多位。



`这两个都主要看书。`

#### TCP的选择确认

TCP用的是选择重传和回退N步的结合。

例题：P193中P37



GBN是收到一个失序的就发一个上一个还没失序的ACK。

SR是收到一个失序的就发这一个的ACK，等失序的那个超时后会自己发过来。

TCP是选择确认，收到一个失序的就发一个上一个还没失序的下一个的ACK。且收到一个包，不是发对这个包的ACK，它的ACK编号为下一个应该收到的包的编号。



#### 序号问题

P150

包的序号不是无限的，到了一定的大小后会清零。

所以要求窗口大小必须小于或等于序号空间大小的一半。

### 捎带Piggybacking

稍等确认（Piggybacking）是一种在传输层中常用的技术，它可以提高网络的效率和带宽利用率。在使用稍等确认技术时，接收方在发送确认信息之前，会将自己要发送的数据一起打包发送给发送方。

具体来说，当接收方收到发送方的数据包时，如果接收方需要发送数据给发送方，则接收方会在发送确认信息之前，将自己要发送的数据打包在确认信息中一起发送给发送方。这样可以避免发送方和接收方之间频繁地进行数据传输，提高了网络的效率和带宽利用率。

稍等确认技术通常用于TCP协议中，可以减少网络上的信令交互次数，减少网络延迟，提高数据传输速度。但是，如果数据包太大，则会导致传输延迟或者数据包丢失的问题。因此，在使用稍等确认技术时需要根据具体情况进行调整和优化。





就是要向对方传输的信息的时候顺便把ACK也发了

### TCP

#### 一些名词

+ MSS：最大报文段长度（由主机的最大链路层帧的长度确定）
+ 序号：将报文段的每个字节给一个序号，然后每个报文段开头的那个字节的序号即为报文段的序号 P155
+ 确认号：确认号为79，就代表希望对面下一个包的序号为79

#### 计算TimeoutInterval 重传间隔

P158

估计的平均RTT计算：
$$
EstimatedRTT = (1 - \alpha) \cdot EstimatedRTT + \alpha \cdot SampleRTT
$$
$\alpha$一般取0.125，$\beta$一般取0.25

估计的RTT偏离程度计算
$$
DevRTT = (1 - \beta) \cdot DevRTT + \beta \cdot |SampleRTT - EstimatedRTT|
$$
重传间隔：
$$
TimeoutInterval = EstimatedRTT + 4 \cdot DevRTT
$$
例题：P191中P31

#### 三次握手，连接的建立和结束

P166

![image-20230612193740136](Pics\pic34.png) 

前两次握手SYN = 1，最后为0

三次握手的具体过程如下：

1. 客户端向服务器发送一个SYN（同步）报文，表示要建立连接，并指定一个初始序列号。
2. 服务器接收到SYN报文后，回复一个SYN+ACK（同步确认）报文，表示接受连接请求，并指定一个确认号，同时也指定一个自己的初始序列号。
3. 客户端接收到服务器的SYN+ACK报文后，再回复一个ACK（确认）报文，表示连接建立成功。

三次握手的原因：保证连接的可靠性



四次挥手断开连接：

![image-20230612193829247](Pics\pic35.png) 



四次挥手：

1. 客户端向服务器发送一个FIN（结束）报文，表示要关闭连接。
2. 服务器接收到FIN报文后，回复一个ACK报文，表示已经接收到结束请求，**但是还有一些数据没有传输完**。
3. **当服务器的所有数据传输完后**，会向客户端发送一个FIN报文，表示服务器已经关闭连接。
4. 客户端接收到服务器的FIN报文后，回复一个ACK报文，表示已经接收到结束请求，连接已经关闭。

四次挥手保证数据的完整性

#### 拥塞控制

P176

##### 一些概念

+ MSS：最大报文段长度（由主机的最大链路层帧的长度确定）
+ 序号：将报文段的每个字节给一个序号，然后每个报文段开头的那个字节的序号即为报文段的序号 P155
+ 确认号：确认号为79，就代表希望对面下一个包的序号为79
+ rwnd：接受方缓存窗口大小（不代表接收方缓存大小，仅代表当前可用的缓存大小，P164）
+ cwnd：拥塞窗口，一般不看rwnd，只看cwnd
+ ssthresh：慢启动阈值，当cwnd到达ssthresh时停止慢启动，转到拥塞避免
+ 冗余ACK：如收到3个冗余ACK，实际上是一共收到了4个ACK，文字游戏

##### 慢启动

cwnd一开始设置为一个MSS的大小，每成功传一次就翻倍。（指数增）

慢启动的停止：

1. 有包的ACK**超时**未送回，那么结束慢启动，并且设置cwnd为1，并且设置ssthresh为cwnd/2（如果ssthresh除完有小数，向下取值，如ssthresh = 14.5，那么记作14），并且重新开始慢启动
2. 当cwnd到达ssthresh时停止慢启动，转到拥塞避免
3. 当检测到3个冗余ACK（实际上是一共收到了4个ACK）后转到快速恢复

##### 拥塞避免

cwnd每成功传一次就加一个MSS（线性增）

拥塞避免的停止：

1. 有包的ACK**超时**未送回，那么结束慢启动，并且设置cwnd为1，并且设置ssthresh为cwnd/2，并且转到慢启动

2. 当检测到3个冗余ACK（实际上是一共收到了4个ACK）后转到快速恢复

##### 快速恢复

注意，只有TCP Reno才有快速恢复，早期的TCP Tahoe没有

1. ssthresh = cwnd/2
2. cwnd = cwnd/2
3. cwnd += 3
4. 然后每次成功cwnd +=MSS（线性增）

#### TCP吞吐量的宏观描述

P182

设一般当cwnd为W时发生丢包，宏观的来看
$$
一条连接的平均吞吐量 = \frac{0.75 \cdot W}{RTT}
$$
用MSS和L（L是丢包率）表示
$$
一条连接的平均吞吐量 = \frac{1.22 \cdot MSS}{RTT \cdot \sqrt{L}}
$$
书后面有题推了，在从W/2到W的过程中只计算一个丢包的原因就是宏观上看，W又变为W/2是丢包造成的，所以只记1个。而W的大小就算反应丢包率的，W很大，说明一直增长到很大的cwnd才丢包，说明丢包率小。



### 传输层和网络层的区别

传输层：

1. 进程到进程的通信服务：传输层提供可靠的进程到进程数据传输服务，确保应用程序之间的通信顺利进行。
2. 数据分段和重组：传输层会将应用层的数据分成小块进行传输，并在接收端将这些数据块重新组合成完整的数据流。
3. 端口号管理：传输层使用端口号来标识不同的应用程序，以便在同一台设备上同时运行多个应用程序。

网络层：

1. 网络层是负责在网络中传输数据包的，而传输层负责在端到端的通信中传输数据流。
2. 网络层使用IP地址来标识不同的网络设备，而传输层使用端口号来标识不同的应用程序。
3. 网络层提供的服务是不可靠的，因为数据包可能会丢失或者重复，而传输层提供的服务是可靠的，因为它会确保数据的正确传输和接收。

传输层是必不可少的，因为它提供了可靠的数据传输服务，保证了应用程序之间的数据传输顺利进行。没有传输层，应用程序之间的通信将会非常困难，并且容易出现数据丢失、重复等问题。



## 第4章  网络层 数据平面

### 转发和路由

转发：将分组从一个输入链路接口转到另一个适当的输出链路接口（开车过立交桥，耗时短）

路由：选择分组到目的地的路径（规划下立交桥的口，耗时长）

### 转发表

P237中P1

是基于目的地的转发，不能指定来源。

形如：

| 目的地 | 链路接口 |
| ------ | -------- |
| H3     | 3        |

......

### 最长前缀匹配

P206

P238中P5

字面意思

### 路由器

如P307

一个路由器有多个接口，每个LAN口一个地址。普通家用路由器一般是内网外网各一套mac和ip地址。

### 交换

P207

就是包从输入链路接口道输出链路接口的过程

三种交换：

+ 经内存交换，从输入端口读到内存，到从内存写到输出缓存中（传统的）
+ 经总线交换，一条共享总线（适合中小型的）
+ 经互联网络交换，2N条总线，连接N个输入端口和N个输出端口（大的，如纵横式交换机，**后面的题基本都是基于纵横式来的**）

#### 输入排队

假设分组是FCFS先来先服务，后面的不能插队，同一个输出的接口一个时隙只能接受一个，一个时隙不同的输出接口可以同时接受一个包

##### HOL 线路前部阻塞

P210

##### 一个例题

P238中P4

![image-20230613134059598](Pics\pic36.png) 

里面注意的意思是，给最下面队列的头加上一个X后要4个时隙，实际上原题最好最坏都是3个时隙

### CIDR 子网地址分配

P239中P8,P11

尤其P8，注意实际上是二进制，一定要保证二进制下从某一位开始全一样，不要串 

[子网划分介绍以及如何划分子网（例题详解）](https://blog.csdn.net/qq_44047479/article/details/109390618)

如留了8个比特作主机位，但是要减去全为0（作子网地址），以及全为1的（作广播地址），实际上只有$2^8$-2 = 62个可以用

B公司：
网络地址：【172.16.100.128/26】
可用地址范围：【172.16.100.129/26~172.16.100.190/26】
广播地址：【172.16.100.191/26】
子网掩码：【255.255.255.128】

子网地址：网络号（照抄）+子网号（照抄）+主机号（全为0）

广播地址：网络号（照抄）+子网号（照抄）+主机号（全为1）

子网掩码：网络号（全为1）+子网号（全为1）+主机号（全为0）

### IP广播地址

当主机发出目的地址为255.255.255.255的数据报时，该数据包会被交付给同一子网下所有主机，甚至还会向相邻子网发。

### IP地址分类

![image-20230613134059598](Pics\pic37.png) 

全0和全1的都保留不用，如A类中的0.0.0.0和127.255.255.255都不使用。

A类：0~127。 B类：128~191。 C类：192~223。 D类：224~239， 组播地址 。 E类：240~254.

### IPv6和隧道技术

总之是IPv4的升级版就对了。

隧道技术：

P230

将完整的IPv6数据包的内容封装到IPv4里面，然后这个IPv4的包就通过支持IPv4的路由器来转发直到发到支持IPv6的路由器，这个路由器再根据观察IPv4包中的协议号为41，从而识别出这个IPv4的包里面有IPv6的包。

### NAT转换表

P226

对于路由器，内网IP和外网IP（两个LAN口之间的IP）之间的转换就需要NAT转换表。（该章后面有例题）

WAN端：外

LAN端：内

### IP分片算偏移量

![image-20230619171233817](Pics\pic38.png) 

### 路由器表的更新

[问题]假定网络中的路由器B的路由表有如下的项目（这三列分别表示“目的网络”、“距离”和“下一跳路由器”）：
N1 7 A
N2 2 C
N6 8 F
N8 4 E
N9 4 F
现在B收到从C发来的路由信息（这两列分别表示“目的网络”“距离”）：
N2 4
N3 8
N6 4
N8 3
N9 5
试求出路由器B更新后的路由表（详细说明每一个步骤）。

[回答]
答：先把B收到的路由信息中“距离”加1，并在后面添加C，得：
新表：
N2 5 C
N3 9 C
N6 5 C
N8 4 C
N9 6 C
再对比上述新表和B表的“目的网络”和“距离”。
N1 7 A （新表无N1的信息,不变）
N2 5 C （两表都有N2，且下一跳相同，那么更新距离，并且更新下一跳路由器”）
N3 9 C （B表中无N3，而新表有，那么添加）
N6 5 C （两表都有N6，但下一跳不同，比较距离，距离短，那么更新）
N8 4 E （两表都有N8，但下一跳不同，比较距离，距离一样，不变）
N9 4 F （两表都有N9，下一跳不同，比较距离，距离更大，不变）

## 第5章  网络层 控制平面

### 名词解释

+ 开销：图（图论里的图）上的权值
+ 最低开销路径：最短路径
+ SDN：软件定义网络，通过软件对路由选择算法等等进行控制P201

### LS算法（Link State链路状态算法）

又称集中式路由选择算法

特点：具有全局状态信息

#### Dijkstra算法

![pic1](Pics\pic1.jpg)  

![pic2](Pics\pic2.jpg) 

![pic3](Pics\pic3.png) 

![pic4](Pics\pic4.png) 

*D(v)：*源点到v点的当前路径长度

*p(v)：*源点到v点的上一个节点

$N'$：已经确定找到的最短路径，就是每轮选一个最短，选出来的那个

大概就是每轮找一个最小的路径出来，然后基于最小的路径的这个节点更新它周围的节点（周围的节点可能之前也更新过，此次更新可能会使周围节点的最短路径变短，也要更新）

#### LS算法的振荡

教材P247，P248

大概就是每次都用LS算法选择最短路径（实际中是链路开销最小，某条链路拥塞程度最小），导致下一次很多路由器都选择这条链路，从而导致这条拥塞小的链路又变得拥塞，称之为振荡。

可以使得让路由器运行LS算法的时间随机化来解决，这样就不是随时每个路由器都在运行LS。

### DV算法（距离向量算法）

又称分散式路由选择算法

特点：分布式的，不具有全局状态信息



*v*：x节点的所有邻接点

$d_x(y)$：从节点x到节点y的最低开销路径

*c(x,v)*：x到v的权值

$d_v(y)$：从节点v到节点y的最低开销路径

距离向量$D_x$：x的所有$d_x(y)$的集合

x到y的距离向量$D_x(y)$：从节点x到节点y的最低开销路径（跟$d_x(y)$很像，就是大写一下）



Bellman-Ford方程：
$$
d_x(y) = min_v\{  c(x,v) + d_v(y)  \}
$$


算法概括：采用一种递归的思想，$min_v$是对于x的所有邻接点而言的，就是x到y的距离等于x到所有邻接点的距离和邻接点到y的距离之和中最小的那一个。当x的$D_x$被更新了，那么它向它所有的邻接点都要发一个它的$D_x$，继而让邻接点更新





每个节点x存储的路由信息

1. 到x的所有邻接点v的开销c(x,v)
2. x到所有目的节点y的开销（估计值）$d_x(y)$
3. 所有邻接点v到y的开销（估计值）$d_v(y)$



P251：一个路由选择表更新的例子

P252：路由选择环路（两个节点来回互相更新）



一个小结：

![pic5](Pics\pic5.png) 



#### 好消息传得快，坏消息传得慢的原因

好消息传得快的原因：每次有更短的路径后路由器都会通知邻居

坏消息传得慢的原因：有路径增长后（如暴增），会出现类似无穷计数的问题

#### DV算法链路故障与毒性逆转

P252

毒性逆转：如果一个节点A第一跳经由节点B到达节点C，那么它告诉节点B它到节点C的距离就是无穷

### AS（自治系统）

路由管理面对的问题

+ 规模：规模太大不好管理，应该切块
+ 管理自治：各个ISP通常选择自己希望的路由选择算法来运行路由器

所以需要AS（自治系统）将路由器组织成一个个的小系统



### RIP（Routing Information Protocol）

RIP是一种AS内部的路由选择协议

使用DV算法

+ DV每隔30秒和邻居交换DV
+ 每个通告包括：最多25个目标子网
+ 毒性逆转：P253，防止路由选择环路使得两个节点来回互相循环更新的方案



### OSPF（开放最短路优先）

OSPF是一种AS内部的路由选择协议

使用LS算法

+ LS 分组在网络中（一个AS内部）分发
+ 全局网络拓扑、代价在每一个节点中都保持
+ 路由计算采用Dijkstra算法

![pic6](Pics\pic6.png) 



### 静态路由，RIP动态路由，OSPF动态路由

1. 静态路由

静态路由是手动配置的路由，管理员需要**手动输入路由信息**，例如目标**网络地址、下一跳地址**等。静态路由适用于网络规模较小、网络拓扑稳定不变的情况。静态路由的优点是易于配置，不需要消耗过多的网络资源；缺点是不够灵活，当网络拓扑发生变化时需要手动修改路由。

 

2. RIP动态路由

RIP（Routing Information Protocol）是一种基于距离向量的路由协议，采用**Bellman-Ford算法（DV算法）**计算最短路径。RIP将路由信息广播到整个网络中，每个路由器都可以通过接收相邻路由器广播的路由信息，更新自己的路由表。RIP适用于中小型网络，但在大型网络中会出现路由表收敛时间长、网络资源消耗大等问题。

 

3. OSPF动态路由

OSPF（Open Shortest Path First）是一种基于链路状态的路由协议，采用**Dijkstra算法**计算最短路径。OSPF通过交换链路状态信息（Link State Advertisement，LSA）来构建网络拓扑，每个路由器都可以根据链路状态信息计算出整个网络的最短路径。OSPF适用于大型复杂网络，能够快速适应网络拓扑的变化，但需要消耗大量的计算和存储资源。

 

综上，静态路由适用于小型网络拓扑不变的情况，RIP动态路由适用于中小型网络，OSPF动态路由适用于大型复杂网络。



### BGP（边界网关协议）

BGP是AS之间的路由选择协议

#### 网关路由器和内部路由器

![pic7](Pics\pic7.png) 

1c：网关路由器（和其它AS有连接）

1b：内部路由器（和其它AS无连接）

#### eBGP/iBGP

eBGP: 用于在不同AS之间交换路由信息，即在AS边界路由器之间交换路由信息（外部）

iBGP: 用于在同一个AS内交换路由信息，即在AS内部的不同路由器之间交换路由信息。（内部）

BGP通信报文：P257

#### 判别路由器从哪里学习前缀x

P257

P280中的P14

前缀x：某个AS内部的一个前缀为x的子网，通过BGP连接来在AS内部，AS之间发送报文来说明通过怎样的路径可达这个子网

学习到前缀x这种，都是通过BGP连接发送报文来说通过哪些AS可达前缀为x的子网

#### 热土豆路由选择

选择AS内代价最小的路径，发到下一个AS去（像热土豆一样烫，赶紧传给下一个AS）

2d要发报到X，这里到2a只要201，到2c最少都是263，所以选2a（虽然AS跳数增多）

![pic8](Pics\pic8.png) 

### 路由选择策略

P262

接入ISP：W,Y那种

多宿接入ISP：X那种

就是防止B，C这种来抢占X的流量，所以X对B说不可达其它地方

P281中P17有题

### 静态路由网络命令格式

![image-20230619173700502](Pics\pic41.png) 

![image-20230619173608343](Pics\pic39.png) 

![image-20230619173629617](Pics\pic40.png) 



格式：#ip+route +（这个路由器不能到的主机的ip地址）+（下一跳的LAN口的IP地址）

### SDN（软件定义网络）

路由选择设备仅执行转发，远程控制器计算并分发转发表

可以看P202

### 网络管理

P274

#### 网络管理的5大功能

1. 配置管理：跟踪设备的配置，管理设备配置信息

2. 性能管理：测量、分析、报告不同网络部件的性能

3. 故障管理：记录、检测和响应故障

4. 安全管理：定义安全策略，控制对网络资源的使用

5. 账户管理：定义、记录和控制用户和设备访问网络资源

#### 网络管理的架构

1. 管理服务器
2. 被管设备
3. 管理信息库MIB：存放被管设备的信息
4. 网络管理代理：运行在被管设备中的一个进程，用来和管理服务器通信
5. 网络管理协议



## 第6章  链路层

### 链路层提供的服务

+ 成帧

  将从网络层来的信息封装进帧，一个帧由一个数据字段和首部字段构成。

+ 链路接入

+ 可靠交付

+ 差错检测和纠正

  看P287

### 链路层在何处实现

主体在网络适配器（也叫网络接口卡/NIC/网卡）实现

部分在CPU中的软件实现

### 错误检验

EDC（差错检测和纠正位）

#### 比特模式

P331中P1

如比特模式1110 0110 1001 1101是一种比特模式

（实际上就是一串数据，像P291一样）

#### 最小长度检验和

最小长度检验和（Minimum Length Checksum）是一种数据校验方式，用于检查数据传输过程中是否出现错误。在最小长度检验和中，数据被分成若干个固定长度的块，在每个块的结尾处添加一个校验和，以检查该块数据是否传输正确。



如对于比特模式1110 0110 1001 1101，那么按最小长度检验和的方式，将比特模式如此划分后，采用二维偶校验方法

| 1    | 1    | 1    | 0    | 1    |
| ---- | ---- | ---- | ---- | ---- |
| 0    | 1    | 1    | 0    | 0    |
| 1    | 0    | 0    | 1    | 0    |
| 1    | 1    | 0    | 1    | 1    |
| 1    | 1    | 0    | 0    | 0    |

最后一列和最后一行为校验位

#### 单比特奇偶校验

就一位校验码，只能防错了一位比特的情况

##### 奇校验码

8位数据位和1位校验位，共9个数据，其中1的个数必须为奇数
一般校验位可以由八位数据位直接相加取反（同样不考虑进位）
11001010的校验位a = **~**(1+1+0+0+1+0+1+0) = 1（十进制的4，二进制的100，只要最后一位0，然后取反为1）
所以发送数据时为110010101

##### 偶校验码

8位数据位和1位校验位，共9个数据，其中1的个数必须为偶数
一般校验位可以由八位数据位按照二进制方式直接相加（不考虑进位）得到
11001010的校验位a = (1+1+0+0+1+0+1+0) = 0
所以发送数据时为110010100

##### 判断校验码

在FPGA的verilog代码设计时，可以使用异或运算，将数据位进行异或运算（这里是指每一位都用异或符号相连得到的结果）之后，若是奇数个1，则其结果应该是1，若是偶数个1结果则结果是0
若是偶校验方式，将每一位依次与0异或，保持
若是奇校验方式，将每一位依次与1异或，取反
最终得到校验码

或者剑伟说的，直接看有几个1，奇数个1（把校验位也算上）就是奇校验码，偶数个1就是偶校验码

#### 二维奇偶校验

如图出现了一位比特差错的情况，观察下行列，发现基本上每行都是偶数个1，所以是偶校验码

然后发现第二行1的数量不对，然后第二列1的数量也不对，所以问题出在第二行第二列相交的那个位上，给改成1

对于两个比特出错，只能检测不能纠正

![pic9](Pics\pic9.png) 

#### CRC（循环冗余校验）

P291

名词解释：

+ D：要传送的d比特的数据
+ R：用来校验的r个CRC校验比特
+ G：生成多项式，发送方和接收方提前协商的r+1（二进制位数为r+1）的比特模式，要求G的最高位为1



对于数据D发送方要选择r个附加比特R，将其附加到D上，形成d+r比特模式，使得这个D+R对G按位异或后刚好整除

![pic10](Pics\pic10.png) 发送方发的内容长这样，G是提前协商好了的，要凑个能被整除的

接受方用G去除接受到的这d+r个bits的数据，余数为0则正确，否则检测出错

在二进制计算中，乘以$2^k$就是左

移k位，所以D附加上R后就是$D\cdot2^r$，然后需要按位异或（XOR）R，注意是最后r位对R进行按位异或，因为最后几位全是0，只要原来R中有1，则就会在D+R中变成1，所以这将R附加到D后完整的那一堆二进制变成了D$\cdot2^r$  XOR  R

所以最终目标是D$\cdot2^r$  XOR  R = nG，这样使得发出来的二进制能被G整除

R = $\frac{D\cdot2^r}{G}$ 的余数

（G是提前商量好的，随便定的，所以在D确定的情况下只需要知道R）



已知D和G，算R

其实有点像十进制一样一直除，但是每一位不是相减，而是按位异或，比如看最后一步就懂了。

但是对于说，如果位数一样就可以按位异或，不是像除法一样非要上面大于下面才商。

![pic11](Pics\pic11.png) 

CRC能检测小于r+1的突发差错P292

### 多路访问（多点接入）协议

多个站点一起发数据给接受方，多个帧的信号会在接收方处纠缠发生碰撞，导致信号混乱从而丢失帧。



#### 信道划分（如TDMA FDMA CDMA）

#### TDMA 时分复用

每个时间片按周期分给站点

![pic12](Pics\pic12.png) 

#### FDMA 频分复用

每个频段分给站点（就像无线广播FM一样，每个FM占一个频率）

![pic12](Pics\pic13.png) 

#### CDMA 码分多址

![pic12](Pics\pic14.png) 

#### 随机接入协议（ALOHA,CSMA）

##### 时隙ALOHA

P295

大概就是时分复用那种，但是每个时隙所有节点都可以用来发送

这样只有一个节点活跃的时候，就不会浪费时隙了。但是同样的，活跃的节点多了，碰撞的概率就增大了。

![pic15](Pics\pic15.png) 



![pic16](Pics\pic16.png) 



![pic17](Pics\pic17.png) 

##### 纯ALOHA

P297

似乎是有点问题，不好理解，但是不管了，背。

大概就是也不管时隙了，有帧就传。撞了之后概率重传（防止立刻再撞）

![pic18](Pics\pic18.png) 

![pic19](Pics\pic19.png) 

##### CSMA/CD载波侦听多路访问

CSMA: 在传输前先侦听信道

+ 如果侦听到信道空闲，传送整个帧
+ 如果侦听到信道忙，推迟传送
+ 侦听到碰撞之后立即停止（为什么已经侦听了还会碰撞？跟传播时延有关 **传播延迟（距离）决定了冲突的概率**  P299顶）
+ 停止随机时间量后再侦听

大量碰撞，停止的随机时间间隔长，少量碰撞，停止的随机时间间隔短 P300

随机等待时间采用二进制指数退避算法

![pic20](Pics\pic20.png) 

$d_{prop}$：传输/发送时延（将所有比特推向链路的时间，类比：准备好弹射的准备时间，加油站中的时间）

$d_{trans}$：传播时延（光速，类比：弹射，高速路）

![pic21](Pics\pic21.png) 

##### CSMA/CA

与CSMA/CD类似，但是发送数据前发RTS和CTS帧来避免冲突。发生冲突不会立刻停止发送。

##### 轮流协议

P301

###### 轮询协议

一个主节点通知各个节点轮流传输

![pic22](Pics\pic22.png) 

###### 令牌传递协议

有令牌的节点才能传帧，令牌在节点之间一直传

![pic23](Pics\pic23.png) 

### MAC地址 

P304

**链路层地址**又叫**MAC地址**，**LAN地址**，**物理地址**

MAC地址写死在网卡上的（其实也能用软件改），且独一无二。由6节16进制的数构成11-22-33-4C-5D-66这种样子。

当适配器向目的适配器发送一个帧时，该帧包含目的适配器的MAC地址。当某个适配器接受到一个帧时，就会检查这个帧的MAC地址是否跟自己的匹配，匹配就沿协议栈上传。

**IP地址用于实现互联网上的逻辑通信，而MAC地址则用于实现局域网内部的快速寻址和数据传输**。

个人看法：由于DHCP过段时间给每个主机换个IP，所以说尽管发包那些路由等等都是按IP来的，但是也只保证了能送到子网去，子网内的IP是经常更换的，所以说送到之后按MAC地址来找来送包才是最保险的。

### ARP寻址

链路层和网络层之间的协议

P306

每台主机有一个ARP表，包含IP地址到MAC地址的映射，且这个表一般20分钟就要换一次。TTL代表过期时间，如P306的表。

ARP寻址流程：

![pic24](Pics\pic24.png) 

内部寻址的时候只知道IP（这个IP肯定是同一个子网的IP，不然就直接往网关路由器发了）不知道MAC地址需要在子网内部广播（广播地址为MAC广播地址，如P306中为FF-FF-FF-FF-FF-FF）一下，子网内发现自己IP与广播寻求的IP相同的，则返回自己的MAC地址。P306

注意ARP只能在内部寻址，如P307-308。先根据之前的IP协议，发到路由器的对应接口去，此时是可以ARP寻址的，该帧的目的MAC地址是路由器的对应接口。之后路由选择到另一个接口，然后再重新封装一个帧，这个帧的源IP与目的IP不变，但是源MAC已经变成由路由器转发出去的那个接口的MAC地址，此时的目的MAC地址变为真的目标IP对应的目标MAC地址。



例题：P333中P15

注意题中c，B不用向A请求一个MAC地址，因为B会看A的数据包的IP，发现是同一个子网下面的，那么说明这个包的MAC就是A的IP对应的MAC



个人看法：只知道IP不知道MAC的情况也与IP与MAC分离的理由不冲突，毕竟已经设定好了要验证MAC是否与自己相同才沿着协议栈上传。IP是上层协议。已知MAC的情况应该是从发来的包中来得到的。

### 以太网帧

P309

结构：

| 数据字段 | 目的地址 | 源地址 | 类型字段 | CRC  | 前同步码 |
| -------- | -------- | ------ | -------- | ---- | -------- |

数据字段：装数据的，最大1500字节，最小46字节

目的地址：目标适配器的MAC地址

源地址：源适配器的MAC地址

类型字段：标明这个以太网帧的内容需要传给哪个网络协议

CRC：检查的

前同步码：前7个字节用来同步时钟（不懂），第8个字节的最后两个用来标志“重要的内容要来了”



以太网技术向网络层提供**不可靠服务**，不会对以太网内容是否通过CRC检查有确认之类的（但是实际上还是会确认，通过应用层和传输层协议TCP这些来确认）

### 交换机

P312

交换机是`透明`的，对于子网中的主机和路由器，不会知道有这么个交换机，数据到这里经过识别后直接发出去，这个东西的接口也没IP之类的

#### 交换机表

形式：

| 地址（MAC） | 接口 | 时间 |
| ----------- | ---- | ---- |

当一个以太网帧到达交换机后的三种情况：P313

#### 交换机自学习

有以太网帧到达交换机后，交换机记住它的源地址和到达的接口、时间。如果过了交换机的老化时间，还没有同接口和源地址的以太网帧到达，那么交换机删除交换机表里的这条记录。

由此体现交换机的**自学习性**和**即插即用**

#### 交换机和路由器的区别

+ 交换机关注MAC地址的转发，路由器关注IP地址的转发
+ 交换机即插即用，路由器不行，要配置IP
+ 交换机对子网其它主机和路由器透明，路由器不透明
+ 交换机不防网络风暴，路由器可以
+ 交换机适合小型网络，路由器适合大型的

#### 集线器和二者的区别

集线器：交换机的丐版，当同时两个接口来帧的时候会碰撞，集线器从一个接口收到帧后它向它其它的每一个接口都转发这个帧，总之很扯就是了。

### 数据中心网络

P322

概念：

+ 刀片：一个小披萨盒一样的主机
+ 机架：很多个刀片叠放
+ TOR交换机：放在机架顶部，与机架的所有刀片相连

主要看下P324，多条流并发时，交换机之间的速率可能限制主机之间传输的速率

P335有题

## 第7章  无线网络

### CDMA

CDMA 码分多址：将一串比特数据用发送端的一个CDMA码进行编码后发送，到接受方后用同样的CDMA码进行解码。

一种防止信号传输在接收方碰撞的手段，与前面时分复用和频分复用类似

例子：一群人在房间里说话，乱七八糟都听不清

解决方案：

+ 时分复用：分时间轮流发送，类比大家轮流说话
+ 频分复用：按频率划分来发送（四六级听力fm xxx），类比大家在房间的不同地方聚成一小团说话
+ 码分多址：不区分，对信号进行编码，而后在接收方进行解码，就算碰撞也能解出来，类比在房间里使用不同语言说话，虽然吵，但是只听得懂中文，还是可以听懂

数学过程：

![image-20230606104934530](D:\Typora\notes\大二下学期\计算机网络\Pics\pic25.png)  

$d_i$：数据比特中的第i个

部分内容与书上有出入

1. 有一串数据比特（当然是二进制的），将0看作-1（为了数学方便），将每个比特分为M个（M的值是为了数学方便随便指定的）。

2. 然后对M个小比特进行编码（实际上是时隙，推出一个比特所需要的时间，但是不用这样理解）。

3. 发送接受双方在数据发送前约定好一串CDMA码，这串码也有M个1或-1组成。

4. 编码：然后用CDMA码中的分别去乘$d_i$中的每一个。比如$d_1$为-1，那么按照书上的结果就是依次的第一个小比特是-1\*1，第二个小比特也是-1\* 1，如此下来，实际上可以看出来比特为-1的情况编码后就跟CDMA码的形状上下颠倒了，比特为1则形状跟CDMA码的形状一致。
5. 解码：如对于$d_1$编码后的数据，接收方将M个小比特对CDMA编码中的M个1或-1依次相乘，得到的结果为 $\frac{(-1\cdot1)+(-1\cdot1)+(-1\cdot1)+(1\cdot-1)+(-1\cdot1)+(1\cdot-1)+(1\cdot-1)+(1\cdot-1)}{8}$ = -1，上面8个-1，那么结果就还会还原成一开始的$d_1$：-1。



对于有干扰的情况：

![image-20230606110357068](D:\Typora\notes\大二下学期\计算机网络\Pics\pic26.png) 



看上面的数学不要被误导，不是平方的意思，是第\*组数据比特

对于发生了碰撞的情况，进行同样的加密之后看起来就会乱掉（如图上下分别与CDMA码相乘后再相加），但是在接受方使用与发送方提前约定好的CDMA码再分别对碰撞后的数据比特进行还原，如想还原得到$d_1^1 = -1的值$，即$\frac{(0 \cdot 1)+(-2 \cdot 1)+(0 \cdot 1)+(2 \cdot -1)+(0 \cdot 1)+(0 \cdot -1)+(2 \cdot -1)+(2 \cdot -1)}{8}$  = -1，分母仍为-8。**不用想里面的具体数学式子，知道是这么个过程就行

### 无线网络例题

P382中P8

### LTE

P364

同时采用时分复用和频分复用，每个插槽（一个格子）代表一个频率的一个时隙。某个节点拿插槽的多少就代表它的传输速率大小。

把插槽称作LTE的时隙

![pic28](Pics\pic28.png) 

例题：P382中P10
