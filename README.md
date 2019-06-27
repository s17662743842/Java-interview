# Java-interview

##Java基础面试题集
- 仅供参考，写到一半（大部分为借鉴别人博客文章，在此表示感谢）才发现已经有了，算是自己的一次复习+新的尝试

###### 1、面向对象的特征有哪些方面？

- 封装
  封装把一个对象的属性私有化，同时提供一些可以被外界访问的属性的方法，如果属性不想被外界访问，我们大可不必提供方法给外界访问。但是如果一个类没有提供给外界访问的方法，那么这个类也没有什么意义了。
- 继承
  继承是使用已存在的类的定义作为基础建立新类的技术，新类的定义可以增加新的数据或新的功能，也可以用父类的功能，但不能选择性地继承父类。通过使用继承我们能够非常方便地复用以前的代码。

关于继承如下 3 点请记住：

1. 子类拥有父类对象所有的属性和方法（包括私有属性和私有方法），但是父类中的私有属性和方法子类是无法访问，**只是拥有**。
2. 子类可以拥有自己属性和方法，即子类可以对父类进行扩展。
3. 子类可以用自己的方式实现父类的方法。（以后介绍）。

- 多态
  所谓多态就是指程序中定义的引用变量所指向的具体类型和通过该引用变量发出的方法调用在编程时并不确定，而是在程序运行期间才确定，即一个引用变量到底会指向哪个类的实例对象，该引用变量发出的方法调用到底是哪个类中实现的方法，必须在由程序运行期间才能决定。

在Java中有两种形式可以实现多态：继承（多个子类对同一方法的重写）和接口（实现接口并覆盖接口中同一方法）。

###### 2、访问修饰符public,private,protected,以及不写（默认）时的区别？(略)

###### 3、String 是最基本的数据类型吗？

- 不是，引用数据类型（可以谈谈object）。

###### 4、float f=3.4;是否正确？

- 错，3.4是双精度数，将双精度型（double）赋值给浮点型（float）属于下转型（down-casting，也称为窄化）会造成精度损失，因此需要强制类型转换float f =(float)3.4; 或者写成float f =3.4F;。

###### 5、short s1 = 1; s1 = s1 + 1;有错吗?short s1 = 1; s1 += 1;有错吗？

- 有，第一个要先short转int再强转short,，第二个对

###### 6、Java有没有goto？(略，保留字)

###### 7、int和Integer有什么区别？

