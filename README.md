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
> *0.格式有些乱，不，是很乱，所以，你就讲究着看把，我没力气改了，马蛋的MD文档，用你妹的html语法啊，就不能安安静静的做个不用费神的文档吗！
> *1.主要做了Python高级特性——切片，迭代，列表生成式，生成器&高阶函数中map/reduce,filter,sorted这三个函数的笔记
> *2.切片：主要应用于list和tuple.list切片：
              list:S=['China','Japan','USA','UK'],S[:3],S[-2:],S[1:3];
              tuple:（'China','Japan','USA','UK'）[1:3]
> *3.迭代：主要通过for循环来遍历list和tuple中的元素.
```
S={'A':1,'B':2,'C':3,'D':4};
for k,v in S.iteritems():
	print k ,v
A 1
C 3
B 2
D 4
```
> *4.列表生成式：主要形式是[表达式 for循环]
```
print [n * (n+1) for n in range(1,10)]
[2, 6, 12, 20, 30, 42, 56, 72, 90]
```
> *5.生成器:有两种方式，一种是将[]变成(),生成器中的元素需要通过for循环遍历出来，第二种是中while循环中将print换成yield
```
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
> *6.map():接收两个参数，一个是函数，一个是列表,基本表现形式就是：def f(x);map(f(x),list)</br>
> *7.reduce():比较麻烦些，通式为：reduce(f, [x1, x2, x3, x4]) = f(f(f(x1, x2), x3), x4)，用法类似于map，传入函数跟list</br>
> *8.filter():过滤列表中的元素，用法同样是接收函数跟list,过滤符合函数中的列表元素</br>
> *9.sorted():对列表进行排序，也可以自定义添加函数来定义排序规则</br>




