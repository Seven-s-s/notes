   # JVM

## 内存结构

> **线程共享：方法区、堆**
>
> **线程独占：程序技术器、本地方法栈、虚拟机栈**

## GC

### 工作机制

>负责回收所有无任何引用对象的内存空间，回收机制有两种算法：引用计数法和可达性分析法（标记-清除、复制、标记-整理、分代收集算法）

# JAVA

## Java基础

### Java跨平台原理

> Java对于不同系统、不同版本、不同位数的Java虚拟机来屏蔽不同的系统指令集差异而对外提供统一的接口

### JDK、JRE、JVM的关系

> **JDK(java development toolkit)：Java开发工具包**
>
> 是java的核心，包括了java运行环境，一堆java工具（javac、java、jdb）和java基础类库（javaAPI包括rt.jar）
>
> **JRE(java runtime environment)：Java运行环境**
>
> 所有的java程序都要在JRE下才能运行，包括JVM和Java核心类库和支持文件，与JDK相比不包含开发工具（编译器、调试器和其他工具）
>
> **JVM(java virtual mechinal)：Java虚拟机**
>
> JVM是JRE的一部分，他是一个虚拟出来的计算机，JVM的主要工作是解释自己的指令集（即字节码）并映射到本地的CPU指令集或OS的系统调用

### 面向对象的特征

四个：封装、抽象、继承、多态

> **封装：将客观的事物封装成抽象的类，并且将自己类中的属性私有化，只对外提供set和get方法来进行属性的赋值和取值**
>
> **继承：子类继承父类，子类可以使用父类的所有功能，并且在无需改变父类的情况下能对这些功能进行扩展**
>
> **多态：允许相同或不同子类型的对象对同一消息作出不同的响应，如重载和重写**

### 访问修饰符public,private,protected,以及默认时的区别

| 修饰符  | 当前类 | 同包 | 子类 | 其他包 |
| :-----: | :----: | :--: | :--: | :----: |
| public  |   √    |  √   |  √   |   √    |
| protect |   √    |  √   |  √   |   ×    |
| default |   √    |  √   |  ×   |   ×    |
| private |   √    |  ×   |  ×   |   ×    |

### 基本数据类型，包装类型

基本数据类型有八种

> **byte、short、int、long、char、boolean、float、double**

