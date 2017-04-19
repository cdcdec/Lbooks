# 11使用JAR文件
JAR文件的全称是Java Archive File,Java档案文件.Jar文件的好处:
* 安全,可以对Jar文件进行数字签名,只让能够识别数字签名的用户使用里面的东西;
* 加快下载速度;
* 压缩,使文件变小,JAR的压缩机制和ZIP完全相同.
* 包装型,能够让JAR包里的文件依赖于统一版本的类文件.
* 可移植性。

## jar命令详解

```txt
用法: jar {ctxui}[vfmn0PMe] [jar-file] [manifest-file] [entry-point] [-C dir] files ...
选项:
    -c  创建新档案
    -t  列出档案目录
    -x  从档案中提取指定的 (或所有) 文件
    -u  更新现有档案
    -v  在标准输出中生成详细输出
    -f  指定档案文件名
    -m  包含指定清单文件中的清单信息
    -n  创建新档案后执行 Pack200 规范化
    -e  为捆绑到可执行 jar 文件的独立应用程序
        指定应用程序入口点
    -0  仅存储; 不使用任何 ZIP 压缩
    -P  保留文件名中的前导 '/' (绝对路径) 和 ".." (父目录) 组件
    -M  不创建条目的清单文件
    -i  为指定的 jar 文件生成索引信息
    -C  更改为指定的目录并包含以下文件
如果任何文件为目录, 则对其进行递归处理。
清单文件名, 档案文件名和入口点名称的指定顺序
与 'm', 'f' 和 'e' 标记的指定顺序相同。

示例 1: 将两个类文件归档到一个名为 classes.jar 的档案中:
       jar cvf classes.jar Foo.class Bar.class
示例 2: 使用现有的清单文件 'mymanifest' 并
           将 foo/ 目录中的所有文件归档到 'classes.jar' 中:
       jar cvfm classes.jar mymanifest -C foo/ .

````




* 创建jar文件:jar cf test.jar test,将当前路径下的test文件夹中的全部内容(包括文件与子文件夹)生成一个test.jar文件,如果当前目录中已经存在了test.jar文件,那么该文件会被覆盖。
* 创建jar文件,并显示压缩过程:jar cvf test.jar test
* 不使用清单文件:jar cvfM test.jar test;
* 自定义清单文件内容:jar cvfm test.jar manifest.mf test
    清单文件的内容由如下格式的多个key-value对组成.key:<空格>value.清单文件的内容格式要求如下:
    * 每行只能定义一个key-value对,每行的key-value对之前不能有空格,即key-value对必须顶格写.
    * 每组key-value对之间以":"(英文冒号后紧跟一个英文空格)分割;
    * 文件开头不能有空行;
    * 文件必须以一个空行结束;
```txt
jar cvfm test.jar aaa.txt test
//aaa.txt的内容是:Specification-Version: 1.1
报错如下:
java.io.IOException: invalid header field
        at java.util.jar.Attributes.read(Attributes.java:410)
        at java.util.jar.Manifest.read(Manifest.java:199)
        at java.util.jar.Manifest.<init>(Manifest.java:69)
        at sun.tools.jar.Main.run(Main.java:176)
        at sun.tools.jar.Main.main(Main.java:1288)

```
* 查看jar包内容:jar tf test.jar,在test.jar文件已经存在的情况下,此命令可以查看test.jar中的内容.当jar包中的文件路径和文件非常多时,直接使用该命令可能将无法看到包的全部内容,此时可利用重定向将显示结果保存到文件中,如:jar tf test.jar > a.txt
* 查看jar包详细内容:jar tvf test.jar;比jar tf test.jar命令多显示了文件的创建时间。
* 解压缩:jar xf test.jar,将test.jar文件解压缩到当前目录下,不显示任何信息.
* 带提示信息解压缩:jar xvf test.jar,将test.jar文件解压缩到当前目录下,并显示解压过程中的详细信息;
* 更新jar文件:jar uf test.jar Hello.class,更新test.jar中的Hello.class文件,如果test.jar中已经有了Hello.class文件,则使用新的class文件替换原来的class文件,如果没有class文件,则将这个文件添加进去.
* 更新时显示详细信息:jar uvf test.jar Hello.class;

## 创建可执行的JAR包
* 使用批处理文件执行java文件:建立一个批处理文件,内容如下:java package.MainClass
  >命令没有执行,原因不明;
* 使用批处理文件执行java文件,并且不保留运行java程序的命令行窗口:建立一个批处理文件,内容如下:start javaw package.MainClass
  >命令没有执行,原因不明;
* 创建可以执行的jar包:jar cvfe e.jar com/cdc/test/Main com
  将com文件夹里面的class文件打成jar包(jar包的名字是e.jar),并指定里面的com.cdc.test.Main.class文件作为主类。
* 执行jar包的两种方式
    * java -jar e.jar 
    * javaw e.jar  //这条命令没有执行