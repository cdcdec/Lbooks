# 1基本Annotation
4个基本的Annotation如下:
@Override,@Deprecated,@Suppress Warnings,@SafeVarargs(Java7新增的),定义在java.lang包下。
## 限定重写父类方法@Override
@Override用来指定方法覆盖的,强制一个子类必须覆盖父类的方法(如果子类没有覆盖这个方法,则编译器会报错)。其只能用于方法，用于避免一些错误。
## 标记已过时@Deprecated
@Deprecated用于标记某一个程序元素(类,方法等)已过时,当其它程序使用这个类或方法时,编译器会发出警告.
## 抑制编译器警告@Suppress Warnings
@Suppress Warnings指示被该Annoation修饰的程序元素(以及该程序元素中的所有子元素)取消显示指定的编译器警告.
```txt
1.在类上面关闭编译器警告
import java.util.ArrayList;
import java.util.List;
//关闭整个类里的编译器警告
@SuppressWarnings({ "rawtypes", "unchecked" })
public class SuppressWarningsTest {
    public static void main(String[] args) 
    {
        List<String> myList = new ArrayList();
        System.out.println(myList.isEmpty());
    }
}
2.在方法上关闭编译器警告:
import java.util.ArrayList;
import java.util.List;
public class SuppressWarningsTest {
    @SuppressWarnings({ "rawtypes", "unchecked" })
    public static void main(String[] args) 
    {
        List<String> myList = new ArrayList();
        System.out.println(myList.isEmpty());
    }
}
3.在相关的代码上面关闭编译器警告
import java.util.ArrayList;
import java.util.List;
public class SuppressWarningsTest {
    public static void main(String[] args) 
    {   
        @SuppressWarnings({ "rawtypes", "unchecked" })
        List<String> myList = new ArrayList();
        System.out.println(myList.isEmpty());
    }
}
```
