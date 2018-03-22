[TOC]
---
## 一、java语言基础
1.	关键字
2.	标识符
3.	注释
4.	常量、进制和进制转换
5.	变量
	1)	浮点数的存储问题
6.	数据类型和类型转换
 
7.	运算符
	1)	算术运算符
	2)	赋值运算符
	3)	比较运算符
	4)	逻辑运算符
		“&”和“&&”的区别：
		单&时，左边无论真假，右边都进行运算；
		双&时，如果左边为真，右边参与运算，如果左边为假，那么右边不参与运算。
		“|”和“||”的区别同理，双或时，左边为真，右边不参与运算。
		异或( ^ )与或( | )的不同之处是：当左右都为true时，结果为false。

	5)	位运算符
	6)	三目(元)运算符

8.	语句
	1)	流程控制语句
		①　顺序结构
		②　选择结构
		③　循环结构

	2)	跳转控制语句
		①　Break
		②　Continue
		③　Return
9.	方法
	1)	方法重载
	2)	方法重写
10.	数组
 

## 二、面向对象
1.	面向对象思想
2.	类与对象及其使用
	1)	类的初始化过程
	**Student s = new Student();在内存中做了哪些事情?**
		```
		加载Student.class文件进内存
		在栈内存为s开辟空间
		在堆内存为学生对象开辟空间
		对学生对象的成员变量进行默认初始化
		对学生对象的成员变量进行显示初始化
		通过构造方法对学生对象的成员变量赋值
		学生对象初始化完毕，把对象地址赋值给s变量
		```
	
	2)	创建对象内存图解
 
3.	成员变量和局部变量
	1)	静态变量
4.	匿名对象
5.	封装
6.	构造方法
	**构造方法的注意事项**
	```
	A:如果我们没写构造方法，系统将提供一个默认的无参构造方法
	B:如果我们给出了构造方法，系统将不再提供默认构造方法
		如果这个时候，我们要使用无参构造方法，就必须自己给出。
		推荐：永远手动自己给出无参构造方法。
	C：构造方法中可不可以有return语句呢?
		可以。而是我们写成这个样子就OK了：return;
		其实，在任何的void类型的方法的最后你都可以写上：return;
	```
7.	关键字
	1)	this、super关键字
	2)	private、public、protected、默认关键字（权限修饰符）
	
	3)	static关键字
	4)	final关键字
	5)	abstract关键字
	6)	关键字总结
 
8.	继承
9.	多态
10.	抽象类
11.	接口
12.	包和导包
13.	权限修饰符
14.	内部类
 

##三、API-常用类	
**常用类**
>	Object类/Scanner类	
	String类/StringBuffer类/StringBuilder类
	数组高级和Arrays类
	基本类型包装类(Integer,Character)
	正则表达式(Pattern,Matcher)
	Math类/Random类/System类
	BigInteger类/BigDecimal类
	Date类/DateFormat类/Calendar类

###1.	Scanner类
```java
/*
 * 基本格式：
 * 		public boolean hasNextXxx():判断是否是某种类型的元素
 * 		public Xxx nextXxx():获取该元素
 * 
 * 举例：用int类型的方法举例
 * 		public boolean hasNextInt()
 * 		public int nextInt()
 * 
 * 注意：
 * 		InputMismatchException：输入的和你想要的不匹配
 */
public class ScannerDemo {
	public static void main(String[] args) {
		// 创建对象
		Scanner sc = new Scanner(System.in);
		// 获取数据
		if (sc.hasNextInt()) {
			int x = sc.nextInt();
			System.out.println("x:" + x);
		} else {
			System.out.println("你输入的数据有误");
		}
	}
}
/*
 * 常用的两个方法：
 * 		public int nextInt():获取一个int类型的值
 * 		public String nextLine():获取一个String类型的值
 * 
 * 出现问题了：
 * 		先获取一个数值，在获取一个字符串，会出现问题。
 * 		主要原因：就是那个换行符号的问题。
 * 如何解决呢?
 * 	A:先获取一个数值后，在创建一个新的键盘录入对象获取字符串。
 * 	B:把所有的数据都先按照字符串获取，然后要什么，你就对应的转换为什么。
 */
public class ScannerDemo {
	public static void main(String[] args) {
		// 创建对象
		Scanner sc = new Scanner(System.in);
		// 先获取一个字符串，在获取一个int值
		// String s1 = sc.nextLine();
		// int b = sc.nextInt();
		// System.out.println("s1:" + s1 + ",b:" + b);
		// System.out.println("-------------------");

		// 先获取一个int值，在获取一个字符串
		// int a = sc.nextInt();
		// String s2 = sc.nextLine();
		// System.out.println("a:" + a + ",s2:" + s2);
		// System.out.println("-------------------");
	}
}
```
###2.	String类
####1)	构造方法
```java
/*
 * 字符串：就是由多个字符组成的一串数据。也可以看成是一个字符数组。
 * 通过查看API，我们可以知道
 * 		A:字符串字面值"abc"也可以看成是一个字符串对象。
 * 		B:字符串是常量，一旦被赋值，就不能被改变。
 * 
 * 构造方法：
 * 		public String():空构造
 *		public String(byte[] bytes):把字节数组转成字符串
 *		public String(byte[] bytes,int index,int length):把字节数组的一部分转成字符串
 *		public String(char[] value):把字符数组转成字符串
 *		public String(char[] value,int index,int count):把字符数组的一部分转成字符串
 *		public String(String original):把字符串常量值转成字符串
 *
 * 字符串的方法：
 * 		public int length()：返回此字符串的长度。
 */
```
####2)	方法
```java
/*
 * String类的判断功能：
 * boolean equals(Object obj):比较字符串的内容是否相同,区分大小写
 * boolean equalsIgnoreCase(String str):比较字符串的内容是否相同,忽略大小写
 * boolean contains(String str):判断大字符串中是否包含小字符串
 * boolean startsWith(String str):判断字符串是否以某个指定的字符串开头
 * boolean endsWith(String str):判断字符串是否以某个指定的字符串结尾
 * boolean isEmpty():判断字符串是否为空。
 * 
 * 注意：
 * 		字符串内容为空和字符串对象为空。
 * 		String s = "";
 * 		String s = null;
 */
/*
 * String类的获取功能
 * int length():获取字符串的长度。
 * char charAt(int index):获取指定索引位置的字符
 * int indexOf(int ch):返回指定字符在此字符串中第一次出现处的索引。
 * 		为什么这里是int类型，而不是char类型?
 * 		原因是：'a'和97其实都可以代表'a'
 * int indexOf(String str):返回指定字符串在此字符串中第一次出现处的索引。
 * int indexOf(int ch,int fromIndex):返回指定字符在此字符串中从指定位置后第一次出现处的索引。
 * int indexOf(String str,int fromIndex):返回指定字符串在此字符串中从指定位置后第一次出现处的索引。
 * String substring(int start):从指定位置开始截取字符串,默认到末尾。
 * String substring(int start,int end):从指定位置开始到指定位置结束截取字符串。
 */
/*
 * String的转换功能：
 * byte[] getBytes():把字符串转换为字节数组。
 * char[] toCharArray():把字符串转换为字符数组。
 * static String valueOf(char[] chs):把字符数组转成字符串。
 * static String valueOf(int i):把int类型的数据转成字符串。
 * 		注意：String类的valueOf方法可以把任意类型的数据转成字符串。
 * String toLowerCase():把字符串转成小写。
 * String toUpperCase():把字符串转成大写。
 * String concat(String str):把字符串拼接。
 */
/*
 * String类的其他功能：
 * 
 * 替换功能：
 * String replace(char old,char new)
 * String replace(String old,String new)
 *
 * 去除字符串前后空格	
 * String trim()
 * 
 * 按字典顺序比较两个字符串  
 * int compareTo(String str)
 * int compareToIgnoreCase(String str)
 */
```
####3)	注意事项：
**String s = new String(“hello”)和String s = “hello”;的区别?**
```
有区别，new String(“hello”)是产生两个对象,一个时new出来的还有一个是参数”hello”.
由此引出：在通过有构造方法来创建对象时，根据参数来产生不同数量的对象。
```

###3.	StringBuffer和StringBuilder类
1)	StringBuffer和StringBuilder的方法基本相同
2)	StringBuffer是线程安全的;StringBulider是非线程安全的,但是速度快,通常情况下,我们是在单线程下操作,所以一般采用StringBulider
3)	StringBuffer构造方法
```java
/*
 * StringBuffer:
 * 		线程安全的可变字符串。
 * 
 * StringBuffer和String的区别?
 * 前者长度和内容可变，后者不可变。
 * 如果使用前者做字符串的拼接，不会浪费太多的资源。
 * 
 * StringBuffer的构造方法：
 * 		public StringBuffer():无参构造方法
 *		public StringBuffer(int capacity):指定容量的字符串缓冲区对象
 *		public StringBuffer(String str):指定字符串内容的字符串缓冲区对象
 *
 * StringBuffer的方法：
 *		public int capacity()：返回当前容量。	理论值
 *		public int length():返回长度（字符数）。 实际值
 */
```
4)	StringBuffer方法
```java
/*
 * StringBuffer的添加功能：
 * public StringBuffer append(String str):可以把任意类型数据添加到字符串缓冲区里面,并返回字符串缓冲区本身
 * 
 * public StringBuffer insert(int offset,String str):在指定位置把任意类型的数据插入到字符串缓冲区里面,并返回字符串缓冲区本身
 */
/*
 * StringBuffer的删除功能
 * public StringBuffer deleteCharAt(int index):删除指定位置的字符，并返回本身
 * public StringBuffer delete(int start,int end):删除从指定位置开始指定位置结束的内容，并返回本身
 */
/*
 * StringBuffer的替换功能：
 * public StringBuffer replace(int start,int end,String str):从start开始到end用str替换
 */
/*
 * StringBuffer的反转功能： public StringBuffer reverse()
 */
/*
 * StringBuffer的截取功能:注意返回值类型不再是StringBuffer本身了
 * public String substring(int start)
 * public String substring(int start,int end)
 */
```
5)	问题
```java
/*
 * 面试题：
 * 1：String,StringBuffer,StringBuilder的区别?
 * A:String是内容不可变的，而StringBuffer,StringBuilder都是内容可变的。
 * B:StringBuffer是同步的，数据安全,效率低;StringBuilder是不同步的,数据不安全,效率高
 * 
 * 2：StringBuffer和数组的区别?
 * 二者都可以看出是一个容器，装其他的数据。
 * 但是呢,StringBuffer的数据最终是一个字符串数据。
 * 而数组可以放置多种数据，但必须是同一种数据类型的。
 * 
 * 3:形式参数问题
 * String作为参数传递
 * StringBuffer作为参数传递 
 * 
 * 形式参数：
 * 		基本类型：形式参数的改变不影响实际参数
 * 		引用类型：形式参数的改变直接影响实际参数
 * 
 * 注意：
 * 		String作为参数传递，效果和基本类型作为参数传递是一样的。
 */
```

###4.	Integer类
```java
/*
 * 需求1：我要求大家把100这个数据的二进制，八进制，十六进制计算出来
 * 需求2：我要求大家判断一个数据是否是int范围内的。
 * 		首先你的知道int的范围是多大?
 * 
 * 为了对基本数据类型进行更多的操作，更方便的操作，Java就针对每一种基本数据类型提供了对应的类类型。包装类类型。
 * byte 				Byte
 * short			Short
 * int				Integer
 * long				Long
 * float			Float
 * double			Double
 * char				Character
 * boolean			Boolean
 * 
 * 用于基本数据类型与字符串之间的转换。
 */
/*
 * Integer的构造方法：
 * public Integer(int value)
 * public Integer(String s)
 * 		注意：这个字符串必须是由数字字符组成
 */
/*
 * int类型和String类型的相互转换
 * 
 * int -- String
 * 		String.valueOf(number)
 * 
 * String -- int
 * 		Integer.parseInt(s)
 */
/*
 * 常用的基本进制转换
 * public static String toBinaryString(int i)
 * public static String toOctalString(int i)
 * public static String toHexString(int i)
 * 
 * 十进制到其他进制
 * public static String toString(int i,int radix)
 * 由这个我们也看到了进制的范围：2-36
 * 为什么呢?0,...9,a...z
 * 
 * 其他进制到十进制
 * public static int parseInt(String s,int radix)
 */
/*
 * JDK5的新特性
 * 自动装箱：把基本类型转换为包装类类型
 * 自动拆箱：把包装类类型转换为基本类型
 * 
 * 注意一个小问题：
 * 		在使用时，Integer  x = null;代码就会出现NullPointerException。
 * 		建议先判断是否为null，然后再使用。
 */
/*
 *  通过查看源码，我们就知道了，针对-128到127之间的数据，做了一个数据缓冲池，	如果数据是该范围内的，每次并不创建新的空间
	 Integer ii = Integer.valueOf(127);
 */
```

