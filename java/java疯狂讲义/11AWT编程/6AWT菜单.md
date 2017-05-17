# 6AWT菜单
创建AWT菜单的方式:将菜单条、菜单、菜单项组合在一起即可.
## 菜单条、菜单和菜单项
AWT中的菜单由如下几个类组合而成:
* MenuBar:菜单条,菜单的容器;
* Menu:菜单组件,菜单项的容器,MunuItem的子类,可以作为菜单项使用;
* PopupMenu:上下文菜单组件(右键菜单组件);
* MenuItem:菜单项组件;
* CheckboxMenuItem:复选框菜单项组件;
* MenuShortcut:菜单快捷键组件;

MenuBar可用于盛装Menu,而Menu可用于盛装MenuItem(包括Menu和CheckMenuItem两个子类对象).Menu还有一个子类:PopupMenu,代表上下文菜单,上下文菜单无须使用MenuBar盛装.


Menu,MenuItem的构造器都可接收一个字符串参数,该字符串作为其对应菜单、菜单项上的标签文本.除此之外,MenuItem还可以接收一个MenuShortcut对象,用于指定该菜单的快捷键.例如:

```txt
//Ctrl+A   快捷键
MenuShortcut ms=new MenuShortcut(KeyEvent.VK_A);

//Ctrl+A+Shift
MenuShortcut ms=new MenuShortcut(KeyEvent.VK_A,true);

```

### 菜单分组  两种方法
* 调用Menu对象的addSeparator()方法来添加菜单分割线;
* 使用添加new MenuItem("-")的方式来添加菜单分割线;

### 创建菜单步骤
* 创建Menu,MenuBar,MenuItem对象;
* 调用Menu的add()方法将多个MenuItem组合成菜单(也可将另一个Menu对象组合进来,从而形成二级菜单);
* 调用MenuBar的add()方法将多个Menu组合成菜单条;
* 最后调用Frame对象的setMenuBar()方法为该窗口添加菜单条;


## 右键菜单
创建右键菜单的步骤如下:
* 创建PopupMenu对象
* 创建多个MenuItem的多个实例,依次将这些实例加入PopupMenu中;
* 将PopupMenu加入到目标组件中;
* 为需要出现上下文菜单的组件编写鼠标监听器,当用户释放鼠标右键时弹出右键菜单;


