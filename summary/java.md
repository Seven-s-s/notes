## Java基础

### **Java语言跨平台原理**

>**在需要运行Java应用程序的操作系统上，安装一个与之对应的Java虚拟机JVM(Java Virtual Machine)即可**
>
>**JRE：运行环境**
>
>**JDK：开发环境**

### 逻辑运算符

>**&：逻辑与，无论左边为真还是假，后面都要执行**
>
>**&&： 短路与，只要左边为假，后面都不执行**
>
>**|：  逻辑或，无论左边是真还是假，后面都要执行**
>
>**||：  短路或，只要左边为真，后面都不执行**

### String与StringBuilder

>**StringBuilder拼接字符串耗时耗空间，需要用StringBuilder**
>
>```java
>String s;
>StringBuilder sb = new StringBuilder(s);
>```
>
>**拼接sb.append(字符串)**
>
>```java
>String s = sb.toString();
>```
>
>****

### @Override

>**可以帮助我们检查重写方法的方法声明的正确性**

### Date

>```java
>Date date = new Date()
>```
>
>获取当前时间返回一个毫秒值
>
>```java 
>Long time = System.currentTimeMills();
>date.setTime(time);
>```
>
>将date转化为String
>
>```java
>SimpleDateFormat sdf = new SimpleDateFormat("yyyy年MM月dd日 HH:mm:ss");
>String s = sdf.format(date);
>```
>
>将String转化为date
>
>```java
>String s = "yyyy-MM-dd HH:mm:ss";
>SimpleDateFormat sdf = new SimpleDateFormat("yyyy年MM月dd日 HH:mm:ss");
>date = sdf.parse(s);
>```

## 集合

### Set

#### 概念

无序的，不可重复的集合

要保证元素的唯一性，需要重写hashCode()和equals()方法

#### 方法

>​	**添加：add()**
>
>​	**删除：remove()**

#### 取值方式

```java
Set<String> set = new HashSet<>();
set.add("apple");
set.add("banana");
set.add("pear");
```

>**foreach遍历**
>
>```java
>for (String s : set){
>    System.out.println(s);
>}
>```
>
>**迭代器遍历**
>
>```java
>Iterator<String> iterator = set.iterator();
>while (iterator.hasNext()){
>    String s = iterator.next();
>    System.out.println(s);
>}
>```

### List

#### 概念

有序的，可重复的集合

#### 方法

>**添加：add()**
>
>**删除：remove()**
>
>**获取：get()**
>
>**长度：size()**

#### 取值方式

```java
List<String> list = new LinkedList<>();
list.add("apple");
list.add("banana");
list.add("pear");
```

>**for循环**
>
>```java
>for (int i = 0;i < list.size();i++){
>    System.out.println(list.get(i));
>}
>```
>
>**foreach循环**
>
>```java
>for (String s : list){
>    System.out.println(s);
>}
>```
>
>**迭代器循环**
>
>```java
>Iterator<String> iterator = list.iterator();
>while (iterator.hasNext()){
>    String s = iterator.next();
>    System.out.println(s);
>}
>```

### Map

#### 概念

无序，键值对集合（映射关系），键不能重复，值可以重复，键可以为null，值也可为null。

#### 方法

>**添加：put(key,value)**
>
>**获取：get(key)**
>
>**删除：remove(key)**

#### **获取所有的值**

```java
Map<String,String> map = new HashMap<>();
map.put("apple","good");
map.put("banana","better");
map.put("pear","best");
Set<String> keySet = map.keySet();
```

拿到所有的key，遍历key，根据key拿值

**foreach循环遍历**

```java
for (String key : keySet){
    System.out.println(map.get(key));
}
```

**迭代器遍历**

```java
while (iterator.hasNext()){
    String s = iterator.next();
    System.out.println(map.get(s));
}
```

#### 获取所有的映射关系集合

```java
Set<Map.Entry<String,String>> entries = map.entrySet();
```

**for循环**

```java
for (Map.Entry<String,String> entry:entries){
    System.out.println(entry.getKey()+" "+entry.getValue());
}
```

**迭代器遍历**

```java
Iterator<Map.Entry<String,String>> iterator = entries.iterator();
while (iterator.hasNext()){
    Map.Entry<String,String> entry = iterator.next();
    System.out.println(entry.getKey()+" "+entry.getValue());
}
```

### 迭代器

