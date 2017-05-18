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
Swing通过JToolBar类来创建工具条,创建JToolBar对象时可以指定两个参数,JToolBar(String name, int orientation):name指定该工具条的名称,orientation指定工具条的方向;

JToolBar对象的几个常用方法:
* JButton add(Action a):通过Action对象为JToolBar添加对应的工具按钮;
* addSeparator(Dimension size):将指定大小的分隔符添加到工具栏的末尾;
* setFloatable(boolean b):设置 floatable 属性，如果要移动工具栏，此属性必须设置为 true。通常，可以将浮动工具栏拖动到同一个容器中的不同位置，或者拖动到自己的窗口中。此属性的默认值为 true。某些外观可能不实现浮动工具栏，它们将忽略此属性。
* setMargin(Insets m):设置工具栏边框和它的按钮之间的空白;
* setOrientation(int o):设置工具栏的方向;
* setRollover(boolean rollover):设置此工具栏的rollover状态;



## 6使用JFileChooser和Java7新增的JColorChooser
JColorChooser用于创建颜色选择器对话框:
* showDialog(Component component, String title, Color initialColor):显示一个模式的颜色选择器对话框,该方法返回用户所选颜色,component - 对话框的父Component,title - 包含对话框标题的String,initialColor - 显示颜色选取器时的初始Color设置;
* JDialog createDialog(Component c,String title,boolean modal,JColorChooser chooserPane,ActionListener okListener,ActionListener cancelListener):创建并返回包含指定 ColorChooser 窗格及 "OK"、"Cancel" 和 "Reset" 按钮的新对话框。如果按下 "OK" 或 "Cancel" 按钮，则对话框自动隐藏（但未释放）。如果按下 "Reset" 按钮，则将颜色选取器的颜色重置为上一次在对话框上调用 show 时设置的颜色，并且对话框仍然显示.


JFileChooser用于生成"打开文件","保存文件"对话框,JFileChooser提供了多个构造器来创建JFileChooser对象,它的构造器总共包含两个参数:
* currentDirectory:指定所创建文件对话框的当前路径;
* FileSystemView:用于指定基于该文件系统外观来创建文件对话框,如果没有指定该参数,则默认以当前文件系统外观创建文件对话框;

使用JFileChooser来建立文件对话框并允许用户选择文件的步骤如下:
* 采用构造器来创建一个JFileChooser对象,JFileChooser(String currentDirectoryPath),JFileChooser jf=new JFileChooser(".");以当前路径创建文件选择器;
* 调用JFileChooser的一系列方法:
    * addChoosableFileFilter(FileFilter filter):向用户可选择的文件过滤器列表添加一个过滤器;
    * setAcceptAllFileFilterUsed(boolean b):确定是否将AcceptAll FileFilter用作可选择过滤器列表中一个可用选项.如果为false,则从可用文件过滤器的列表中移除AcceptAll文件过滤器.如果为true,则AcceptAll文件过滤器将成为可用的文件过滤器.
    * setDialogTitle(String dialogTitle):设置显示在JFileChooser窗口标题栏的字符串.
    * setSelectedFile(File file):设置选中的文件.如果该文件的父目录不是当前目录,则将当前目录更改为该文件的父目录.
    * setSelectedFiles(File[] selectedFiles):如果将文件选择器设置为允许选择多个文件,则设置选中文件的列表.
    * setMultiSelectionEnabled(boolean b):设置文件选择器,以允许选择多个文件;
    * setFileSelectionMode(int mode):设置JFileChooser,以允许用户只选择文件、只选择目录,或者可选择文件和目录.默认值是JFilesChooser.FILES_ONLY.mode--要显示的文件类型,JFileChooser.FILES_ONLY,JFileChooser.DIRECTORIES_ONLY,JFileChooser.FILES_AND_DIRECTORIES.
    * setFileFilter(FileFilter filter):设置当前文件过滤器.文件选择器使用文件过滤器从用户的视图中过滤文件.
    * setFileView(FileView fileView):设置用于检索UI信息的文件视图,如表示文件的图标或文件的类型描述.
    * int showDialog(Component parent,String approveButtonText):弹出具有自定义approve按钮的自定义文件选择器对话框,parent 参数确定两件事情:打开的对话框所依赖的窗体,以及组件(放置对话框时外观应该考虑该组件的位置).如果parent是一个Frame对象(例如JFrame),则该对话框取决于该窗体,并且外观相对于窗体放置该对话框(例如在窗体上居中).如果parent是一个组件,则该对话框取决于包含该组件的窗体,并且相对于该组件放置该对话框(例如在组件上居中).如果parent为null,则该对话框取决于不可见的窗口,并且将其放置到与外观相关的位置,如屏幕的中央.返回值:该文件选择器被弹下时的返回状态,JFileChooser.CANCEL_OPTION,JFileChooser.APPROVE_OPTION,JFileChooser.ERROR_OPTION 如果发生错误或者该对话框已被解除.
    * int showOpenDialog(Component parent):弹出文件对话框,该对话框具有默认标题,"同意"按钮的文本是"打开";
    * int showSaveDialog(Component parent):弹出文件对话框,该对话框具有默认标题,"同意"按钮的文本是"保存";
    * File getSelectedFile():返回选中的文件.可由程序员通过setFile或者通过用户操作(如在UI中键入文件名,或者从UI中的列表内选择文件)来进行此设置.
    * File[] getSelectedFiles():如果将文件选择器设置为允许选择多个文件,则返回选中文件的列表.
    * void setAccessory(JComponent newAccessory):设置accessory组件.accessory通常用于显示已选中文件的预览图像;可按程序员的要求将其用来显示任何内容,如额外的自定义文件选择器控件.

FileView类用于改变文件对话框中文件的视图风格,其是一个抽象类,可以选择性地重写下面的几个方法:
    * String getDescription(File f):返回指定文件的可读描述;
    * Icon getIcon(File f):返回指定文件在JFileChooser对话框中的图标;
    * String getName(File f):返回指定文件的文件名;
    * String getTypeDescription(File f):返回指定文件所属文件类型的描述;
    * Boolean isTraversable(File f):当该文件是目录时,返回该目录是否是可遍历的;

## 7使用JOptionPane
JOptionPane可以用于创建一些简单的对话框.
