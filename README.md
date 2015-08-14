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

2015.08.05
----------
>1.主要学习了IO编程，其中包括文件读写，操作文件与目录以及序列化
>2.文件读写：
```
>>> f = open('/home/SETSUNA/Desktop/1.txt', 'r')    #r表示读
>>> f.read()    #read()读取内容
'Soft kitty, warm kitty, little ball of fur. \nHappy kitty, sleepy kitty, purr purr purr.'
>>>f.close()    #close()来关闭文件
```
with方式：
```
with open('/home/SETSUNA/Desktop/1.txt', 'r') as f :     #避免了f.close()出错
	print f.read()
Soft kitty, warm kitty, little ball of fur.
Happy kitty, sleepy kitty, purr purr purr.
```

转码：
```
import codecs    #codecs帮助自动转码
f = open('/home/SETSUNA/Desktop/1.txt', 'r')
with codecs.open('/home/SETSUNA/Desktop/1.txt', 'r', 'utf-8'):
	print f.read()
```

写文件：
```
import codecs    #自动转码
f = open('/home/SETSUNA/Desktop/1.txt', 'r')
with codecs.open('/home/SETSUNA/Desktop/1.txt', 'w', 'utf-8') as f:
	f.write('Small Kitty')
```

>3.操作文件与目录
```
>>> import os
>>> os.path.abspath('.')    #查看当前目录的绝对路径
'/home/SETSUNA'
>>> os.path.join('/home/SETSUNA', 'test')    #在某个目录下创建一个新目录，首先把新目录的完整路径表示出来
'/home/SETSUNA/test'
>>> os.mkdir('/home/SETSUNA/test')    #创建test目录
>>> os.rmdir('/home/SETSUNA/test')    #删除test目录
```

>4.pickel
```
>>> import pickle
>>> d = dict(name = 'Bob', age = 20, score = 88)
>>> pickle.dumps(d)    #pickle.dumps()方法把任意对象序列化成一个str
"(dp0\nS'age'\np1\nI20\nsS'score'\np2\nI88\nsS'name'\np3\nS'Bob'\np4\ns."
>>> f = open('dump.txt', 'wb')    #pickle.dump()把对象序列化后写入一个file-like Object
>>> pickle.dump(d, f)
>>> f.close()
>>> f = open('dump.txt', 'rb')
>>> d = pickle.load(f)    #pickle.loads()方法反序列化出对象
>>> f.close()
>>> d    #这个变量和原来的变量是完全不相干的对象，它们只是内容相同而已
{'age': 20, 'score': 88, 'name': 'Bob'}
```

>5.JSON
```
import json
class Student(object):
	def __init__(self, name, age,score):
		self.name = name
		self.age = age
		self.score = score
def student2dict(std):
		return {
		'name' : std.name ,
		'age' : std.age ,
		'score' : std.score
		}
s = Student('Bob', 20 , 88)
print(json.dumps(s, default = student2dict))
print(json.dumps(s, default=lambda obj: obj.__dict__))    #推荐！把任意class的实例变为dict,通常class的实例都有一个__dict__属性，它就是一个dict，用来存储实例变量.
                                                           也有少数例外，比如定义了__slots__的class
{"age": 20, "score": 88, "name": "Bob"}
{"age": 20, "score": 88, "name": "Bob"}
```

2015.08.06
----------
>1.主要学习了多进程，多线程，ThreadLocal,以及分布式进程

>2.多进程主要有两种：fork(),multiprocessing,Pool()
```
import os    #fork():普通的函数调用，调用一次，返回一次，fork()调用一次，返回两次，操作系统自动把当前进程（称为父进程）复制了一份（称为子进程），分别在父进程和子进程内返回
print 'Process (%s) start...' % os.getpid()
pid = os.fork() 
if pid == 0:
	print 'I am child process (%s) and my parent is %s.' % (os.getpid(), os.getppid())
else :
	print 'I (%s) just created a child process (%s).' % (os.getpid(), pid)
Process (20965) start...
I (20965) just created a child process (20966).
I am child process (20966) and my parent is 20965.
```

```
from multiprocessing import Process    #multiprocessing模块就是跨平台版本的多进程模块
import os
def run_proc(name):
	print 'Run child process %s (%s)... ' % (name, os.getpid())
if __name__ == '__main__' :
	print 'Parent process %s.' % os.getpid()
	p = Process(target = run_proc, args = ('test',))
	print 'Process will start.'
	p.start()    #用start()方法启动
	p.join()    #join()方法可以等待子进程结束后再继续往下运行，通常用于进程间的同步
	print 'Process end.'

Parent process 7792.
Process will start.
Run child process test (7793)... 
Process end.
```