###5.	Character
```java
/*
 * Character 类在对象中包装一个基本类型 char 的值
 * 此外，该类提供了几种方法，以确定字符的类别（小写字母，数字，等等），并将字符从大写转换成小写，反之亦然
 * 
 * 构造方法：
 * 		Character(char value)
 */
/*
 * public static boolean isUpperCase(char ch):判断给定的字符是否是大写字符
 * public static boolean isLowerCase(char ch):判断给定的字符是否是小写字符
 * public static boolean isDigit(char ch):判断给定的字符是否是数字字符
 * public static char toUpperCase(char ch):把给定的字符转换为大写字符
 * public static char toLowerCase(char ch):把给定的字符转换为小写字符
 */
```

###6.	Arrays类
```java
/*
 * Arrays:针对数组进行操作的工具类。比如说排序和查找。
 * 1:public static String toString(int[] a) 把数组转成字符串
 * 2:public static void sort(int[] a) 对数组进行排序
 * 3:public static int binarySearch(int[] a,int key) 二分查找
 */

//选择排序和冒泡排序
public static void bubbleSort(int[] arr){
	/*
	 * 冒泡排序原理
	 * arr[0]和arr[1]比较，arr[1]<arr[0],值互换
	 * arr[1]和arr[2]比较，arr[2]<arr[1],值互换
	 * 。。。
	 * arr[length-1]和arr[length-2]比较，。。。
	 * 。。。。。。	
	 * arr[0]和arr[1]比较，arr[1]<arr[0],值互换
	 * arr[1]和arr[2]比较，arr[2]<arr[1],值互换
	 * 。。。
	 * arr[length-2]和arr[length-3]比较，。。。
	 * 。。。。。。
	 * arr[length-length]和arr[length-(length-1)]比较，arr[1]<arr[0],值互换		
	 */
		for(int out=0;out<arr.length;out++){
			for(int in=0;in<arr.length-out-1;in++){
				if(arr[in]>arr[in+1]){
					int temp=arr[in];
					arr[in]=arr[in+1];
					arr[in+1]=temp;
				}
			}
		}
	}
public static void selectSort(int[] arr){
		/*
		 * 选择排序原理
		 * arr[0]与arr[1]比较，如果arr[0]>arr[1],值互换
		 * arr[0]与arr[2]比较，如果arr[0]>arr[2],值互换
		 * 。。。
		 * arr[0]与arr[length-1]比较，如果arr[0]>arr[length-1],值互换
		 * .。。。。。
		 * arr[1]与arr[2]比较，如果arr[1]>arr[2],值互换
		 * arr[1]与arr[3]比较，如果arr[1]>arr[3],值互换
		 * .。。
		 * arr[1]与arr[length-1]比较，如果arr[1]>arr[length-1],值互换
		 * ......
		 * arr[length-2]与arr[lenght-1]比较，如果arr[length-2]>arr[length-1],值互换
		 */
		
		for(int out=0;out<arr.length-1;out++){
			for(int in=1+out;in<arr.length;in++){
				if(arr[out]>arr[in]){
					int temp=arr[out];
					arr[out]=arr[in];
					arr[in]=temp;
				}
			}
		}
	}
//回文:
public class Palindrome {
	public	static Scanner sc;
	public static void main(String[] args) {
		sc=new Scanner(System.in);
		StringBuffer sb=new StringBuffer(sc.nextLine());
		
		System.out.println("is it palindrome?:"+palindrome(sb));
		System.out.println("is it palindrome?:"+palindrome2(sb));
		
	}
	
	public static boolean palindrome(StringBuffer sb){
		String str=sb.toString();
		//利用StringBuffer的反转功能与源字符串对比		
	return sb.reverse().toString().equals(str);
	}
	
	public static boolean palindrome2(StringBuffer sb){
		String str=sb.toString();
		boolean flag=true;
		char[] arr=str.toCharArray();
		for(int start=0,end=arr.length-1;start<arr.length/2;start++,end--){
			if(arr[start]!=arr[end])
				flag=false;
		}
		return flag;	
	}
}
```
###7.	BigDecimal
```java
/*
 * 看程序写结果：结果和我们想的有一点点不一样，这是因为float类型的数据存储和整数不一样导致的。它们大部分的时候，都是带有有效数字位。
 * 
 * 由于在运算的时候，float类型和double很容易丢失精度，演示案例。所以，为了能精确的表示、计算浮点数，Java提供了BigDecimal
 * 
 * BigDecimal类：不可变的、任意精度的有符号十进制数,可以解决数据丢失问题。
 */
/*
 * 构造方法：
 * 		public BigDecimal(String val)
 * 
 * public BigDecimal add(BigDecimal augend)
 * public BigDecimal subtract(BigDecimal subtrahend)
 * public BigDecimal multiply(BigDecimal multiplicand)
 * public BigDecimal divide(BigDecimal divisor)
 * public BigDecimal divide(BigDecimal divisor,int scale,int roundingMode):商，几位小数，如何舍取
 */
```
###8.	BigInteger
```java
/*
 * BigInteger:可以让超过Integer范围内的数据进行运算
 * 
 * 构造方法：
 * BigInteger(String val) 
 */
/*
 * public BigInteger add(BigInteger val):加
 * public BigInteger subtract(BigInteger val):减
 * public BigInteger multiply(BigInteger val):乘
 * public BigInteger divide(BigInteger val):除
 * public BigInteger[] divideAndRemainder(BigInteger val):返回商和余数的数组
 */
```

###9.	Calendar
```java
/*
 * public void add(int field,int amount):根据给定的日历字段和对应的时间，来对当前的日历进行操作。
 * public final void set(int year,int month,int date):设置当前日历的年月日
 * 获取任意一年的二月有多少天
 * 
 * 分析：
 * 		A:键盘录入任意的年份
 * 		B:设置日历对象的年月日
 * 			年就是A输入的数据
 * 			月是2
 * 			日是1
 * 		C:把时间往前推一天，就是2月的最后一天
 * 		D:获取这一天输出即可
 */
public class CalendarTest {
	public static void main(String[] args) {
		// 键盘录入任意的年份
		Scanner sc = new Scanner(System.in);
		System.out.println("请输入年份：");
		int year = sc.nextInt();

		// 设置日历对象的年月日
		Calendar c = Calendar.getInstance();
		c.set(year, 2, 1); // 其实是这一年的3月1日
		// 把时间往前推一天，就是2月的最后一天
		c.add(Calendar.DATE, -1);

		// 获取这一天输出即可
		System.out.println(c.get(Calendar.DATE));
	}
}
```

###10.	Date&DateFormat
```java
/*
 * Date:表示特定的瞬间，精确到毫秒。 
 * 
 * 构造方法：
 * 		Date():根据当前的默认毫秒值创建日期对象
 * 		Date(long date)：根据给定的毫秒值创建日期对象
 * public long getTime():获取时间，以毫秒为单位
 * public void setTime(long time):设置时间
 * 
 * 从Date得到一个毫秒值
 * 		getTime()
 * 把一个毫秒值转换为Date
 * 		构造方法
 * 		setTime(long time)
 */
/*
 * Date	 --	 String(格式化)
 * 		public final String format(Date date)
 * 
 * String -- Date(解析)
 * 		public Date parse(String source)
 * 
 * DateForamt:可以进行日期和字符串的格式化和解析，但是由于是抽象类，所以使用具体子类SimpleDateFormat。
 * 
 * SimpleDateFormat的构造方法：
 * 		SimpleDateFormat():默认模式
 * 		SimpleDateFormat(String pattern):给定的模式
 * 			这个模式字符串该如何写呢?
 * 			通过查看API，我们就找到了对应的模式
 * 			年 y
 * 			月 M	
 * 			日 d
 * 			时 H
 * 			分 m
 * 			秒 s
 * 
 * 			2014年12月12日 12:12:12
 */
public class DateUtil {
	private DateUtil() {
	}

	/**
	 * 这个方法的作用就是把日期转成一个字符串
	 * 
	 * @param d
	 *            被转换的日期对象
	 * @param format
	 *            传递过来的要被转换的格式
	 * @return 格式化后的字符串
	 */
	public static String dateToString(Date d, String format) {
		// SimpleDateFormat sdf = new SimpleDateFormat(format);
		// return sdf.format(d);
		return new SimpleDateFormat(format).format(d);
	}

	/**
	 * 这个方法的作用就是把一个字符串解析成一个日期对象
	 * 
	 * @param s
	 *            被解析的字符串
	 * @param format
	 *            传递过来的要被转换的格式
	 * @return 解析后的日期对象
	 * @throws ParseException
	 */
	public static Date stringToDate(String s, String format)
			throws ParseException {
		return new SimpleDateFormat(format).parse(s);
	}
}
```
###11.	System
```java
/*
 * System类包含一些有用的类字段和方法。它不能被实例化。 
 * 
 * 方法：
 * 		public static void gc()：运行垃圾回收器。 
 *		public static void exit(int status):终止当前正在运行的 Java 虚拟机。参数用作状态码；根据惯例，非 0 的状态码表示异常终止。 
 *		public static long currentTimeMillis():返回以毫秒为单位的当前时间
 *		public static void arraycopy(Object src,int srcPos,Object dest,int destPos,int length)
 *			从指定源数组中复制一个数组，复制从指定的位置开始，到目标数组的指定位置结束。
 */
```

###12.	Math
```java
/*
 * Math:用于数学运算的类。
 * 成员变量：
 * 		public static final double PI
 * 		public static final double E
 * 成员方法：
 * 		public static int abs(int a)：绝对值
 *		public static double ceil(double a):向上取整
 *		public static double floor(double a):向下取整
 *		public static int max(int a,int b):最大值 (min自学)
 *		public static double pow(double a,double b):a的b次幂
 *		public static double random():随机数 [0.0,1.0)
 *		public static int round(float a) 四舍五入(参数为double的自学)
 *		public static double sqrt(double a):正平方根
 */
```

###13.	Random
```
/*
 * Random:产生随机数的类
 * 
 * 构造方法：
 * 		public Random():没有给种子，用的是默认种子，是当前时间的毫秒值
 *		public Random(long seed):给出指定的种子
 *
 *		给定种子后，每次得到的随机数是相同的。
 *
 * 成员方法：
 * 		public int nextInt()：返回的是int范围内的随机数
 *		public int nextInt(int n):返回的是[0,n)范围的内随机数
 */
```

###14.	String
 ```java
/*
 * 判断功能
 *		String类的public boolean matches(String regex)
 *
 * 分割功能
 *		String类的public String[] split(String regex)
 *		根据给定正则表达式的匹配拆分此字符串。 
 * 替换功能
 *  	String类的public String replaceAll(String regex,String replacement)
 *  	使用给定的 replacement 替换此字符串所有匹配给定的正则表达式的子字符串。 
A:字符
	x 字符 x。举例：'a'表示字符a
	\\ 反斜线字符。
	\n 新行（换行）符 ('\u000A') 
	\r 回车符 ('\u000D')
	
B:字符类
	[abc] a、b 或 c（简单类） 
	[^abc] 任何字符，除了 a、b 或 c（否定） 
	[a-zA-Z] a到 z 或 A到 Z，两头的字母包括在内（范围） 
	[0-9] 0到9的字符都包括
	
C:预定义字符类
	. 任何字符。我的就是.字符本身，怎么表示呢? \.
	\d 数字：[0-9]
	\w 单词字符：[a-zA-Z_0-9]
		在正则表达式里面组成单词的东西必须有这些东西组成

D:边界匹配器
	^ 行的开头 
	$ 行的结尾 
	\b 单词边界
		就是不是单词字符的地方。
		举例：hello world?haha;xixi
	
E:Greedy 数量词 
	X? X，一次或一次也没有
	X* X，零次或多次
	X+ X，一次或多次
	X{n} X，恰好 n 次 
	X{n,} X，至少 n 次 
	X{n,m} X，至少 n 次，但是不超过 m 次 
*/
/*
 * 获取功能
 *		Pattern和Matcher类的使用(java.util.regex包下)
 *		
 *		模式和匹配器的基本使用顺序
 */
public class RegexDemo {
	public static void main(String[] args) {
		// 模式和匹配器的典型调用顺序
		// 把正则表达式编译成模式对象
		Pattern p = Pattern.compile("a*b");
		// 通过模式对象得到匹配器对象，这个时候需要的是被匹配的字符串
		Matcher m = p.matcher("aaaaab");
		// 调用匹配器对象的功能
		boolean b = m.matches();
		System.out.println(b);
		
		//这个是判断功能，但是如果做判断，这样做就有点麻烦了，我们直接用字符串的方法做
		String s = "aaaaab";
		String regex = "a*b";
		boolean bb = s.matches(regex);
		System.out.println(bb);
	}
}
```


