# Python基本语法

首先，Python与其他语言区别很大的地方

* name 与 object 直接匹配 根本不用定义变量类型 
* 不用分号，用回车/换行代替分号
* 代码块不使用大括号 **{}**，而是用***缩进***写模块
* 缩进用tab，取消缩进用shift+tab

* 常见单词
  * parameters：形参
  * arguments： 实参   无歧义时可视为参数
  * attribute:  属性
  * module:     模块

运算符

```
print(7/3)   #2.3333333333333335  正常的除法
print(7//3)  #2 整除 向下取整
print(2**3)  #8 2的3次方 幂运算

and #即&&
or  #即||
not #即!
```

一些内置函数
* 数学运算
  ```
  abs()        求绝对值
  round(num)   求近似整数
  round(num,n) 保留n位小数
  pow()        求次方
  divmod(x,y)  求x/y的商和余数 构成的元组
  min()        求最小值
  max()        求最大值
  sum()        求和
  eval()       执行一个字符串表达式
  ```

* random库 随机数
  ```
  import random
  print(random.random())               # 产生 0 到 1 之间的随机浮点数
  print( random.uniform(1.1,5.4) )     # 产生  1.1 到 5.4 之间的随机浮点数
  print( random.randint(1,10) )        # 产生 1 到 10 的一个整数型随机数 

  a=[1,3,5,6,7]                        # 将序列a中的元素随机打乱
  random.shuffle(a)
  print(a)

  print( random.randrange(1,100,2) )   # 生成从1到100的间隔为2的随机整数
  print (random.choice('cyl'))         # 生成随机字符

  random.seed(x) 表示设置随机数种子 种子x相同时，每次产生的随机数也都相同
  tips:如果不设置种子，默认情况下，随机数生成器将使用系统时间作为种子，因此每次运行程序时都会生成不同的随机数序列。
  ```

* 其他
  ```
  num = int(x)   #char->int
  a = chr(num)   #int->char
  len()  求长度
  type() 查看变量的数据类型
  id()   查看变量的内存地址
  range(x,y) 创建整数列表 [x,y) x到y-1的范围 若range(x) 即range(0,x) 即[0,x)
  zip() 将对象中对应的元素打包成一个个元组，然后返回由这些元组组成的对象 可以使用 list() 转换来输出列表
  ```


## 1.注释

* 单行注释    

  ```
  # 这是单行注释
  # 这是单行注释
  ```

* 多行注释

  ```
  """
  这是多行注释
  """
  ```

## 2.输入输出

* 输入input

```
x = input("提示文字:")  #x默认是字符型str类型
强转 
num = int(x)   #char->int
a = chr(num)       #int->char

age = int(input("请输入年龄："))  #或者直接强转
```

* 输出print

```
print()函数是一个标准格式化输出函数
print(value, sep=’ ’,end（）=’\n’, file = sys.stdout, flush = False)
sep:分隔符 默认空格  
end:尾打印 默认换行 所以每次一个print()后都会自动换行 
后面两个基本不用

```

字符串格式化输出str {}.format()
```
#一 外定义参数
name = "陈言泷"
age = 20
print("我的名字是{},我的年龄是{}".format(name,age))
#二 内定义参数
print("姓名:{name},住址:{url}".format(name="陈",url="www.com"))
#三 用字典或列表...
```

## 3.选择结构

* if else

  ```
  if 判断条件1:
      执行语句1……
  elif 判断条件2:
      执行语句2……
  elif 判断条件3:
      执行语句3……
  else:
      执行语句4……
  ```

* match

  ```
  num=int(input("请输入数字："))
  print(num)
  
  match num:
      case 5:
          print("数字5")
      case 4:
          print("数字4")
      case _:
          print(".....")
  ```

## 4.循环结构

* for循环

  ```
  for i in "HELLO":
      print(i) 
      
  x="HELLO"
  for i in x:
      print(i) 
  
  for i in range(len(x)):
  	print(x[i])
  ```

* while循环

  ```
  while 判断条件(condition)：
      执行语句(statements)……
  ```

## 5.序列