```
from multiprocessing import Pool
import os, time, random
def long_time_task(name):
	print 'Run task %s (%s)... ' % (name, os.getpid())
	start = time.time()
	time.sleep(random.random() * 3)
	end = time.time()
	print 'Task %s runs %0.2f seconds.' % (name, (end-start))

if __name__ == '__main__' :
	print 'Parent process %s.' % os.getpid()
	p = Pool()    #由于Pool的默认大小是CPU的核数，如果Pool(5),则同时运行5个进程
	for i in range(5):
		p.apply_async(long_time_task, args = (i, ))
	print 'Waiting for all subprocess done...'
	p.close()
	p.join()
	print 'All subprocess done.'	

Parent process 8120.
Waiting for all subprocess done...
Run task 0 (8121)... 
Run task 1 (8122)... 
Run task 2 (8123)... 
Run task 3 (8124)... 
Task 2 runs 1.12 seconds.
Run task 4 (8123)... 
Task 0 runs 1.51 seconds.
Task 3 runs 1.61 seconds.
Task 1 runs 2.48 seconds.
Task 4 runs 2.73 seconds.
All subprocess done.
```

```
from multiprocessing import Process , Queue    #进程间通信
import os, time , random
def write(q):
	for value in ['A', 'B', 'C'] :
		print 'Put %s to queue...' % value
		q.put(value)
		time.sleep(random.random())
def read(q):
	while True:
		value = q.get(True)
		print 'Get %s from queue.' % value
if __name__ == '__main__':
	q = Queue()
	pw = Process(target = write, args = (q, ))
	pr = Process(target = read, args = (q, ))
	pw.start()
	pr.start()
	pw.join()
	pr.terminate()
Put A to queue...
Get A from queue.
Put B to queue...
Get B from queue.
Put C to queue...
Get C from queue.
```

>3.多线程：threading, Lock
```
import time, threading
def loop():
	print 'thread %s is running...' % threading.current_thread().name    #current_thread()函数，它永远返回当前线程的实例
	n = 0
	while n < 5 :
		n = n + 1
		print 'thread %s >>> %s ' % (threading.current_thread().name, n)
		time.sleep(1)
	print 'thread %s ended.' % threading.current_thread().name
print 'thread %s is running...' % threading.current_thread().name
t = threading.Thread(target = loop, name = 'LoopThread')
t.start()
t.join()
print 'thread %s ended.' % threading.current_thread().name	
thread MainThread is running...
thread LoopThread is running...
thread LoopThread >>> 1 
thread LoopThread >>> 2 
thread LoopThread >>> 3 
thread LoopThread >>> 4 
thread LoopThread >>> 5 
thread LoopThread ended.
thread MainThread ended.
```

```
import time , threading
balance = 0
lock = threading.Lock()
def change_it(n):
	global balance
	balance = balance + n 
	balance = balance - n
def run_thread(n):
	for i in range(100000):
		lock.aquire()
		try:
			change_it(n)
		finally:
			lock.release()
		
t1 = threading.Thread(target = run_thread, args = (5, ))
t2 = threading.Thread(target = run_thread, args = (8, ))
t1.start()
t2.start()
t1.join()
t2.join()
print balance
```

>4.ThreadLocal
```
import threading
local_school = threading.local()
def process_student():
	print 'Hello, %s (in %s)' % (local_school.student, threading.current_thread().name)
def process_thread(name):
	local_school.student = name
	process_student()
t1 = threading.Thread(target = process_thread, args = ('Alice', ), name = 'Thread-A')
t2 = threading.Thread(target = process_thread, args = ('Bob', ), name = 'Thread-B')
t1.start()
t2.start()
t1.join()
t2.join()
Hello, Alice (in Thread-A)
Hello, Bob (in Thread-B)
```

>5.进程与线程：不表

2015.08.07
----------
>今天基本没干什么，就回顾了，所以就不上传什么东西了

