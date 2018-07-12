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

`三阶张量`以上的才可以成为`张量`，  一个tensorflow的数据有3个属性（数据的阶，形状，数据类型）

| 阶   | 数学实例             | Python例子                                                   |
| ---- | -------------------- | ------------------------------------------------------------ |
| 0    | 标量（只有大小）     | s = 123                                                      |
| 1    | 向量（有大小和方向） | v = [1.1, 2.2, 3.3]                                          |
| 2    | 矩阵（数据表）       | m = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]                        |
| 3    | 张量（数据立体）     | t = [[[2], [4], [6]], [[8], [10], [12]], [[14], [16], [18]]] |
| n    | n阶                  | ......                                                       |

数据形状：

| 阶   | 形状             | 维数 | 实例                                |
| ---- | ---------------- | ---- | ----------------------------------- |
| 0    | []               | 0-d  | 一个0维张量。一个纯量。             |
| 1    | [D0]             | 1-d  | 一个1维张量的形式[5]。              |
| 2    | [D0，D1]         | 2-d  | 一个2维张量的形式[3,4]。            |
| 3    | [D0，D1，D2]     | 3-d  | 一个3维张量的形式[1,4,3]。          |
| ñ    | [D0，D1，... Dn] | ND   | 一个n维张量的形式[D0，D1，... Dn]。 |

形状可以通过Python中的整数列表或元祖（int list or tuples）来表示。

数据类型：

| 数据类型       | Python类型     | 描述                                                 |
| -------------- | -------------- | ---------------------------------------------------- |
| `DT_FLOAT`     | `tf.float32`   | 32位浮点数。                                         |
| `DT_DOUBLE`    | `tf.float64`   | 64位浮点数。                                         |
| `DT_INT64`     | `tf.int64`     | 64位有符号整型。                                     |
| `DT_INT32`     | `tf.int32`     | 32位有符号整型。                                     |
| `DT_INT16`     | `tf.int16`     | 16位有符号整型。                                     |
| `DT_INT8`      | `tf.int8`      | 8位有符号整型。                                      |
| `DT_UINT8`     | `tf.uint8`     | 8位无符号整型。                                      |
| `DT_STRING`    | `tf.string`    | 可变长度的字节数组。每一个张量元素都是一个字节数组。 |
| `DT_BOOL`      | `tf.bool`      | 布尔型。                                             |
| `DT_COMPLEX64` | `tf.complex64` | 由两个32位浮点数组成的复数：实数和虚数。             |
| `DT_QINT32`    | `tf.qint32`    | 用于量化行动的32位有符号整型。                       |
| `DT_QINT8`     | `tf.qint8`     | 用于量化行动的8位有符号整型。                        |
| `DT_QUINT8`    | `tf.quint8`    | 用于量化行动的8位无符号整型。                        |

 定义常量，同时把数据类型定义为能够进行GPU计算的tf.float32.

tf.constant(1, dtype=tf.floaf32)

 定义可以训练的变量，

tf.Variable(2, dtype=tf.float32)	

###3.Tensorflow运行模型--会话

​	tensorflow.Session()

前面已经有了计划图，和数据类型了。

tensorflow的使用就是在刚开始的是把计算的过程设计好， 把数据类型设计好，最后在使用session.run(计算图)，这样才会真的执行tensorflow。在运行之前需要把数据都初始化。



​	