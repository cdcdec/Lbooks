# 7在AWT中绘图

## 画图的实现原理
在Component类里面提供了和绘图有关的三个方法:
* paint(Graphics g):绘制组件的外观;
* update(Graphics g):调用paint()方法,刷新组件外观;
* repaint():调用update()方法,刷新组件外观.

Container类中的update()方法先以组件的背景色填充整个组件区域,然后调用paint()方法重画组件.程序不应该主动调用组件的paint()和update()方法,这两个方法都由AWT系统负责调用.通常情况下,程序通过重写paint()方法实现在AWT组件上绘图;


## 使用Graphics类
Graphics是一个抽象的画笔对象,Graphics可以在组件上绘制几何图像和位图.
* drawLine():绘制直线;
* drawString():绘制字符串;
* drawRect():绘制矩形;
* drawRoundRect():绘制圆角矩形;
* drawOval():绘制椭圆形状;
* drawPolygon():绘制多边形边框;
* drawArc():绘制一段圆弧(可能是椭圆的圆弧)
* drawPolyline():绘制折线;
* fillRect():填充一个矩形区域;
* fillRoundRect():填充一个圆角矩形区域;
* fillOval():填充椭圆区域;
* fillPolygon():填充一个多边形区域;
* fillArc():填充圆弧和圆弧两个端点到中心线所包围的区域;
* drawImage():绘制位图.

setColor(),setFont()用于设置画笔的颜色和字体(仅当绘制字符串时有效);


### Canvas类
绘图的画布,程序可以通过创建Canvas类的子类,并重写它的paint()方法来实现绘图.

### 动画
可以利用Timer类和组件的repaint()方法开发动画.
Timer(int delay,ActionListener listener)每间隔delay秒,系统自动触发ActionListener监听器里面的事件处理器(actionPerformed()方法).

>Swing组件没有提供Canvas对应的组件,使用Swing的Panel组件作为画布即可.