2015.08.08
----------
>1.主要学习了正则表达式以及几个常用内建模块的学习
>2.正则表达式：
<li>用\d可以匹配一个数字，\w可以匹配一个字母或数字</li>
<li>.可以匹配任意字符</li>
<li>用*表示任意个字符（包括0个），用+表示至少一个字符，用?表示0个或1个字符，用{n}表示n个字符，用{n,m}表示n-m个字符</li>
<li>用[]表示范围</li>
<li>A|B可以匹配A或B，所以[P|p]ython可以匹配'Python'或者'python'.</li>
<li>^表示行的开头，^\d表示必须以数字开头.</li>
<li>$表示行的结束，\d$表示必须以数字结束.</li>
>3.re模块：
```
import re
test = raw_input('Please enter sth to use:')
if re.match(r'^\d{3}\-\d{3,8}$', test ):    #使用r前缀，不用考虑转义的问题
	print 'OK'
else:
	print 'Failed'
Please enter sth to use:011-4657984
OK
```

```
>>> import re
>>> re.match(r'^(\d+)(0*)$', '102300').groups()
('102300', '')
>>> re.match(r'^(\d+?)(0*)$', '102300').groups()    #加个?就可以让\d+采用非贪婪匹配
('1023', '00')
```
>4.collections:
```
from collections import namedtuple    #namedtuple
Point = namedtuple('Point', ['x', 'y'])
p = Point(1, 2)
print p.x
print p.y
print isinstance(p, Point)
print isinstance(p, tuple)
1
2
True
True
```

```
from collections import deque    #deque
q = deque (['a', 'b', 'c'])
q.append('x')
q.appendleft('y')
print q
deque(['y', 'a', 'b', 'c', 'x'])
```

```
from collections import defaultdict    #defaultdict
dd = defaultdict(lambda : 'N/A')
dd['key1'] = 'abc'
print dd['key1']
print dd['key2']
abc
N/A
```

```
from collections import OrderedDict    #OrderedDict
d = dict([('a', 1), ('b', 2), ('c', 3)])
print d
od = OrderedDict([('a', 1), ('b', 2), ('c', 3)])
print od
{'a': 1, 'c': 3, 'b': 2}
OrderedDict([('a', 1), ('b', 2), ('c', 3)])
```

```
from collections import Counter    #Counter
c = Counter()
for ch in 'programming':
	c[ch] = c[ch] + 1
print c
Counter({'g': 2, 'm': 2, 'r': 2, 'a': 1, 'i': 1, 'o': 1, 'n': 1, 'p': 1})
```

>5.base64:准备一个包含64个字符的数组,对二进制数据进行处理，每3个字节一组，一共是3x8=24bit，划为4组，每组正好6个bit,得到4个数字作为索引，然后查表，获得相应的4个字符，就是编码后的字符串,Base64编码会把3字节的二进制数据编码为4字节的文本数据，长度增加33%，好处是编码后的文本数据可以在邮件正文、网页等直接显示.
```
import base64
print base64.b64encode('binary\x00string')
print base64.b64decode('YmluYXJ5AHN0cmluZw==')
YmluYXJ5AHN0cmluZw==
binarystring 
```

>6.struct:解决str和其他二进制数据类型的转换
```
>>> import struct
>>> struct.pack('>I', 10240099)    #pack的第一个参数是处理指令，'>I'：，>表示字节顺序是big-endian，也就是网络序，I表示4字节无符号整数，后面的参数个数要和处理指令一致
'\x00\x9c@c'
>>> struct.unpack('>IH', '\xf0\xf0\xf0\xf0\x80\x80')    #>IH的说明，后面的str依次变为I：4字节无符号整数和H：2字节无符号整数
(4042322160, 32896)
```

>7.hashlib:通过摘要函数f()对任意长度的数据data计算出固定长度的摘要digest，目的是为了发现原始数据是否被人篡改过.
```
import hashlib    #MD5是最常见的摘要算法，速度很快，生成结果是固定的128 bit字节，通常用一个32位的16进制字符串表示
md5 = hashlib.md5()
md5.update('how to use md5 in python hashlib')    #若数据量较大，可分割，如md5.update('how to use md5 in ')\md5.update('python hashlib?')
print md5.hexdigest()
846014c3556d79e878be15fde5426e8a
```
```
import hashlib    #SHA1的结果是160 bit字节，通常用一个40位的16进制字符串表示
sha1 = hashlib.sha1()
sha1.update('how to use sha1 in python hashlib')
print sha1.hexdigest()
e9282e41aaf5ef53fd4ca3c191ed1e2546dbf3f2
```

