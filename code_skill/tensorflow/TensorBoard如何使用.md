# TensorBoard如何使用



在写好tensorflow的代码之后，

在给命名的前面加上

with tf.name_scope('名字')：

​	原来的代码，缩进4个空格.





最后要加上一句

writer = tf.summary.FileWriter("log/simple_example.log",sess.graph)