| 数据类型 |    占用字节     |     取值范围     |    默认值    | 包装类型  |
| :------: | :-------------: | :--------------: | :----------: | :-------: |
| boolean  | 只有true和false |   true、false    |    false     |  Boolean  |
|   byte   |     1(8位）     |     -128~127     |      0       |   Byte    |
|  short   |     2(16位)     |   -32768~32767   |      0       |   Short   |
|   int    |     4(32位)     |   -2^31~2^31-1   |      0       |  Integer  |
|   long   |        8        |   -2^63~2^63-1   |     0.0l     |   Long    |
|  float   |        4        |  3.4E-45~1.4E38  |     0.0f     |   Float   |
|  double  |        8        | 4.9E-324~1.8E308 |      0       |  Double   |
|   char   |        2        |     0~65535      | \u0000(空格) | Character |

包装类型：每一个基本数据类型都一一对于一个包装类型

java是一个面向对象的语言，而基本数据类型不具备面向对象的特征

### 拆箱和装箱

> **装箱：把基本数据类型转化为对应的包装类型**
>
> **Integer i = 1;**
>
> **自动装箱实际上会在编译时会调用Integer.valueOf()方法来装箱**
>
> **拆箱：把包装类型转换为基本数据类型**
>
> **int j = i;**
>
> **实际上在编译时会调用intValue()方法来拆箱**

### ==和equals的区别

> **==用来判断两个变量之间的值是否相等，变量可分为基本数据变量和引用类型，如果比较的是基本数据类型，那么就是比较他们的值是否相等，如果比较的是引用类型，那么比较的是他们引用的内存地址**
>
> **equals不能用于作用与基本数据类型的变量，他继承至Object类，比较的是是否是同一对象，如果没有对equals方法进行重写，则比较的是引用类型变量所指向对象的地址**

### 重写equals为何要重写hashcode

> 1. **使用hashcode方法提前校验，可以避免每一次对比都调用equals方法，提高效率（因为hashcode不等，equals一定不等）**
> 2. **为了保证是同一对象，如果重写了equals方法，而没有重写hashcode方法，会出现equals相等，hashcode不相等的情况，重写hashcode方法就是为了避免这种情况发生**

### String，StringBuilder，StringBuffer的区别

> **String是字符串常量，其值不能改变，底层是使用了一个不可变的数组对象(final char[])**
>
> **StringBulider是线程不安全的，其值可以改变，速度快，底层是使用了一个可变的数组对象（没有用final修饰）**
>
> **StringBuffer是线程安全的，其值可以改变，速度慢。**

### 拼接字符串

> ```java
> String s = "a" + "b";
> ```
>
> **开辟了三个内存空间**

> ```java
> StringBuilder sb = new StringBuilder();
> sb.append("a").append("b");
> ```
>
> **只开辟了一个内存空间**
>
> **拼接字符串不能使用String，要是有StringBuilder或StringBuffer**

## 集合

### Map

可分为HashMap和TreeMap

>HashMap：hash表无序，不能放重复键，允许放空键空值
>
>TreeMap：数据结构是树，有序

### Collection

分为List和Set

> List：有序的，可以重复的
>
> Set：无序的，不可重复的，需要重写equals和hashcode方法

List接口：ArrayList、LinkedList

Set接口：HashSet、TreeSet

> HashSet：底层数据结构是哈希链表，保证元素的唯一，不保证元素顺序不变，需要使用equals方法和hashcode方法
>
> TreeSet：底层数据结构是二叉树，保证元素唯一，并对元素按自然排序进行排序，可以实现Compareable接口重写compareTo()实现自定义排序

### ArrayList、LinkedList和vector的区别

ArrayLsit和LinkedList都是实现了List接口

ArrayList是基于动态数组的数据结构，LinkedList是基于链表的

> **ArrayList：查询快，增加删除慢，由于数组在内存中是一块连续的内存，查询根据索引就能找到，所以快，而添加和删除需要移动内存，所以慢。**
>
> **LinkedList：增加删除快，查询慢，由于链表在内存中不是连续的，查找时，需要从头部开始，挨着找，所以查询慢，而添加删除时，只需要改变引用指向即可，所以增加删除快**
>
> **ArrayList：默认容量10，每次扩容时为之前的1.5倍，是线程不安全的，效率高**
>
> **vector：默认容量10，每次扩容是为之前的2倍，是线程安全的，效率低**

### HashMap和HashTable的区别

相同点

> **HashMap和HashTable都是通过键值对来存储值的**

不同点

>**HashMap：可以把null作为键或值，是线程安全的，效率较高，默认容量16，每次扩容时为原来的两倍**
>
>**HashTable：不能把null作为键或值，是线程不安全的，效率较低，默认容量为11，每次 扩容为原来的两倍加一**

创建时，如果给定容量初始值，那么HashTable就是给定的初始值，而HashMap会自动扩充为2的幂次方大小

### HashMap与concurrentHashMap的区别

> **concurrentHashMap对整个Map进行了分段分割，分为了N个Segment，默认提升16倍，相对于HashTable的synchronized锁粒度更精细了一些，并发性能更好，而HashMap没有锁机制，不是线程安全的，JDk1.8之后concurrentHashMap摒弃了Segment的数据结构，直接采用数组+链表+红黑树的数据结构实现，并发控制使用synchronized和CAS(compare and swap)来操作**

## IO

### BIO、NIO、AIO的区别

> **BIO：同步阻塞**
>
> **用户发起一个IO操作请求后，必须等待IO操作的完成，只有当真正完成了IO操作之后，用户进程才能运行**
>
> **NIO：同步非阻塞**
>
> **用户发起一个IO操作请求后，后边可以做其他事情，但是用户进程需要时不时的询问IO操作是否就绪，从而引起不必要的CPU资源浪费**
>
> **AIO：异步非阻塞**
>
> **用户发起一个IO操作请求后立即返回，等IO操作真正完成之后，应用程序会得到IO操作完成的通知。**

### 实现拷贝文件的工具类使用字符流还是字节流

> **我们拷贝的文件不确定是只包含字符流，又可能是字节流（图片、声音、图像等），为保证通用性，要是有字节流**

## 多线程

### 实现线程的方式

> 1. **继承Thread类**
> 2. **实现Runnable接口**
> 3. **实现Callable接口**

继承拓展性不强，Java总是单继承，如果一个类继承了Thread类就不能继承其他类了

### 线程的启动方式

> **启动线程调用start方法，而启动以后执行的是run方法**

### 区分线程

> **调用setName方法，设置一个线程名称，只是一种规范，在线程创建完成后，都需要设置名称**

### sleep和wait的区别

> 1. **sleep定义在Thread类上，不会释放锁，使用在任何地方**
> 2. **wait定义在object类上，会释放锁，必须在同步方法或同步代码块中执行**
> 3. **超时或调用interrupt方法唤醒sleep线程**
> 4. **notify随机唤醒一个wait线程，notifyall唤醒所有wait线程**

### synchronized和lock的区别

> **synchronized时一个关键字，lock是一个接口**
>
> **synchronized可以给方法和同步代码块加锁，lock只能给同步代码块加锁**
>
> **synchronized无需手动获取和释放锁，发生异常时会自动解锁，不会出现死锁，lock需要自己手动加锁和释放锁，如lock()、unlock()，如果忘记使用unlock()，则会出现死锁，所以一般在finally里面加上unlock()**

### synchronized和volatile的区别

> 1. **作用位置不同**
>
>    **synchronized修饰方法、代码块**
>
>    **volatile修饰变量**
>
> 2. **作用不同**
>
>    **synchronized可以保证原子性和可见性，可能会造成线程阻塞**
>
>    **volatile仅能保证可见性，无法保证原子性，不会造成线程阻塞**

### 什么是死锁，如何解决

死锁

> 线程1独占资源a并且尝试获取独占资源b，而线程2独占资源b并尝试获取独占资源a，两个线程在等待另一个资源的同时不释放资源，就形成了死锁

形成死锁的四个必要条件

> 1. 互斥条件：一个资源每次只能被一个进程使用
> 2. 请求与保持条件：一个进程因请求资源而阻塞时，对已获得的资源保持不放
> 3. 不剥夺资源：进程以获得的资源，在未完成之前，不能强行剥夺
> 4. 循环等待条件：若干个进程形成一种头尾相接的循环等待资源关系

预防死锁

> 1. **破坏请求和保存条件**
>
>    **一次性的申请所有资源，之后不再申请资源，如果不满足资源条件则得不到资源分配。**
>
>    **只获得初期资源运行，之后将运行完的资源释放，请求新的资源**
>
> 2. **破坏不可抢占条件**
>
>    **当一个进程获取某种不可抢占资源，提出新的资源申请，若不能满足，则释放所有资源，以后需要，再次重新申请**
>
> 3. **破坏循环等待条件**
>
>    **对资源进行排号，按照序号递增的顺序请求资源，若进程获得序号高的资源想要获取序号低的资源，就需要先释放序号高的资源**

### 线程并发库

创建线程池的四种方式

|          方法名           |         作用         |
| :-----------------------: | :------------------: |
|   newFixedThreadPool()    | 创建固定数量的线程池 |
|   newCachedThreadPool()   |   创建缓存的线程池   |
| newSingleThreadExecutor() |     创建单个线程     |
| newScheduledThreadPool()  |   创建定时器线程池   |

### 线程池的作用

> 1. **限定线程的个数，提高线程的可管理性**
> 2. **提高响应速度**
> 3. **降低资源消耗**

## 反射

### 什么是反射

> **程序在运行时可以通过类名获取类的所有信息**

### 反射的实现方式

>1. **Class.forName()**
>2. **类名.class**
>3. **对象.getClass()**

### 反射的优缺点

> **优点：在运行期间绑定对象，提高了灵活性**
>
> **缺点：有性能有影响，他的操作总是慢于直接代码**

### 怎么实现动态代理

JDK动态代理和Cglib代理

> **JDK代理是基于接口实现的**
>
> **Cglib代理是基于继承实现的**

# WEB

## Get和Post的区别

get和post都是http的请求方式，用户通过不同的请求方式来完成对资源的不同操作，get、post、put、delete分别对应着资源的查、改、增、删四个操作，一般来说get用来获取资源，post用于更新资源

> 1. **get请求提交的数据会在地址栏显示出来，post请求不会**
> 2. **由于地址栏长度有限，导致get传输的数据有限，而post不会**
> 3. **安全性，post安全性比get高**

## 对Servlet的理解

> **Servlet是用Java程序编写的服务端程序，而这些Servlet都要实现Servlet接口，其主要功能是用于交互式的浏览和修改数据，生成动态网页**
>
> **HttpServlet重写doget和dopost方法或者重写service方式可以实现对get和post请求的响应**

## Servlet的生命周期

> 加载Servlet的生命周期，调用init()进行初始化，然后调用service()方法来处理客户端的请求，最后调用destroy()终止

## forward与redirect的区别

> 1. forward地址栏不会发生改变，redirect地址栏会发生改变
> 2. forward是服务器上的行为，redirect是客户端的行为
> 3. forward是一次请求完成的，redirect是两次请求完成的
> 4. forward效率较高

## JSP与Servlet的相同点与不同点

> 相同点：JSP是Servlet的扩展，所有的JSP文件最终都会被翻译成一个继承HttpServlet类，也就是说JSP最终也是一个Servlet
>
> 不同点：JSP侧重于视图，Servlet侧重于控制逻辑

## JSP的九大内置对象与四大作用域

九大内置对象

> **Request：客户端的请求**
>
> **Response：网页传回客户端的响应**
>
> **PageContext：网页属性的管理**
>
> **Session：会话**
>
> **Application：servlet正在执行的内容**
>
> **Out：传递回应的输出**
>
> **Config：servlet的架构不见**
>
> **Page：Jsp网页本身**
>
> **Exception：针对错误的网页**

四大作用域

> **page：只在一个页面保留数据**
>
> **request：只在一个请求中保存数据**
>
> **Session：再一次会话中保存数据，仅供单个用户使用**
>
> **Application：在整个服务器中保存数据，全部用户共享**

## Cookie与Session的区别

**cookie和session都是会话跟踪技术**

不同点

> 1. **cookie的数据是存在客户端的，session的数据是存在服务器上的**
> 2. **cookie是不安全的**
> 3. **session会在一定时间内存放在服务器上，当访问增多时，会占用服务器的性能**
> 4. **单个cookie的保存数据不能超过4k,很多浏览器一个站点最多存放20个cookie**

建议

> **将登录信息等重要信息保存在session中，其他信息如需保留，可以放在cookie中，如：购物车**
>
> **购物车最好使用cookie，范式cookie实在客户端禁用的，只是要我们需要使用cookie+数据库的方式实现，当从cookie中不能取出数据时，就从数据库中取**

## MVC的各个部分有哪些技术实现

> **M(Model)：模型 Javabean**
>
> **V(View)：视图 jsp、html**
>
> **C(Control)：控制器：Servlet、Action**
>
> **JSP+Servlet+Javabean是最经典的mvc模式，实际上就是model2的实现方式，将逻辑与视图隔离开**
>
> **model1：jsp+service+dao**
>
> **model2：jsp+servlet+service+dao**

# 数据库

## 数据库的分类

> **非关系数据库：mysql、oracle、sqlserver等**
>
> **关系型数据库：redis、memcache、mongodb、hahdoop等**
>
> **redis：键值对数据库**
>
> **mongodb：文档数据库**

## 数据库三范式

范式就是规范，就是在关系型数据库设计表时要遵循的规范

要想满足第二范式就必须满足第一范式，要想满足第三范式就必须满足第二范式

>**第一范式：要求属性具有原子性，不可再分解**
>
>**第二范式：每一行必须被唯一标识（主键）**
>
>**第三范式：任何字段不能由其他字段派生出来，要求字段没有冗余（外键）**

## 事务四个基本特性

事务是并发控制的单位，是用户定义的一个操作序列，这些操作要么都做要么都不做，是一个不可分割的工作单位

> 1. **原子性（A）**
>
>    **一个事务要么完整执行，要么就不执行**
>
> 2. **一致性（C）**
>
>    **底层数据存储的完整性**
>
> 3. **隔离性（I）**
>
>    **事务必须在不干扰其他进程或事务的前提下独立完成**
>
> 4. **持久性（D）**
>
>    **某个事务的执行过程中，对数据所做的所有改动都必须再事务成功结束前保存至某种物理存储设备**

## 事务的隔离级别

> **脏读：A查询B修改后问提交的数据，当B回滚时，A查询的数据是无效的**
>
> **不可重复读：A在第一次查询用户甲的信息，B将用户甲的信息修改并提交；A再次读取用户甲的信息，A两次获取的信息不同则称为“不可重复读”**
>
> **幻读：A查询用户数量时，当B新增或删除用户时，A再次获取用户数量时，两次数量不一致，则称为“幻读”**
>
> **注意：“不可重复读”与“幻读”的区别在于，不可重复读强调的是数据信息的改变，幻读强调的是数量上的改变**
>
> |          隔离级别          | 脏读 | 不可重复读 | 幻读 |
> | :------------------------: | :--: | :--------: | :--: |
> | 读未提交(Read Uncommitted) |  ×   |     ×      |  ×   |
> |  读已提交(Read Committed)  |  √   |     ×      |  ×   |
> |  可重复读(Repeated Read)   |  √   |     √      |  ×   |
> |    串行化(Serializable)    |  √   |     √      |  √   |
>
> **以上四种隔离级别，串行化的级别最高，读未提交的级别最低，级别越高，效率越低**
>
> **MySQL支持以上四种隔离级别，默认的隔离级别是可重复度**
>
> **Oracle数据库只支持串行化和读已提交 ，默认是读已提交；**

## Mysql最大的默认连接数

> **100**

为什么需要最大连接数？

>**特定服务器上面数据库最多只能支持一定数目同时连接**

## Mysql分页？Oracle分页

为什么需要分页？

> **当有很多数据，一个页面不可能显示为所有数据，需要进行分段显示**

mysql使用了limit关键字来限制查询条数

oracle使用了rownum三层嵌套循环

## 对JDBC的理解

> **他就是Java与数据库建立连接的桥梁或插件，用Java代码就能操作数据库的增删查改、存储过程、事务等**

## 写一个简单的JDBC程序

### 操作步骤

> 1. **加载驱动(com.mysql.jdbc.Driver)**
> 2. **获取参数(DriverManager.getConnection(url,username,password))**
> 3. **设置参数(Statement PrepareStatement)**
> 4. **执行(execute)**

### 例子

```java
Class.forName("com.mysql.cj.jdbc.Driver");
String url = "jdbc:mysql://localhost:3306/user?serverTimezone=GMT";
String username = "root";
String password = "123456";
Connection connection = DriverManager.getConnection(url,username,password);
String sql = "select * from user";
PreparedStatement preparedStatement = connection.prepareStatement(sql);
ResultSet resultSet = preparedStatement.executeQuery();
while (resultSet.next()){
    System.out.println(resultSet.getObject(1)+" "+resultSet.getObject(2));
}
connection.close();
preparedStatement.close();
resultSet.close();
```

## PreparedStatement相比于statement的好处

> 1. **PreparedStatement是预编译的，比statement快**
> 2. **代码的可读性和可维护性高**
> 3. **可以防SQL注入**

## 数据库连接池的作用

> 1. **限定数据库的连接个数，进行统一的连接管理**
> 2. **节约资源**
> 3. **加快响应速度**

## 数据库优化



# 框架

## Spring

### Spring的核心



> IOC(控制反转)或DI(依赖注入)：解决对象之间的依赖关系，把所有bean的依赖关系通过配置文件或注解关联起来，降低耦合度
>
> AOP(面向切面编程)：解决业务逻辑的耦合，用于那些将与业务无关，但却对多个对象产生公共行为和逻辑，抽象并封装成一个可重用的模块，减少系统中的重复代码降低模块间耦合度

AOP最直接的体现就是事务管理、权限判断、日志等。

### Spring的优点

> 1. 降低组件之间的耦合度
> 2. 提供了众多服务，如事务管理、消息服务等
> 3. 提供了AOP技术，容易实现权限管理、运行期监控等
> 4. 能够与各种优秀的框架继承
> 5. 属于低侵入式设计，代码的污染性极低
> 6. 提供了DI机制，降低了业务对象替换的复杂性

### Spring事务的传播特性

> PROPAGATION_REQUIRE：需要，如果存在一个事务就支持该事务，没有就开启事务
>
> PROPAGATION_SUPPORTS：支持，如果存在一个事务就支持该事务，没有就以非事务执行
>
> PROPAGATION_MANADTORY：必须，如果存在一个事务就支持该事务，没有就抛出异常
>
> PROPAGATION_REQUIRED_NEW：总是开启一个新事务，如果一个事务存在就将该事务挂起
>
> PROPAGATION_NOT_SUPPORTS：不支持，总是以非事务执行，并挂起任何以存在的事务
>
> PROPAGATION_NEVER：绝不，总是以非事务执行，如果存在一个事务，就抛出异常
>
> PROPAGATION_NESTED：嵌套的，如果有事务就嵌套，没有就开启事务

### Spring的事务隔离

有五大隔离级别，默认(ISOLATION_DEFAULT)是使用数据库的隔离级别，其他四个隔离级别跟数据库一致

> 1. ISOLATION_DEFAULT：默认隔离级别，数据库用什么，我就用什么
> 2. ISOLATION_READ_UNCOMMITTED：读未提交
> 3. ISOLATION_READ_COMMITTED：读已提交
> 4. ISOLATION_REPAREBLE_READ：可重复读
> 5. ISOLATION_SERIALIZABLE：序列化

## SpringMVC

### springmvc的执行流程

> 1. 发送请求到前端控制器DispatcherServlet
> 2. 前端控制器请求处理映射器HandlerMapping查找Handler
> 3. 处理映射器向前端控制器返回Handler
> 4. 前端控制器调用处理适配器去执行Handler
> 5. Handler执行完给适配器返回ModelAndView
> 6. 处理适配器向前端控制器返回ModelAndView
> 7. 前端控制器请求视图解析器ViewResolver去进行视图解析
> 8. 视图解析器向前端控制器返回View视图
> 9. 前端控制器进行视图渲染
> 10. 前端控制器向用户响应结果

## Mybatis

### 什么是Mybatis

> Mybatis是一款优秀的持久层框架，一个半ORM（对象关系映射）框架，它支持定制SQL、存储过程以及高级映射
>
> Mybatis可以使用简单的XML或注解来配置和映射原生类型、接口和Java的POJO为数据库中的记录

### #{}和${}的区别

> #{}是占位符，预编译处理；${}是拼接符，字符串替换；
>
> 处理#{}时，#{}传入参数是以字符串传入，会将#{}替换为?，调用PrepareStatement的set方法进行赋值
>
> 变量替换后#{}对应的变量自动加上单引号''，${}对应的变量不会加上单引号''；
>
> #{}可以有效的防止SQL注入，提高系统安全

### 一级缓存和二级缓存

> 一级缓存：是Session缓存，是基于HashMap存储的，作用域为SqlSession范围的，默认是打开一级缓存
>
> 二级缓存：是namespace缓存，是基于HashMap存储的，作用域为Mapper的，默认不开启

# Linux

## 为什么使用LInux

>  Linux是一个长时间运行比较稳定的操作系统，所以我们一般将它作为服务器
>
> Linux本身具有C编译的环境，我们的一些软件是没有软件包的（Redis、Nginx等），需要在Linux的C编译环境编译得到软件包

## 常用命令

### 获取当前路径

> pwd

### 跳转目录

> cd

### 切换管理员

> su

### 列出当前目录下的所有内容

> ls
>
> -a：隐藏文件
>
> -l：以列的形式查看

### 编辑文件

> vi
>
> i：编辑
>
> :wq 保存退出

### 删除文件

> rm

### 创建文件夹

> mkdir

### 移动文件

> mv

### 复制文件

> cp