##四、API-集合(Collection)和Collections
 

###1.	集合简介
```java
/*
 * 集合的由来：
 * 		我们学习的是面向对象语言，而面向对象语言对事物的描述是通过对象体现的，为了方便对多个对象进行操作，我们就必须把这多个对象进行存储。
 * 		而要想存储多个对象，就不能是一个基本的变量，而应该是一个容器类型的变量，在我们目前所学过的知识里面，有哪些是容器类型的呢?
 * 		数组和StringBuffer。但是呢?StringBuffer的结果是一个字符串，不一定满足我们的要求，所以我们只能选择数组，这就是对象数组。
 * 		而对象数组又不能适应变化的需求，因为数组的长度是固定的，这个时候，为了适应变化的需求，Java就提供了集合类供我们使用。
 * 
 * 数组和集合的区别?
 * 		A:长度区别
 * 			数组的长度固定
 * 			集合长度可变
 * 		B:内容不同
 * 			数组存储的是同一种类型的元素
 * 			而集合可以存储不同类型的元素
 * 		C:元素的数据类型问题	
 * 			数组可以存储基本数据类型，也可以存储引用数据类型
 * 			集合只能存储引用类型
//但是java提供了自动装箱和拆箱功能
 * 
 * 刚说过集合是存储多个元的，但是呢，存储多个元素我们也是有不同需求的：比如说，我要这多个元素中不能有相同的元素，
 * 再比如说，我要这多个元素按照某种规则排序一下。针对不同的需求，Java就提供了不同的集合类，这样呢，Java就提供了很多个集合类。
 * 这多个集合类的数据结构不同,结构不同不重要的，重要的是你要能够存储东西，并且还要能够使用这些东西，比如说判断，获取等。
 * 既然这样，那么，这多个集合类是有共性的内容的，我们把这些集合类的共性内容不断的向上提取，最终就能形成集合的继承体系结构。
 * 
 * 数据结构：数据的存储方式。
 */
 ```

###2.	集合类和接口
####1)	Collection
```java
/*
 * Collection:是集合的顶层接口，它的子体系有重复的，有唯一的，有有序的，有无序的。(后面会慢慢的讲解)
 * 
 * Collection的功能概述：
 * 1：添加功能
 * 		boolean add(Object obj):添加一个元素
 * 		boolean addAll(Collection c):添加一个集合的元素
 * 2:删除功能
 * 		void clear():移除所有元素
 * 		boolean remove(Object o):移除一个元素
 * 		boolean removeAll(Collection c):移除一个集合的元素(是一个还是所有)//所有
 * 3:判断功能
 * 		boolean contains(Object o)：判断集合中是否包含指定的元素
 * 		boolean containsAll(Collection c)：判断集合中是否包含指定的集合元素(是一个还是所有)
 * 		boolean isEmpty()：判断集合是否为空
 * 4:获取功能
 * 		Iterator<E> iterator()(重点)
 * 5:长度功能
 * 		int size():元素的个数
 * 		面试题：数组有没有length()方法呢?字符串有没有length()方法呢?集合有没有length()方法呢?
 * 6:交集功能
 * 		boolean retainAll(Collection c):两个集合都有的元素?思考元素去哪了，返回的boolean又是什么意思呢?
 * 7：把集合转换为数组
 * 		Object[] toArray()
/*
 * Iterator iterator():迭代器，集合的专用遍历方式
 * 		Object next():获取元素,并移动到下一个位置。
 * 			NoSuchElementException：没有这样的元素，因为你已经找到最后了。
 * 		boolean hasNext():如果仍有元素可以迭代，则返回 true。（
 */
/*
 * Collection
 * 		|--List
 * 			有序(存储顺序和取出顺序一致),可重复
 * 		|--Set
 * 			无序(存储顺序和取出顺序不一致),唯一
 * 
 * HashSet：它不保证 set 的迭代顺序；特别是它不保证该顺序恒久不变。
 * 注意：虽然Set集合的元素无序，但是，作为集合来说，它肯定有它自己的存储顺序，
 * 而你的顺序恰好和它的存储顺序一致，这代表不了有序，你可以多存储一些数据，就能看到效果。
 */
```

####2)	List
```java
/*
 * List集合的特点：
 * 		有序(存储和取出的元素一致)，可重复的。
 * List集合的特有功能：
 * A:添加功能
 * 		void add(int index,Object element):在指定位置添加元素
 * B:获取功能
 * 		Object get(int index):获取指定位置的元素
 * C:列表迭代器
 * 		ListIterator listIterator()：List集合特有的迭代器
 * D:删除功能
 * 		Object remove(int index)：根据索引删除元素,返回被删除的元素
 * E:修改功能
 * 		Object set(int index,Object element):根据索引修改元素，返回被修饰的元素
/*
 * 列表迭代器：
 * 		ListIterator listIterator()：List集合特有的迭代器
 * 		该迭代器继承了Iterator迭代器，所以，就可以直接使用hasNext()和next()方法。
 * 
 * 特有功能：
 * 		Object previous():获取上一个元素
 * 		boolean hasPrevious():判断是否有元素
 * 
 * 		注意：ListIterator可以实现逆向遍历，但是必须先正向遍历，才能逆向遍历，所以一般无意义，不使用。
 *

List:(面试题List的子类特点)
	ArrayList:
		底层数据结构是数组，查询快，增删慢。
		线程不安全，效率高。
	Vector:
		底层数据结构是数组，查询快，增删慢。
		线程安全，效率低。
	LinkedList:
		底层数据结构是链表，查询慢，增删快。
		线程不安全，效率高。
		
	List有三个儿子，我们到底使用谁呢?
		看需求(情况)。
		
	要安全吗?
		要：Vector(即使要安全，也不用这个了，后面有替代的)
		不要：ArrayList或者LinkedList
			查询多：ArrayList
			增删多：LinkedList
			
	如果你什么都不懂，就用ArrayList。
*/
//通过加锁实现ArrayList的线程安全替代Vector
public class ThreadDemo {
	public static void main(String[] args) {
		// 线程安全的类
		StringBuffer sb = new StringBuffer();
		Vector<String> v = new Vector<String>();
		Hashtable<String, String> h = new Hashtable<String, String>();

		// Vector是线程安全的时候才去考虑使用的，但是我还说过即使要安全，我也不用你
		// 那么到底用谁呢?
		// public static <T> List<T> synchronizedList(List<T> list)
		List<String> list1 = new ArrayList<String>();// 线程不安全
		List<String> list2 = Collections
				.synchronizedList(new ArrayList<String>()); // 线程安全
	}
}
```
**List 的子类**
	①　ArrayList
	②　Vector
```java
/*
 * Vector的特有功能：
 * 1：添加功能
 * 		public void addElement(Object obj)		--	add()
 * 2：获取功能
 * 		public Object elementAt(int index)		--  get()
 * 		public Enumeration elements()			--	Iterator iterator()
 * 				boolean hasMoreElements()				hasNext()
 * 				Object nextElement()					next()
　LinkedList
 * LinkedList的特有功能：
 * 		A:添加功能
 * 			public void addFirst(Object e)
 * 			public void addLast(Object e)
 * 		B:获取功能
 * 			public Object getFirst()
 * 			public Obejct getLast()
 * 		C:删除功能
 * 			public Object removeFirst()
 * 			public Object removeLast()
 */

```
####3)	Set

**Set集合(理解)**
```
	(1)Set集合的特点
		无序,唯一
	(2)HashSet集合(掌握)
		A:底层数据结构是哈希表(是一个元素为链表的数组)
		B:哈希表底层依赖两个方法：hashCode()和equals()
		  执行顺序：
			首先比较哈希值是否相同
				相同：继续执行equals()方法
					返回true：元素重复了，不添加
					返回false：直接把元素添加到集合
				不同：就直接把元素添加到集合
		C:如何保证元素唯一性的呢?
			由hashCode()和equals()保证的
		D:开发的时候，代码非常的简单，自动生成即可。
		E:HashSet存储字符串并遍历
		F:HashSet存储自定义对象并遍历(对象的成员变量值相同即为同一个元素)
	(3)TreeSet集合
		A:底层数据结构是红黑树(是一个自平衡的二叉树)
		B:保证元素的排序方式
			a:自然排序(元素具备比较性)
				让元素所属的类实现Comparable接口
			b:比较器排序(集合具备比较性)
				让集合构造方法接收Comparator的实现类对象
		C:把我们讲过的代码看一遍即可
	(4)案例：
		A:获取无重复的随机数
		B:键盘录入学生按照总分从高到底输出
|--Set	无序,唯一
			|--HashSet
				底层数据结构是哈希表。
				如何保证元素唯一性的呢?
					依赖两个方法：hashCode()和equals()
					开发中自动生成这两个方法即可
				|--LinkedHashSet
					底层数据结构是链表和哈希表
					由链表保证元素有序
					由哈希表保证元素唯一
			|--TreeSet
				底层数据结构是红黑树。
				如何保证元素排序的呢?
					自然排序
					比较器排序
				如何保证元素唯一性的呢?
					根据比较的返回值是否是0来决定

```
**Set的子类:**
```
①　HashSet
HashSet类概述
不保证 set 的迭代顺序
特别是它不保证该顺序恒久不变。
HashSet如何保证元素唯一性
底层数据结构是哈希表(元素是链表的数组)
哈希表依赖于哈希值存储
添加功能底层依赖两个方法：
int hashCode()
boolean equals(Object obj)
LinkedHashSet类概述
元素有序唯一
由链表保证元素有序
由哈希表保证元素唯一

②　TreeSet
TreeSet类概述
使用元素的自然顺序对元素进行排序
或者根据创建 set 时提供的 Comparator 进行排序
具体取决于使用的构造方法。 
TreeSet是如何保证元素的排序和唯一性的
底层数据结构是红黑树(红黑树是一种自平衡的二叉树)
```


###3.	集合类和接口的比较
###4.	Map
```java
/*
 * 作为学生来说，是根据学号来区分不同的学生的，那么假设我现在已经知道了学生的学号，我要根据学号去获取学生姓名，请问怎么做呢?
 * 如果采用前面讲解过的集合，我们只能把学号和学生姓名作为一个对象的成员，然后存储整个对象，将来遍历的时候，判断，获取对应的名称。
 * 但是呢，如果我都能把学生姓名拿出来了，我还需要根据编号去找吗?
 * 针对我们目前的这种需求：仅仅知道学号，就想知道学生姓名的情况，Java就提供了一种新的集合 Map。
 * 通过查看API，我们知道Map集合的一个最大的特点，就是它可以存储键值对的元素。这个时候存储我们上面的需求，就可以这样做
 * 		学号1		姓名1
 * 		学号2 	姓名2
 * 		学号3		姓名3
 * 		学号2(不行)姓名4
 * 		学号4               姓名4
 * Map集合的特点：
 * 		将键映射到值的对象。一个映射不能包含重复的键；每个键最多只能映射到一个值。 
 * 
 * Map集合和Collection集合的区别?
 * 		Map集合存储元素是成对出现的，Map集合的键是唯一的，值是可重复的。可以把这个理解为：夫妻对
 * 		Collection集合存储元素是单独出现的，Collection的儿子Set是唯一的，List是可重复的。可以把这个理解为：光棍(11.11)
 * 
 * 注意：
 * 		Map集合的数据结构值针对键有效，跟值无关	
 * 			HashMap，TreeMap等会讲。
 *		Collection集合的数据结构是针对元素有效
 * 
 * Map集合的功能概述：
 * 1:添加功能
 * 		V put(K key,V value):添加元素。这个其实还有另一个功能?先不告诉你，等会讲
 * 			如果键是第一次存储，就直接存储元素，返回null
 * 			如果键不是第一次存在，就用值把以前的值替换掉，返回以前的值
 * 2:删除功能
 * 		void clear():移除所有的键值对元素
 * 		V remove(Object key)：根据键删除键值对元素，并把值返回
 * 3:判断功能
 * 		boolean containsKey(Object key)：判断集合是否包含指定的键
 * 		boolean containsValue(Object value):判断集合是否包含指定的值
 * 		boolean isEmpty()：判断集合是否为空
 * 4:获取功能
 * 		Set<Map.Entry<K,V>> entrySet():???
 * 		V get(Object key):根据键获取值
 * 		Set<K> keySet():获取集合中所有键的集合
 * 		Collection<V> values():获取集合中所有值的集合
 * 5：长度功能
 * 		int size()：返回集合中的键值对的对数
 */
```
####1)	实现Map(接口)的的类
①　HashMap
* HashMap:是基于哈希表的Map接口实现。
* 哈希表的作用是用来保证键的唯一性的。
HashMap的子类
 * LinkedHashMap:是Map接口的哈希表和链接列表实现，具有可预知的迭代顺序。
 * 由哈希表保证键的唯一性
 * 由链表保证键盘的有序(存储和取出的顺序一致)