>8.itertools:count(),cycle(),repeat(),groupby(),chain(),imap()这些个函数基本都是用来迭代运算的

2015.08.09
----------
>整个大脑处于当机状态，折腾图形库今天，由于升级把Tkinter GUI没跟现在的python链接起来，懒得折腾了，学学看QT的使用......

2015.08.10
----------
>花了一天时间安装软件，PyQt5安装失败，PyQt4安装成功，但在编写程序时导入QtGui失败，后通过PyCharm导入py程序图形界面运行成功，希望安装Eric6，但死在了前一步QScintilla2的安装上，我操啊，一整天啊，现在整个人都处于相当不好的状态......

2015.08.11
----------
>1.主要看了下TCP/IP，Email收发邮件编写，以及数据库的简单应用
>2.TCP编程：
```
import socket , time, threading     #服务器端
def tcplink(sock, addr):
	print 'Accept new connection from %s:%s...' % addr
	sock.send('Welcome!')
	while True:
		data = sock.recv(1024)
		time.sleep(1)
		if data == 'exit' or not data:
			break
		sock.send('Hello, %s!' % data)
	sock.close()
	print 'Connection from %s:%s clsoed.' % addr
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.bind(('127.0.0.1', 9999))
s.listen(5)
print 'Waiting for connection...'
while True:
	sock, addr = s.accept()
	t = threading.Thread(target = tcplink, args = (sock, addr))
	t.start()
import socket    #客户端
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect(('127.0.0.1', 9999))
print s.recv(1024)
for data in ['Michael', 'Tracy', 'Sarah']:
	s.send(data)
	print s.recv(1024)
s.send('exit')
s.close()
Waiting for connection...    #服务器端运行
Accept new connection from 127.0.0.1:35985...
Connection from 127.0.0.1:35985 clsoed.
Welcome!    #客户端运行
Hello, Michael!
Hello, Tracy!
Hello, Sarah!
```
>3.UDP编程：
```
import socket, time    #服务器端
s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)    #SOCK_DGRAM指定了这个Socket的类型是UDP
s.bind(('127.0.0.1', 9999))    #UDP的9999端口与TCP的9999端口可以各自绑定，绑定端口和TCP一样，但是不需要调用listen()方法，而是直接接收来自任何客户端的数据
print 'Bind UDP  on 9999...'
while True:
	data, addr = s.recvfrom(1024)
	print 'Received from %s:%s.' % addr
	s.sendto('Hello , %s!' % data, addr)
import socket    #客户端
s =socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
for data in ['Michael', 'Tracy', 'Sarah']:
	s.sendto(data, ('127.0.0.1', 9999))    #不需要调用connect()，直接通过sendto()给服务器发数据
	print s.recv(1024)
s.close()
Bind UDP  on 9999...    #服务器端运行
Received from 127.0.0.1:42136.
Received from 127.0.0.1:42136.
Received from 127.0.0.1:42136.
Hello , Michael!    #客户端运行
Hello , Tracy!
Hello , Sarah!
```

>4.要编写程序来发送和接收邮件，本质上就是：1.编写MUA把邮件发到MTA，2.编写MUA从MDA上收邮件

发邮件时，MUA和MTA使用的协议就是SMTP：Simple Mail Transfer Protocol，后面的MTA到另一个MTA也是用SMTP协议

收邮件时，MUA和MDA使用的协议有两种：POP：Post Office Protocol，目前版本是3，俗称POP3；IMAP：Internet Message Access Protocol，目前版本是4，优点是不但能取邮件，还可以直接操作MDA上存储的邮件，比如从收件箱移到垃圾箱，等等

>5.SQLite3
```
import sqlite3
conn = sqlite3.connect('test.db')    #数据库文件是test.db,如果文件不存在，会自动在当前目录创建
cursor = conn.cursor()    #创建一个Cursor
print cursor.execute('create table user (id varchar(20) primary key, name varchar(20))')    #执行一条SQL语句，创建user表
print cursor.execute('insert into user (id, name) values (\'1\', \'Michael\')')    #继续执行一条SQL语句，插入一条记录
print cursor.rowcount    #通过rowcount获得插入的行数
cursor.close()
conn.commit()    #提交事务
conn.close()    #关闭Connection
conn = sqlite3.connect('test.db')    #查询记录
cursor = conn.cursor()
print cursor.execute('select * from user where id=?', '1')    #执行查询语句
values = cursor.fetchall()    #获得查询结果集
print values
cursor.close()
conn.close()
<sqlite3.Cursor object at 0x7f7205bda810>
<sqlite3.Cursor object at 0x7f7205bda810>
1
<sqlite3.Cursor object at 0x7f7205bda880>
[(u'1', u'Michael')]
```

