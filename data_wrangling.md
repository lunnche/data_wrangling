## data wrangling with pandas,numpy and ipython

问号的三种用法

1.自省
在变量后使用问号，可以显示对象的信息  

2.使用双问号，会显示函数源码

3.问号还有个用途，就是像Unix或Windows命令行一样搜索IPython的命名空间。字符与通配符结合可 以匹配所有的名字。例如，我们可以获得所有包含load的顶级NumPy命名空间：

```python
In [13]: np.*load*?
np.__loader__
np.load
np.loads
np.loadtxt
np.pkload
```


## `%run命令`

可以用于运行所有的Python程序

用`%load`可以将脚本导入到一个代码格中

## 中断运行的代码

`Ctrl-c'

## 从剪贴板执行程序

`%paste`
`%cpaste`

使用`%cpaste`,会多给出一条提示，可以粘贴任意多的代码再运行。你可能想在运行前，先看看代码。如果粘贴了错误的代码，可以用`Ctrl-c`中断。  

`%paste`和`cpaste`在ipython里用，jupyter notebook 里用不着  

## 魔术命令

如`%timeit`测量任何Python语句，例如矩阵乘法的执行时间

魔术命令可以被看做IPython中运行的命令行。许多魔术命令有”命令行“选项，可以通过？查看：
```python
%debug?
```

魔术函数默认可以不用百分号，只要没有变量和函数名相同。这个特点被称为“自动魔术”，可以 用 %automagic 打开或关闭。

一些魔术函数与Python函数很像，它的结果可以赋值给一个变量
```python
In [22]: %pwd 
Out[22]: '/home/wesm/code/pydata-book

In [23]: foo = %pwd

In [24]: foo Out[24]: '/home/wesm/code/pydata-book'
```


IPython的文档可以在shell中打开，我建议你用 %quickref 或 %magic 学习下所有特殊命令。表2-2 列出了一些可以提高生产率的交互计算和Python开发的IPython指令。

![image-20220321143230909](https://raw.githubusercontent.com/lunnche/picgo-image/main/image-20220321143230909.png)

## 集成Matplotlib

看这个区别

```python
a = [1,2,3]
b = a
a.append(4)
b
```

结果是[1,2,3,4]
但改成这样：
```python
a = [1,2,3]
b = a
a = [1,2,3,4]
b
```
结果是[1,2,3]

为啥 a 改变了引用,a和b指向的不是同一个对象了  


来看这个惊人的🌰

```python
def append_element(some_list,element):
    some_list.append(element)

In:data = [1,2,3]
In:append_element(data,4)

In:data
Out:[1,2,3,4]

函数把原本的参数给改变了


编写可以接受多种输入类型的函数。常见的栗子是编写一个函数可以接受任意类型的序列（list,tuple,ndarray)或是迭代器。你可以先检验对象是否是列表（或是NUmPy数组），如果不是的话，将其转变成列表：
```python
if not isinstance(x,list) and isiterable(x):
    x = list(x)
```

isiterable(x)的定义:
```python
def isiterable(obj):
    try:
        iter(obj)
        return True
    except TypeError: # not iterable
        return False
```


记住，可以修改一个对象并不意味就要修改它。这被称为副作用。例如，当写一个函数，任何副作 用都要在文档或注释中写明。如果可能的话，我推荐避免副作用，采用不可变的方式，即使要用到 可变对象。

对于有换行符的字符串，可以使用三引号，'''或"""都行：

```python
c = """

This is a longer string that spans multiple lines """
```

反斜杠是转义字符，意思是它备用来表示特殊字符，比如换行符\n或Unicode字符。要写一个包含 反斜杠的字符串，需要进行转义：
```python
In: s = '12\\34'
In: prints(s)
12\34
```


如果字符串中包含许多反斜杠，但没有特殊字符，这样做就很麻烦。幸好，可以在字符串前面加一 个r，表明字符就是它自身：
```python
In [69]: s = r'this\has\no\special\characters'

In [70]: s Out[70]: 'this\\has\\no\\special\\characters'
```

字符串的模板化或格式化,字符串对象有format方法，

该看while了 第45页
