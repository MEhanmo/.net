<!-- TOC -->

- [常用类库](#常用类库)
    - [字符串](#字符串)
        - [成员方法和属性](#成员方法和属性)
        - [静态方法](#静态方法)
        - [不可变性](#不可变性)
        - [字符串池（只针对字符串常量）](#字符串池只针对字符串常量)
        - [StringBuilder](#stringbuilder)
        - [String和string](#string和string)
    - [DateTime](#datetime)
    - [数据集合DataCollection](#数据集合datacollection)
        - [Array](#array)
        - [ArrayList](#arraylist)
        - [Hashtable](#hashtable)
        - [排序列表SortedList](#排序列表sortedlist)
        - [堆栈Stack](#堆栈stack)
        - [队列Queue](#队列queue)
    - [泛型](#泛型)
        - [泛型使用](#泛型使用)
        - [泛型集合List<T>](#泛型集合listt)
        - [Dictionay<Tkey,Tvalue>](#dictionaytkeytvalue)

<!-- /TOC -->

<a id="markdown-常用类库" name="常用类库"></a>
# 常用类库

<a id="markdown-字符串" name="字符串"></a>
## 字符串
<a id="markdown-成员方法和属性" name="成员方法和属性"></a>
### 成员方法和属性

方法/属性 | 说明
---------------------|-----------------
Contains(String str) | 判断字符串中是否包含指定字符串。
StartsWith(String str) | 判断字符串对象是否以指定字符串开头。
EndWith(String str) | 判断字符串对象是否以指定字符串结尾。
Length属性 | 获取字符串的长度
IndexOf(String str) | 获取指定字符/字符串.....在对象字符串中第一次出现的位置，从0开始
LastIndexOf(String str) | 获取指定字符/字符串....在对象字符串中最后一次 出现的位置。
SubString(int start) | 从指定位置，截取字符串。
SubString(int strat, int length) | 从指定位置，截取length长度字符串
ToLower()/ToUpper() | 将字符串转换成小写/大写，返回一个新的全小写/大写的字符串。
Replace(string oldStr,string newStr) | 用新的字符串，替换对象字符串中老的字符串部分。
Trim()/TrimStart()/TrimEnd() | 去掉对象字符串两端/开始/结尾的空格
Split() | 把对象字符串，按照指定字符分割成一个字符串数组！

<a id="markdown-静态方法" name="静态方法"></a>
### 静态方法

方法名 | 说明
----|---
string.IsNullOrEmpty(string) | 判断某字符串是否为null，或者为空字符串，为null或空时返回真值
string.Equals(string,string,StringComparison.OrdianlIgnore) | 忽略大小写比较两个字符串是否相同。
string.Join(string,string[]) | 把一个数组按照指定字符串，拼接成一个字符串。

<a id="markdown-不可变性" name="不可变性"></a>
### 不可变性
string，首先是引用类型，由于字符串是不可变的的，每次修改字符串，都是创建了一个单独字符串副本（拷贝了一个字符串副本）。

之所以发生改变只是因为指向了一块新的地址。

<a id="markdown-字符串池只针对字符串常量" name="字符串池只针对字符串常量"></a>
### 字符串池（只针对字符串常量）
当一个程序中有多个相同的字符串常量时，多个变量指向的是内存中同一块字符串！

这个特性叫字符串池。不会造成程序混乱，是因为字符串的不可变性。

<a id="markdown-stringbuilder" name="stringbuilder"></a>
### StringBuilder
在需要对字符串执行重复修改的情况下，与创建新的 String 对象相关的系统开销可能会非常昂贵。

如果要修改字符串而不创建新的对象，则可以使用System.Text.StringBuilder 类

例如，当在一个循环中将许多字符串连接在一起时，使用 StringBuilder 类可以提升性能。

<a id="markdown-string和string" name="string和string"></a>
### String和string
String是.NET  Framework里面的String，小写的string是C#语言中的string。

用C#编写代码的情况下尽量使用小写的string，比较符合规范，

如果在追求效率的情况下可以使用大写的String，因为最终通过编译后，小写的string会变成大写的String，可以给编译减少负荷，从而运行效率提高。

MSDN中对string的说明：string is an alias for String in the .NET Framework

<a id="markdown-datetime" name="datetime"></a>
## DateTime
DateTime是.NET中的时间类型，可以通过DateTime完成诸如获取当前的系统时间等操作。

需要注意的是，DateTime在.NET中是一个结构体，而并不是一个类。

方法/属性 | 说明
------|---
Now | 获取当前系统时间。格式：2018/9/5 8:27:02
Today | 获取今天的日期。格式：2018/9/5 0:00:00
Now.Year | 获取年
Now.Month | 获取月
Now.Day | 获取日
Now.Hour | 获取小时
Now.Minute | 获取分钟
Now.Second | 获取秒
DayOfWeek | 获取当前日期是星期几
DayOfYear | 以及获取当前日期是一年中的第几天
Parse() | 转换为DateTime对象
TryParse() | 判断是否是时间类型，参数中有一个out可以输出一个DateTime对象。
AddDays()、AddHours() | 在当前时间基础上加几天/几个小时，返回一个DateTime
Subtract(DateTime.Now) | 比较两个时间的 时间差 | 返回一个TimeSpan

DateTime.ToString()的各种日期格式
```cs
//常用的预定义模式
DateTime.Now.ToString("d");// ShortDatePattern  2018/9/5
DateTime.Now.ToString("D");// LongDatePattern  2018年9月5日
DateTime.Now.ToString("f");// 完整日期和时间（长日期和短时间） 2018年9月5日 9:03
DateTime.Now.ToString("F");// FullDateTimePattern（长日期和长时间）  2018年9月5日 9:05:15
DateTime.Now.ToString("g");// 常规（短日期和短时间） 2018/9/5 9:05
DateTime.Now.ToString("G");// 常规（短日期和长时间） 2018/9/5 9:05:54
DateTime.Now.ToString("m");//DateTime.Now.ToString("M");  9月5日
```

DateTime的字符串格式除了预定义还有自定义的模式，如下：
* d 月中的某一天。一位数的日期没有前导零。 
* dd 月中的某一天。一位数的日期有一个前导零。 
* ddd 周中某天的缩写名称，在 AbbreviatedDayNames 中定义。 
* dddd 周中某天的完整名称，在 DayNames 中定义。 
* M 月份数字。一位数的月份没有前导零。 
* MM 月份数字。一位数的月份有一个前导零。 
* MMM 月份的缩写名称，在 AbbreviatedMonthNames 中定义。 
* MMMM 月份的完整名称，在 MonthNames 中定义。 
* y 不包含纪元的年份。如果不包含纪元的年份小于 10，则显示不具有前导零的年份。 
* yy 不包含纪元的年份。如果不包含纪元的年份小于 10，则显示具有前导零的年份。 
* yyyy 包括纪元的四位数的年份。 
* gg 时期或纪元。如果要设置格式的日期不具有关联的时期或纪元字符串，则忽略该模式。 
* h 12 小时制的小时。一位数的小时数没有前导零。 
* hh 12 小时制的小时。一位数的小时数有前导零。 
* H 24 小时制的小时。一位数的小时数没有前导零。 
* HH 24 小时制的小时。一位数的小时数有前导零。 
* m 分钟。一位数的分钟数没有前导零。 
* mm 分钟。一位数的分钟数有一个前导零。 
* s 秒。一位数的秒数没有前导零。 
* ss 秒。一位数的秒数有一个前导零。

例如：
```cs
DateTime.Now.ToString("yyyy-MM-dd");//2018-09-05
DateTime.Now.ToString("yyyy-MM-dd HH");//2018-09-05 09
```

<a id="markdown-数据集合datacollection" name="数据集合datacollection"></a>
## 数据集合DataCollection

<a id="markdown-array" name="array"></a>
### Array
Array类是一个抽象类，无法实例化该类。主要作为基类进行扩展，实际使用中很少直接使用Array类。

但可以通过它的一些静态方法来进行数组的创建、遍历、拷贝、排序等操作，下面给出部分示例：
```cs
/*
以下两种初始化的方式是等效的
*/
string[] arr = { "a", "b", "c" };

Array arr = Array.CreateInstance(typeof(string), 3);
arr.SetValue("a", 0);
arr.SetValue("b", 1);
arr.SetValue("c", 2);
```

<a id="markdown-arraylist" name="arraylist"></a>
### ArrayList
在System.Collections命名空间下，同时继承了IList接口。

ArrayList对象的大小可按照其中存储的数据进行动态增减，所以在声明ArrayList对象时并不需要指定它的长度。

但是由于ArrayList会把插入其中的所有数据当作为object类型来处理，在存储或检索值类型时会发生装箱和拆箱操作，带来很大的性能耗损。

另外，ArrayList没有泛型的实现，也就是ArrayList不是类型安全的，在我们使用ArrayList处理数据时，很可能会报类型不匹配的错误。

因为ArrayList存在不安全类型与装箱拆箱的缺点，所以出现了泛型的概念。
```cs
//没有类型的约束，数值、字符串、布尔值均可以作为元素
ArrayList arrList = new ArrayList();
arrList.Add(1);//装箱 int->object
arrList.Add("abc");//装箱 string->object
arrList.Add(true);//装箱 bool->object
```

<a id="markdown-hashtable" name="hashtable"></a>
### Hashtable
Hashtable也并非类型安全的，用于处理和表现类似key-value的键值对，其中key通常可用来快速查找，同时key是区分大小写；

value用于存储对应于key的值。Hashtable中key-value键值对均为object类型，所以Hashtable可以支持任何类型的key-value键值对.

```cs
Hashtable ht = new Hashtable();
ht.Add(0, 1);
ht.Add("key", "name");
ht.Add(1.23, true);

//添加一个keyvalue键值对：
ht.Add(key,value);

//移除某个keyvalue键值对：
ht.Remove(key);

//移除所有元素：           
ht.Clear(); 

// 判断是否包含特定键key：
ht.Contains(key);
```

什么情况下应该使用Hashtable：
1. 某些数据会被高频率查询
2. 数据量大
3. 查询字段包含字符串类型
4. 数据类型不唯一

<a id="markdown-排序列表sortedlist" name="排序列表sortedlist"></a>
### 排序列表SortedList
SortedList 类代表了一系列按照键来排序的键/值对，这些键值对可以通过键和索引来访问。

排序列表是数组和哈希表的组合。它包含一个可使用键或索引访问各项的列表。

如果您使用索引访问各项，则它是一个动态数组（ArrayList）；

如果您使用键访问各项，则它是一个哈希表（Hashtable）。

集合中的各项总是按键值排序。

```cs
//需要添加 using System.Collections;
SortedList sl = new SortedList();
sl.Add("002", "钱二");
sl.Add("001", "赵一");
sl.Add("003", "孙三");
sl.Add("004", "李四");

//通过key值进行访问
Console.WriteLine(sl["001"]);

//虽然添加时并未排序，但遍历时会按照key进行排序
foreach (var item in sl.Keys)
{
    Console.WriteLine("遍历：" + sl[item]);
}
```

<a id="markdown-堆栈stack" name="堆栈stack"></a>
### 堆栈Stack
堆栈（Stack）代表了一个后进先出LIFO的对象集合。当您需要对各项进行后进先出的访问时，则使用堆栈。

当您在列表中添加一项，称为推入元素，当您从列表中移除一项时，称为弹出元素。

* Count：返回栈中所包含的元素个数
* Clear：删除所有的项
* Peek：返回一个处于调用栈顶端的对象的引用，但不删除它。
* Pop：返回并删除顶端的对象
* Push：向栈中添加指定的对象

```cs
//需要添加 using System.Collections;
Stack st = new Stack();
st.Push(1);
st.Push("abc");
st.Push(true);
st.Push(new object());

Console.WriteLine("长度：" + st.Count);

Console.WriteLine(st.Peek());
Console.WriteLine("长度：" + st.Count);

Console.WriteLine(st.Pop());
Console.WriteLine("长度：" + st.Count);
```

<a id="markdown-队列queue" name="队列queue"></a>
### 队列Queue
队列（Queue）代表了一个先进先出的对象集合。

当您需要对各项进行先进先出的访问时，则使用队列。

当您在列表中添加一项，称为入队，当您从列表中移除一项时，称为出队。类似排队的效果。

```cs
//需要添加 using System.Collections;
Queue qu = new Queue();
qu.Enqueue("赵一");
qu.Enqueue("钱二");
qu.Enqueue("孙三");
qu.Enqueue("李四");

foreach (var item in qu)
{
    Console.WriteLine("入队后：" + item);
}
qu.Dequeue();
foreach (var item in qu)
{
    Console.WriteLine("出队：" + item);
}
```

<a id="markdown-泛型" name="泛型"></a>
## 泛型
泛型可以定义类型安全的数据结构，而无须使用实际的数据类型。有助于最大限度地重用代码、保护类型的安全以及提高性能。

泛型（Generic）允许您延迟编写类或方法中的编程元素的数据类型的规范，直到实际在程序中使用它的时候。

换句话说，泛型允许您编写一个可以与任何数据类型一起工作的类或方法。

我们可以通过数据类型的替代参数编写类或方法的规范。

当编译器遇到类的构造函数或方法的函数调用时，它会生成代码来处理指定的数据类型。

<a id="markdown-泛型使用" name="泛型使用"></a>
### 泛型使用
泛型类：
```cs
/// <summary>
/// 泛型数组类
/// 数组类型由调用者决定
/// </summary>
/// <typeparam name="T"></typeparam>
public class MyGenericArray<T>
{
    private T[] array;
    public MyGenericArray(int size)
    {
        array = new T[size + 1];
    }
    public T getItem(int index)
    {
        return array[index];
    }
    public void setItem(int index, T value)
    {
        array[index] = value;
    }
}
```

泛型方法：
```cs
/// <summary>
/// 泛型方法
/// 同样的交换逻辑，不同数据类型的交换不需要重复的定义方法，调用的时候决定类型即可
/// </summary>
/// <typeparam name="T"></typeparam>
/// <param name="t1"></param>
/// <param name="t2"></param>
static void Swap<T>(ref T t1, ref T t2)
{
    T temp = t1;
    t1 = t2;
    t2 = temp;
}

static void Main()
{
    int a = 1, b = 2;
    string str1 = "hello", str2 = "world";

    Swap<int>(ref a, ref b);
    Swap<string>(ref str1, ref str2);

    Console.WriteLine("交换后a:{0}\t b:{1}", a, b);
    Console.WriteLine("交换后str1:{0}\t str2:{1}", str1, str2);
}
```

<a id="markdown-泛型集合listt" name="泛型集合listt"></a>
### 泛型集合List<T>
List<T>类是 ArrayList 类的泛型等效类。

不会强行对值类型进行装箱和拆箱，或对引用类型进行向下强制类型转换，所以性能得到提高。

```cs
//限制类型只能是string，同样的限定类型也可以是值类型
List<string> lstRes = new List<string>();
//添加对象到结尾处
lstRes.Add("a");
lstRes.Add("b");
lstRes.Add("c");

//长度
int len = lstRes.Count;

//删除
lstRes.Remove("a");

//是否包含某个对象
lstRes.Contains("a");
```
更多的方法等待你去探索。。。

<a id="markdown-dictionaytkeytvalue" name="dictionaytkeytvalue"></a>
### Dictionay<Tkey,Tvalue>
在初始化的时候也必须指定其类型，而且他还需要指定一个Key,并且这个Key是唯一的。

正因为这样，Dictionary的索引速度非常快。但是也因为他增加了一个Key,Dictionary占用的内存空间比其他类型要大。

他是通过Key来查找元素的，元素的顺序是不定的。

```cs
Dictionary<string, string> dicRes = new Dictionary<string, string>();
dicRes.Add("zhangsan","张三");
dicRes.Add("zhaofugui", "赵富贵");
```

---

参考引用：

[.NET常用类库知识总结](https://www.cnblogs.com/1030351096zzz/p/6234896.html)