* 都有索引 切片等功能
* 相关内置函数
  ```
  1.sorted()函数 默认升序排序，且返回的是一个新的 list，而原来的序列不变 
  sorted(iterable, cmp=None, key=None, reverse=False) 
  key 指定可迭代对象中的一个元素来进行排序。
  reverse = True降序，reverse = False 升序。
  示例如下
  >>> students = [('john', 'A', 15), ('jane', 'B', 12), ('dave', 'B', 10)]
  >>> sorted(students, key=lambda s: s[2])            # 按年龄排序
  [('dave', 'B', 10), ('jane', 'B', 12), ('john', 'A', 15)]

  >>> sorted(students, key=lambda s: s[2], reverse=True)       # 按降序
  [('john', 'A', 15), ('jane', 'B', 12), ('dave', 'B', 10)]
  ```

### ①字符串类型Str

假设字符串长度为n     正向序列0 ~ n-1    反向序列-n ~ -1

字符串片段 [start,end,step]    即[start,end） step:步长 每次迈step步 默认为1

```
s = "abcdefg"       #长度n为7
print(s[0], s[-7])  #a a
print(s[2:5])       #cde 左闭右开[ ) 即2~4  
print(s[2:])        #cdefg 从2到最后    2~n-1
print(s[:5])        #abcde 从最开始到4  0~4
print(s[2:5:2])     #ce   2~4 但一次迈两步 即只有2 4
print(s[::-1])      #gfedcba  逆着走 逆序遍历

print(s[:-1])       #除了最后一个元素，获取其他所有的元素
```

字符串其他操作

```
x = "abc" 
y = "def"
print(x+y)  #abcdef 字符串拼接
print(5*x)  #abcabcabcabcabc 复制x五次
print(x in y) #False  若x在y中 即x是y的子串则输出True 否则 False
print(x not in y)  #True 与上面相反
max(str)
min(str)
str.count(x)  #字符串str中x的计数
str.index(x)  #字符串str中x的第一个下标
str.split("")  分割字符串，返回字符串列表
```

### ②列表List
* 列表可变
  
*  列表创建

  ```
  lis = ["HELLO", "WORLD", 5, 3]
  print(lis)           # ['HELLO', 'WORLD', 5, 3]
  
  lis1 = list("HELLO")
  print(lis1)          # ['H', 'E', 'L', 'L', 'O']
  
  list = []          ## 空列表
  list.append('Google')   ## 使用 append() 添加元素
  list.append('Runoob')
  print(list)          # ['Google', 'Runoob']
  
  list = [i for i in range(10)]
  print(list)          # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
  
  list = [i for i in range(10) if i%2]
  print(list)          # [1, 3, 5, 7, 9]
  ```

* 列表删除

  ```
  list1 = ['physics', 'chemistry', 1997, 2000]
  print(list1)
  del list1[2] #删除列表中某个元素 
  print(list1)
  del list1    #删除整个列表
  ```

* 列表增删改查

  ```
  list.append(x)
  list.insert(index,x)
  list.clear()
  list.pop(index)
  list.remove(x)
  list.reverse()
  list.copy
  list.sort() 默认升序排序
  ......
  ```

* 其他操作与字符串基本一致

### ③元组Tuple

* 与列表很相似

* 但元组不可变，也就是元组定义好以后我们不能修改里面的元素，所以无增删改查 只能用del

  ```
  创建空元组
  tup1 = ()
  
  tup = ("hello","world",5,[1,2,3])
  print(tup)   #('hello', 'world', 5, [1, 2, 3])
  
  tup1 = tuple("hello")
  print(tup1)  #('h', 'e', 'l', 'l', 'o')
  
  元组中只包含一个元素时，需要在元素后面添加逗号
  tup1 = (50,)
  print(type(tup1))  #<class 'tuple'>
  tup1 = (50)
  print(type(tup1))  #<class 'int'>
  ```

### ④字典Dict

* 键值对 key-value
* tips 键必须不可变，所以可以用数字，字符串或元组充当，所以用列表就不行
* 格式 `d = {key1 : value1, key2 : value2 }`
* 访问 `d["key1"]`
* 修改 `d["age"] = 8`
* 删除
  ```
  tinydict = {'Name': 'Zara', 'Age': 7, 'Class': 'First'}

  del tinydict['Name']  # 删除键是'Name'的条目
  tinydict.clear()      # 清空字典所有条目
  del tinydict          # 删除字典
  ```
* 一些内置函数
  ```
  dict = {"name":"cyl","age":100}
  for key in dict.keys():
    print(key)
  for value in dict.values():
    print(value)
  for key,value in dict.items():
    print("{}:{}".format(key,value))
  ```

### ⑤集合Set
* 无序的不重复元素序列
* 创建集合
  ``` 
  set1 = {1, 2, 3, 4}           # 直接使用大括号创建集合
  set2 = set([4, 5, 6, 7])      # 使用 set() 函数从列表创建集合
  set3 = set("abswdw")
  ```
* 两集合间的运算
  ```
  a = set('abracadabra')
  b = set('alacazam')
  print(a&b) #交集
  print(a|b) #并集
  print(a-b) #差集
  print(a^b) #对称差集
  ```
* 其他操作
  ```
  set.add(x) 添加元素x
  set.remove(x) 移除元素x
  ```




## 6.时间和日期
* 1)打印格式化本地时间
  ```
  import time 
  x = time.asctime(time.localtime(time.time()))
  print("本地时间是",x)
  ```