②　TreeMap
 	TreeMap类概述
	键是红黑树结构，可以保证键的排序和唯一性
```java
/*
 * 需求：请按照姓名的长度排序
 * 
 * TreeSet集合保证元素排序和唯一性的原理
 * 唯一性：是根据比较的返回是否是0来决定。
 * 排序：
 * 		A:自然排序(元素具备比较性)
 * 			让元素所属的类实现自然排序接口 Comparable
 * 		B:比较器排序(集合具备比较性)
 * 			让集合的构造方法接收一个比较器接口的子类对象 Comparator
 */
```
比较器排序--让集合的构造方法接收一个比较器接口的子类对象 Comparator
```java
// 创建集合对象
		// TreeSet<Student> ts = new TreeSet<Student>(); //自然排序
		// public TreeSet(Comparator comparator) //比较器排序
		// TreeSet<Student> ts = new TreeSet<Student>(new MyComparator());

		// 如果一个方法的参数是接口，那么真正要的是接口的实现类的对象
public class MyComparator implements Comparator<Student>
		// 而匿名内部类就可以实现这个东西
		TreeSet<Student> ts = new TreeSet<Student>(new Comparator<Student>() 		{
			@Override
			public int compare(Student s1, Student s2) {
				// 姓名长度
				int num = s1.getName().length() - s2.getName().length();
				// 姓名内容
				int num2 = num == 0 ? s1.getName().compareTo(s2.getName())
						: num;
				// 年龄
				int num3 = num2 == 0 ? s1.getAge() - s2.getAge() : num2;
				return num3;
			}
		});
```
自然排序--让元素所属的类实现自然排序接口 Comparable
```java
/*
 * 如果一个类的元素要想能够进行自然排序，就必须实现自然排序接口
 */
public class Student implements Comparable<Student> {
	private String name;
	private int age;

	@Override
	public int compareTo(Student s) {
		// 主要条件 姓名的长度
		int num = this.name.length() - s.name.length();
		// 姓名的长度相同，不代表姓名的内容相同
		int num2 = num == 0 ? this.name.compareTo(s.name) : num;
		// 姓名的长度和内容相同，不代表年龄相同，所以还得继续判断年龄
		int num3 = num2 == 0 ? this.age - s.age : num2;
		return num3;
	}
}
```
####2)	HashTable
* 1:Hashtable和HashMap的区别?
	* Hashtable:线程安全，效率低。不允许null键和null值
	* HashMap:线程不安全，效率高。允许null键和null值

###5.	Iterator
###6.	常用数据结构(数据的存储方式)
###7.	泛型
###8.	Collections
```java
/*
 * Collections:是针对集合进行操作的工具类，都是静态方法。
 * 
 * 面试题：
 * Collection和Collections的区别?
 * Collection:是单列集合的顶层接口，有子接口List和Set。
 * Collections:是针对集合操作的工具类，有对集合进行排序和二分查找的方法
 * 
 * 要知道的方法
 * public static <T> void sort(List<T> list)：排序 默认情况下是自然顺序。
 * public static <T> int binarySearch(List<?> list,T key):二分查找
 * public static <T> T max(Collection<?> coll):最大值
 * public static void reverse(List<?> list):反转
 * public static void shuffle(List<?> list):随机置换
 */
```

###9.	hashCode()和equals()方法的重写
```java
 @Override
	 public int hashCode() {
	 // return 0;
	 // 因为成员变量值影响了哈希值，所以我们把成员变量值相加即可
	 // return this.name.hashCode() + this.age;
	 // 看下面
	 // s1:name.hashCode()=40,age=30
	 // s2:name.hashCode()=20,age=50
	 // 尽可能的区分,我们可以把它们乘以一些整数
	 return this.name.hashCode() + this.age * 15;
	 }
	
	 @Override
	 public boolean equals(Object obj) {
	 // System.out.println(this + "---" + obj);
	 if (this == obj) {
	 return true;
	 }
	 if (!(obj instanceof Student)) {
	 return false;
	 }
	 Student s = (Student) obj;
	 return this.name.equals(s.name) && this.age == s.age;
}
```
###10.	集合注意事项
1)	集合只能存储引用类型数据
用于操作数组的工具类Arrays，它有一个方法asList（）（将数组变成List集合）。它在将数组变成集合时，如果数组中的元素都是对象，那么变成集合时，数组中的对象直接成集合中的对象。
如果数组中的元素都是基本数据类型，那么会将该数组作为集合中的元素。
由此联想到，在集合中应该是不能存放基本数据类型的。
集合中为什么不能存放基本数据类型？
这个你必须得知道集合中是怎么存放元素的，集合中存放的可都是对象的引用，实际内容都在堆上面或者方法区里面，但是基本数据类型是在栈上分配空间的。随时就被收回的。但是通过自动包装类就可以把基本类型转为对象类型，存放引用就解决了这个问题。

2)	ConcurrentModificationException
```java
/*
 * ConcurrentModificationException:当方法检测到对象的并发修改，但不允许这种修改时，	抛出此异常。 
 * 产生的原因：
 * 		迭代器是依赖于集合而存在的，在判断成功后，集合的中新添加了元素，而迭代器却不知道，所以就报错了，这个错叫并发修改异常。
 * 		其实这个问题描述的是：迭代器遍历元素的时候，通过集合是不能修改元素的。
 * 如何解决呢?
 * 		A:迭代器迭代元素，迭代器修改元素
 * 			元素是跟在刚才迭代的元素后面的。
 * 		B:集合遍历元素，集合修改元素(普通for)
 * 			元素在最后添加的。
 */
```


##五、Exception
 

##六、IO流
###1.	File
```java
/*
 * 我们要想实现IO的操作，就必须知道硬盘上文件的表现形式。
 * 而Java就提供了一个类File供我们使用。
 * 
 * File:文件和目录(文件夹)路径名的抽象表示形式
 * 构造方法：
 * 		File(String pathname)：根据一个路径得到File对象
 * 		File(String parent, String child):根据一个目录和一个子文件/目录得到File对象
 * 		File(File parent, String child):根据一个父File对象和一个子文件/目录得到File对象
 */

/*
 *创建功能：
 *public boolean createNewFile():创建文件 如果存在这样的文件，就不创建了
 *public boolean mkdir():创建文件夹 如果存在这样的文件夹，就不创建了
 *public boolean mkdirs():创建文件夹,如果父文件夹不存在，会帮你创建出来
 *
 *骑白马的不一定是王子，可能是班长。
 *注意：你到底要创建文件还是文件夹，你最清楚，方法不要调错了。
 */

/*
 * 删除功能:public boolean delete()
 * 
 * 注意：
 * 		A:如果你创建文件或者文件夹忘了写盘符路径，那么，默认在项目路径下。
 * 		B:Java中的删除不走回收站。
 * 		C:要删除一个文件夹，请注意该文件夹内不能包含文件或者文件夹
 */

/*
 * 重命名功能:public boolean renameTo(File dest)
 * 		如果路径名相同，就是改名。
 * 		如果路径名不同，就是改名并剪切。
 * 
 * 路径以盘符开始：绝对路径	c:\\a.txt
 * 路径不以盘符开始：相对路径	a.txt
 */

/*
 * 判断功能:
 * public boolean isDirectory():判断是否是目录
 * public boolean isFile():判断是否是文件
 * public boolean exists():判断是否存在
 * public boolean canRead():判断是否可读
 * public boolean canWrite():判断是否可写
 * public boolean isHidden():判断是否隐藏
 */

/*
 * 获取功能：
 * public String getAbsolutePath()：获取绝对路径
 * public String getPath():获取相对路径
 * public String getName():获取名称
 * public long length():获取长度。字节数
 * public long lastModified():获取最后一次的修改时间，毫秒值
 * public String[] list():获取指定目录下的所有文件或者文件夹的名称数组
 * public File[] listFiles():获取指定目录下的所有文件或者文件夹的File数组
 * public String[] list(FilenameFilter filter)
 * public File[] listFiles(FilenameFilter filter)

 */
/*
 * 判断E盘目录下是否有后缀名为.jpg的文件，如果有，就输出此文件名称
 * A:先获取所有的，然后遍历的时候，依次判断，如果满足条件就输出。
 * B:获取的时候就已经是满足条件的了，然后输出即可。
 * 
 * 要想实现这个效果，就必须学习一个接口：文件名称过滤器
 * public String[] list(FilenameFilter filter)
 * public File[] listFiles(FilenameFilter filter)
 */
public class FileDemo2 {
	public static void main(String[] args) {
		// 封装e判断目录
		File file = new File("e:\\");
		// 获取该目录下所有文件或者文件夹的String数组
		// public String[] list(FilenameFilter filter)
		String[] strArray = file.list(new FilenameFilter() {
			@Override
			public boolean accept(File dir, String name) {
				return new File(dir, name).isFile() && name.endsWith(".jpg");
			}
		});
		// 遍历
		for (String s : strArray) {
			System.out.println(s);
		}
	}
}
```
###2.	递归
```java
/*
 * 需求：请用代码实现求5的阶乘。
 * 下面的知识要知道：
 * 		5! = 1*2*3*4*5
 * 		5! = 5*4!
 * 
 * 有几种方案实现呢?
 * 		A:循环实现
 * 		B:递归实现
 * 			a:做递归要写一个方法
 * 			b:出口条件
 * 			c:规律
 */
public class DiGuiDemo {
	public static void main(String[] args) {
		int jc = 1;
		for (int x = 2; x <= 5; x++) {
			jc *= x;
		}
		System.out.println("5的阶乘是：" + jc);
		System.out.println("5的阶乘是："+jieCheng(5));
	}
	
	/*
	 * 做递归要写一个方法:
	 * 		返回值类型：int
	 * 		参数列表：int n
	 * 出口条件:
	 * 		if(n == 1) {return 1;}
	 * 规律:
	 * 		if(n != 1) {return n*方法名(n-1);}
	 */
	//n=5,5*(4*(3*(2*1)))
	public static int jieCheng(int n){
		if(n==1){
			return 1;
		}else {
			return n*jieCheng(n-1);
		}
	}
}
/*
 * 需求：请大家把E:\JavaSE目录下所有的java结尾的文件的绝对路径给输出在控制台。
 * 
 * 分析：
 * 		A:封装目录
 * 		B:获取该目录下所有的文件或者文件夹的File数组
 * 		C:遍历该File数组，得到每一个File对象
 * 		D:判断该File对象是否是文件夹
 * 			是：回到B
 * 			否：继续判断是否以.java结尾
 * 				是：就输出该文件的绝对路径
 * 				否：不搭理它
 */
public class FilePathDemo {
	public static void main(String[] args) {
		// 封装目录
		File srcFolder = new File("E:\\JavaSE");

		// 递归功能实现
		getAllJavaFilePaths(srcFolder);
	}

	private static void getAllJavaFilePaths(File srcFolder) {
		// 获取该目录下所有的文件或者文件夹的File数组
		File[] fileArray = srcFolder.listFiles();

		// 遍历该File数组，得到每一个File对象
		for (File file : fileArray) {
			// 判断该File对象是否是文件夹
			if (file.isDirectory()) {
				getAllJavaFilePaths(file);
			} else {
				// 继续判断是否以.java结尾
				if (file.getName().endsWith(".java")) {
					// 就输出该文件的绝对路径
					System.out.println(file.getAbsolutePath());
				}
			}
		}
	}
}
```
###3.	IO流
 
