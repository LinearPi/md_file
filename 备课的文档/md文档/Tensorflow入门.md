## Tensorflow入门 (2个小时的课程)

###1. Tensorflow计算模型--计算图

​	Tensorflow的tensor（张量）flow（流），它直观表达张量之间通过计算相互转化的过程。

​	可以设置一个计算图，TensorBoard来显示。

![a+b](images\a+b.png)  

​										  a + b 



 

​	 `添加一个a+b`的图片，使用TensorBoard计算出一个，我们就可 以看着这个图表来显示相对应的计算图

​	计算图的使用：

```python
import tensorflow as tf

# 定义两个变量
a = tf.Variable(100, name="a")
b = tf.Variable(200, name="b")
# 添加一个函数
add = tf.add(a, b, name='add') 
# 初始化所有的变量
init = tf.initialize_all_variables()
# 创建一个会话
sess = tf.Session()
# 开始对tensorflow进行使用run函数进行使用相对应的操作
sess.run(init)
sess.run(add)
# 关闭会话，释放资源
sess.close()

# 生产一个写日志的writer， 并将当前的tensorflow计算图写入日志
writer = tf.summary.FileWriter("log/add.log",sess.graph)
writer.close()
```



###2.Tensorflow数据模型--张量

​	从tensorflow的名字就可以看出张量（tensor）就是一个很重要的概念，在tensorflow程序中，所有的数据都通过张量的形式来表示。从功能的角度上来看，张量可以被简单理解为多组数组。

其中 `零阶张量`叫做`标量`，就是一个数，

`一阶张量`叫做`向量`，就是一个一维数组，

`二阶张量`叫做`矩阵`，就是一个二维数组，

`三阶张量`以上的才可以成为`张量`，

| 阶   | 数学实例             | Python例子                                                   |
| ---- | -------------------- | ------------------------------------------------------------ |
| 0    | 标量（只有大小）     | s = 123                                                      |
| 1    | 向量（有大小和方向） | v = [1.1, 2.2, 3.3]                                          |
| 2    | 矩阵（数据表）       | m = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]                        |
| 3    | 张量（数据立体）     | t = [[[2], [4], [6]], [[8], [10], [12]], [[14], [16], [18]]] |
| n    | n阶                  | ......                                                       |

把数学写入tensorflow

| 数学         | Tensorflow代码 |
| ------------ | -------------- |
| 标量（一维） | tf.Variable()  |
| 向量（二维） | tf.            |
|              |                |
|              |                |
|              |                |
|              |                |

 定义常量，同时把数据类型定义为能够进行GPU计算的tf.float32.

tf.constant(1, dtype=tf.floaf32)

 定义可以训练的变量，

tf.Variable(2, dtype=tf.float32)



​	

###3.Tensorflow运行模型--回话

​	

​	