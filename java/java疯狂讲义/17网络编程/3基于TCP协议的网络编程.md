# 3基于TCP协议的网络编程
TCP/IP通信协议是一种可靠的网络通信协议,其在通信的两端各建立一个Socket,从而在通信的两端之间形成网络虚拟链路.一旦建立了虚拟的网络链路,两端的程序就可以通过虚拟链路进行通信.Java使用Socket对象来代表两端的通信端口,并通过Socket产生IO流来进行网络通信.
## TCP协议基础
IP协议全称是:Internet Protocol,即Internet协议,简称IP协议.通过使用IP协议,使Internet成为一个允许连接不同类型的计算机和不同操作系统的网络.IP协议负责将消息从一个主机传送到另一个主机,消息在传送的过程中被分割成一个个的小包.IP协议只保证计算机能发送和接收分组数据.

TCP协议是一种端对端协议,其负责收集信息包并将这些包按照适当的次序放好传送,接收端收到后再将其正确地还原.TCP协议保证了数据包在传送中的准确无误,TCP协议使用重发机制---当一个通信实体发送一个消息给另一个通信实体后,需要收到另一个通信实体的确认信息,如果没有收到另一个通信实体的确认信息,则会再次重发刚才发送的信息.

## 使用ServerSocket创建TCP服务器端
ServerSocket对象用于监听来自客户端的Socket连接,如果没有连接,它将一直处于等待状态.
### ServerSocket的构造函数:
* ServerSocket():创建非绑定服务器套接字;
* ServerSocket(int port):创建绑定到特定端口的服务器套接字.
    >port:端口号;或者为0,表示使用任何空闲端口.
* ServerSocket(int port,int backlog):利用指定的backlog创建服务器套接字并将其绑定到指定的本地端口号.
    >port:端口号;或者为0,表示使用任何空闲端口.
    >backlog:队列的最大长度,参数必须是大于0的正值,如果传递的值等于或小于0,则使用默认值.
* ServerSocket(int port,int backlog,InetAddress bindAddr):使用指定的端口、侦听backlog和要绑定到的本地IP地址创建服务器.
    >在机器上存在多个ip地址的情况下,可以使用bindAddr指定IP地址.

### ServerSocket的一些方法
* Socket accept():侦听并接受到此套接字的连接。此方法在连接传入之前一直阻塞;
* void close():关闭此套接字;

## 使用Socket进行通信
此类实现客户端套接字(也可以就叫“套接字”).套接字是两台机器间通信的端点.套接字的实际工作由SocketImpl类的实例执行。应用程序通过更改创建套接字实现的套接字工厂可以配置它自身，以创建适合本地防火墙的套接字。
### Socket的构造函数
* Socket():通过系统默认类型的 SocketImpl 创建未连接套接字;
* Socket(InetAddress address,int port):创建一个流套接字并将其连接到指定IP地址的指定端口号。
* Socket(String host,int port):创建一个流套接字并将其连接到指定主机上的指定端口号;
* Socket(InetAddress/String address,int port,InetAddress localAddr,int localPort):创建连接到指定远程主机、远程端口的Socket,并指定本地IP地址和本地端口,适用于本地主机有多个IP地址的情形;
### Socket的重要方法
* InputStream getInputStream():返回此套接字的输入流。
* OutputStream getOutputStream():返回此套接字的输出流。
### 加入多线程
客户端和服务端需要保持长时间的通信,并不断地读取对方的数据.
### 记录用户信息
客户端发送来的信息必须有特殊的标记,这样服务端可以判断这些信息是发给那个客户端的.
### 半关闭的Socket
Socket提供的半关闭方法:
* void shutdownInput():关闭该Socket的输入流;
* void shutdownOutput():关闭该Socket的输出流;
* boolean isInputShutdown():返回输入流是否被关闭;
* boolean isOutputShutdown():返回输出流是否被关闭;

>即使同一个Socket实例,先后调用了shutdownInput(),shutdownOutput方法,该Socket实例依然没有被关闭,只是该Socket既不会输出数据也不会输入数据.
当调用了Socket的半关闭方法关闭的输出流或输入流后,该Socket无法再次打开输入流或输出流,因此这种做法不适合保持持久通信状态的交互式应用.只适用于一站式的通信协议,例如http协议.

### 使用NIO实现非阻塞Socket通信



### 使用Java7的AIO实现非阻塞通信