```java
/*
 * 复制文本文件
 * 
 * 分析：
 * 		复制数据，如果我们知道用记事本打开并能够读懂，就用字符流，否则用字节流。
 * 		通过该原理，我们知道我们应该采用字符流更方便一些。
 * 		而字符流有5种方式，所以做这个题目我们有5种方式。推荐掌握第5种。
 * 数据源：
 * 		c:\\a.txt -- FileReader -- BufferdReader
 * 目的地：
 * 		d:\\b.txt -- FileWriter -- BufferedWriter
 */
public class CopyFileDemo {
	public static void main(String[] args) throws IOException {
		String srcString = "c:\\a.txt";
		String destString = "d:\\b.txt";
		// method1(srcString, destString);
		// method2(srcString, destString);
		// method3(srcString, destString);
		// method4(srcString, destString);
		method5(srcString, destString);
	}

	// 字符缓冲流一次读写一个字符串
	private static void method5(String srcString, String destString)
			throws IOException {
		BufferedReader br = new BufferedReader(new FileReader(srcString));
		BufferedWriter bw = new BufferedWriter(new FileWriter(destString));

		String line = null;
		while ((line = br.readLine()) != null) {
			bw.write(line);
			bw.newLine();
			bw.flush();
		}

		bw.close();
		br.close();
	}

	// 字符缓冲流一次读写一个字符数组
	private static void method4(String srcString, String destString)
			throws IOException {
		BufferedReader br = new BufferedReader(new FileReader(srcString));
		BufferedWriter bw = new BufferedWriter(new FileWriter(destString));

		char[] chs = new char[1024];
		int len = 0;
		while ((len = br.read(chs)) != -1) {
			bw.write(chs, 0, len);
		}

		bw.close();
		br.close();
	}

	// 字符缓冲流一次读写一个字符
	private static void method3(String srcString, String destString)
			throws IOException {
		BufferedReader br = new BufferedReader(new FileReader(srcString));
		BufferedWriter bw = new BufferedWriter(new FileWriter(destString));

		int ch = 0;
		while ((ch = br.read()) != -1) {
			bw.write(ch);
		}

		bw.close();
		br.close();
	}

	// 基本字符流一次读写一个字符数组
	private static void method2(String srcString, String destString)
			throws IOException {
		FileReader fr = new FileReader(srcString);
		FileWriter fw = new FileWriter(destString);

		char[] chs = new char[1024];
		int len = 0;
		while ((len = fr.read(chs)) != -1) {
			fw.write(chs, 0, len);
		}

		fw.close();
		fr.close();
	}

	// 基本字符流一次读写一个字符
	private static void method1(String srcString, String destString)
			throws IOException {
		FileReader fr = new FileReader(srcString);
		FileWriter fw = new FileWriter(destString);

		int ch = 0;
		while ((ch = fr.read()) != -1) {
			fw.write(ch);
		}

		fw.close();
		fr.close();
	}
}

/*
 * 复制图片
 * 
 * 分析：
 * 		复制数据，如果我们知道用记事本打开并能够读懂，就用字符流，否则用字节流。
 * 		通过该原理，我们知道我们应该采用字节流。
 * 		而字节流有4种方式，所以做这个题目我们有4种方式。推荐掌握第4种。
 * 
 * 数据源：
 * 		c:\\a.jpg -- FileInputStream -- BufferedInputStream
 * 目的地：
 * 		d:\\b.jpg -- FileOutputStream -- BufferedOutputStream
 */
public class CopyImageDemo {
	public static void main(String[] args) throws IOException {
		// 使用字符串作为路径
		// String srcString = "c:\\a.jpg";
		// String destString = "d:\\b.jpg";
		// 使用File对象做为参数
		File srcFile = new File("c:\\a.jpg");
		File destFile = new File("d:\\b.jpg");

		// method1(srcFile, destFile);
		// method2(srcFile, destFile);
		// method3(srcFile, destFile);
		method4(srcFile, destFile);
	}

	// 字节缓冲流一次读写一个字节数组
	private static void method4(File srcFile, File destFile) throws IOException {
		BufferedInputStream bis = new BufferedInputStream(new FileInputStream(
				srcFile));
		BufferedOutputStream bos = new BufferedOutputStream(
				new FileOutputStream(destFile));

		byte[] bys = new byte[1024];
		int len = 0;
		while ((len = bis.read(bys)) != -1) {
			bos.write(bys, 0, len);
		}

		bos.close();
		bis.close();
	}

	// 字节缓冲流一次读写一个字节
	private static void method3(File srcFile, File destFile) throws IOException {
		BufferedInputStream bis = new BufferedInputStream(new FileInputStream(
				srcFile));
		BufferedOutputStream bos = new BufferedOutputStream(
				new FileOutputStream(destFile));

		int by = 0;
		while ((by = bis.read()) != -1) {
			bos.write(by);
		}

		bos.close();
		bis.close();
	}

	// 基本字节流一次读写一个字节数组
	private static void method2(File srcFile, File destFile) throws IOException {
		FileInputStream fis = new FileInputStream(srcFile);
		FileOutputStream fos = new FileOutputStream(destFile);

		byte[] bys = new byte[1024];
		int len = 0;
		while ((len = fis.read(bys)) != -1) {
			fos.write(bys, 0, len);
		}

		fos.close();
		fis.close();
	}

	// 基本字节流一次读写一个字节
	private static void method1(File srcFile, File destFile) throws IOException {
		FileInputStream fis = new FileInputStream(srcFile);
		FileOutputStream fos = new FileOutputStream(destFile);

		int by = 0;
		while ((by = fis.read()) != -1) {
			fos.write(by);
		}

		fos.close();
		fis.close();
	}
}
```

 
##七、多线程
 
 
###1．实现多线程的三种方式(主要两种)
* 1)继承Thread类
* 2)实现Runnable接口
* 3)扩展一种：实现Callable接口。这个得和线程池结合。

**继承Thread类**
```java
/*
 * 该类要重写run()方法,为什么呢?
 * 不是类中的所有代码都需要被线程执行的。
 * 而这个时候，为了区分哪些代码能够被线程执行，java提供了Thread类中的run()用来包含那些被线程执行的代码。
 */
public class MyThread extends Thread {

	@Override
	public void run() {
		// 自己写代码
		// System.out.println("好好学习，天天向上");
		// 一般来说，被线程执行的代码肯定是比较耗时的。所以我们用循环改进
		for (int x = 0; x < 200; x++) {
			System.out.println(x);
		}
	}
}
/*
 * 需求：我们要实现多线程的程序。
 * 如何实现呢?
 * 		由于线程是依赖进程而存在的，所以我们应该先创建一个进程出来。
 * 		而进程是由系统创建的，所以我们应该去调用系统功能创建一个进程。
 * 		Java是不能直接调用系统功能的，所以，我们没有办法直接实现多线程程序。
 * 		但是呢?Java可以去调用C/C++写好的程序来实现多线程程序。
 * 		由C/C++去调用系统功能创建进程，然后由Java去调用这样的东西，
 * 		然后提供一些类供我们使用。我们就可以实现多线程程序了。
 * 那么Java提供的类是什么呢?
 * 		Thread
 * 		通过查看API，我们知道了有2中方式实现多线程程序。
 * 
 * 方式1：继承Thread类。
 * 步骤
 * 		A:自定义类MyThread继承Thread类。
 * 		B:MyThread类里面重写run()?
 * 			为什么是run()方法呢?
 * 		C:创建对象
 * 		D:启动线程
 */
public class MyThreadDemo {
	public static void main(String[] args) {
		// 创建线程对象
		// MyThread my = new MyThread();
		// // 启动线程
		// my.run();
		// my.run();
		// 调用run()方法为什么是单线程的呢?
		// 因为run()方法直接调用其实就相当于普通的方法调用,所以你看到的是单线程的效果
		// 要想看到多线程的效果，就必须说说另一个方法：start()
		// 面试题：run()和start()的区别?
		// run():仅仅是封装被线程执行的代码，直接调用是普通方法
		// start():首先启动了线程，然后再由jvm去调用该线程的run()方法。
		// MyThread my = new MyThread();
		// my.start();
		// // IllegalThreadStateException:非法的线程状态异常
		// // 为什么呢?因为这个相当于是my线程被调用了两次。而不是两个线程启动。
		// my.start();

		// 创建两个线程对象
		MyThread my1 = new MyThread();
		MyThread my2 = new MyThread();

		my1.start();
		my2.start();
	}
}
```
**实现Runnable接口**
```java
public class MyRunnable implements Runnable {

	@Override
	public void run() {
		for (int x = 0; x < 100; x++) {
			// 由于实现接口的方式就不能直接使用Thread类的方法了,但是可以间接的使用
		System.out.println(Thread.currentThread().getName() + ":" + x);
		}
	}
}
/*
 * 方式2：实现Runnable接口
 * 步骤：
 * 		A:自定义类MyRunnable实现Runnable接口
 * 		B:重写run()方法
 * 		C:创建MyRunnable类的对象
 * 		D:创建Thread类的对象，并把C步骤的对象作为构造参数传递
 */
public class MyRunnableDemo {
	public static void main(String[] args) {
		// 创建MyRunnable类的对象
		MyRunnable my = new MyRunnable();

		// 创建Thread类的对象，并把C步骤的对象作为构造参数传递
		// Thread(Runnable target)
		// Thread t1 = new Thread(my);
		// Thread t2 = new Thread(my);
		// t1.setName("林青霞");
		// t2.setName("刘意");

		// Thread(Runnable target, String name)
		Thread t1 = new Thread(my, "林青霞");
		Thread t2 = new Thread(my, "刘意");

		t1.start();
		t2.start();
	}
}
```
**扩展一种：实现Callable接口。这个得和线程池结合。**
```java
//Callable:是带泛型的接口。
//这里指定的泛型其实是call()方法的返回值类型。
public class MyCallable implements Callable {

	@Override
	public Object call() throws Exception {
		for (int x = 0; x < 100; x++) {
			System.out.println(Thread.currentThread().getName() + ":" + x);
		}
		return null;
	}

}
/*
 * 多线程实现的方式3：
 *  	A:创建一个线程池对象，控制要创建几个线程对象。
 * 			public static ExecutorService newFixedThreadPool(int nThreads)
 * 		B:这种线程池的线程可以执行：
 * 			可以执行Runnable对象或者Callable对象代表的线程
 * 			做一个类实现Runnable接口。
 * 		C:调用如下方法即可
 * 			Future<?> submit(Runnable task)
 *			<T> Future<T> submit(Callable<T> task)
 *		D:我就要结束，可以吗?
 *			可以。
 */
public class CallableDemo {
	public static void main(String[] args) {
		//创建线程池对象
		ExecutorService pool = Executors.newFixedThreadPool(2);
		
		//可以执行Runnable对象或者Callable对象代表的线程
		pool.submit(new MyCallable());
		pool.submit(new MyCallable());
		
		//结束
		pool.shutdown();
	}
}
```
**匿名内部类格式的线程创建**
```java
/*
 * 匿名内部类的格式：
 * 		new 类名或者接口名() {
 * 			重写方法;
 * 		};
 * 		本质：是该类或者接口的子类对象。
 */
public class ThreadDemo {
	public static void main(String[] args) {
		// 继承Thread类来实现多线程
		new Thread() {
			public void run() {
				for (int x = 0; x < 100; x++) {
					System.out.println(Thread.currentThread().getName() + 												":"+ x);
				}
			}
		}.start();

		// 实现Runnable接口来实现多线程
		new Thread(new Runnable() {
			@Override
			public void run() {
				for (int x = 0; x < 100; x++) {
					System.out.println(Thread.currentThread().getName() + 												":"+ x);
				}
			}
		}) {
		}.start();

		// 更有难度的
		new Thread(new Runnable() {
			@Override
			public void run() {
				for (int x = 0; x < 100; x++) {
					System.out.println("hello" + ":" + x);
				}
			}
		}) {
			public void run() {
				for (int x = 0; x < 100; x++) {
					System.out.println("world" + ":" + x);
				}
			}
		}.start();
	}
}
```
###2.	线程的一下方法
1)	获取线程对象的名称
```java
/*
 * 如何获取线程对象的名称呢?
 * public final String getName():获取线程的名称。
 * 如何设置线程对象的名称呢?
 * public final void setName(String name):设置线程的名称
 * 
 * 针对不是Thread类的子类中如何获取线程对象名称呢?
 * public static Thread currentThread():返回当前正在执行的线程对象
 * Thread.currentThread().getName()
 */
public class MyThreadDemo {
	public static void main(String[] args) {
		// 创建线程对象
		//无参构造+setXxx()
		// MyThread my1 = new MyThread();
		// MyThread my2 = new MyThread();
		// //调用方法设置名称
		// my1.setName("林青霞");
		// my2.setName("刘意");
		// my1.start();
		// my2.start();
		
		//带参构造方法给线程起名字
		// MyThread my1 = new MyThread("林青霞");
		// MyThread my2 = new MyThread("刘意");
		// my1.start();
		// my2.start();
		
		//我要获取main方法所在的线程对象的名称，该怎么办呢?
		//遇到这种情况,Thread类提供了一个很好玩的方法:
		//public static Thread currentThread():返回当前正在执行的线程对象
		System.out.println(Thread.currentThread().getName());
	}
}
```

 2)	守护线程
