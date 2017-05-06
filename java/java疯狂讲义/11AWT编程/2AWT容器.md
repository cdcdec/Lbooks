# 2AWT容器
容器(Container)是Component的子类,容器本身也是一个组件,具有组件的所有性质.
Component类的方法:


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
ScrollPane是一个带滚动条的容器,不能独立存在,必须被添加到其它容器中,默认使用BorderLayout作为其布局管理器.


