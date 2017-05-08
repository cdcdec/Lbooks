# 10使用JTree和TreeModel创建树
计算机里面的树是由一系列具有严格父子关系的节点组成的.节点的分类:
* 普通节点:包含子节点的节点,具有唯一的父节点;
* 叶子节点:没有子节点的节点,不能作为父节点;
* 根节点:没有父节点的节点；
使用Swing里面的JTree和TreeModel和相关的辅助类创建树.
## 1创建树
JTree的构造函数:
* JTree():返回带有示例模型的JTree;
* JTree(Hashtable<?,?> value)返回从Hashtable创建的JTree，它不显示根;
* JTree(Object[] value)返回JTree,指定数组的每个元素作为不被显示的新根节点的子节点。
* JTree(TreeModel newModel)返回JTree的一个实例，它显示根节点-使用指定的数据模型创建树。
* JTree(TreeNode root)返回JTree,指定的TreeNode作为其根,它显示根节点。
* JTree(TreeNode root, boolean asksAllowsChildren)
返回JTree,指定的TreeNode作为其根,它用指定的方式显示根节点,并确定节点是否为叶节点。
* JTree(Vector<?> value)返回JTree,指定Vector的每个元素作为不被显示的新根节点的子节点.

TreeNode接口及其子接口和实现类

MutableTreeNode是TreeNode的子接口;
DefaultMutableTreeNode是MutableTreeNode的默认实现类.此类提供按各种顺序有效地遍历树或子树,或者沿着两节点间的路径进行遍历的枚举,还可以保存对用户对象的引用,用户对象由用户使用.常用方法如下:
* Enumeration breadthFirstEnumeration():创建并返回一个枚举,该枚举按广度优先的顺序遍历以此节点为根的子树.由枚举的nextElement()方法返回的第一个节点是此节点.通过插入、移除或移动节点修改树可以使修改前创建的任何枚举无效.
* Enumeration preorderEnumeration():创建并返回按前序遍历以此节点为根的子树的一个枚举.由枚举的nextElement()方法返回的第一个节点是此节点.通过插入、移除或移动节点修改树可以使修改前创建的任何枚举无效。
* Enumeration depthFirstEnumeration():创建并返回一个枚举,该枚举按深度优先的顺序遍历以此节点为根的子树.由枚举的nextElement()方法返回的第一个节点是最左边的叶节点.这与后序遍历相同.
通过插入、移除或移动节点修改树可以使修改前创建的任何枚举无效。
* Enumeration postorderEnumeration():创建并返回按后序遍历以此节点为根的树的一个枚举.由枚举的nextElement()方法返回的第一个节点是最左边的叶节点.这与深度优先遍历相同.
通过插入、移除或移动节点修改树可以使修改前创建的任何枚举无效.
* DefaultMutableTreeNode getNextSibling():返回父节点的子节点数组中此节点的下一个兄弟节点.如果此节点没有父节点,或者是父节点的最后一个子节点,则返回null.
* add(MutableTreeNode newChild):从其父节点移除newChild,并通过将其添加到此节点的子数组的结尾,使其成为此节点的子节点.


DefaultMutableTreeNode的构造函数:
* DefaultMutableTreeNode():创建没有父节点和子节点的树节点,该树节点允许有子节点.
* DefaultMutableTreeNode(Object userObject)创建没有父节点和子节点、但允许有子节点的树节点,并使用指定的用户对象对它进行初始化.
* DefaultMutableTreeNode(Object userObject, boolean allowsChildren)创建没有父节点和子节点的树节点,使用指定的用户对象对它进行初始化,仅在指定时才允许有子节点.


## 2拖动、编辑树节点
## 3监听节点事件
## 4使用DefaultTreeCellRenderer改变节点外观
## 5扩展DefaultTreeCellRenderer改变节点外观
## 6实现TreeCellRenderer改变节点外观