- 基本数据类型和包装类（引用数据类型）回答从equals方法，常量池引用（-128~127）来答[详情见博客](https://blog.csdn.net/chenliguan/article/details/53888018)

###### 8、&amp;和&amp;&的区别？

- 与运算分为普通与（&）和短路与（&&）两种

  ①普通与：所有的判断条件都要判断. 

  ②短路与：如果前面的判断返回了false,那么后面不再判断，最终结果就是false.

- 或运算分为普通或（|）和短路（||）或两种

  ①普通或：所有的判断条件都要判断.

  ②短路或：如果前面的判断返回了true,那么后面不再判断，最终结果就是true.

位运算：

位与运算（&）和位或运算（|），其中“&&”和“||”不能应用在位运算上。

###### 10、Math.round(11.5) 等于多少？Math.round(-11.5)等于多少？

- 12  ,-11 

###### 11、switch 是否能作用在byte 上，是否能作用在long 上，是否能作用在String上？

- switch只能是int 或这能转化为int型的byte,short,char,jdk1.7之后String也可以。[详情见博客](https://blog.csdn.net/singit/article/details/47708797)

###### 12、用最有效率的方法计算2乘以8？

- 2 << 3 位运算

###### 13、数组有没有length()方法？String有没有length()方法？

- 数组中没有length()这个方法，但是数组中有length这个属性。用来表示数组的长度。

  String中有length()这个方法。用来得到字符串的长度。

###### 14、在Java中，如何跳出当前的多重嵌套循环？

- break语句2种，(break是结束整个循环体，continue是结束单次循环（跳出当前循环，到下一步))[详情见博客](https://blog.csdn.net/singit/article/details/47708797)
- return 

###### 15、构造器（constructor）是否可被重写（override）？

- Constructor(构造器)不能被继承，所以不能被override(重写)，但是可以被overloading(重载)

###### 16、两个对象值相同(x.equals(y) == true)，但却可有不同的hash code，这句话对不对？

不对，（JVM中有一个不成文的约束，就是两个对象value相同，即equal，那么其hashcode也要相同），根据引用数据类型和基本数据类型，分地址值（值），hashcode，equals方法来答

- [详情见博客](https://blog.csdn.net/menghuanguaishou/article/details/80025647)

###### 17、是否可以继承String类？

- 不可以，因为String类有final修饰符，而final修饰的类是不能被继承的，实现细节不允许改变

###### 18、当一个对象被当作参数传递到一个方法后，此方法可改变这个对象的属性，并可返回变化后的结果，那么这里到底是值传递还是引用传递？

- 是值传递。Java编程语言中只有由值传递参数的。当一个对象实例作为一个参数被传递到方法中时，参数的值就是该对象的引用。对象的内容可以在被调用的方法中改变，但对象的引用是永远不会改变的。[详见]([https://snailclimb.gitee.io/javaguide/#/./essential-content-for-interview/MostCommonJavaInterviewQuestions/%E7%AC%AC%E4%B8%80%E5%91%A8%EF%BC%882018-8-7%EF%BC%89](https://snailclimb.gitee.io/javaguide/#/./essential-content-for-interview/MostCommonJavaInterviewQuestions/第一周（2018-8-7）))

  ###### 19、String和StringBuilder、StringBuffer的区别？

- String 类中使用 final 关键字字符数组保存字符串，`private　final　char　value[]`，所以 String 对象是不可变的。而StringBuilder 与 StringBuffer 都继承自 AbstractStringBuilder 类，在 AbstractStringBuilder 中也是使用字符数组保存字符串`char[]value` 但是没有用 final 关键字修饰，可变，但 StringBuffer对方法加了同步锁或者对调用的方法加了同步锁，是线程安全的

###### 20、重载（Overload）和重写（Override）的区别。重载的方法能否根据返回类型进行区分？

- 重载： 发生在同一个类中，方法名必须相同，参数类型不同、个数不同、顺序不同，方法返回值和访问修饰符可以不同，发生在编译时。 　　
- 重写： 发生在父子类中，方法名、参数列表必须相同，返回值范围小于等于父类，抛出的异常范围小于等于父类，访问修饰符范围大于等于父类；如果父类方法访问修饰符为private则子类就不能重写该方法。

###### 21、描述一下JVM加载class文件的原理机制？

- JVM中类的装载是由类加载器（ClassLoader）和它的子类来实现的，Java中的类加载器是一个重要的Java运行时系统组件，它负责在运行时查找和装入类文件中的类。 由于Java的跨平台性，经过编译的Java源程序并不是一个可执行程序，而是一个或多个类文件。

- 当Java程序需要使用某个类时，JVM会确保这个类已经被加载、连接（验证、准备和解析）和初始化

- 类的加载是指把类的.class文件中的数据读入到内存中，通常是创建一个字节数组读入.class文件，然后产生与所加载类对应的Class对象。加载完成后，Class对象还不完整，所以此时的类还不可用。当类被加载后就进入连接阶段，这一阶段包括验证、准备（为静态变量分配内存并设置默认的初始值）和解析（将符号引用替换为直接引用）三个步骤。最后JVM对类进行初始化，包括：1)如果类存在直接的父类并且这个类还没有被初始化，那么就先初始化父类；2)如果类中存在初始化语句，就依次执行这些初始化语句。 

- 双亲委派机制：

  ​		类加载器包括(从上到下，父类加载器与子类加载器不一定是继承关系（包装）)

  ​		根加载器（BootStrap）、扩展加载器（Extension）、系统加载器（System）和用户自定义类加载器（java.lang.ClassLoader的子类）。

  ​		类的加载首先请求父类加载器加载，父类加载器无能为力时才由其子类加载器自行加载（不同类加载器加载同一个class没有可比性，jvm会认为是不同的类）

###### 22、char 型变量中能不能存贮一个中文汉字，为什么？

- 可以，char类型是用来存储unicode编码的，汉字包含在了unicode编码中，所以char可以存储汉字，如果unicode编码不包含某个特殊的汉字那就不能存储这个汉字了，unicode编码占2字节，所以char类型的变量占2个字节

###### 23、抽象类（abstract class）和接口（interface）有什么异同？

1. 接口的方法默认是public，所有方法在接口中不能有实现，抽象类可以有非抽象的方法
2. 接口中的实例变量默认是final类型的，而抽象类中则不一定
3. 一个类可以实现多个接口，但最多只能实现一个抽象类
4. 一个类实现接口的话要实现接口的所有方法，而抽象类不一定
5. 接口不能用new实例化，但可以声明，但是必须引用一个实现该接口的对象 从设计层面来说，抽象是对类的抽象，是一种模板设计，接口是行为的抽象，是一种行为的规范。

- 注意：Java8 后接口可以有默认实现( default )。

###### 24、静态嵌套类(Static Nested Class)和内部类（Inner Class）的不同？

- Static Nested Class是被声明为静态（static）的内部类，它可以不依赖于外部类实例被实例化。而通常的内部类需要在外部类实例化后才能实例化
  [详情见博客](https://blog.csdn.net/fanguangjun123/article/details/78665546)

###### 25、Java 中会存在内存泄漏吗，请简单描述。

- 逃逸分析[建议拥有jvm知识后再看](https://www.cnblogs.com/lsx1993/p/4620017.html) 面试考点：对象实例是否都是在堆上分配，内存泄漏
- 内存泄露的发生场景，通俗地说，就是程序员可能创建了一个对象，以后一直不再使用这个对象，这个对象却一直被引用，即这个对象无用但是却无法被垃圾回收器回收的，这就是**java**中的内存泄露，一定要让程序将各种分支情况都完整执行到程序结束，然后看某个对象是否被使用过，如果没有，则才能判定这个对象属于内存泄露
- 如果一个外部类的实例对象的方法返回了一个内部类的实例对象，这个内部类对象被长期引用了，即使那个外部类实例对象不再被使用，但由于内部类持久外部类的实例对象，这个外部类对象将**不会**被垃圾回收，这也会造成内存泄露。
- 当一个对象被存储进HashSet集合中以后，就不能修改这个对象中的那些参与计算哈希值的字段了，否则，对象修改后的哈希值与最初存储进HashSet集合中时的哈希值就不同了，在这种情况下，即使在contains方法使用该对象的当前引用作为的参数去HashSet集合中检索对象，也将返回找不到对象的结果，这也会导致无法从HashSet集合中单独删除当前对象，造成内存泄露。

###### 26、抽象的（abstract）方法是否可同时是静态的（static）,是否可同时是本地方法（native），是否可同时被synchronized修饰？

- 抽象方法需要子类重写，而静态的方法是无法被重写的，因此二者是矛盾的。
  本地方法是由本地代码（如C代码）实现的方法，而抽象方法是没有实现的，也是矛盾的。

  synchronized和方法的实现细节有关，抽象方法不涉及实现细节，因此也是相互矛盾的

###### 27、阐述静态变量和实例变量的区别。

- 静态（static）变量不需要实例化，类被加载后即可调用，实例变量属于某个对象的属性，必须创建了实例对象，其中的实例变量才会被分配空间，才能使用这个实例变量。

###### 28、是否可以从一个静态（static）方法内部发出对非静态（non-static）方法的调用？

- 不可以，静态方法调用时，非静态方法的对象可能没有实例化

29、如何实现对象克隆？（https://www.cnblogs.com/Qian123/p/5710533.html）

- 实现对象克隆有两种方式：

  1). 实现Cloneable接口并重写Object类中的clone()方法；

  2). 实现Serializable接口，通过对象的序列化和反序列化实现克隆，可以实现真正的深度克隆。

- **注意：**基于序列化和反序列化实现的克隆不仅仅是深度克隆，更重要的是通过泛型限定，可以检查出要克隆的对象是否支持序列化，这项检查是编译器完成的，不是在运行时抛出异常，这种是方案明显优于使用Object类的clone方法克隆对象。让问题在编译的时候暴露出来总是优于把问题留到运行时。

###### 31、String s = new String("xyz");创建了几个字符串对象？

- 两个，一个string s对象，一个“xyz”常量池对象

###### 32、接口是否可继承（extends）接口？抽象类是否可实现（implements）接口？抽象类是否可继承具体类（concrete class）？

- 接口可以继承接口，而且支持多重继承。

  抽象类可以实现(implements)接口。

  抽象类可继承具体类也可以继承抽象类。

###### 33、一个".java"源文件中是否可以包含多个类（不是内部类）？有什么限制？

- 可以 ，但有且仅有一个public类，类名与xxx.java的xxx相同

###### 34、Anonymous Inner Class(匿名内部类)是否可以继承其它类？是否可以实现接口？

- 匿名内部类在实现时必须借助一个借口或者一个抽象类或者一个普通类来构造，从这过层次上讲匿名内部类是实现了接口或者继承了类，但是不能通过extends或implement关键词来继承类或实现接口。

  匿名内部类即没有名字的内部类。当我们只需要用某一个类一次时，且该类从意义上需要实现某个类或某个接口，这个特殊的扩展类就以匿名内部类来展现。

  一般的用途：

  1、覆盖某个超类的方法，并且该扩展类只在本类内用一次。

  2、继承抽象类，并实例化其抽象方法，并且该扩展类只在本类内用一次。

  3、实现接口，实例化其方法，并且该扩展类只在本类内用一次。

- 注意：
  一、由于匿名内部类没有名字，所以它没有构造函数。因为没有构造函数，所以它必须完全借用父类的构造函数来实例化，匿名内部类完全把创建对象的任务交给了父类去完成。
  二、在匿名内部类里创建新的方法没有太大意义，但它可以通过覆盖父类的方法达到神奇效果，如上例所示。这是多态性的体现。 
      三、因为匿名内部类没有名字，所以无法进行向下的强制类型转换，持有对一个匿名内部类对象引用的变量类型一定是它的直接或间接父类类型。 
  四、注意匿名内部类的声明是在编译时进行的，实例化在运行时进行。这意味着for循环中的一个new语句会创建相同匿名类的几个实例，而不是创建几个不同匿名类的一个实例。

###### 35、内部类可以引用它的包含类（外部类）的成员吗？有没有什么限制？

- 完全可以。如果不是静态内部类，那没有什么限制！ 一个内部类对象可以访问创建它的外部类对象的成员包括私有成员。
  如果你把静态嵌套类当作内部类的一种特例，那在这种情况下不可以访问外部类的普通成员变量，而只能访问外部类中的静态成员。
- [四种内部类](https://blog.csdn.net/singit/article/details/47708797)

###### 36、Java 中的final关键字有哪些用法？

- (1)修饰类：表示该类不能被继承；

  (2)修饰方法：表示方法不能被重写；

  (3)修饰变量：表示变量只能一次赋值以后值不能被修改（常量）

###### 38、数据类型之间的转换：

- 1）低级到高级的自动类型转换；

  2）高级到低级的强制类型转换（会导致溢出或丢失精度）；

  3）基本类型向类类型转换；

  4）基本类型向字符串的转换；

  5）类类型向字符串转换

###### 39、如何实现字符串的反转及替换？

- StringBuilder的reverse和replace方法

- 也可以手动替换
       

  ```java
   String str = new Scanner(System.in).nextLine(); //输入字符串 
   String s2[] = str.split("\\s");//以空格（\s）为分隔符拆分字符串,并保存到数组s2
        for (int i = s2.length-1; i >= 0; i--) {  //反向输出数组
               System.out.print(s2[i]+" "); 
               ｝
  ```

###### 40、怎样将GB2312编码的字符串转换为ISO-8859-1编码的字符串？

```java
try{
		String s = "java学习";
        System.out.println(s);
        String result = new String(s.getBytes("GB2312"),"iso-8859-1");
        System.out.println(s);
    } catch (UnsupportedEncodingException e) {
        // TODO Auto-generated catch block
        e.printStackTrace();
    }
```

###### 41、日期和时间：

```java
        public class DateDemo {
        public static void main(String args[]) {
        // 初始化 Date 对象
        Date date = new Date();
        // 使用 toString() 函数显示日期时间
        System.out.println(date.toString());
        	}
        }
```

###### 42、打印昨天的当前时刻。

```java
package com.test;
import java.util.Calendar;
public class test {
    public static void main(String[] args) {
    Calendar cal = Calendar.getInstance();
    cal.add(Calendar.DATE, -1);
    System.out.println(cal.getTime());
    }
```

###### 43、比较一下Java和JavaSciprt。

- 1）基于对象和面向对象：Java是一种真正的面向对象的语言，即使是开发简单的程序，必须设计对象；JavaScript是种脚本语言，它可以用来制作与网络无关的，与用户交互作用的复杂软件。它是一种基于对象（Object-Based）和事件驱动（Event-Driven）的编程语言。因而它本身提供了非常丰富的内部对象供设计人员使用；
  2）解释和编译：Java 的源代码在执行之前，必须经过编译；JavaScript 是一种解释性编程语言，其源代码不需经过编译，由浏览器解释执行；
  3）强类型变量和类型弱变量：Java采用强类型变量检查，即所有变量在编译之前必须作声明；JavaScript中变量声明，采用其弱类型。即变量在使用前不需作声明，而是解释器在运行时检查其数据类型；

  4）代码格式不一样。

  44、什么时候用断言（assert）？

- debug，了解学习一个新项目、技术z

###### 45、Error和Exception有什么区别？

- Exception 是程序正常运行中，可以预料的意外情况，可能并且应该被捕获，进行相应处理。

  Error 是指在正常情况下，不大可能出现的情况，绝大部分的 Error 都会导致程序（比如 JVM 自身）处于非正常的、不可恢复状态。既然是非正常情况，所以不便于也不需要捕获，常见的比如 OutOfMemoryError 之类，都是 Error 的子类

###### 46、try{}里有一个return语句，那么紧跟在这个try后的finally{}里的代码会不会被执行，什么时候被执行，在return前还是后?

- 会，在return前，有争议

###### 47、Java语言如何进行异常处理，关键字：throws、throw、try、catch、finally分别如何使用？

- 一般情况下是用try来执行一段程序，如果系统会抛出（throw）一个异常对象，可以通过它的类型来捕获（catch）它，或通过总是执行代码块（finally）来处理；try用来指定一块预防所有异常的程序；

  catch子句紧跟在try块后面，用来指定你想要捕获的异常的类型；

  throw语句用来明确地抛出一个异常；

  throws用来声明一个方法可能抛出的各种异常（当然声明异常时允许无病呻吟）；

  finally为确保一段代码不管发生什么异常状况都要被执行；

###### 48、运行时异常与受检异常有何异同？

###### 49、列出一些你常见的运行时异常？

- ArithmeticException(算术异常)
- ClassCastException (类转换异常)
- IllegalArgumentException (非法参数异常)
- IndexOutOfBoundsException (下标越界异常)
- NullPointerException (空指针异常)
- SecurityException (安全异常)

###### 50、阐述final、finally、finalize的区别。

- final：修饰符（关键字）有三种用法：如果一个类被声明为final，意味着它不能再派生出新的子类，即不能被继承，因此它和abstract是反义词。将变量声明为final，可以保证它们在使用中不被改变，被声明为final的变量必须在声明时给定初值，而在以后的引用中只能读取不可修改。被声明为final的方法也同样只能使用，不能在子类中被重写。

- finally：通常放在try…catch…的后面构造总是执行代码块，这就意味着程序无论正常执行还是发生异常，这里的代码只要JVM不关闭都能执行，可以将释放外部资源的代码写在finally块中。 

- finalize：Object类中定义的方法，Java中允许使用finalize()方法在垃圾收集器将对象从内存中清除出去之前做必要的清理工作。这个方法是由垃圾收集器在销毁对象时调用的，通过重写finalize()方法可以整理系统资源或者执行其他清理工作（重写finalize()方法jvm进行第二次GC时失效）。

  （深入理解jvm一书中提到finalize不要使用，详见书 [或者博客](https://www.cnblogs.com/smilesmile/p/3849122.html)）

###### 51、类ExampleA继承Exception，类ExampleB继承ExampleA。请问执行此段代码的输出是什么？

```java
try {
	throw new ExampleB("b")
} catch（ExampleA e）{
	System.out.println("ExampleA");
} catch（Exception e）{
    System.out.println("Exception");
 }
```

- 输出ExampleA

###### 52、List、Set、Map是否继承自Collection接口？

Collection 

　　├List 

　　│├LinkedList 

　　│├ArrayList 

　　│└Vector 

　　│　└Stack 

　　└Set 

　　Map 

　　├Hashtable 

　　├HashMap 

　　└WeakHashMap 

###### 53、阐述ArrayList、Vector、LinkedList的存储性能和特性。

- ArrayList 和Vector他们底层都是使用数组方式存储数据，数组元素数大于实际存储的数据以便增加和插入元素，都允许直接按序号索引元素，插入元素要涉及数组元素移动等内存操作，索引数据快而插入数据慢。
- Vector中的方法由于添加了synchronized修饰，线程安全，性能差
- LinkedList使用双向链表实现存储（将内存中零散的内存单元通过附加的引用关联起来，形成一个可以按序号索引的线性结构，链式存储方式与数组的连续存储方式相比，内存的利用率更高，但因为双表头实际占空间更大），按序号索引数据需要进行前向或后向遍历，插入数据时只需要记录本项的前后项即可，插入速度较快。

###### 54、Collection和Collections的区别？

Collection是集合类的上级接口，继承与他有关的接口主要有List和Set

Collections是针对集合类的一个帮助类，他提供一系列静态方法实现对各种集合的搜索、排序、线程安全等操作

###### 55、List、Map、Set三个接口存取元素时，各有什么特点？

- Set不允许有重复元素，

  存元素：add方法有一个boolean的返回值，当集合中没有某个元素，此时add方法可成功加入该元素时，则返回true；当集合含有与某个元素equals相等的元素时，此时add方法无法加入该元素，返回结果为false。

  取元素：没法说取第几个，只能以Iterator接口取得所有的元素，再逐一遍历各个元素

- List表示有先后顺序的集合，
  存元素：多次调用add(Object)方法时，每次加入的对象按先来后到的顺序排序，也可以插队，即调用add(int index,Object)方法，就可以指定当前对象在集合中的存放位置。
  取元素：方法1：Iterator接口取得所有，逐一遍历各个元素
                 方法2：调用get(index i)来明确说明取第几个。使用此接口能够精确的控制每个元素插入的位置。用户能够使用索引（元素在List中的位置，类似于数组下标）来访问List中的元素，这类似于Java的数组。

- Map**是**双列的集合，存放用put方法:put(obj key,obj value)，每次存储时，要存储一对key/value，不能存储重复的key，这个重复的规则也是按equals比较相等。

  取元素：用get(Object key)方法根据key获得相应的value。
  也可以获得所有的key的集合，还可以获得所有的value的集合，
  还可以获得key和value组合成的Map.Entry对象的集合。

- 总结：List以特定次序来持有元素，可有重复元素。Set 无法拥有重复元素,内部排序。Map 保存	  key-value值，value可多值。

###### 56、TreeMap和TreeSet在排序时如何比较元素？Collections工具类中的sort()方法如何比较元素？[博客](https://www.cnblogs.com/bahcelor/p/6717839.html)

- TreeSet要求存放的对象所属的类必须实现Comparable接口，该接口提供了比较元素的compareTo()方法，当插入元素时会回调该方法比较元素的大小。TreeMap要求存放的键值对映射的键必须实现Comparable接口从而根据键对元素进行排序。Collections工具类的sort方法有两种重载的形式，第一种要求传入的待排序容器中存放的对象比较实现Comparable接口以实现元素的比较；第二种不强制性的要求容器中的元素必须可比较，但是要求传入第二个参数，参数是Comparator接口的子类型（需要重写compare方法实现元素的比较），相当于一个临时定义的排序规则，其实就是通过接口注入比较元素大小的算法，也是对回调模式的应用（Java中对函数式编程的支持）。

###### 57、Thread类的sleep()方法和对象的wait()方法都可以让线程暂停执行，它们有什么区别?

- *sleep()*方法（休眠）是线程类（*Thread*）的静态方法，调用此方法会让当前线程暂停执行指定的时间，将执行机会（*CPU*）让给其他线程，但是对象的锁依然保持，因此休眠时间结束后会自动恢复（线程回到就绪状态）
- wait()是Object类的方法，调用对象的wait()方法导致当前线程放弃对象的锁（线程暂停执行），进入对象的等待池（wait pool），只有调用对象的notify()方法（或notifyAll()方法）时才能唤醒等待池中的线程进入等锁池（lockpool），如果线程重新获得对象的锁就可以进入就绪状态

###### 58、线程的sleep()方法和yield()方法有什么区别？

- ① sleep()方法给其他线程运行机会时不考虑线程的优先级，因此会给低优先级的线程以运行的机会；yield()方法只会给相同优先级或更高优先级的线程以运行的机会;

  ② 线程执行sleep()方法后转入阻塞（blocked）状态，而执行yield()方法后转入就绪（ready）状态;

  ③ sleep()方法声明抛出InterruptedException，而yield()方法没有声明任何异常; 

  ④ sleep()方法比yield()方法（跟操作系统CPU调度相关）具有更好的可移植性

###### 59、当一个线程进入一个对象的synchronized方法A之后，其它线程是否可进入此对象的synchronized方法B？

- 不能。其它线程只能访问该对象的非同步方法，同步方法则不能进入。因为非静态方法上的synchronized修饰符要求执行方法时要获得对象的锁，如果已经进入A方法说明对象锁已经被取走，那么试图进入B方法的线程就只能在等锁池（注意不是等待池哦）中等待对象的锁。

###### 60、请说出与线程同步以及线程调度相关的方法。

- -wait()：使一个线程处于等待（阻塞）状态，并且释放所持有的对象的锁；

  -sleep()：使一个正在运行的线程处于睡眠状态，是一个静态方法，调用此方法要处理InterruptedException异常；

  -notify()：唤醒一个处于等待状态的线程，当然在调用此方法的时候，并不能确切的唤醒某一个等待状态的线程，而是由JVM确定唤醒哪个线程，而且与优先级无关；

  -notityAll()：唤醒所有处于等待状态的线程，该方法并不是将对象的锁给所有线程，而是让它们竞争，只有获得锁的线程才能进入就绪状态

###### 61、编写多线程程序有几种实现方式？

- 一种是继承Thread类；另一种是实现Runnable接口。

  两种方式都要通过重写run()方法来定义线程的行为，推荐使用后者，因为Java中的继承是单继承，一个类有一个父类，如果继承了Thread类就无法再继承其他类了，显然使用Runnable接口更为灵活

  补充：Java 5以后创建线程还有第三种方式：实现Callable接口，该接口中的call方法可以在线程执行结束时产生一个返回值

###### 62、synchronized关键字的用法？

- 同步方法，代码块

  自由发挥部分（链接可能讲的不够清楚，详细请自行搜索相关内容）

- volatile关键字：[禁止指令重排和保持变量可见性](https://www.cnblogs.com/dolphin0520/p/3920373.html)

- 讲讲锁的分类和优化：[锁分类](http://treenpool.com/html/index.html?branchId=488)      [锁的优化](https://www.cnblogs.com/-new/p/7427036.html)

- 讲讲数据库锁：[数据库锁总结](https://www.cnblogs.com/ismallboy/p/5574006.html)

###### 63、举例说明同步和异步。

- 同步:发送一个请求,等待返回,然后再发送下一个请求
  异步:发送一个请求,不等待返回,随时可以再发送下一个请求

  自己举例子

###### 64、启动一个线程是调用run()还是start()方法？

- start(),run()方法只是调用方法，不启动线程

###### 65、什么是线程池（thread pool）？66、线程的基本状态以及状态之间的关系？

- [线程池详解](https://www.cnblogs.com/kuoAT/p/6714762.html)

###### 67、简述synchronized 和java.util.concurrent.locks.Lock的异同？

- 主要相同点：Lock能完成synchronized所实现的所有功能

  主要不同点：Lock有比synchronized更精确的线程语义和更好的性能。synchronized会自动释放锁，而Lock一定要求程序员手工释放，并且必须在finally从句中释放。Lock还有更强大的功能，例如，它的tryLock方法可以非阻塞方式去拿锁。

###### 68、Java中如何实现序列化，有什么意义？

- 序列化就是一种用来处理对象流的机制，所谓对象流也就是将对象的内容进行流化。可以对流化后的对象进行读写操作，也可将流化后的对象传输于网络之间。序列化是为了解决对象流读写操作时可能引发的问题（如果不进行序列化可能会存在数据乱序的问题）。
  要实现序列化，需要让一个类实现Serializable接口，该接口是一个标识性接口，标注该类对象是可被序列化的，然后使用一个输出流来构造一个对象输出流并通过writeObject(Object)方法就可以将实现对象写出（即保存其状态）；如果需要反序列化则可以用一个输入流建立对象输入流，然后通过readObject方法从流中读取对象。序列化除了能够实现对象的持久化之外，还能够用于对象的深度克隆

###### 69、Java中有几种类型的流？

- Java中的流分为两种，一种是字节流，另一种是字符流，分别由四个抽象类来表示（每种流包括输入和输出两种所以一共四个）:InputStream，OutputStream，Reader，Writer。
- 字节流就是普通的二进制流，读出来的是bit，字符流就是在字节流的基础按照字符编码处理，处理的是char

###### 70、写一个方法，输入一个文件名和一个字符串，统计这个字符串在这个文件中出现的次数。

```Java
/**
- 写入一个方法，输入一个文件名和一个字符串，统计这个字符串在这个文件中出现的次数。
   @param fileName 文件名
  - @param str 查找的字符串
     @return
    - @throws Exception
  **/
      //方法一
      public static int funCount1(String fileName,String str) throws Exception {
      int count = 0;
      BufferedReader bf = new BufferedReader(new InputStreamReader(new FileInputStream(fileName)));
      String line ;
      StringBuilder sb = new StringBuilder();
      while((line = bf.readLine() )!= null) {
          sb = sb.append(line);
      }
      int a = 0;
      while((a = sb.indexOf(str)) != -1) {
          sb = sb.delete(a, a + str.length());
          count++;
      }
      return count;
          }
	//方法二：正则表达式
	public static int funCount2(String fileName,String str) throws Exception {
    int count =0 ;
    BufferedReader bf = new BufferedReader(new InputStreamReader(new 			 FileInputStream(fileName)));
    String line ;
    StringBuilder sb = new StringBuilder();
    while((line = bf.readLine() )!= null) {
        sb = sb.append(line);
    }
    String pattern = ".*" + str + ".*";
    while(Pattern.matches(pattern, sb.toString())) {
        count ++;
        int a = sb.indexOf(str);
        sb.delete(a, a + str.length());
    }
    return count;
}
```

###### 71、如何用Java代码列出一个目录下所有的文件？

```java
File file=new File("H:\\");
        for(File temp:file.listFiles()){
            /**Java5的新特性之一就是增强的for循环。上面的for循环的意思是：定义一个File的变量temp，变量child会自动递增遍历File类型的数组listFiles java我们不再需要写得像原来那么复杂了，数组、迭代器都可以这样使用**/
            //列出目录
            if(temp.isDirectory()){
                System.out.println("目录"+temp.toString());
            }
           /* 
           //列出文件
            if(temp.isFile()){
                System.out.println("文件"+temp.toString());
            }
           */
           else{
                 System.out.println("文件"+temp.toString());
            }
      	}
```

###### 72、用Java的套接字编程实现一个多线程的回显（echo）服务器。

###### 73、XML文档定义有几种形式？它们之间有何本质区别？解析XML文档有哪几种方式？ 74、你在项目中哪些地方用到了XML？



###### 75、阐述JDBC操作数据库的步骤。

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;
public class JDBCTest {
	/**
	 * 使用JDBC连接并操作mysql数据库
	 */
	public static void main(String[] args) {
		// 数据库驱动类名的字符串
		String driver = "com.mysql.jdbc.Driver";
		// 数据库连接串
		String url = "jdbc:mysql://127.0.0.1:3306/jdbctest";
		// 用户名
		String username = "root";
		// 密码
		String password = "mysqladmin";
		Connection conn = null;
		Statement stmt = null;
		ResultSet rs = null;
		try {
			// 1、加载数据库驱动（ 成功加载后，会将Driver类的实例注册到DriverManager类中）
			Class.forName(driver );
			// 2、获取数据库连接
			conn = DriverManager.getConnection(url, username, password);
			// 3、获取数据库操作对象
			stmt = conn.createStatement();
			// 4、定义操作的SQL语句
			String sql = "select * from user where id = 100";
			// 5、执行数据库操作
			rs = stmt.executeQuery(sql);
			// 6、获取并操作结果集
			while (rs.next()) {
				System.out.println(rs.getInt("id"));
				System.out.println(rs.getString("name"));
			}
		} catch (Exception e) {
			e.printStackTrace();
		} finally {
			// 7、关闭对象，回收数据库资源
			if (rs != null) { //关闭结果集对象
				try {
					rs.close();
				} catch (SQLException e) {
					e.printStackTrace();
				}
			}
			if (stmt != null) { // 关闭数据库操作对象
				try {
					stmt.close();
				} catch (SQLException e) {
					e.printStackTrace();
				}
			}
			if (conn != null) { // 关闭数据库连接对象
				try {
					if (!conn.isClosed()) {
						conn.close();
					}
				} catch (SQLException e) {
					e.printStackTrace();
				}
			}
		}
	}
}
```

###### 76、Statement和PreparedStatement有什么区别？哪个性能更好？

- 与Statement相比，①PreparedStatement接口代表预编译的语句，它主要的优势在于可以减少SQL的编译错误并增加SQL的安全性（减少SQL注射攻击的可能性）；

  ②PreparedStatement中的SQL语句是可以带参数的，避免了用字符串连接拼接SQL语句的麻烦和不安全；

  ③当批量处理SQL或频繁执行相同的查询时，PreparedStatement有明显的性能上的优势，由于数据库可以将编译优化后的SQL语句缓存起来，下次执行相同结构的语句时就会很快（不用再次编译和生成执行计划）。

###### 77、使用JDBC操作数据库时，如何提升读取数据的性能？如何提升更新数据的性能？

- 要提升读取数据的性能，可以指定通过结果集（ResultSet）对象的setFetchSize()方法指定每次抓取的记录数（典型的空间换时间策略）；要提升更新数据的性能可以使用PreparedStatement语句构建批处理，将若干SQL语句置于一个批处理中执行。

###### 78、在进行数据库编程时，连接池有什么作用？

- 由于创建连接和释放连接都有很大的开销（尤其是数据库服务器不在本地时，每次建立连接都需要进行TCP的三次握手，释放连接需要进行TCP四次握手，造成的开销是不可忽视的）。
- 为了提升系统访问数据库的性能，可以事先创建若干连接置于连接池中，需要时直接从连接池获取，使用结束时归还连接池而不必关闭连接，从而避免频繁创建和释放连接所造成的开销，这是典型的用空间换取时间的策略（浪费了空间存储连接，但节省了创建和释放连接的时间）。
  - Druid据说是目前最好的数据库连接池
  - [DRUID连接池的实用 配置详解](https://www.cnblogs.com/wuyun-blog/p/5679073.html)         [Druid连接池介绍](https://www.cnblogs.com/wuyun-blog/p/5679073.html)

###### 79、什么是DAO模式？

- 1.Data Access Object（数据存取对象）

  2.位于业务逻辑和持久化数据之间

  3.实现对持久化数据的访问

   **DAO模式的作用**

  1隔离业务逻辑代码和数据访问代码

  2.隔离不同数据库的实现

  业务逻辑层，数据访问层（Oracle，SQLServer，MySQL）

  **DAO模式的组成部分**

  DAO接口

  DAO实现类

  实体类

  数据库连接和关闭工具类

###### 80、事务的ACID是指什么？

- 1)原子性(Atomic)：事务中各项操作，要么全做要么全不做，任何一项操作的失败都会导致整个事务的失败；

  2)一致性(Consistent)：事务结束后系统状态是一致的；

  3)隔离性(Isolated)：并发执行的事务彼此无法看到对方的中间状态；

  4)持久性(Durable)：事务完成后所做的改动都会被持久化，即使发生灾难性的失败。通过日志和同步备份可以在故障发生后重建数据。

  [理解数据库的事务，ACID，CAP和一致性](https://www.jianshu.com/p/2c30d1fe5c4e)

###### 81、JDBC中如何进行事务处理？

- `try{`
      `con.setAutoCommit(false);//开启事务`
      `......`
      `con.commit();//try的最后提交事务      
  } catch（） {`
      `con.rollback();//回滚事务`
  `}`

[JDBC处理事务](https://www.cnblogs.com/gdwkong/p/7633016.html)

###### 82、JDBC能否处理Blob和Clob？

- 二进制大对象（`Binary Large Object`） 大字符对象（`Character Large Object`）
- [JDBC的PreparedStatement和ResultSet都提供了相应的方法来支持Blob和Clob操作。](https://yq.aliyun.com/articles/635009)

###### 83、简述正则表达式及其用途。

- 在编写处理字符串的程序时，经常会有查找符合某些复杂规则的字符串的需要。正则表达式就是用于描述这些规则的工具。换句话说，正则表达式就是记录文本规则的代码。

###### 84、Java中是如何支持正则表达式操作的？

- `Java中的String类提供了支持正则表达式操作的方法，包括：matches()、replaceAll()、replaceFirst()、split()。此外，Java中可以用Pattern类表示正则表达式对象，它提供了丰富的API进行各种正则表达式操作`

  ```java
  public static void main(String[] args) {
      String str = "北京市(朝阳区)(西城区)(海淀区)";
      Pattern p = Pattern.compile(".*?(?=\\()");
      Matcher m = p.matcher(str);
      if(m.find()) {
          System.out.println(m.group());
      }
  }
  
  ```

###### 85、获得一个类的类对象有哪些方式？86、如何通过反射创建对象？

- `方法1：通过类对象调用newInstance()方法，例如：String.class.newInstance()` 
- `方法2：通过类对象的getConstructor()或getDeclaredConstructor()方法获得构造器（Constructor）对象并调用其newInstance()方法创建对象，例如：String.class.getConstructor(String.class).newInstance("Hello");`  
- https://uploadfiles.nowcoder.com/images/20190202/242025553_1549100782844_C375DEF54499BAA37941F93164F9C467

###### 87、如何通过反射获取和设置对象私有字段的值？

- [可以通过类对象的getDeclaredField()方法字段（Field）对象，然后再通过字段对象的setAccessible(true)将其设置为可以访问，接下来就可以通过get/set方法来获取/设置字段的值](https://blog.csdn.net/oMrLai1/article/details/78086419)

###### 88、如何通过反射调用对象的方法？

1. 获取当前类的Class对象。              （通过forName（）动态加载类）
2. 实例化这个Class对象。                （通过newInstance：  Object obj=student.newInstance() )
3. 获取当前类的某个（些）方法
4. 用   方法对象名.invoke ,通过Class对象的实例，调用带相应参数的，当前类的方法

```java
 public static void main(String[] args) throws Exception {
         Class student=Class.forName("zj4_6.Student");//动态加载类，获取当前类的Class对象
          //获取Student类名称为printinfo地方法
         Method methods1=student.getMethod("printInfo");
             //调用frintInfo方法
         methods1.invoke(student.newInstance()); //通过实例化的对象，调用无参数的方法
             //获取类中名称为printInfo地方法，String，class是参数类型
         Method methods2=student.getMethod("printAddress", String.class);//注意参数不是String
         //调用printAddress方法，其中HK是方法传入的参数值
         methods2.invoke(student.newInstance(),"HK");//通过对象，调用有参数的方法
 	} catch (ClassNotFoundException e) { e.printStackTrace(); } 
 } 
}

```

###### 89、简述一下面向对象的"六原则一法则"。

- [下面向对象的"六原则一法则"](https://yq.aliyun.com/articles/635009)

- 单一职责原则：一个类只做它该做的事情。

- 开闭原则：软件实体应当对扩展开放，对修改关闭。

  开闭两个要点：①抽象是关键，一个系统中如果没有抽象类或接口系统就没有扩展点；②封装可变性，将系统中的各种可变因素封装到一个继承结构中，如果多个可变因素混杂在一起，系统将变得复杂而换乱，如果不清楚如何封装可变性，可以参考《设计模式精解》一书中对桥梁模式的讲解的章节。） 

- 依赖倒转原则：面向接口编程。（该原则说得直白和具体一些就是声明方法的参数类型、方法的返回类型、变量的引用类型时，尽可能使用抽象类型而不用具体类型，因为抽象类型可以被它的任何一个子类型所替代，请参考下面的里氏替换原则。） 
  里氏替换原则：任何时候都可以用子类型替换掉父类型。 

- 接口隔离原则：接口要小而专，绝不能大而全。

- 合成聚合复用原则：优先使用聚合或合成关系复用代码

- 迪米特法则：迪米特法则又叫最少知识原则，一个对象应当对其他对象有尽可能少的了解。

###### 90、简述一下你了解的设计模式。91、用Java写一个单例类。

- https://blog.csdn.net/xsl1990/article/details/16359289

###### 92、什么是UML？93、UML中有哪些常用的图？（ 略）

94、用Java写一个冒泡排序。 95、用Java写一个折半查找。

- ###### [八大基础排序](https://github.com/ZhongFuCheng3y/3y/blob/master/src/sort.md)

###### 97、Servlet接口中有哪些方法？

- Servlet接口定义了5个方法，其中前三个方法与Servlet生命周期相关： 
- void init(ServletConfig config) throws ServletException 
- void service(ServletRequest req, ServletResponse resp) throws ServletException, java.io.IOException 
- void destory() 
- java.lang.String getServletInfo() 
- ServletConfig getServletConfig()
- Web容器加载Servlet并将其实例化后，Servlet生命周期开始，容器运行其init()方法进行Servlet的初始化；请求到达时调用Servlet的service()方法，service()方法会根据需要调用与请求对应的doGet或doPost等方法；当服务器关闭或项目被卸载时服务器会将Servlet实例销毁，此时会调用Servlet的destroy()方法。

###### 99、JSP有哪些内置对象？作用分别是什么？

- `九大内置对象Page，pageContext，request，response，session，application，out，config，exception`

  `Page指的是JSP被翻译成Servlet的对象的引用.`

  `pageContext对象可以用来获得其他8个内置对象,还可以作为JSP的域范围对象使用.pageContext中存的值是当前的页面的作用范围》`

  `request代表的是请求对象,可以用于获得客户机的信息,也可以作为域对象来使用，使用request保存的数据在一次请求范围内有效。`

  `Session代表的是一次会话，可以用于保存用户的私有的信息,也可以作为域对象使用，使用session保存的数据在一次会话范围有效`

  `Application：代表整个应用范围,使用这个对象保存的数据在整个web应用中都有效。`

  `Response是响应对象,代表的是从服务器向浏览器响应数据.`

  `Out:JSPWriter是用于向页面输出内容的对象`

  `Config：指的是ServletConfig用于JSP翻译成Servlet后 获得Servlet的配置的对象.`

  `Exception:在页面中设置isErrorPage=”true”，即可使用，是Throwable的引用.用来获得页面的错误信息。`

###### 100、get和post请求的区别？

- `GET在浏览器回退时是无害的，而POST会再次提交请求。`
  `GET产生的URL地址可以被Bookmark，而POST不可以。`
  `GET请求会被浏览器主动cache，而POST不会，除非手动设置。`
  `GET请求只能进行url编码，而POST支持多种编码方式。`
  `GET请求参数会被完整保留在浏览器历史记录里，而POST中的参数不会被保留。`
  `GT请求在URL中传送的参数是有长度限制的，而POST么有。` 
  `对参数的数据类型，GET只接受ASCII字符，而POST没有限制。`
  `GET比POST更不安全，因为参数直接暴露在URL上，所以不能用来传递敏感信息。` 
  `GET参数通过URL传递，POST放在Request body中。`
- **重大区别**： **GET产生一个TCP数据包；POST产生两个TCP数据包。**
  ``对于GET方式的请求，浏览器会把http header和data一并发送出去，服务器响应200（返回数据）`
  `而对于POST，浏览器先发送header，服务器响应100 continue，浏览器再发送data，服务器响应200 ok（返回数据）。`
   `GET与POST都有自己的语义，不能随便混用。`
   `据研究，在网络环境好的情况下，发一次包的时间和发两次包的时间差别基本可以无视。而在网络环境差的情况下，两次包的TCP在验证数据包完整性上，有非常大的优点。`
   `并不是所有浏览器都会在POST中发送两次包，Firefox就只发送一次。``

###### 101、常用的Web服务器有哪些？

- `①Apache`

  `Apache是世界使用排名的Web服务器软件。它几乎可以运行在所有的计算机平台上。由于Apache是开源免费的，因此有很多人参与到新功能的开发设计，不断对其进行完善。  Apache的特点是简单、速度快、性能稳定，并可做代理服务器来使用。`

  `②IIS`

  `IIS(Internet信息服务)英文Internet Informatio  Server的缩写。它是微软公司主推的服务器。IIS的特点具有：安全性，强大，灵活。`

  `③Nginx`

  `Nginx不仅是一个小巧且高效的HTTP服务器，也可以做一个高效的负载均衡反向代理，通过它接受用户的请求并分发到多个Mongrel进程可以极大提高Rails应用的并发能力。`

  `④Tomcat`

  `Tomcat是Apache 软件基金会(Apache Software Foundation)的Jakarta  项目中的一个核心项目，由Apache、Sun 和其他一些公司及个人共同开发而成。Tomcat 技术先进、性能稳定，而且免费，因而深受Java  爱好者的喜爱并得到了部分软件开发商的认可，成为目前比较流行的Web 应用服务器。`

  `⑤Lighttpd`

  `Lighttpd是由德国人 Jan Kneschke 领导开发的，基于BSD许可的开源WEB服务器软件，其根本的目的是提供一个专门针对高性能网站，安全、快速、兼容性好并且灵活的web  server环境。具有非常低的内存开销，CPU占用率低，效能好，以及丰富的模块等特点。支持FastCGI, CGI, Auth, 输出压缩(output  compress), URL重写, Alias等重要功能。`

  `⑥Zeus`

  `Zeus是一个运行于Unix下的非常的Web 服务器，据说性能超过Apache，是效率的Web 服务器之一。`

###### 102、JSP和Servlet是什么关系？

- Servlet是一个特殊的Java程序，它运行于服务器的JVM中，能够依靠服务器的支持向浏览器提供显示内容。  

  JSP本质上是Servlet的一种简易形式， JSP会被服务器处理成一个类似于Servlet的Java程序，可以简化页面内容的生成。

  Servlet和JSP最主要的不同点在于，Servlet 的应用逻辑是在Java 文件中，并且完全从表示层中的HTML分离开来。而JSP的情况是Java和HTML可以组合成一个扩展名为.jsp 的文件（有人说，Servlet就是在Java中写HTML，而JSP就是在HTML中写Java代码，当然，这个说法还是很片面的）。

  JSP侧重于视图，Servlet更侧重于控制逻辑，在MVC[**架构**](http://lib.csdn.net/base/16)模式中，JSP适合充当视图（view）而Servlet适合充当控制器（controller）。

###### 103、讲解JSP中的四种作用域。

- JSP中的四种作用域包括page、request、session和application，具体来说：
  - page代表与一个页面相关的对象和属性。
  - request代表与Web客户机发出的一个请求相关的对象和属性。一个请求可能跨越多个页面，涉及多个Web组件；需要在页面显示的临时数据可以置于此作用域。
  - session代表与某个用户与服务器建立的一次会话相关的对象和属性。跟某个用户相关的数据应该放在用户自己的session中。
  - application代表与整个Web应用程序相关的对象和属性，它实质上是跨越整个Web应用程序，包括多个页面、请求和会话的一个全局作用域。

###### 104、如何实现JSP或Servlet的单线程模式？

- JSP页面，可以通过page指令进行设置。	

```
<%@page isThreadSafe=”false”%>

```

​	对于Servlet，可以让自定义的`Servlet`实现`SingleThreadModel`标识接口。

​	说明：如果将JSP或Servlet设置成单线程工作模式，会导致每个请求创建一个Servlet实例，这种实	践将导致严重的性能问题（服务器的内存压力很大，还会导致频繁的垃圾回收），所以通常情况下	并不会这么做。Servlet是单例的，可以提高性能

###### 105、实现会话跟踪的技术有哪些？

- `简单回答就可以从下面来说：`
  `Cookie，session和application， Cookie是http对象，客户端与服务端都可以操纵`
  - `cookie是在客户端保持状态，session是在服务器端保持状态，由于cookie是保存在客户端本地的，所以数据很容易被窃取，当访问量很多时，使用session则会降低服务器的性能，`
  - `application的作用域是整个工程里只有一个，可以在不同浏览器之间共享数据，所有人都可以共享，因此application也是不安全的。`
- `①URL 重写：在URL中添加用户会话的信息作为请求的参数，或者将唯一的会话ID添加到URL结尾以标识一个会话。` 
  `②设置表单隐藏域：将和会话跟踪相关的字段添加到隐式表单域中，这些信息不会在浏览器中显示但是提交表单时会提交给服务器。` 
  `这两种方式很难处理跨越多个页面的信息传递，因为如果每次都要修改URL或在页面中添加隐式表单域来存储用户会话相关信息，事情将变得非常麻烦。` 
  `③cookie：cookie有两种，一种是基于窗口的，浏览器窗口关闭后，cookie就没有了；另一种是将信息存储在一个临时文件中，并设置存在的时 间。当用户通过浏览器和服务器建立一次会话后，会话ID就会随响应信息返回存储在基于窗口的cookie中，那就意味着只要浏览器没有关闭，会话没有超 时，下一次请求时这个会话ID又会提交给服务器让服务器识别用户身份。会话中可以为用户保存信息。会话对象是在服务器内存中的，而基于窗口的cookie 是在客户端内存中的。如果浏览器禁用了cookie，那么就需要通过下面两种方式进行会话跟踪。当然，在使用cookie时要注意几点：首先不要在 cookie中存放敏感信息；其次cookie存储的数据量有限（4k），不能将过多的内容存储cookie中；再者浏览器通常只允许一个站点最多存放 20个cookie。当然，和用户会话相关的其他信息（除了会话ID）也可以存在cookie方便进行会话跟踪。` 
  `④HttpSession：在所有会话跟踪技术中，HttpSession对象是最强大也是功能最多的。当一个用户第一次访问某个网站时会自动创建 HttpSession，每个用户可以访问他自己的HttpSession。可以通过HttpServletRequest对象的getSession方 法获得HttpSession，通过HttpSession的setAttribute方法可以将一个值放在HttpSession中，通过调用 HttpSession对象的getAttribute方法，同时传入属性名就可以获取保存在HttpSession中的对象。与上面三种方式不同的 是，HttpSession放在服务器的内存中，因此不要将过大的对象放在里面，即使目前的Servlet容器可以在内存将满时将HttpSession 中的对象移到其他存储设备中，但是这样势必影响性能。添加到HttpSession中的值可以是任意Java对象，这个对象最好实现了 Serializable接口，这样Servlet容器在必要的时候可以将其序列化到文件中，否则在序列化时就会出现异常。`

###### 106、过滤器有哪些作用和用法？

- `对于一个web应用程序来说，过滤器是处于web容器内的一个组件，它会过滤特定请求资源请求信息和响应信息。一个请求来到时，web容器会判断是否有过滤器与该信息资源相关联，如果有则交给过滤器处理，然后再交给目标资源，响应的时候则以相反的顺序交给过滤器处理，最后再返回给用户浏览器。`

  `过滤器类需要实现javax.servlet.Filter，该接口的doFilter()方法是业务处理的核心代码区，类似于servlet的service()方法。doFilter()方法的参数列表有一个FilterChain接口的实现对象，它只有一个方法doFilter(),在调用该方法之前的代码会在达到目标资源前执行，之后的代码会在目标资源已经响应后执行`

  [[拦截器和过滤器的区别](https://www.cnblogs.com/panxuejun/p/7715917.html)]

###### 107、监听器有哪些作用和用法？

- `javaWeb开发中的监听器（listener）就是application、session、request三个对象创建、销毁或者往其中添加修改删除属性时自动执行代码的功能组件，如下所示：`
  `①ServletContextListener：对Servlet上下文的创建和销毁进行监听。`
  `②ServletContextAttributeListener：监听Servlet上下文属性的添加、删除和替换。`
  `③HttpSessionListener：对Session的创建和销毁进行监听。`

  `补充：session的销毁有两种情况：1). session超时（可以在web.xml中通过/标签配置超时时间）；2). 通过调用session对象的invalidate()方法使session失效。`

  `④HttpSessionAttributeListener：对Session对象中属性的添加、删除和替换进行监听。`
  `⑤ServletRequestListener：对请求对象的初始化和销毁进行监听。`
  `⑥ServletRequestAttributeListener：对请求对象属性的添加、删除和替换进行监听。`

###### 108、web.xml文件中可以配置哪些内容？

- web.xml用于配置Web应用的相关信息，如：监听器（listener）、过滤器（filter）、Servlet、相关参数、会话超时时间、安全验证方式、错误页面等

###### 109、你的项目中使用过哪些JSTL标签？（略）

###### 110、使用标签库有什么好处？如何自定义JSP标签？（略）

###### 111、说一下表达式语言（EL）的隐式对象及其作用。（略）

###### 112、表达式语言（EL）支持哪些运算符？（略）

###### 113、Java Web开发的Model 1和Model 2分别指的是什么？

- 

  Model 1是以页面为中心的Java Web开发，使用JSP+JavaBean技术将页面显示逻辑和业务逻辑处理分开，JSP实现页面显示，JavaBean对象用来保存数据和实现业务逻辑。

  Model 2是基于MVC（模型-视图-控制器，Model-View-Controller）架构模式的开发模型，实现了模型和视图的彻底分离，利于团队开发和代码复用

###### 114、Servlet 3中的异步处理指的是什么？（略）

###### 115、如何在基于Java的Web项目中实现文件上传和下载？

- 文件上传和下载在web应用中非常普遍，要在jsp环境中实现文件上传功能是非常容易的，因为网上有许多用[Java](http://lib.csdn.net/base/javase)开发的文件上传组件。以commons-fileupload组件为例，为jsp应用添加文件上传功能。common-fileupload组件是apache的一个开源项目之一，可以从http://jakarta.apache.org/commons/fileupload/下载。用该组件可实现一次上传一个或多个文件，并可限制文件大小
- 通过`Sevlet3`的api来实现

###### 116、服务器收到用户提交的表单数据，到底是调用Servlet的doGet()还是doPost()方法？

- `HTML的<form>元素有一个method属性，用来指定提交表单的方式，其值可以是get或post。我们自定义的Servlet一般情况下会重写doGet()或doPost()两个方法之一或全部，如果是GET请求就调用doGet()方法，如果是POST请求就调用doPost()方法，那为什么这样呢？我们自定义的Servlet通常继承自HttpServlet，HttpServlet继承自GenericServlet并重写了其中的service()方法，这个方法是Servlet接口中定义的。HttpServlet重写的service()方法会先获取用户请求的方法，然后根据请求方法调用doGet()、doPost()、doPut()、doDelete()等方法，如果在自定义Servlet中重写了这些方法，那么显然会调用重写过的（自定义的）方法，这显然是对模板方法模式的应用。当然，自定义Servlet中也可以直接重写service()方法，那么不管是哪种方式的请求，都可以通过自己的代码进行处理，这对于不区分请求方法的场景比较合适。`

###### 117、JSP中的静态包含和动态包含有什么区别？略

###### 118、Servlet中如何获取用户提交的查询参数或表单数据？

- `可以通过请求对象（HttpServletRequest）的getParameter()方法通过参数名获得参数值。如果有包含多个值的参数（例如复选框），可以通过请求对象的getParameterValues()方法获得。当然也可以通过请求对象的getParameterMap()获得一个参数名和参数值的映射（Map）。`

###### 119、Servlet中如何获取用户配置的初始化参数以及服务器上下文参数？

- `可以通过重写Servlet接口的init(ServletConfig)方法并通过ServletConfig对象的getInitParameter()方法来获取Servlet的初始化参数。`

  `可以通过ServletConfig对象的getServletContext()方法获取ServletContext对象，并通过该对象的getInitParameter()方法来获取服务器上下文参数。当然，ServletContext对象也可以在处理用户请求的方法（如doGet()方法）中通过请求对象的getServletContext()方法`

###### 121、解释一下网络应用的模式及其特点。略

###### 122、什么是Web Service（Web服务）？123、概念解释：SOAP、WSDL、UDDI。略

- https://blog.csdn.net/u013168253/article/details/79695492

###### 124、Java规范中和Web Service相关的规范有哪些？略

###### 125、介绍一下你了解的Java领域的Web Service框架。略

- https://blog.csdn.net/u014231646/article/details/80840821
