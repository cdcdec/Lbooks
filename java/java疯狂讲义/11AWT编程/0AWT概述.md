# 0AWT概述
Java使用AWT和Swing类完成图形用户界面编程,AWT全称是:抽象窗口工具集(Abstract Window Toolkit).

所有和AWT编程相关的类都放在java.awt包以及它的子包中,AWT编程中有两个基类:Component和MenuComponent.Component代表一个能以图像化方式显示出来,并可以与用户交互的对象;MenuComponent代表图形界面的菜单组件,包括MenuBar(菜单条),MenuItem(菜单项)等子类;

## Container和LayoutManager
Container是一种特殊的Component,它代表一种容器,可以盛装普通的Component;
LayoutManager:是容器管理其它组件布局的方式;


