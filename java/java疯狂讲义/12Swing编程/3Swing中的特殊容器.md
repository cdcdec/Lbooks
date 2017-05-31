# 3Swing中的特殊容器

## 1使用JSplitPane
JSplitPane用于创建一个分割面板,它可以将一个组件(通常是一个容器)分割成来两个部分,并提供一个分割条,用户可以拖动该分割条来调整两个部分的大小.分割面板实质上是一个容器,该容器只能容纳两个组件(上下两个或者左右两个).

* setDividerSize(int newSize)/int getDividerSize():设置/返回分隔条的大小,以像素为单位;
* void setResizeWeight(double value):指定当分隔窗格的大小改变时如何分配额外空间.在默认情况下,值为0表示右边/底部的组件获得所有额外空间(左边/顶部的组件固定),而值为1表示左边/顶部的组件获得所有额外空间(右边/底部的组件固定).特别地,左边/顶部的组件获得(weight * diff)额外空间,并且右边/底部的组件获得(1 - weight)*diff额外空间.
* setContinuousLayout(boolean newContinuousLayout):该参数指定分割面板是否支持"连续布局",如果分割面板支持连续布局,则用户拖动分割条时两边组件将会不断调整大小;如果不支持连续布局,则拖动分割条时两边组件不会调整大小,而是只看到一条虚拟的分割条在移动.JSplitPane默认关闭连续布局特性,因为使用连续布局需要不断重绘两边的组件,因此运行效率很低.
* setOneTouchExpandable(boolean newValue):设置oneTouchExpandable属性的值,要使JSplitPane 在分隔条上提供一个 UI 小部件来快速展开/折叠分隔条,此属性必须为true.此属性的默认值为false.有些外观可能不支持一键展开;它们将忽略此属性.
* setDividerLocation(double proportionalLocation):设置分隔条的位置为JSplitPane大小的一个百分比;
* setDividerLocation(int location):设置分隔条的位置,一个值小于0意味着分隔条应该重设为试图遵守左边/顶部组件首选大小的一个值;
* setLeftComponent(Component comp)/setTopComponent(Component comp):将分割条设置在面板的上边或者左边;
* setRightComponent(Component comp)/setBottomComponent(Component comp):将分割条设置在面板的下边或者右边;


## 2使用JTabbedPane
JTabbedPane可以很方便地在窗口上放置多个标签页,每个标签页相当于获得了一个与外部容器具有相同大小的组件摆放区域.
JTabbedPane的构造函数:
* JTabbedPane():创建一个具有默认的JTabbedPane.TOP选项卡布局的空TabbedPane.
* JTabbedPane(int tabPlacement):创建一个空的TabbedPane,使其具有以下指定选项卡布局中的一种:JTabbedPane.TOP、JTabbedPane.BOTTOM、JTabbedPane.LEFT或JTabbedPane.RIGHT;
* JTabbedPane(int tabPlacement,int tabLayoutPolicy):创建一个空的TabbedPane,使其具有指定的选项卡布局和选项卡布局策略.布局可以是以下几种之一:JTabbedPane.TOP、JTabbedPane.BOTTOM、JTabbedPane.LEFT或JTabbedPane.RIGHT.布局策略可以是以下两种之一:JTabbedPane.WRAP_TAB_LAYOUT或JTabbedPane.SCROLL_TAB_LAYOUT.

JTabbedPane对象的常用方法:


## 3使用JLayeredPane、JDesktopPane和JInternalFrame
JLayeredPane是一个代表有层次深度的容器,它允许组件在需要时互相重叠.当向JLayeredPane容器中添加组件时,需要为该组件指定一个深度索引,其中层次索引较高的层里面的组件位于其他层的组件之上.为方便起见,JLayeredPane将该深度范围分成几个不同的层.将组件放入相应的层,这样更容易确保组件正确地重叠,而不必担心为具体的深度指定编号:
* DEFAULT_LAYER:大多数组件位于的标准层.这是最底层.
* PALETTE_LAYER:调色板层位于默认层之上.它们对于浮动工具栏和调色板很有用,因此可以位于其他组件之上.
* MODAL_LAYER:该层用于模式对话框.它们将出现在容器中所有工具栏、调色板或标准组件的上面.
* POPUP_LAYER:弹出层显示在对话框的上面.这样,与组合框、工具提示和其他帮助文本关联的弹出式窗口将出现在组件、调色板或生成它们的对话框之上.
* DRAG_LAYER:拖动一个组件时,将该组件重分配到拖动层可确保将其定位在容器中的其他所有组件之上.完成拖动后,可将该组件重分配到其正常层.

可以使用JLayeredPane的方法moveToFront(Component)、moveToBack(Component)和setPosition在组件所在层中对其进行重定位.还可以使用setLayer方法更改该组件的当前层.

JDesktopPane用于创建多文档界面或虚拟桌面的容器.用户可创建JInternalFrame对象并将其添加到 JDesktopPane.JDesktopPane扩展了JLayeredPane,以管理可能的重叠内部窗体.它还维护了对DesktopManager实例的引用,这是由UI类为当前的外观(L&F)所设置的.注意,JDesktopPane不支持边界.

此类通常用作JInternalFrames的父类,为JInternalFrames提供一个可插入的DesktopManager对象.特定于L&F的实现installUI负责正确设置desktopManager变量.JInternalFrame的父类是JDesktopPane时,它应该将其大部分行为(关闭、调整大小等)委托给desktopManager.

使用JDesktopPane和JInternalFrame创建内部窗口按如下步骤进行即可:
* 创建一个JDesktopPane对象,该对象代表一个虚拟桌面;
* 使用JInternalFrame创建一个内部窗口,创建窗口时可以传入一些参数用于指定JInternalFrame的标题,图标以及是否可调整、可关闭、可最大化,可图表化.
* 将该内部窗口以合适大小、在合适位置显示出来.该窗口默认大小是0X0像素,位于0,0位置(虚拟桌面的左上角处),并且默认处于隐藏状态.
    ```txt
        //同时设置窗口的大小和位置
        iframe.reshape(20,20,300,400);
        //使该窗口可见,并尝试选中它
        iframe.show();
    ```
* 将内部窗口添加到JDesktopPane容器中,再将JDesktopPane容器添加到其他容器中.


拖动虚拟窗口的模式:JDesktopPane的setDragMode()方法设置内部窗口的拖动模式:
* JDesktopPane.OUTLINE_DRAG_MODE:拖动过程中仅显示内部窗口的轮廓;
* JDesktopPane.LIVE_DRAG_MODE:拖动过程中显示完整窗口,这是默认选项.系统会不断重绘虚拟桌面的内部窗口,从而引起性能下降.

弹出内部对话框showInternalXxxDialog()方法:
当使用该方法弹出内部对话框时,需要指定一个父组件,这个父组件即可以是虚拟桌面(JDesktopPane对象),也可以是内部窗口(JInternalFrame对象)