```java
/*
 * public final void setDaemon(boolean on):将该线程标记为守护线程或用户线程。
 * 当正在运行的线程都是守护线程时，Java 虚拟机退出。 该方法必须在启动线程前调用。 
 * 
 * 游戏：坦克大战。
 */
public class ThreadDaemonDemo {
	public static void main(String[] args) {
		ThreadDaemon td1 = new ThreadDaemon();
		ThreadDaemon td2 = new ThreadDaemon();

		td1.setName("关羽");
		td2.setName("张飞");

		// 设置收获线程
		td1.setDaemon(true);
		td2.setDaemon(true);

		td1.start();
		td2.start();

		Thread.currentThread().setName("刘备");
		for (int x = 0; x < 5; x++) {
			System.out.println(Thread.currentThread().getName() + ":" + x);
		}
	}
}
```
3)	join()
```java
/*
 * public final void join():等待该线程终止。 
 */
public class ThreadJoinDemo {
	public static void main(String[] args) {
		ThreadJoin tj1 = new ThreadJoin();
		ThreadJoin tj2 = new ThreadJoin();
		ThreadJoin tj3 = new ThreadJoin();

		tj1.setName("李渊");
		tj2.setName("李世民");
		tj3.setName("李元霸");

		tj1.start();
		try {
			tj1.join();
		} catch (InterruptedException e) {
			e.printStackTrace();
		}
		
		tj2.start();
		tj3.start();
	}
}
```
4)	线程优先级
```java
/*
 * 我们的线程没有设置优先级,肯定有默认优先级。
 * 那么，默认优先级是多少呢?
 * 如何获取线程对象的优先级?
 * 		public final int getPriority():返回线程对象的优先级
 * 如何设置线程对象的优先级呢?
 * 		public final void setPriority(int newPriority)：更改线程的优先级。 
 * 
 * 注意：
 * 		线程默认优先级是5。
 * 		线程优先级的范围是：1-10。
 * 		线程优先级高仅仅表示线程获取的 CPU时间片的几率高，但是要在次数比较多，或者多次运行的时候才能看到比较好的效果。
 * 		
 * IllegalArgumentException:非法参数异常。
 * 抛出的异常表明向方法传递了一个不合法或不正确的参数。 
 * 
 */
```
5)	线程休眠
```java
/*
 * 线程休眠
 *		public static void sleep(long millis)
 */	
```

7)	线程终止
```java
/*
 * public final void stop():让线程停止，过时了，但是还可以使用。
 * public void interrupt():中断线程。 把线程的状态终止，并抛出一个InterruptedException。
 */
```
8)	线程暂停
```java
/*
 * public static void yield():暂停当前正在执行的线程对象，并执行其他线程。 
 * 让多个线程的执行更和谐，但是不能靠它保证一人一次。
 */
```
###3.	线程组合线程池
```java
/*
 * 线程组： 把多个线程组合到一起。
 * 它可以对一批线程进行分类管理，Java允许程序直接对线程组进行控制。
 */
public class ThreadGroupDemo {
	public static void main(String[] args) {
		// method1();

		// 我们如何修改线程所在的组呢?
		// 创建一个线程组
		// 创建其他线程的时候，把其他线程的组指定为我们自己新建线程组
		method2();

		// t1.start();
		// t2.start();
	}

	private static void method2() {
		// ThreadGroup(String name)
		ThreadGroup tg = new ThreadGroup("这是一个新的组");

		MyRunnable my = new MyRunnable();
		// Thread(ThreadGroup group, Runnable target, String name)
		Thread t1 = new Thread(tg, my, "林青霞");
		Thread t2 = new Thread(tg, my, "刘意");
		
		System.out.println(t1.getThreadGroup().getName());
		System.out.println(t2.getThreadGroup().getName());
		
		//通过组名称设置后台线程，表示该组的线程都是后台线程
		tg.setDaemon(true);
	}

	private static void method1() {
		MyRunnable my = new MyRunnable();
		Thread t1 = new Thread(my, "林青霞");
		Thread t2 = new Thread(my, "刘意");
		// 我不知道他们属于那个线程组,我想知道，怎么办
		// 线程类里面的方法：public final ThreadGroup getThreadGroup()
		ThreadGroup tg1 = t1.getThreadGroup();
		ThreadGroup tg2 = t2.getThreadGroup();
		// 线程组里面的方法：public final String getName()
		String name1 = tg1.getName();
		String name2 = tg2.getName();
		System.out.println(name1);
		System.out.println(name2);
		// 通过结果我们知道了：线程默认情况下属于main线程组
		// 通过下面的测试，你应该能够看到，默任情况下，所有的线程都属于同一个组
		System.out.println(Thread.currentThread().getThreadGroup().getName());
	}
}

/*
 * 线程池的好处：线程池里的每一个线程代码结束后，并不会死亡，而是再次回到线程池中成为空闲状态，等待下一个对象来使用。
 * 
 * 如何实现线程的代码呢?
 * 		A:创建一个线程池对象，控制要创建几个线程对象。
 * 			public static ExecutorService newFixedThreadPool(int nThreads)
 * 		B:这种线程池的线程可以执行：
 * 			可以执行Runnable对象或者Callable对象代表的线程
 * 			做一个类实现Runnable接口。
 * 		C:调用如下方法即可
 * 			Future<?> submit(Runnable task)
 *			<T> Future<T> submit(Callable<T> task)
 *		D:我就要结束，可以吗?
 *			可以。
 */
public class ExecutorsDemo {
	public static void main(String[] args) {
		// 创建一个线程池对象，控制要创建几个线程对象。
		// public static ExecutorService newFixedThreadPool(int nThreads)
		ExecutorService pool = Executors.newFixedThreadPool(2);

		// 可以执行Runnable对象或者Callable对象代表的线程
		pool.submit(new MyRunnable());
		pool.submit(new MyRunnable());

		//结束线程池
		pool.shutdown();
	}
}
```
###4.	线程同步的两种方式(解决多线程的安全问题)
1)	同步代码块
2)	同步方法

```java
/*
 * 如何解决线程安全问题呢?
 * 
 * 要想解决问题，就要知道哪些原因会导致出问题:(而且这些原因也是以后我们判断一个程序是否会有线程安全问题的标准)
 * A:是否是多线程环境
 * B:是否有共享数据
 * C:是否有多条语句操作共享数据
 * 
 * 我们来回想一下我们的程序有没有上面的问题呢?
 * A:是否是多线程环境	是
 * B:是否有共享数据	是
 * C:是否有多条语句操作共享数据	是
 * 
 * 由此可见我们的程序出现问题是正常的，因为它满足出问题的条件。
 * 接下来才是我们要想想如何解决问题呢?
 * A和B的问题我们改变不了，我们只能想办法去把C改变一下。
 * 思想：
 * 		把多条语句操作共享数据的代码给包成一个整体，让某个线程在执行的时候，别人不能来执行。
 * 问题是我们不知道怎么包啊?其实我也不知道，但是Java给我们提供了：同步机制。
 * 
 * 同步代码块：
 * 		synchronized(对象){
 * 			需要同步的代码;
 * 		}
 * 
 * 		A:对象是什么呢?
 * 			我们可以随便创建一个对象试试。
 * 		B:需要同步的代码是哪些呢?
 * 			把多条语句操作共享数据的代码的部分给包起来
 * 
 * 		注意：
 * 			同步可以解决安全问题的根本原因就在那个对象上。该对象如同锁的功能。
 * 			多个线程必须是同一把锁。
 */
```
**一个测试锁对象的程序**
```java
public class SellTicket implements Runnable {

	// 定义100张票
	private static int tickets = 100;

	// 定义同一把锁
	private Object obj = new Object();
	private Demo d = new Demo();

	private int x = 0;
	
	//同步代码块用obj做锁
//	@Override
//	public void run() {
//		while (true) {
//			synchronized (obj) {
//				if (tickets > 0) {
//					try {
//						Thread.sleep(100);
//					} catch (InterruptedException e) {
//						e.printStackTrace();
//					}
//					System.out.println(Thread.currentThread().getName()
//							+ "正在出售第" + (tickets--) + "张票 ");
//				}
//			}
//		}
//	}
	
	//同步代码块用任意对象做锁
//	@Override
//	public void run() {
//		while (true) {
//			synchronized (d) {
//				if (tickets > 0) {
//					try {
//						Thread.sleep(100);
//					} catch (InterruptedException e) {
//						e.printStackTrace();
//					}
//					System.out.println(Thread.currentThread().getName()
//							+ "正在出售第" + (tickets--) + "张票 ");
//				}
//			}
//		}
//	}
	
	@Override
	public void run() {
		while (true) {
			if(x%2==0){
				synchronized (SellTicket.class) {
					if (tickets > 0) {
						try {
							Thread.sleep(100);
						} catch (InterruptedException e) {
							e.printStackTrace();
						}
						System.out.println(Thread.currentThread().getName()
								+ "正在出售第" + (tickets--) + "张票 ");
					}
				}
			}else {
//				synchronized (d) {
//					if (tickets > 0) {
//						try {
//							Thread.sleep(100);
//						} catch (InterruptedException e) {
//							e.printStackTrace();
//						}
//						System.out.println(Thread.currentThread().getName()
//								+ "正在出售第" + (tickets--) + "张票 ");
//					}
//				}
				
				sellTicket();
				
			}
			x++;
		}
	}

//	private void sellTicket() {
//		synchronized (d) {
//			if (tickets > 0) {
//			try {
//					Thread.sleep(100);
//			} catch (InterruptedException e) {
//					e.printStackTrace();
//			}
//			System.out.println(Thread.currentThread().getName()
//						+ "正在出售第" + (tickets--) + "张票 ");
//			}
//		}
//	}
	
	//如果一个方法一进去就看到了代码被同步了，那么我就再想能不能把这个同步加在方法上呢?
//	 private synchronized void sellTicket() {
//			if (tickets > 0) {
//			try {
//					Thread.sleep(100);
//			} catch (InterruptedException e) {
//					e.printStackTrace();
//			}
//			System.out.println(Thread.currentThread().getName()
//						+ "正在出售第" + (tickets--) + "张票 ");
//			}
//	}
	
	private static synchronized void sellTicket() {
		if (tickets > 0) {
		try {
				Thread.sleep(100);
		} catch (InterruptedException e) {
				e.printStackTrace();
		}
		System.out.println(Thread.currentThread().getName()
					+ "正在出售第" + (tickets--) + "张票 ");
		}
}
}

class Demo {
}
/*
 * A:同步代码块的锁对象是谁呢?
 * 		任意对象。
 * 
 * B:同步方法的格式及锁对象问题?
 * 		把同步关键字加在方法上。
 * 
 * 		同步方法是谁呢?
 * 			this
 * 
 * C:静态方法及锁对象问题?
 * 		静态方法的锁对象是谁呢?
 * 			类的字节码文件对象。(反射会讲)
 */
public class SellTicketDemo {
	public static void main(String[] args) {
		// 创建资源对象
		SellTicket st = new SellTicket();

		// 创建三个线程对象
		Thread t1 = new Thread(st, "窗口1");
		Thread t2 = new Thread(st, "窗口2");
		Thread t3 = new Thread(st, "窗口3");

		// 启动线程
		t1.start();
		t2.start();
		t3.start();
	}
}
```
###5.	JDK5以后提供的一个新的锁对象Lock
```java
/*
 * 虽然我们可以理解同步代码块和同步方法的锁对象问题，但是我们并没有直接看到在哪里加上了锁，在哪里释放了锁，
 * 为了更清晰的表达如何加锁和释放锁,JDK5以后提供了一个新的锁对象Lock。
 * 
 * Lock：
 * 		void lock()： 获取锁。
 * 		void unlock():释放锁。  
 * ReentrantLock是Lock的实现类.
 */
public class SellTicketDemo {
	public static void main(String[] args) {
		// 创建资源对象
		SellTicket st = new SellTicket();

		// 创建三个窗口
		Thread t1 = new Thread(st, "窗口1");
		Thread t2 = new Thread(st, "窗口2");
		Thread t3 = new Thread(st, "窗口3");

		// 启动线程
		t1.start();
		t2.start();
		t3.start();
	}
}
public class SellTicket implements Runnable {

	// 定义票
	private int tickets = 100;

	// 定义锁对象
	private Lock lock = new ReentrantLock();

	@Override
	public void run() {
		while (true) {
			try {
				// 加锁
				lock.lock();
				if (tickets > 0) {
					try {
						Thread.sleep(100);
					} catch (InterruptedException e) {
						e.printStackTrace();
					}
					System.out.println(Thread.currentThread().getName()
							+ "正在出售第" + (tickets--) + "张票");
				}
			} finally {
				// 释放锁
				lock.unlock();
			}
		}
	}
}
```