2015.08.12
----------
>1.主要学习了HTTP协议，WSGI接口，FLASK，以及Jinja2，gevent，完成了Python教程基础知识的笔记任务
>2.HTTP请求：
<p>步骤1：浏览器首先向服务器发送HTTP请求，请求包括：</p>
<p>方法：GET还是POST，GET仅请求资源，POST会附带用户数据；</p>
<p>路径：/full/url/path；</p>
<p>域名：由Host头指定：Host: www.sina.com.cn</p>
<p>以及其他相关的Header；</p>
<p>如果是POST，那么请求还包括一个Body，包含用户数据.</p>
<p>步骤2：服务器向浏览器返回HTTP响应，响应包括：</p>
<p>响应代码：200表示成功，3xx表示重定向，4xx表示客户端发送的请求有错误，5xx表示服务器端处理时发生了错误；</p>
<p>响应类型：由Content-Type指定；</p>
<p>以及其他相关的Header；</p>
<p>通常服务器的HTTP响应会携带内容，也就是有一个Body，包含响应的内容，网页的HTML源码就在Body中.</p>
<p>步骤3：如果浏览器还需要继续向服务器请求其他资源，比如图片，就再次发出HTTP请求，重复步骤1、2.</p>

>3.WSGI接口：
```
def application(environ, start_response):    #hello.py
    start_response('200 OK', [('Content-Type', 'text/html')])
    return '<h1>Hello, web!</h1>'
from wsgiref.simple_server import make_server    #server.py
from hello import application
httpd = make_server('', 8000, application)    # 创建一个服务器，IP地址为空，端口是8000，处理函数是application
print "Serving HTTP on port 8000..."
httpd.serve_forever() 
[SETSUNA@localhost Desktop]$ python server.py
Serving HTTP on port 8000...
127.0.0.1 - - [12/Aug/2015 18:35:28] "GET / HTTP/1.1" 200 20
127.0.0.1 - - [12/Aug/2015 18:35:28] "GET /favicon.ico HTTP/1.1" 200 20
```

>4.WEB框架：
```
from flask import Flask    #app.py
from flask import request
app = Flask(__name__)
@app.route('/', methods = ['GET', 'POST'])
def home():
	return '<h1>Home</h1>'
@app.route('/signin', methods = ['GET'])
def signin_form():
	return '''<form action="/signin" method = "post">
	<p><input name = "username"></p>
	<p><input name = "password" type = "password"></p>
	<p><button type = "submit">Sign In</button></p>
	</form>'''
@app.route('/signin', methods = ['POST'] )
def signin():
	if request.form['username'] == 'admin' and request.form['password'] == 'password':
		return '<h3>Hello ,admin!</h3>'
	return '<h3>Bad username or password.</h3>'
if __name__ == '__main__':
	app.run()
[SETSUNA@localhost Desktop]$ sudo python app.py
[sudo] password for SETSUNA: 
 * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)    #浏览器中输入http://localhost:5000/，显示Home
127.0.0.1 - - [12/Aug/2015 19:02:46] "GET / HTTP/1.1" 200 -
127.0.0.1 - - [12/Aug/2015 19:02:46] "GET /favicon.ico HTTP/1.1" 404 -    #以上两行为输入第一个地址后终端中所显示
127.0.0.1 - - [12/Aug/2015 19:02:58] "GET /signin HTTP/1.1" 200 -    #输入http://localhost:5000/signin后终端中显示，浏览器中出现输入登录和密码对话框
127.0.0.1 - - [12/Aug/2015 19:03:18] "POST /signin HTTP/1.1" 200 -    #正确输入admin,password后显示
```

