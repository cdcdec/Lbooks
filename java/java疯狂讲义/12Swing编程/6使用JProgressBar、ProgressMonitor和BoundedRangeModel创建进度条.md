# 6使用JProgressBar、ProgressMonitor和BoundedRangeModel创建进度条

## 1创建进度条
创建JProgressBar对象时可以指定进度条的排列方向(竖直和水平),进度条的最大值和最小值.JProgressBar的常用方法:
* 排列方向,最大值,最小值的setter和getter方法;
* setBorderPainted(boolean b):设置进度条是否使用边框;
* setIndeterminate(boolean newValue):进度是否确定;
* setStringPainted(boolean b):设置是否在进度条中显示完成百分比;
* getPercentComplete():返回进度条的完成百分比;
* getString():返回当前进度的String表示形式;
* getModel().addChangeListener(new ChangeListener(){}):进度条改变的事件监听
## 2创建进度对话框
ProgressMonitor(Component parentComponent,Object message,String note,int min,int max):
* parentComponent - 对话框的父组件
* message - 要显示给用户的描述消息，以指示在监视什么操作。这不随操作进度而更改;
* note - 描述操作状态的简短注释.随着操作的进行,可以调用setNote来更改显示的注释.
* min - 范围的下边界;
* max - 范围的上边界;