* 2)打印某月日历
  ```
  import calendar
  cal = calendar.month(2024,2)
  print("打印2024年1月的日历",cal)
  ```

* 3)....
  
## 7.函数
* 基本格式
  ```
  def func(a,b):
    return a+b
  print(func(1,2))
  ```
* 各种类型的参数都能传，字符串、列表、元组、字典.... 甚至能传对象obj
* 传入不定长参数 *x表示传入一个元组
  ```
  def func(*x):
    sum=0
    for i in x:
        sum+=i
    return sum
  
  print(func(1,2,3,4,5))
  ```
* 匿名函数 lambda
  ```
  sum = lambda x,y:x+y
  print(sum(1,2))
  ```

## 8.面向对象
* 四个点 封装 继承 多态 抽象
* 封装
  * 类名 类的属性和方法
    * 类属性 实例属性
    * 类对象 实例对象
      * (class 类名)   即创建类对象
      * 在类外x=类名()  即创建实例对象    
    * 类方法 实例方法 静态方法
      * 类方法用@classmethod标识 类方法第一个默认参数为***cls*** 类方法内只能调用类属性和类方法
      * 实例方法第一个默认参数为***self***
      * 静态方法用@staticmethod标识 不需要额外的参数 一般不与实例对象交互 直接用类对象调用 省资源
  * self相当于this指针，因此self可以等价为实例化对象
  * 两个下划线开头__ 即private 私有属性或方法 
  * 单下划线开头_ 即proteced 保护属性或方法
  
* 用装饰器@property @属性名.setter 来调用私有属性(相当于写了get和set函数)
  ```
  class People:
    def __init__(self):
        self.__age=18 # 私有属性age
    @property    # 提供getter
    def age(self):
        return self.__age
    @age.setter  # 提供setter
    def age(self,x):
        if x<0:
            print("年龄不能小于0")
        else:
            self.__age=x

  xm=People()
  print(xm.age) # 实质上是调用了与私有属性age同名的getter函数
  xm.age=20     # 实质上是调用了与私有属性age同名的setter函数，并传入实参20
  print(xm.age) # 同理
  ```

* 类的专有方法(魔术方法)
  ```
  1.__new__():      new一个对象  也会自动调用
  2.__init__(self): 构造函数 在类实例化时会自动调用
  3.__del__(self):  析构函数 同样自动调用
  4.__str__(self):  自定义输出字符串
  
  new比init更早执行 即要先new出一个对象，然后再init初始化
  
  class People:
    name=""  #类属性
    def __init__(self, name, gender, age, play):
        self.name = name       #实例属性
        self.gender = gender
        self.age = age
        self.play = play
    def eat(self, food):
        print(self.name + "喜欢吃" + food)
    def __str__(self):
        return self.name + "爱玩" + self.play

  x1 = People("小明", "男", 20, "CSGO")  # init构造函数自动调用
  x1.eat("西瓜")
  print(x1.name, x1.gender, x1.age)
  print(x1)  # str 让实例对象自定义输出
  ```

* 类外动态绑定属性和方法，并用__slots__变量限制要添加的属性
  * `__slot__ =(属性，属性)` 只有slots变量内的属性才可在类外动态添加，slots变量的属性子类不会继承，需要在子类中再声明slots


