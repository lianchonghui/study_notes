# java基础笔记
---
[TOC]
---


## java关键术语
---
## java环境配置
---
## java程序结构基础
---
## java类和对象
### 细节总结
#### static类和非static类
##### static类
static类是
##### static类和非static类的关系
static类只能使用static类创建对象，非static类能用非static类和static类创建对象。

---
## java继承
## java接口和内部类
### 接口
### 对象克隆
#### 拷贝和克隆
##### 浅拷贝和深拷贝
默认的clone()是浅拷贝，clone()继承自Object类的protected方法，Object对具体的一无所知，如果子类只有数组和基本类型则没有问题，如果含有子对象的引用，这些子对象也是需要自己调用clone()方法。这就要求对需要克隆的类重写clone()方法，并声明为public,表明该类所有的方法能克隆对象。该类要实现一个标记接口Cloneable，否则会报一个已检验异常(checked exception)。
```java
class Person implements Cloneable{
    private Date birth=new Date();
    @Override
    public Object clone() throws CloneNotSupportedException {
        Person cloned=(Person)super.clone();
        cloned.birth=(Date)birth.clone();
        return cloned;
    }
}
```
### 接口与回调
### 内部类
### 代理
代理包含静态代理和动态代理。
#### 静态代理
```java
interface Subject {
    void request();
}
class RealSubject implements Subject {
    public void request(){
        System.out.println("RealSubject");
    }
}
class Proxy implements Subject {
    private Subject subject;

    public Proxy(Subject subject){
        this.subject = subject;
    }
    public void request(){
        System.out.println("begin");
        subject.request();
        System.out.println("end");
    }
}
public class ProxyTest {
    public static void main(String args[]) {
        RealSubject subject = new RealSubject();
        Proxy p = new Proxy(subject);
        p.request();
    }
}
```
#### 动态代理
实现动态代理主要关注以下对象或方法：
- 被代理对象实现的接口
- 被代理对象
  ```proxyed```
- 代理对象
  代理对象通过```Proxy.newProxyInstance(ClassLoader loader, Class<?>[] interfaces, InvocationHandler h)```生成
  - 参数loader： 
  1.```YourProxy.class.getClassLoader()```
  2.```Thread.currentThread().getContextClassLoader()```
  3.根据情况可以传入```null```
  - 参数interfaces,被代理对象数组需要实现的接口
  ```proxyed.getClass().getInterfaces()```
  - 参数h
  ```new InvocationHandler(){}```适合匿名内部类实现
  
- 实现InvocationHandler类的对象
    将该InvocationHandler对象传入newProxyInstance()中，生成的代理对象一旦调用任何方法时，其invoke方法都会被调用。实现```invoke(Object proxy, Method method,Object[] args)```方法，在该方法内通过反射```method.invoke(proxyed,args)```调用被代理对象的方法
### 细节总结
#### 接口可以包含常量
对于接口的变量,如```int i=10```,会自动设为```public static final```,java规范建议我们不要书写这个多余的关键字。

#### static关键字
原则：
```
1.非static class内可以创建static和非static class对象，static类内只能创建static类对象。
2.如果函数main所在的类中，其内部类一般都是static内部类（因为main方法是static，如果被main方法所直接或间接引用的就会是static内部类）
3.方法内的内部类不能使用public，protected，private，static限定。
```
------
## 图形程序设计
------
## 事件处理
------
## Swing用户界面组件
------
## 部署应用程序和applet
### jar文件
```
javac filename.java file2.java
jar cvf jarname.jar *.class icon.gif
//在包名外执行
java pckname.mainclassfilename
jar cvfe pkgname.mainclassfilename jarfilename.jar pkgname
java -jar jarfile.jar
```
### 应用程序首选项存储

------
## 异常、断言、日志和调试
### 断言

```java
assert 条件;
assert 条件:表达式；
//当条件为flase，出发断言，如果有表达式，则将表达式作为字符串传递给AssertionError
//开启断言
java -ea file
//关闭断言
java -da file
```