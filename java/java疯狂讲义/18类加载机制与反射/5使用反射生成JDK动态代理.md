# 5使用反射生成JDK动态代理
在java.lang.reflect包下面的Proxy类和InvocationHandler接口,通过使用这个类和接口可以生成JDK动态代理类和动态代理对象.
## 使用Proxy和InvocationHandler创建动态代理
Proxy提供用于创建动态代理类和实例的静态方法,它还是由这些方法创建的所有动态代理类的超类.Proxy提供的用于实现创建动态代理类和动态代理实例的方法:
* static Class<?> getProxyClass(ClassLoader loader,Class<?>... interfaces):返回代理类的 java.lang.Class对象,并向其提供类加载器和接口数组。该代理类将由指定的类加载器定义,并将实现提供的所有接口。如果类加载器已经定义了具有相同排列接口的代理类，那么现有的代理类将被返回;否则,类加载器将动态生成并定义这些接口的代理类。
* static Object newProxyInstance(ClassLoader loader,Class<?>[]interfaces,InvocationHandler h):返回一个指定接口的代理类实例，该接口可以将方法调用指派到指定的调用处理程序.
```txt
package reflex;
import java.lang.reflect.InvocationHandler;
import java.lang.reflect.Method;
import java.lang.reflect.Proxy;
public class ProxyTest {
    public static void main(String[] args) {
        // 创建一个InvocationHandler对象
        InvocationHandler handler = new MyInvokationHandler();
        // 使用指定的InvocationHandler来生成一个动态代理对象
        Person p = (Person) Proxy.newProxyInstance(
                Person.class.getClassLoader(), new Class[] { Person.class },
                handler);
        // 调用动态代理对象的walk()和sayHello()方法
        p.walk();
        p.sayHello("孙悟空");
    }
}
interface Person {
    void walk();

    void sayHello(String name);
}
class MyInvokationHandler implements InvocationHandler {
    /*
     * 执行动态代理对象的所有方法时,都会被替换成执行如下的invoke方法:
     * 其中:proxy:代表动态代理对象
     * method:代表正在执行的方法
     * args:代表调用目标方法时传入的实参。
     */
    public Object invoke(Object proxy, Method method, Object[] args) {
        System.out.println("----正在执行的方法:" + method);
        if (args != null) {
            System.out.println("下面是执行该方法时传入的实参为：");
            for (Object val : args) {
                System.out.println(val);
            }
        } else {
            System.out.println("调用该方法没有实参！");
        }
        return null;
    }
}
```
在普通编程过程中,无须使用动态代理,但是在编写框架或底层基础代码时,动态代理的作用就非常大。

## 动态代理和AOP
JDK动态代理只能为接口创建动态代理.
场景:既要执行某方法,又不以硬编码的方式去调用某个方法.
AOP(Aspect Orient Programming,面向切面编程)。