>5.Jinja2模板：
```
from flask import Flask, request, render_template    #app.py
app = Flask(__name__)
@app.route('/', methods = ['GET', 'POST'])
def home():
	return render_template('home.html')
@app.route('/signin', methods = ['GET'])
def signin_form():
	return render_template('form.html')
@app.route('/signin', methods = ['POST'] )
def signin():
	username = request.form['username']
	password = request.form['password']
	if username == 'admin' and password == 'password':
		return render_template('signin-ok.html', username = username)
	return render_template('form.html', message = 'Bad username or password', username = username)
if __name__ == '__main__':
	app.run()
<!DOCTYPE html>    #home.html
<html>
<head>
	<title>Home</title>
</head>
<body>
	<h1 style="font-style:italic">Home</h1>
</body>
</html>
<!DOCTYPE html>    #form.html
<html>
<head>
	<title>Please Sign In</title>
</head>
<body>
	{% if message %}
	<p style="color:red">{{message}}</p>
	{% endif %}
	<form action="/signin" method="post">
		<legend>Please sign in:</legend>
		<p><input name="username" placeholder="Username" value="{{username}}"></p>
		<p><input name="password" placeholder="Password" type="password"></p>
		<p><button type="submit">Sign In</button></p>
	</form>
</body>
</html>
<!DOCTYPE html>    #signin-ok.html
<html>
<head>
	<title>Welcome, {{username}}</title>
</head>
<body>
	<p>Welcome,{{username}}!</p>
</body>
</html>
[SETSUNA@localhost Desktop]$ sudo python app.py
[sudo] password for SETSUNA: 
 * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
127.0.0.1 - - [12/Aug/2015 19:49:06] "GET / HTTP/1.1" 200 -    #浏览器中输入http://127.0.0.1:5000/，显示Home
127.0.0.1 - - [12/Aug/2015 19:50:04] "GET /signin HTTP/1.1" 200 -    #输入http://127.0.0.1:5000/signin，显示登录框
127.0.0.1 - - [12/Aug/2015 19:50:39] "POST /signin HTTP/1.1" 200 -    #输入form的admin,password后显示Welcome,admin!
```

>6.gevent:
```
from gevent import monkey;monkey.patch_all()
import gevent
import urllib2
def f(url):
	print('GET: %s' % url)
	resp = urllib2.urlopen(url)
	data = resp.read()
	print('%d bytes received from %s.' % (len(data), url))
gevent.joinall([
	gevent.spawn(f, 'https://www.python.org/'),
	gevent.spawn(f, 'https://www.yahoo.com/'),
	gevent.spawn(f, 'https://github.com/'),
])
[SETSUNA@localhost Desktop]$ sudo python app.py    #3个网络操作是并发执行的，而且结束顺序不同，但只有一个线程
GET: https://www.python.org/
GET: https://www.yahoo.com/
GET: https://github.com/
47067 bytes received from https://www.python.org/.
282652 bytes received from https://www.yahoo.com/.
18189 bytes received from https://github.com/.
```

2015.08.13
----------
>今天状态不佳，没做什么工作，简单的看了下thinkpython这本书，英文教材，写的挺简单的，可以看看......

2015.08.14
----------
>爬虫主要涉及到python的基础知识，urllib,urllib2,cookielib,re等几个库/模块的使用，正则表达式，以及框架Scrapy的使用

>简单爬虫的一般形式：
```
import urllib
import urllib2
url = 'http://...........'
values = {'username':'*****', 'password':'*****'}    #适合配合cookie访问网站
user_agent = 'Mozila/4.0(compatible; MSIE 5.5; Windows NT)'    #设置用户代理，以便cheat网站
headers = {'User-Agent': user_agent, 'Referer':'http://.........'}    #Referer用来防盗链重定向用
data = urllib.encode(values)    #urllib库的用处基本就这个，将字典里的ky编码转换保存到变量中供后面使用
request = urllib2.Request(url, data, headers)    #模拟浏览器访问请求网站
response = urllib2.urlopen(request, timeout)    #传入之前的请求值及响应时间用以打开网站
print response.read()
```

>使用cookie文件模拟登录网站例子：
```
import urllib
import urllib2
import cookielib
filename = 'cookie.txt'
cookie = cookielib.MozillaCookieJar(filename)
opener = urllib2.build_opener(urllib2.HTTPCookieProcessor(cookie))
postdata = urllib.urlencode({
	'stuid':'201200131012',
              'pwd':'23342321'
	})
loginUrl = 'http://jwxt.sdu.edu.cn:7890/pls/wwwbks/bks_login2.login'
result = opener.open(loginUrl, postdata)
cookie.save(ignore_discard = True, ignore_expires = True)
gradeUrl = 'http://jwxt.sdu.edu.cn:7890/pls/wwwbks/bkscjcx.curscopre'
result = opener.open(gradeUrl)
print result.read()
```
