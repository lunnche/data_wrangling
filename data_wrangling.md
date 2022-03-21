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



