# 7使用JSlider和BoundedRangeModel创建滑动条
使用JSlider创建滑动条的步骤如下:
* 通过构造器创建JSlider对象,可以接收如下四个参数:
    * orientation:指定滑动条的摆放方向,默认是水平摆放.
    * min:指定滑动条的最小值,默认值是0;
    * max:指定滑动条的最大值,默认值是100;
    * value:指定滑动条的当前值,默认值是50;
* 调用JSlider的如下方法来设置滑动条的外观样式:
    * setExtent(int extent):设置滑动条上的保留区,用户拖动滑块时不能超过保留区.最大值为100的滑动条,如果设置保留区为20,则滑块最大只能拖动到80;
    * setInverted(boolean b):设置是否需要反转滑动条;
    * setLabelTable(Dictionary labels):为该滑动条指定刻度标签.刻度标签可以是任何组件;
    * setMajorTickSpacing(int n):设置主刻度标记的间隔;
    * setMinorTickSpacing(int n):设置次刻度标记的间隔;
    * setPaintLabels(boolean bl):设置是否在滑块上绘制刻度标签;
    * setPaintTrack(boolean bl):设置是否为滑块绘制滑轨;
    * setSnapToTicks(boolean bl):设置滑块是否必须停在滑道的有刻度处.
* 在拖动滑块时的监听:addChangeListener();
* 将JSlider对象添加到其他容器中显示出来.



