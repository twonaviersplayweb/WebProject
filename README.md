# WebProject
2015.07.27
----------
>1.配置多人账户登录github时出现问题导致分支冲突，致使之前的被md被删除，现在重现写md文档</br>
>2.不知道怎么的已经变成另外一个账号在向仓库混合添加了,不折腾了，添加进去就好了，git pull origin master --->  git push origin master

2015.07.28
----------
>1.主要学习了dict，set的用法,以及函数的初级知识</br>
>2.深深的觉得算法的重要性</br>
>3.开始调用函数时误加print，致使结果出来带了None,而后解决

2015.07.29
----------
> 0.格式有些乱，不，是很乱，所以，你就讲究着看把，我没力气改了，马蛋的MD文档，用你妹的html语法啊，就不能安安静静的做个不用费神的文档吗！
> 
> 1.主要做了Python高级特性——切片，迭代，列表生成式，生成器&高阶函数中map/reduce,filter,sorted这三个函数的笔记
> 
> 2.切片：主要应用于list和tuple.list切片：
              list:S=['China','Japan','USA','UK'],S[:3],S[-2:],S[1:3];
              tuple:（'China','Japan','USA','UK'）[1:3]

> 3.迭代：主要通过for循环来遍历list和tuple中的元素.
```
S={'A':1,'B':2,'C':3,'D':4};
for k,v in S.iteritems():
	print k ,v
A 1
C 3
B 2
D 4
```

> 4.列表生成式：主要形式是[表达式 for循环]
```
print [n * (n+1) for n in range(1,10)]
[2, 6, 12, 20, 30, 42, 56, 72, 90]
```

> 5.生成器:有两种方式，一种是将[]变成(),生成器中的元素需要通过for循环遍历出来，第二种是中while循环中将print换成yield
```python
def fib(max):
	n, a, b = 0, 0, 1
	while n < max:
		yield b    
		a, b = b, a + b
		n = n +1
for n in fib(6):
	print n
print fib(6)
1
1
2
3
5
8
<generator object fib at 0xa981e0></generator>
```

> 6.map():接收两个参数，一个是函数，一个是列表,基本表现形式就是：def f(x);map(f(x),list)
> 
> 7.reduce():比较麻烦些，通式为：reduce(f, [x1, x2, x3, x4]) = f(f(f(x1, x2), x3), x4)，用法类似于map，传入函数跟list
> 
> 8.filter():过滤列表中的元素，用法同样是接收函数跟list,过滤符合函数中的列表元素
> 
> 9.sorted():对列表进行排序，也可以自定义添加函数来定义排序规则

2015.07.30
----------
>0.win10升级搞什么鬼！从昨夜到今天中午，91%-->0%，76%-->0%，你妹啊！断次网就给我清零断次网就清零！还能愉快的玩耍吗？

>1.主要学习了返回函数，闭包，匿名函数，装饰器，偏函数

>2.闭包：返回函数的延伸，程序不返回结果，返回函数，通过多层嵌套（2层到3层合适），逐层返回函数，返回函数不要引用循环变量
```python
def count():
	fs = []
	for i in range(1,4):
		def f(j):
			def g():
				return j *j
			return g
		fs.append(f(i))
	return  fs
f1, f2, f3 = count()
print f1(), f2(), f3()
```
>3.匿名函数lambda，使用范围不广
>4.装饰器：用来在代码运行其间增加功能，通过多层嵌套，顶层函数使用@元素来调用次级函数
```python
def los(text):
	def decorator(func):
		@functools.wraps(func)
		def wrapper(*args, **kw):
			print '%s %s(): ' % (text, func.__name__)
			return func(*args, **kw)
		return wrapper
	return decorator
```
>5.偏函数：引用functools.partical功能来固定函数中的一些参数，并返回一个新的函数，来使函数变得更加简单，接收函数对象，可变参数，**kw等三个变量
```python
int2 = functools.partial(int, base=2)
print int2('1000000')
print int2('1010101')
64
85
```

