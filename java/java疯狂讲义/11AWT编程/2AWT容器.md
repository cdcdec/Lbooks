# 2AWT容器
容器(Container)是Component的子类,容器本身也是一个组件,具有组件的所有性质.component是一个具有图形表示能力的对象,可在屏幕上显示，并可与用户进行交互。典型图形用户界面中的按钮、复选框和滚动条都是组件示例.
Component类的方法:
* setLocation(int x, int y)/setLocation(Point p):设置组件的位置
* setSize(int width, int height)/setSize(Dimension d):设置组件的大小;
* setBounds(int x, int y, int width, int height)/setBounds(Rectangle r):同时设置组件的大小和位置;
* setVisible(boolean b):设置组件的可见性;
* setPreferredSize(Dimension preferredSize):将组件的首选大小设置为常量值;


## AWT提供的两种主要容器类
* Window:可独立存在的顶级窗口;
* Panel:可做为容器容纳其他组件,但不能独立存在,必须被添加到其它容器中.

## AWT常用的组件

### Frame组件
* Frame是Window的子类.Frame对象有标题,允许通过拖拉来改变窗口的位置,大小.
* 初始化时为不可见,可用setVisible(true)使其显示出来;
* 默认使用BorderlLayout作为其布局管理器.

### Panel组件
Panel代表不能独立存在,必须放在其它容器中的容器.Panel外在表现为一个矩形区域,该区域可盛装其它组件.其存在的意义是为其它组件提供空间.默认使用FlowLayout作为其布局管理器.

### ScrollPane
ScrollPane是一个带滚动条的容器,不能独立存在,必须被添加到其它容器中,默认使用BorderLayout作为其布局管理器.ScrollPane通常用于盛装其它容器,通常不允许改变ScrollPane的布局管理器.




