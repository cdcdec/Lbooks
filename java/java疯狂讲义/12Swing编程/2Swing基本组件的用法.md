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
JOptionPane所产生的对话框都是模式的,在用户完成与对话框的交互之前,showXxxDialog方法都将一直阻塞当前线程.JOptionPane所产生的对话框的布局是一定的,此布局包含以下四个区域:
* 输入区:输入区可以是普通文本框组件,也可以是下拉列表框组件.如果创建的对话框无须接收用户输入,则输入区不存在.
* 图标区:左上角的图标会随创建的对话框所包含消息类型的不同而不同,JOptionPane提供了如下5种消息类型:
    * ERROR_MESSAGE:错误信息,其图标是一个红色的X图标;
    * INFORMATION_MESSAGE:普通信息,其默认图标是蓝色的感叹号;
    * WARNING_MESSAGE:警告信息,其默认图标是黄色的感叹号;
    * QUESTION_MESSAGE:问题信息,其默认图标是绿色的问号;
    * PLAIN_MESSAGE:普通消息,没有默认图标;
* 消息区:消息区总是存在的,消息区的内容通过message参数来指定,根据message参数的类型不同,消息区显示的内容也是不同的.该message参数可以是如下几种类型:
    * String类型:系统将该字符串对象包装成JLabel对象,然后显示在对话框中;
    * Icon:该Icon被包装成JLabel后作为对话框的消息;
    * Component:将该Component在对话框的消息区中显示出来;
    * Object[]:对象数组被解释为在纵向排列的一系列message对象,每个message对象根据其实际类型又可以是字符串、图标、组件、对象数组等.
    * 其它类型:系统调用该对象的toString()方法返回一个字符串,并将该字符串对象包装成JLabel对象,然后显示在对话框中.
* 按钮区:对话框底部的按钮一定是存在的,但其所包含的按钮会随对话框的类型、选项类型而改变.
    * showInputDialog()和showMessageDialog()得到的对话框,底部是"确定","取消";
    * showConfirmDialog(),可以指定一个整数类型的optionType参数,该参数可以取如下几个值:
        * DEFAULT_OPTION:按钮区只包含一个"确定"按钮;
        * YES_NO_OPTION:按钮区包含"是""否"两个按钮;
        * YES_NO_CANCEL_OPTION:按钮区包含"是""否""取消"三个按钮;
        * OK_CANCEL_OPTION:按钮区包含"确定""取消"两个按钮;
    * showOptionDialog()创建对话框时,可以通过指定一个Object[]类型的options参数来设置按钮区能使用的选项按钮,options数组的数组元素可以是如下几种类型:
        * String类型:使用该字符串来创建一个JButton,并将其显示在按钮区;
        * Icon:使用该Icon来创建一个JButton,并将其显示在按钮区;
        * Component:直接将该组件显示在按钮区;
        * 其他类型:系统调用该对象的toString()方法返回一个字符串,并使用该字符串来创建一个JButton,并将其显示在按钮区;

当用户与对话框交互结束后,不同类型对话框的返回值如下:
* showMessageDialog:无返回值;
* showInputDialog:返回用户输入或选择的字符串;
* showConfirmDialog:返回一个整数代表用户选择的选项;
* showOptionDialog:返回一个整数代表用户选择的选项;

showConfirmDialog产生的对话框,有如下几个返回值:
* YES_OPTION:用户单击了"是"按钮后返回;
* NO_OPTION:用户单击了"否"按钮后返回;
* CANCEL_OPTION:用户单击了"取消"按钮后返回;
* OK_OPTION:用户单击了"确定"按钮后返回;
* CLOSED_OPTION:用户单击了对话框右上角的"X"按钮后返回;

JOptionPane常用的一些方法:

### showMessageDialog/showInternalMessageDialog消息对话框,告知用户某事已经发生
* static void showMessageDialog(Component parentComponent,Object message):
  调出标题为 "Message" 的信息消息对话框;
* static void showMessageDialog(Component parentComponent,Object message,String title,int messageType):调出对话框,它显示使用由messageType参数确定的默认图标的message.message表示要显示的Object,title对话框的标题字符串,messageType要显示的消息类型:ERROR_MESSAGE、INFORMATION_MESSAGE、WARNING_MESSAGE、QUESTION_MESSAGE 或 PLAIN_MESSAGE;
* static void showMessageDialog(Component parentComponent,Object message,String title,int messageType,Icon icon):调出一个显示信息的对话框,为其指定了所有参数.message:要显示的Object,
title:对话框的标题字符串,messageType:要显示的消息类型:ERROR_MESSAGE、INFORMATION_MESSAGE、WARNING_MESSAGE、QUESTION_MESSAGE或PLAIN_MESSAGE,
icon:要在对话框中显示的图标,该图标可以帮助用户识别要显示的消息种类.

### showConfirmDialog/showInternalConfirmDialog  确认对话框
* showConfirmDialog(Component parentComponent,Object message):调出带有选项Yes、No和Cancel的对话框;标题为Select an Option.
* showConfirmDialog(Component parentComponent,Object message,String title,int optionType):调出一个由optionType参数确定其中选项数的对话框.
* showConfirmDialog(Component parentComponent,Object message,String title,int optionType,int messageType):用一个由optionType参数确定其中选项数的对话框,messageType 参数确定要显示的图标.messageType参数主要用于提供来自外观的默认图标.
* showConfirmDialog(Component parentComponent,Object message,String title,int optionType,int messageType,Icon icon):调出一个带有指定图标的对话框,其中的选项数由optionType参数确定.messageType 参数主要用于提供来自外观的默认图标.

### showInputDialog/showInternalInputDialog 输入对话框
* Object showInputDialog(Component parentComponent,Object message,String title,int messageType,Icon icon,Object[] selectionValues,Object initialSelectionValue):提示用户在可以指定初始选择、可能选择及其他所有选项的模块化的对话框中输入内容.用户可以从selectionValues中进行选择,其中null表示用户可以输入想输入的任何内容,通常依靠JTextField来实现.initialSelectionValue是用于提示用户的初始值.由UI 决定如何最好的表示selectionValues,但通常情况下将使用JComboBox、JList或JTextField.
* String showInputDialog(Component parentComponent,Object message,Object initialSelectionValue):显示请求用户输入内容的问题消息对话框,它以parentComponent为父级.输入值将被初始化为initialSelectionValue.该对话框显示于Component的窗体的上部,通常位于Component之下.

### showOptionDialog/showInternalOptionDialog 自定义选项对话框
* int showOptionDialog(Component parentComponent,Object message,String title,int optionType,int messageType,Icon icon,Object[] options,Object initialValue):
    * parentComponent - 确定在其中显示对话框的Frame;如果为null或者parentComponent不具有Frame,则使用默认的Frame;
    * message - 要显示的Object;
    * title - 对话框的标题字符串;
    * optionType - 指定可用于对话框的选项的整数:DEFAULT_OPTION、YES_NO_OPTION、YES_NO_CANCEL_OPTION或OK_CANCEL_OPTION;
    * messageType - 指定消息种类的整数,主要用于确定来自可插入外观的图标:ERROR_MESSAGE、INFORMATION_MESSAGE、WARNING_MESSAGE、QUESTION_MESSAGE或PLAIN_MESSAGE;
    * icon - 在对话框中显示的图标;
    * options-指示用户可能选择的对象组成的数组;如果对象是组件,则可以正确呈现;非 String对象使用其toString方法呈现;如果此参数为null,则由外观确定选项;
    * initialValue - 表示对话框的默认选择的对象;只有在使用options时才有意义;可以为null.








