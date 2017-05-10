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
## 3使用JLayeredPane、JDesktopPane和JInternalFrame