* 继承(单继承 多继承)
  * 方法可以被重写覆盖
  * super() 用于调用父类中的函数
  * 单继承 `class 子类（父类）`
  ```
  # Animal是父类 Dog Cat是继承的子类

  class Animal:
      name=""
      age=""
      gender=""
      def __init__(self,name,age,gender):
          self.name=name
          self.age=age
          self.gender=gender

      def eat(self):
          print("它正在吃饭~~~")

      def sleep(self):
          print("它睡着了~~~")

  class Dog(Animal):
      hobby=""
      # 子类重写了父类的构造函数，并用super函数调用了父类的构造函数
      
      def __init__(self, name, age, gender, hobby):
          Animal.__init__(self,name,age,gender)  # 直接调用父类Animal的函数
          # super.__init__(name,age,gender)
          self.hobby = hobby

      def eat(self):
          print(self.name+"在吃饭")
      def sleep(self):
          print(self.name+"睡着了")
      def bark(self):
          super().sleep()  # 在类内用super函数调用了父类中已被覆盖的sleep函数
          print(self.name+"在狗叫")

      def __str__(self):
          return self.name+"年龄是"+self.age+"岁,爱好是"+self.hobby

  class Cat(Animal):
      def eat(self):
          print(self.name+"在吃饭")
      def sleep(self):
          print(self.name+"睡着了")
      def mew(self):
          print(self.name+"在喵叫")

  a=Dog("贝拉","8","girl","ball")
  a.bark()
  print(a)
  super(Dog,a).eat()  # 在类外用super函数调用对象a父类中已被覆盖的eat函数

  print("*"*40)

  b=Cat("多多","3","boy")
  b.mew()
  b.eat()
  ```

  * 多继承 `class 子类(父类1,父类2)`
    * 需要注意圆括号中父类的顺序，若是父类中有相同的方法名，而在子类使用时未指定，python从左至右搜索 即方法在子类中未找到时，从左到右查找父类中是否包含方法。 即广度优先查找
  
    ```
    # 见上面代码
    class faker(Dog,Cat):
      theme=""
      def __init__(self,name,age,gender,hobby,theme):
          Dog.__init__(self,name,age,gender,hobby)
          self.theme=theme

    a1=faker("狗猫","8","mixed","play football","PEACE&LOVE")
    a1.sleep()
    ```
  
* 多态 不同对象调用同一函数 结果是不同的(方法重写)
    ```
    class Animal:
    def talk(self):
        print("None")
    def sleep(self):
        print("动物在睡觉")

    class Dog(Animal):
        def talk(self):
            print("汪汪叫")
        def sleep(self):
            print("小狗在睡觉")

    class Cat(Animal):
        def talk(self):
            print("喵喵叫")
        def sleep(self):
            print("小猫在睡觉")

    class Dragon(Animal):
        def talk(self):
            print("轰轰轰")
        def sleep(self):
            print("小龙在睡觉")

    def func(obj):
        obj.sleep()

    lis=[Dog(),Cat(),Dragon()]

    for item in lis:
        func(item)
        
    ```
  
* 单例模式

## 9.异常处理
* `try-except-else-finally`
  ```
  try:
      # 可能出现错误的代码块
      print(b)
  except NameError as e:
      # 异常之后的执行的代码块 捕获NameError异常 其他无法捕获
      print(e)
  except Exception as msg: 
      # 异常之后的执行的代码块 Exception可以捕获大部分异常
      print(msg)
  else:
      # 如果try中没有异常，则执行else代码块，否则不执行
      print("这段代码没有错误")
  finally:
      # 异常与否，都会执行finally代码块
      print("错误与否，我都会执行")
  ```
* 用户自定义异常
  * 创建一个异常类，要继承Exception类
  * 要用raise主动抛出自定义异常
  ```
  class TooLongMyException(Exception):
      def __init__(self,lenth):
          self.lenth=lenth
      def __str__(self):
          return "您输入的名字长度为{}，太长啦，请修改".format(self.lenth)

  def Name():
      name=input("请输入您的名字：")
      try:
          if len(name)>5:
              raise TooLongMyException(len(name))
      except TooLongMyException as e:
          print(e)
          Name()     # 捕获异常后重新调用Name()
      else:
          print(name)
          
  Name()
  ```