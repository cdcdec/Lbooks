# Java7新增的包装类
为了解决8中基本数据类型不能当成Object类型变量使用的问题,Java提供了包装类,通过包装类可以进行基本数据类型和Object对象之间的转换。
## 8中基本数据类型和它们对应的包装类
* byte---------->Byte
* short--------->Short
* int----------->Integer
* long---------->Long
* char---------->Character
* float--------->Float
* double-------->Double
* boolean------->Boolean

## 示例
```txt
//基本数据类型转对象
boolean bl=true;
Boolean blObj1=new Boolean(bl);
Boolean blObj2=new Boolean("true");//true不论大小写都可以
Boolean blObj3=new Boolean("FALSE");//非true(大小写不敏感)的字符串,都将解析为false
Boolean blObj4=new Boolean("kl");//非true(大小写不敏感)的字符串,都将解析为false

int a=8;
Integer integer1=new Integer(a);
/**
 * Integer(String s) 
 * 构造一个新分配的 Integer对象，它表示String参数所指示的int值。
 * s必须是数字型的整数,否则会报java.lang.NumberFormatException
 * 如:Integer integer2=new Integer("80.7");
 */
Integer integer2=new Integer("80");
```
>如果使用一个字符串来创建Byte,Short,Integer,Long,Float和Double等包装类对象时,如果传入的字符串不能成功转换成相应的基本数据类型,则会引发java.lang.NumberFormatException异常。

```txt
//获取包装类中对应的基本数据类型
boolean b=blObj1.booleanValue();
int c=integer1.intValue();
float fl=ff.floatValue();


```

## 自动装箱和自动拆箱(Java1.5提供)
* 自动装箱(Autoboxing):把一个基本类型变量直接赋给对应的包装类变量,或者赋给Object变量.Integet a=5;Object ob=false;
* 自动拆箱(AutoUnboxing):允许直接把包装类对象直接赋给一个对应的基本类型变量.Interger a=new Integer("5");int b=a;

## 字符串和基本类型变量之间的转换
* 利用包装类提供的静态方法parseXXX(String s),除了Character之外的所有包装类都提供了该方法;
* 利用包装类提供的Xxx(String s)构造器;
* String类提供的多个重载的valueOf()方法,将基本类型变量转成字符串;
* 将基本类型变量和""进行连接运算,则系统自动将基本类型变量转成字符串.

## 比较
* 包装类的实例可以直接和数值类型的值比较(系统会自动取出包装类实例所包装的数值),例如:Integer a=new Integer(5);boolean bl=a>5.0;
* 两个包装类实例进行比较,只有两个包装类指向同一个对象时才返回true.
    ```txt
    Integer a=new Integer(2);
    Integer b=new Integer(2);
    blloean bl=a==b;//false

    ```
* 自动装箱的比较
    ```txt
    Integer a=2;
    Integer b=2;
    System.out.println(a==b);//true
    Integer a2=128;
    Integer b2=128;
    //不在-127到128之间的会返回false
    System.out.println(a2==b2);//false
    ```
* Java7为包装类提供的静态compare(xxx val1,xxx val2)方法可以比较两个基本数据类型的大小;

