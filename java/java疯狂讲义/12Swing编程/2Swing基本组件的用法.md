# 2Swing基本组件的用法
## 1Java7的Swing组件层次
大部分Swing组件都是JComponent抽象类的直接或间接子类.JComponent是java.awt.Container类的子类.Swing组件中的有四个组件直接继承了AWT组件,而不是从JComponent派生的,它们分别是JFrame,JWindow,JDialog和JApplet,它们不是轻量级组件,是重量级组件.Swing组件的类名和和对应AWT组件的类型也基本一致,只要在原来的AWT组件类型前添加"J"即可,但有如下几个例外:
* JComboBox:--->Choice;
* JFileChooser:--->FileDialog;
* JSrcollBar--->Scrollbar;
* JCheckBox:--->Checkbox;
* JCheckBoxMenuItem--->CheckboxMenuItem;

将Swing组件按照功能来分,可分为如下几类:
* 顶层容器:JFrame,JApplet,JDialog和JWindow;
* 中间容器:JPanel,JScrollPane,JSplitPane,JToolBar等;
* 特殊容器:在用户界面上具有特殊作用的中间容器,如JInternalFrame,JRootPane,JLayeredPane,JDestopPane等;
* 基本组件:JButton,JComboBox,JList,JMenu,JSlider等;
* 不可编辑信息的显示组件:JLabel,JProgressBar,JToolTip;
* 可编辑信息的显示组件:JTable,JTextArea,JTextField等;
* 特殊对话框组件:JColorChooser,JFileChooser;
## 2AWT组件的Swing实现
Swing为除了Canvas之外的所有AWT组件提供了相应的实现.相对于AWT组件,Swing组件具有以下4个额外的功能:
* 可以为Swing组件设置提示信息---setToolTipText()方法;
* 很多Swing组件除了使用文字外,还可以使用图标修饰自己;
* 支持插拔式的外观风格;
* 支持设置边框;

## 3为组件设置边框
可以调用JComponent提供的setBorder(Border b)方法为Swing组件设置边框,其中Border是Swing提供的一个接口.为Swing组件添加边框可按如下步骤进行:
* 使用BorderFactory或者XxxBorder创建XxxBorder实例;
* 调用Swing组件的setBorder(Border b)方法为该组件设置边框;
## 4Swing组件的双缓冲和键盘驱动
* 所有的Swing组件默认启用双缓冲绘图技术,如果要关闭双缓冲,则调用setDoubleBuffered(false)方法;
* 所有的Swing组件都提供了简单的键盘驱动,允许用户通过键盘操作来替代鼠标驱动GUI上的Swing组件,相当于为GUI组件提供快捷键;
## 5使用JToolBar创建工具条


## 6使用JFileChooser和Java7新增的JColorChooser

## 7使用JOptionPane

