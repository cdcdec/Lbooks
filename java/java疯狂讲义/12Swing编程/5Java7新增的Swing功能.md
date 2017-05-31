# 5Java7新增的Swing功能

## 1使用JLayer装饰组件
JLayer的功能是在指定组件上额外地添加一个装饰层,开发者可以在这个装饰层上进行任意绘制(直接重写paint(Graphics g, JComponent c)方法),JLayer一般总是要和LayerUI一起使用,而LayerUI用于被扩展,扩展LayerUI时重写它的paint(Graphics g, JComponent c)方法.

## 2使用透明、不规则形状窗口
Frame的以下两个方法可以创建透明、不规则形状的窗口:
* setShape(Shape shape):设置窗口的形状,可以将窗口设置成任意不规则的形状;
* setOpacity(float opacity):设置窗口的透明度,可以将窗口设置成半透明的.当opacity为1.0f时,该窗口完全不透明.






