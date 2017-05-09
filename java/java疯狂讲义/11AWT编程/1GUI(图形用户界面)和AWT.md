# 1GUI(图形用户界面)和AWT
AWT是抽象窗口工具集,是窗口框架,它从不同平台的窗口系统中抽取共同组件,AWT程序仅指定了界面组件的位置和行为,当程序运行时,JVM调用操作系统本地的图形界面来创建和平台一致的对等体.

所有和AWT编程相关的类都放在java.awt包及其子包下面.
* 两种基类表示图形界面元素:
Component和MenuComponent,其中Component代表一个能以图形化方式显示出来,并可与用户交互的对象.MenuComponent代表图形界面的菜单组件.
* 两个重要的概念
Container和LayoutManager,其中Container是一种特殊的Component,它代表一种容器,可以盛装普通的Component;LayoutManager则是容器管理其它组件布局的方式.



Toolkit类:
此类是所有Abstract Window Toolkit实际实现的抽象超类.Toolkit的子类被用于将各种组件绑定到特定本机工具包实现.大多数应用程序不应直接调用该类中的任何方法.Toolkit定义的方法是一种“胶水”,将java.awt包中与平台无关的类与java.awt.peer中的对应物连接起来。Toolkit定义的一些方法能直接查询本机操作系统。
* static Toolkit getDefaultToolkit():获取默认工具包;
* abstract Dimension getScreenSize():获取屏幕的大小,在具有多个显示屏的系统上,使用主显示屏.以像素为单位.
* abstract int getScreenResolution():返回屏幕分辨率，以每英寸的点数为单位.