2015.07.31
----------
>1.今天时间基本栽第三方库上面了，先是pip安装问题，后是配置PYTHONPATH

>2.python2.7.9以上默认自带pip，pip未安装的话可以去官方下载脚本安装，使用pip命令：pip install packsges，安装库出现问题的话直接在前面加sudo，sudo大法好

>3.配置PYTHONPATH:
```
有三种修改方法，两种临时的，一种永久的
临时的：1.直接命令行中输入:export PYTHONPATH=/usr/lib/python2.7/site-packages/
       2.sudo vim /etc/profile:export PYTHONPATH=/usr/lib/python2.7/site-packages/
永久的：sudo vim /etc/bashrc:export PYTHONPATH=/usr/lib/python2.7/site-packages/
查看路径方式：bash: python --> import sys --> sys.path
```

2015.08.01
----------
> A day past with nothing.

2015.08.02
----------
>1.今天的状态不佳，主要看了模块的__future__特性和面向对象编程：类和实例，访问限制，继承和多态内容

>2.类的一般形似：
```
class Student(object):
	def __init__(self, name, score):    #通过定义一个特殊的__init__方法，在创建实例的时候，就把name，score等属性绑上去，self，表示创建的实例本身
		self.name = name
		self.score = score
bart = Student('Bart Simpon', 59)
print bart.name
print bart.score
Bart Simpon
59
```
>3.访问限制：将属性名改为：__xxx__

>4.继承和多态：
```
class Animal(object):
	def run(self):
		print 'Animal is running...'
class Dog(Animal):
	def run(self): 
		print 'Dog is running...'
	def eat(self):
		print 'Eating meat... '
class Cat(Animal):
	def run(self):
		print 'Cat is running...'
dog = Dog()
cat = Cat()
dog.run()
dog.eat()
cat.run()
Dog is running...
Eating meat... 
Cat is running...
```

2015.08.03
----------
>1.主要学习了对象编程中的获取对象属性，__slots__,@property,多重继承,以及部分定制类函数

>2.获取对象属性的方法有这几个函数：type(),isinstance(),dir(),在class中可用hasattr(),setattr(),getattr()

>3.__slots__主要用来限制类属性的添加，仅对它所在的类有用，继承类无效，除非在子类中也定义__slots__

>4.@property装饰器主要用来把方法变为属性调用：
```
class Student(object):
	@property    
	def score(self):
	    return self._score
	@score.setter
	def score(self,value):
		if not isinstance(value, int):
			raise ValueError('score must be an integer!')
		if value < 0 or value > 100:
			raise ValueError('score must between 0 ~ 100!')
		self._score = value
s = Student()
s.score = 60
print s.score
s.score = 9999
print s.score
```
>5.多重继承：class Dog(Mammal, RunnableMixin, CarnivorousMixin)

>6.定制类函数：__str__,__iter__,暂且不表

2015.08.04
----------
>1.主要学习了元类，错误处理的几种方式以及调试