###6.	多线程同步的两个经典案例
 
**生产者和消费者模式的案例代码**
```java
/*
 * 分析：
 * 		资源类：Student	
 * 		设置学生数据:SetThread(生产者)
 * 		获取学生数据：GetThread(消费者)
 * 		测试类:StudentDemo
 * 
 * 问题1：按照思路写代码，发现数据每次都是:null---0
 * 原因：我们在每个线程中都创建了新的资源,而我们要求的时候设置和获取线程的资源应该是同一个
 * 如何实现呢?
 * 		在外界把这个数据创建出来，通过构造方法传递给其他的类。
 * 
 * 问题2：为了数据的效果好一些，我加入了循环和判断，给出不同的值,这个时候产生了新的问题
 * 		A:同一个数据出现多次
 * 		B:姓名和年龄不匹配
 * 原因：
 * 		A:同一个数据出现多次
 * 			CPU的一点点时间片的执行权，就足够你执行很多次。
 * 		B:姓名和年龄不匹配
 * 			线程运行的随机性
 * 线程安全问题：
 * 		A:是否是多线程环境		是
 * 		B:是否有共享数据		是
 * 		C:是否有多条语句操作共享数据	是
 * 解决方案：
 * 		加锁。
 * 		注意：
 * 			A:不同种类的线程都要加锁。
 * 			B:不同种类的线程加的锁必须是同一把。
 * 
 * 问题3:虽然数据安全了，但是呢，一次一大片不好看，我就想依次的一次一个输出。
 * 如何实现呢?
 * 		通过Java提供的等待唤醒机制解决。
 * 
 * 等待唤醒：
 * 		Object类中提供了三个方法：
 * 			wait():等待
 * 			notify():唤醒单个线程
 * 			notifyAll():唤醒所有线程
 * 		为什么这些方法不定义在Thread类中呢?
 * 			这些方法的调用必须通过锁对象调用，而我们刚才使用的锁对象是任意锁对象。
 * 			所以，这些方法必须定义在Object类中。
 * 
 * 最终版代码中：
 * 		把Student的成员变量给私有的了。
 * 		把设置和获取的操作给封装成了功能，并加了同步。
 * 		设置或者获取的线程里面只需要调用方法即可。
 */
public class StudentDemo {
	public static void main(String[] args) {
		//创建资源
		Student s = new Student();
		
		//设置和获取的类
		SetThread st = new SetThread(s);
		GetThread gt = new GetThread(s);

		//线程类
		Thread t1 = new Thread(st);
		Thread t2 = new Thread(gt);

		//启动线程
		t1.start();
		t2.start();
	}
}
public class Student {
	private String name;
	private int age;
	private boolean flag; // 默认情况是没有数据，如果是true，说明有数据

	public synchronized void set(String name, int age) {
		// 如果有数据，就等待
		if (this.flag) {
			try {
				this.wait();
			} catch (InterruptedException e) {
				e.printStackTrace();
			}
		}

		// 设置数据
		this.name = name;
		this.age = age;

		// 修改标记
		this.flag = true;
		this.notify();
	}

	public synchronized void get() {
		// 如果没有数据，就等待
		if (!this.flag) {
			try {
				this.wait();
			} catch (InterruptedException e) {
				e.printStackTrace();
			}
		}

		// 获取数据
		System.out.println(this.name + "---" + this.age);

		// 修改标记
		this.flag = false;
		this.notify();
	}
}
public class SetThread implements Runnable {

	private Student s;
	private int x = 0;

	public SetThread(Student s) {
		this.s = s;
	}

	@Override
	public void run() {
		while (true) {
			if (x % 2 == 0) {
				s.set("林青霞", 27);
			} else {
				s.set("刘意", 30);
			}
			x++;
		}
	}
}
public class GetThread implements Runnable {
	private Student s;

	public GetThread(Student s) {
		this.s = s;
	}

	@Override
	public void run() {
		while (true) {
			s.get();
		}
	}
}
```
###7.	基于多线程知识的一个定时器
```java
/*
 * 定时器：可以让我们在指定的时间做某件事情，还可以重复的做某件事情。
 * 依赖Timer和TimerTask这两个类：
 * Timer:定时
 * 		public Timer()
 * 		public void schedule(TimerTask task,long delay)
 * 		public void schedule(TimerTask task,long delay,long period)
 * 		public void cancel()
 * TimerTask:任务
 */
public class TimerDemo2 {
	public static void main(String[] args) {
		// 创建定时器对象
		Timer t = new Timer();
		// 3秒后执行爆炸任务第一次，如果不成功，每隔2秒再继续炸
		t.schedule(new MyTask2(), 3000, 2000);
	}
}

// 做一个任务
class MyTask2 extends TimerTask {
	@Override
	public void run() {
		System.out.println("beng,爆炸了");
	}
}
```

8.	同步的弊端
```java
/*
 * 		A:效率低
 * 		B:容易产生死锁
 * 
 * 死锁：
 * 		两个或两个以上的线程在争夺资源的过程中，发生的一种相互等待的现象。
 */
```
 

##八、GUI
 

##九、网络编程
###1．网络编程模型
a)	OSI参考模型
  

b)	TCP/IP参考模型
 

###2．网络编程三要素
```
		A:IP地址
			a:点分十进制
			b:IP地址的组成
			c:IP地址的分类
			d:dos命令
			e:InetAddress
		B:端口
			是应用程序的标识。范围：0-65535。其中0-1024不建议使用。
		C:协议
			UDP:数据打包,有限制,不连接,效率高,不可靠
			TCP:建立数据通道,无限制,效率低,可靠
```
1)	IP地址
```
	IP地址的分类：
		A类	1.0.0.1---127.255.255.254	
(1)10.X.X.X是私有地址(私有地址就是在互联网上不使用，而被用在局域网络中的地址)			(2)127.X.X.X是保留地址，用做循环测试用的。
		B类	128.0.0.1---191.255.255.254	172.16.0.0---172.31.255.255是私有地址。169.254.X.X			是保留地址。
		C类	192.0.0.1---223.255.255.254	192.168.X.X是私有地址
		D类	224.0.0.1---239.255.255.254 	
E类	240.0.0.1---247.255.255.254
```

2)	InetAddress类
```
* public static InetAddress getByName(String host):根据主机名或者	  IP地址的字符串表示得到IP地址对象
```

3)	UDP和TCP协议
```
UDP
将数据源和目的封装成数据包中，不需要建立连接；每个数据报的大小在限制在64k；因无连接，是不可靠协议；不需要建立连接，速度快.
TCP
建立连接，形成传输数据的通道；在连接中进行大数据量传输；通过三次握手完成连接，是可靠协议；必须建立连接，效率会稍低.
```

###3．Socket机制
**Socket套接字：**
网络上具有唯一标识的IP地址和端口号组合在一起才能构成唯一能识别的标识符套接字。
**Socket原理机制：**
通信的两端都有Socket。
网络通信其实就是Socket间的通信。
数据在两个Socket间通过IO传输。
 


###4．UDP协议发送和接收数据
```java
/*
 * UDP协议发送数据：
 * A:创建发送端Socket对象
 * B:创建数据，并把数据打包
 * C:调用Socket对象的发送方法发送数据包
 * D:释放资源
 */
public class SendDemo {
	public static void main(String[] args) throws IOException {
		// 创建发送端Socket对象
		// DatagramSocket()
		DatagramSocket ds = new DatagramSocket();

		// 创建数据，并把数据打包
		// DatagramPacket(byte[] buf, int length, InetAddress address, int 			port)
		// 创建数据
		byte[] bys = "hello,udp,我来了".getBytes();
		// 长度
		int length = bys.length;
		// IP地址对象
		InetAddress address = InetAddress.getByName("192.168.12.92");
		// 端口
		int port = 10086;
		DatagramPacket dp = new DatagramPacket(bys, length, address, port);

		// 调用Socket对象的发送方法发送数据包
		// public void send(DatagramPacket p)
		ds.send(dp);

		// 释放资源
		ds.close();
	}
}
/*
 * UDP协议接收数据：
 * A:创建接收端Socket对象
 * B:创建一个数据包(接收容器)
 * C:调用Socket对象的接收方法接收数据
 * D:解析数据包，并显示在控制台
 * E:释放资源
 */
public class ReceiveDemo {
	public static void main(String[] args) throws IOException {
		// 创建接收端Socket对象
		// DatagramSocket(int port)
		DatagramSocket ds = new DatagramSocket(10086);

		// 创建一个数据包(接收容器)
		// DatagramPacket(byte[] buf, int length)
		byte[] bys = new byte[1024];
		int length = bys.length;
		DatagramPacket dp = new DatagramPacket(bys, length);

		// 调用Socket对象的接收方法接收数据
		// public void receive(DatagramPacket p)
		ds.receive(dp); // 阻塞式

		// 解析数据包，并显示在控制台
		// 获取对方的ip
		// public InetAddress getAddress()
		InetAddress address = dp.getAddress();
		String ip = address.getHostAddress();
		// public byte[] getData():获取数据缓冲区
		// public int getLength():获取数据的实际长度
		byte[] bys2 = dp.getData();
		int len = dp.getLength();
		String s = new String(bys2, 0, len);
		System.out.println(ip + "传递的数据是:" + s);

		// 释放资源
		ds.close();
	}
}
```

###5．TCP协议发送和接收数据
```java
/*
 * TCP协议发送数据：
 * A:创建发送端的Socket对象
 * 		这一步如果成功，就说明连接已经建立成功了。
 * B:获取输出流，写数据
 * C:释放资源
 * 
 * 连接被拒绝。TCP协议一定要先看服务器。
 * java.net.ConnectException: Connection refused: connect
 */
public class ClientDemo {
	public static void main(String[] args) throws IOException {
		// 创建发送端的Socket对象
		// Socket(InetAddress address, int port)
		// Socket(String host, int port)
		// Socket s = new Socket(InetAddress.getByName("192.168.12.92"), 				8888);
		Socket s = new Socket("192.168.12.92", 8888);

		// 获取输出流，写数据
		// public OutputStream getOutputStream()
		OutputStream os = s.getOutputStream();
		os.write("hello,tcp,我来了".getBytes());

		// 释放资源
		s.close();
	}
}


/*
 * TCP协议接收数据：
 * A:创建接收端的Socket对象
 * B:监听客户端连接。返回一个对应的Socket对象
 * C:获取输入流，读取数据显示在控制台
 * D:释放资源
 */
public class ServerDemo {
	public static void main(String[] args) throws IOException {
		// 创建接收端的Socket对象
		// ServerSocket(int port)
		ServerSocket ss = new ServerSocket(8888);

		// 监听客户端连接。返回一个对应的Socket对象
		// public Socket accept()
		Socket s = ss.accept(); // 侦听并接受到此套接字的连接。此方法在连接传入之前									一直阻塞。
		// 获取输入流，读取数据显示在控制台
		InputStream is = s.getInputStream();

		byte[] bys = new byte[1024];
		int len = is.read(bys); // 阻塞式方法
		String str = new String(bys, 0, len);

		String ip = s.getInetAddress().getHostAddress();

		System.out.println(ip + "---" + str);

		// 释放资源
		s.close();
		// ss.close(); //这个不应该关闭
	}
}

```
###6．UDP与TCP比较
 

