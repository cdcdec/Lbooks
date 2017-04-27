# 3基于TCP协议的网络编程
TCP/IP通信协议在通信的两端各建立一个Socket,从而在通信的两端之间形成网络虚拟链路.一旦建立了虚拟的网络链路,两端的程序就可以通过虚拟链路进行通信.Java使用Socket对象来代表两端的通信端口,并通过Socket产生IO流来进行网络通信.
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
### Socket的构造函数