>2.元类：定义metaclass，就可以创建类，最后创建实例
```python
class ListMetaclass(type):
	def __new__(cls, name, bases, attrs):
		attrs['add'] = lambda self, value :self.append(value)
		return type.__new__(cls, name, bases, attrs)
class MyList(list):
	__metaclass__ = ListMetaclass    #指示Python解释器在创建MyList时，要通过ListMetaclass.__new__()来创建，在此，我们可以修改类的定义，
                                         比如，加上新的方法，然后，返回修改后的定义
L = MyList()
L.add(1)
print L
l = list()    #普通元类没有add()方法
l.add(1)
print l
[1]
Traceback (most recent call last):
  File "1.py", line 13, in <module>
    l.add(1)
AttributeError: 'list' object has no attribute 'add'
```
>3.ORM:Object Relational Mapping，即对象-关系映射，就是把关系数据库的一行映射为一个对象，也就是一个类对应一个表
```python
#!/usr/bin/env python
# -*- coding: utf-8 -*-
' Simple ORM using metaclass '
__author__ = 'Michael Liao'
class Field(object):
    def __init__(self, name, column_type):
        self.name = name
        self.column_type = column_type
    def __str__(self):
        return '<%s:%s>' % (self.__class__.__name__, self.name)
class StringField(Field):
    def __init__(self, name):
        super(StringField, self).__init__(name, 'varchar(100)')
class IntegerField(Field):
    def __init__(self, name):
        super(IntegerField, self).__init__(name, 'bigint')
class ModelMetaclass(type):
    def __new__(cls, name, bases, attrs):
        if name=='Model':
            return type.__new__(cls, name, bases, attrs)
        print('Found model: %s' % name)
        mappings = dict()
        for k, v in attrs.iteritems():
            if isinstance(v, Field):
                print('Found mapping: %s ==> %s' % (k, v))
                mappings[k] = v
        for k in mappings.iterkeys():
            attrs.pop(k)
        attrs['__mappings__'] = mappings # 保存属性和列的映射关系
        attrs['__table__'] = name # 假设表名和类名一致
        return type.__new__(cls, name, bases, attrs)
class Model(dict):
    __metaclass__ = ModelMetaclass
    def __init__(self, **kw):
        super(Model, self).__init__(**kw)
    def __getattr__(self, key):
        try:
            return self[key]
        except KeyError:
            raise AttributeError(r"'Model' object has no attribute '%s'" % key)
    def __setattr__(self, key, value):
        self[key] = value
    def save(self):
        fields = []
        params = []
        args = []
        for k, v in self.__mappings__.iteritems():
            fields.append(v.name)
            params.append('?')
            args.append(getattr(self, k, None))
        sql = 'insert into %s (%s) values (%s)' % (self.__table__, ','.join(fields), ','.join(params))
        print('SQL: %s' % sql)
        print('ARGS: %s' % str(args))
class User(Model):    #测试代码
    id = IntegerField('uid')
    name = StringField('username')
    email = StringField('email')
    password = StringField('password')
u = User(id=12345, name='Michael', email='test@orm.org', password='my-pwd')
u.save()
```

>4.错误处理方式主要有：
```python
try:
	print 'try...'
	r = 10 / int('a')
	print 'result:', r
except ValueError, e:
	print 'ValueError:', e
except ZeroDivisionError, e:
	print 'ZeroDivisionError', e
else:
	print 'no error!'
finally:
	print 'finally...'
print 'END'
try...
ValueError: invalid literal for int() with base 10: 'a'
finally...
END
```

```
def foo(s):
	return 10 / int(s)
def bar(s):
	return foo(s) * 2
def main():
	bar('0')
main()
Traceback (most recent call last):    
  File "1.py", line 7, in <module>
    main()
  File "1.py", line 6, in main
    bar('0')
  File "1.py", line 4, in bar
    return foo(s) * 2
  File "1.py", line 2, in foo
    return 10 / int(s)
ZeroDivisionError: integer division or modulo by zero
```

```
def foo(s):
	return 10 / int(s)
def bar(s):
	return foo(s) * 2
def main():
	try:
		bar('0')
	except StandardError, e:
		logging.exception(e)
main()
print 'END'
ERROR:root:integer division or modulo by zero
Traceback (most recent call last):
  File "1.py", line 9, in main
    bar('0')
  File "1.py", line 6, in bar
    return foo(s) * 2
  File "1.py", line 4, in foo
    return 10 / int(s)
ZeroDivisionError: integer division or modulo by zero
END
```

>5.调试：print,assert,logging,pdb(命),pdb.set_trace()(命),IDE
```python
import pdb
s = '0'
n = int(s)
pdb.set_trace()    #运行到这里会自动暂停
print 10/n
> /home/SETSUNA/Desktop/1.py(5)<module>()
-> print 10/n
(Pdb) p n    #命令p查看变量
0
(Pdb) c    #命令c继续运行
Traceback (most recent call last):
  File "1.py", line 5, in <module>
    print 10/n
ZeroDivisionError: integer division or modulo by zero
```