#### Iterator

##### 方法

>**next()：返回迭代中的下一个元素**
>
>**hasNext()：如果迭代器有下一个元素，返回true**

#### ListIterator

>**next()**
>
>**hasNext()**
>
>**previous()：返回列表中的上一个元素** 
>
>**hasPrevious()：如果迭代在相反方向上遍历有更多元素，返回true**
>
>**add()：向指定的元素插入列表**

## File

### 方法

>**File file = new File(路径);**
>
>**createNewFile()：创建文件，如果有没有该文件就创建文件并返回true，否则返回false**
>
>**mkdir()：创建目录，如果有该目录则创建该目录并返回true，否则返回false**
>
>**mkdirs()：创建多级目录，如果有这多级目录则创建多级目录并返回true，否则返回false**
>
>**isDirectory()：判断file是否为目录**
>
>**isFile()：判断file是否为文件**
>
>**exists()：判断file是否存在**
>
>**getAbsolutePath()：返回该路径的绝对路径名字符串**
>
>**getPath()：返回该路径的路径名字符串**
>
>**getName()：返回该路径表示的文件或目录**
>
>**list()：返回该目录中的文件和目录的名称字符串数组**
>
>**listFiles()：返回该目录中的文件和目录的file对象数组**
>
>**delete()：删除该目录，如果目录中有内容，不能直接删除，先要删除目录中的内容，在删除目录**

### 例子

1. 在D盘下创建文件file.txt

   ```java
   File file = new File("D://file.txt");
   try {
      boolean b = file.createNewFile();
   } catch (IOException e) {
       e.printStackTrace();
   }
   System.out.println(b);
   ```

2. 在D盘下创建目录file

   ```java
   File file = new File("D://file");
   boolean b = file.mkdir();
   System.out.println(b);
   ```

   

3. 在D盘下创建目录file，在file目录下在创建目录files

   ```java
   File file = new File("D://file//files");
   boolean b = file.mkdirs();
   System.out.println(b);
   ```

## IO

### 字节流

#### 输出流

##### 方法

> **FileOutputStream fos = new FileOutputStream(文件名);**
>
> **write()：往文件里面写数据**
>
> **getBytes()：返回字符串对应的字节数组**
>
> **close()：释放资源**

##### **换行符**

>**Window：\r\n**
>
>**Linux：\n**
>
>**Mac：\r**

##### 例子

向file.txt文件写入HelloWorld

```java
FileOutputStream fos = new FileOutputStream("D://file.txt");
String s = "Hello World";
fos.write(s.getBytes());
fos.close();
```



#### 输入流

##### 方法

>**FileInputStream fis = new FileInputStream(文件名);**
>
>**read()：读取一个字节，如果有参数并且是byte数组，则返回的数据长度**
>
>**close()：释放资源**

##### 例子

> **向file.txt读取数据**
>
> **方法一**
>
> ```java
> FileInputStream fis = new FileInputStream("D://file.txt");
> byte b[] = new byte[1024];
> int length = fis.read(b);
> System.out.println(new String(b));
> System.out.println(length);
> fis.close();
> ```
>
> **方法二**
>
> ```java
> FileInputStream fis = new FileInputStream("D://file.txt");
> int data = 0;
> while ((data=fis.read())!=-1) {
>     System.out.print((char)data);
> }
> fis.close();
> ```

### 字符流

#### 输出流

##### 方法

> **FileWriter fw = new FileWriter();**
>
> **write()：写数据**
>
> **flush()：刷新**
>
> **close()：释放资源**

##### 例子

> **向file.txt写入Hello World**
>
> ```java
> FileWriter fw = new FileWriter("D://file.txt");
> String s = "Hello World";
> fw.write(s);
> fw.flush();//不刷新将不会写入
> fw.close();//关闭资源前会自动刷新
> ```

#### 输入流

##### 方法

> **FileReader fr = new FileReader();**
>
> **read()：读取数据**

##### 例子

> 方法一
>
> ```java
> FileReader fr = new FileReader("D://file.txt");
> char c[] = new char[1024];
> fr.read(c);
> System.out.println(new String(c));
> ```
>
> 方法二
>
> ```java
> FileReader fr = new FileReader("D://file.txt");
> int data = 0;
> while ((data=fr.read())!=-1) {
>     System.out.print((char)data);
> }
> fr.close();
> ```
>