##十、反射
###1．类加载器
1)	类的加载
当程序要使用某个类时，如果该类还未被加载到内存中，则系统会通过加载，连接，初始化三步来实现对这个类进行初始化。
①　加载 :
就是指将class文件读入内存，并为之创建一个Class对象。
任何类被使用时系统都会建立一个Class对象。
②　连接 :
验证 是否有正确的内部结构，并和其他类协调一致
准备 负责为类的静态成员分配内存，并设置默认初始化值
解析 将类的二进制数据中的符号引用替换为直接引用
初始化 就是我们以前讲过的初始化步骤
2)	类的初始化时机
①　创建类的实例
②　访问类的静态变量，或者为静态变量赋值
③　调用类的静态方法
④　使用反射方式来强制创建某个类或接口对应的java.lang.Class对象
⑤　初始化某个类的子类
⑥　直接使用java.exe命令来运行某个主类

3)	类加载器
负责将.class文件加载到内在中，并为之生成对应的Class对象。
虽然我们不需要关心类加载机制，但是了解这个机制我们就能更好的理解	程序的运	行。
类加载器的组成
Bootstrap ClassLoader 根类加载器
Extension ClassLoader 扩展类加载器
Sysetm ClassLoader 系统类加载器

4)	类加载器的作用
①　Bootstrap ClassLoader 根类加载器
也被称为引导类加载器，负责Java核心类的加载
比如System,String等。在JDK中JRE的lib目录下rt.jar文件中
②　Extension ClassLoader 扩展类加载器
负责JRE的扩展目录中jar包的加载。
在JDK中JRE的lib目录下ext目录
③　Sysetm ClassLoader 系统类加载器
负责在JVM启动时加载来自java命令的class文件，以及classpath环境变量所指定的jar包和类路径



###2．反射
JAVA反射机制是在运行状态中，对于任意一个类，都能够知道这个类的所有属性和方法；对于任意一个对象，都能够调用它的任意一个方法和属性；这种动态获取的信息以及动态调用对象的方法的功能称为java语言的反射机制。
要想解剖一个类,必须先要获取到该类的字节码文件对象。而解剖使用的就是Class类中的方法.所以先要获取到每一个字节码文件对应的Class类型的对象.
```java
/*
 * 反射：就是通过class文件对象，去使用该文件中的成员变量，构造方法，成员方法。
 * 
 * Person p = new Person();
 * p.使用
 * 
 * 要想这样使用，首先你必须得到class文件对象，其实也就是得到Class类的对象。
 * Class类：
 * 		成员变量	Field
 * 		构造方法	Constructor
 * 		成员方法	Method
 * 
 * 获取class文件对象的方式：
 * A:Object类的getClass()方法
 * B:数据类型的静态属性class
 * C:Class类中的静态方法
 * 		public static Class forName(String className)
 * 
 * 一般我们到底使用谁呢?
 * 		A:自己玩	任选一种，第二种比较方便
 * 		B:开发	第三种
 * 			为什么呢?因为第三种是一个字符串，而不是一个具体的类名。这样我们就可以把这样的字符串配置到配置文件中。
 */
public class ReflectDemo {
	public static void main(String[] args) throws ClassNotFoundException {
		// 方式1
		Person p = new Person();
		Class c = p.getClass();

		Person p2 = new Person();
		Class c2 = p2.getClass();

		System.out.println(p == p2);// false
		System.out.println(c == c2);// true

		// 方式2
		Class c3 = Person.class;
		// int.class;
		// String.class;
		System.out.println(c == c3);//true

		// 方式3
		// ClassNotFoundException
		Class c4 = Class.forName("cn.itcast_01.Person");
		System.out.println(c == c4);//true
	}
}
```

1)	通过反射获取构造方法
```java
/*
 * 通过反射获取构造方法并使用。
 */
public class ReflectDemo {
	public static void main(String[] args) throws Exception {
		// 获取字节码文件对象
		Class c = Class.forName("cn.itcast_01.Person");

		// 获取构造方法
		// public Constructor[] getConstructors():所有公共构造方法
		// public Constructor[] getDeclaredConstructors():所有构造方法
		// Constructor[] cons = c.getDeclaredConstructors();
		// for (Constructor con : cons) {
		// System.out.println(con);
		// }

		// 获取单个构造方法
		// public Constructor<T> getConstructor(Class<?>... parameterTypes)
		// 参数表示的是：你要获取的构造方法的构造参数个数及数据类型的class字节码文件对象
		Constructor con = c.getConstructor();// 返回的是构造方法对象

		// Person p = new Person();
		// System.out.println(p);
		// public T newInstance(Object... initargs)
		// 使用此 Constructor 对象表示的构造方法来创建该构造方法的声明类的新实例，并用指定的初始化参数初始化该实例。
		Object obj = con.newInstance();
		System.out.println(obj);
		
		// Person p = (Person)obj;
		// p.show();
		
		//---------------------------------------------------
		
		// 获取带参构造方法对象
		// public Constructor<T> getConstructor(Class<?>... parameterTypes)
		Constructor con2 = c.getConstructor(String.class, int.class,
						String.class);

		// 通过带参构造方法对象创建对象
		// public T newInstance(Object... initargs)
		Object obj2 = con2.newInstance("林青霞", 27, "北京");
		
		//---------------------------------------------------
		
		Constructor con3 = c.getDeclaredConstructor(String.class);

		// 用该私有构造方法创建对象
		// IllegalAccessException:非法的访问异常。
		// 暴力访问
		con3.setAccessible(true);// 值为true则指示反射的对象在使用时应该取消Java语言访问检查。
		Object obj3 = con3.newInstance("风清扬");

		System.out.println(obj3);
	}
}
```

2)	通过反射获取成员变量
```java
/*
 * 通过发生获取成员变量并使用
 */
public class ReflectDemo {
	public static void main(String[] args) throws Exception {
		// 获取字节码文件对象
		Class c = Class.forName("cn.itcast_01.Person");

		// 获取所有的成员变量
		// Field[] fields = c.getFields();
		// Field[] fields = c.getDeclaredFields();
		// for (Field field : fields) {
		// System.out.println(field);
		// }

		/*
		 * Person p = new Person(); p.address = "北京"; System.out.println(p);
		 */

		// 通过无参构造方法创建对象
		Constructor con = c.getConstructor();
		Object obj = con.newInstance();
		System.out.println(obj);

		// 获取单个的成员变量
		// 获取address并对其赋值
		Field addressField = c.getField("address");
		// public void set(Object obj,Object value)
		// 将指定对象变量上此 Field 对象表示的字段设置为指定的新值。
		addressField.set(obj, "北京"); // 给obj对象的addressField字段设置值为"北京"
		System.out.println(obj);

		// 获取name并对其赋值
		// NoSuchFieldException
		Field nameField = c.getDeclaredField("name");
		// IllegalAccessException
		nameField.setAccessible(true);
		nameField.set(obj, "林青霞");
		System.out.println(obj);

		// 获取age并对其赋值
		Field ageField = c.getDeclaredField("age");
		ageField.setAccessible(true);
		ageField.set(obj, 27);
		System.out.println(obj);
	}
}
```

3)	通过反射获取方法
```java
public class ReflectDemo {
	public static void main(String[] args) throws Exception {
		// 获取字节码文件对象
		Class c = Class.forName("cn.itcast_01.Person");

		// 获取所有的方法
		// Method[] methods = c.getMethods(); // 获取自己的包括父亲的公共方法
		// Method[] methods = c.getDeclaredMethods(); // 获取自己的所有的方法
		// for (Method method : methods) {
		// System.out.println(method);
		// }

		Constructor con = c.getConstructor();
		Object obj = con.newInstance();

		/*
		 * Person p = new Person(); p.show();
		 */

		// 获取单个方法并使用
		// public void show()
		// public Method getMethod(String name,Class<?>... parameterTypes)
		// 第一个参数表示的方法名，第二个参数表示的是方法的参数的class类型
		Method m1 = c.getMethod("show");
		// obj.m1(); // 错误
		// public Object invoke(Object obj,Object... args)
		// 返回值是Object接收,第一个参数表示对象是谁，第二参数表示调用该方法的实际参数
		m1.invoke(obj); // 调用obj对象的m1方法

		System.out.println("----------");
		// public void method(String s)
		Method m2 = c.getMethod("method", String.class);
		m2.invoke(obj, "hello");
		System.out.println("----------");

		// public String getString(String s, int i)
		Method m3 = c.getMethod("getString", String.class, int.class);
		Object objString = m3.invoke(obj, "hello", 100);
		System.out.println(objString);
		// String s = (String)m3.invoke(obj, "hello",100);
		// System.out.println(s);
		System.out.println("----------");

		// private void function()
		Method m4 = c.getDeclaredMethod("function");
		m4.setAccessible(true);
		m4.invoke(obj);
	}
}
```

3．动态代理
在Java中java.lang.reflect包下提供了一个Proxy类和一个InvocationHandler接口，通过使用这个类和接口就可以生成动态代理对象。JDK提供的代理只能针对接口做代理。我们有更强大的代理cglib.
Proxy类中的方法创建动态代理类对象
```public static Object newProxyInstance(ClassLoader loader,Class<?>[] interfaces,InvocationHandler h)```
最终会调用InvocationHandler的方法
**InvocationHandler** 
```Object invoke(Object proxy,Method method,Object[] args);```

```java
public class Test {
	public static void main(String[] args) {
		UserDao ud = new UserDaoImpl();
		ud.add();
		ud.delete();
		ud.update();
		ud.find();
		System.out.println("-----------");
		// 我们要创建一个动态代理对象
		// Proxy类中有一个方法可以创建动态代理对象
		// public static Object newProxyInstance(ClassLoader loader,Class<?>[]
		// interfaces,InvocationHandler h)
		// 我准备对ud对象做一个代理对象
		MyInvocationHandler handler = new MyInvocationHandler(ud);
		UserDao proxy = (UserDao) Proxy.newProxyInstance(ud.getClass()
				.getClassLoader(), ud.getClass().getInterfaces(), handler);
		proxy.add();
		proxy.delete();
		proxy.update();
		proxy.find();
		System.out.println("-----------");

		StudentDao sd = new StudentDaoImpl();
		MyInvocationHandler handler2 = new MyInvocationHandler(sd);
		StudentDao proxy2 = (StudentDao) Proxy.newProxyInstance(sd.getClass()
				.getClassLoader(), sd.getClass().getInterfaces(), handler2);
		proxy2.login();
		proxy2.regist();
	}

/*
 * 用户操作接口
 */
public interface UserDao {
	public abstract void add();
	public abstract void delete();
	public abstract void update();
	public abstract void find();
}

public class UserDaoImpl implements UserDao {
	@Override
	public void add() {
		System.out.println("添加功能");
	}
	@Override
	public void delete() {
		System.out.println("删除功能");
	}
	@Override
	public void update() {
		System.out.println("修改功能");
	}
	@Override
	public void find() {
		System.out.println("查找功能");
	}
}


public class MyInvocationHandler implements InvocationHandler {
	private Object target; // 目标对象

	public MyInvocationHandler(Object target) {
		this.target = target;
	}

	@Override
	public Object invoke(Object proxy, Method method, Object[] args)
			throws Throwable {
		System.out.println("权限校验");
		Object result = method.invoke(target, args);
		System.out.println("日志记录");
		return result; // 返回的是代理对象
	}
}
```

**一个通过反射读取配置文件运行类中的方法的案例**
```java
/*
 * 通过配置文件运行类中的方法
 * 
 * 反射：
 * 		需要有配置文件配合使用。
 * 		用class.txt代替。
 * 		并且你知道有两个键。
 * 			className
 * 			methodName
 */
public class Test {
	public static void main(String[] args) throws Exception {
		// 反射前的做法
		// Student s = new Student();
		// s.love();
		// Teacher t = new Teacher();
		// t.love();
		// Worker w = new Worker();
		// w.love();
		// 反射后的做法

		// 加载键值对数据
		Properties prop = new Properties();
		FileReader fr = new FileReader("class.properties");
		prop.load(fr);
		fr.close();

		// 获取数据
		String className = prop.getProperty("className");
		String methodName = prop.getProperty("methodName");

		// 反射
		Class c = Class.forName(className);

		Constructor con = c.getConstructor();
		Object obj = con.newInstance();

		// 调用方法
		Method m = c.getMethod(methodName);
		m.invoke(obj);
	}
}

```