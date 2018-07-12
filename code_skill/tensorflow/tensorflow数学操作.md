### tensorflow数学操作

tensorflow数学操作代码，说明，数据类型

##### 算术运算符：

| tf 数学运算符号        | 数学说明 | 说明       |
| ---------------------- | -------- | ---------- |
| tf.add(x,y, name=None) | x + y    | y,x同类型  |
| tf.sub(x,y, name=None) | x - y    | y,x同类型  |
| tf.mul(x,y, name=None) | x * y    | y,x同类型  |
| tf.div(x,y, name=None) | x / y    | y,x同类型  |
| tf.mod(x,y, name=None) | 除法余数 | 只能是整型 |

##### tf基本数学函数：

| tf.表达式                   | 数学说明                                                |
| --------------------------- | ------------------------------------------------------- |
| tf.add_n(inputs, name=None) | 明智地添加所有输入张量元素 (inputs是一个同类型的数据组) |
| tf.abs(x, name=None)        | 计算张量的绝对值。  即：$y=|x|$                         |
| tf.neg(x, name=None)        | 按元素计算数值负值。 即： $y=-x$                        |
| tf.sign(x, name=None)       | 数字符号的元素指示 y : -1 x<0 elif 0 x=0 else 1 0<x     |
| tf.inv(x, name=None)        | x元素的倒数 ,即 : $y = 1/x$                             |
| tf.square(x, name=None)     | x元素的平方 ,即：$y=x*x=x^2$                            |
| tf.round(x, name=None)      | 张量的值按元素方式舍入为最接近的整数 (4舍5入)           |
| tf.sqrt(x, name=None)       | 开根$ \sqrt x$                                          |
| tf.rsqrt(x, name=None)      | 开跟的倒数 $ \frac 1 {\sqrt x}$                         |
| tf.pow(x, y, name=None)     | 幂运算 $x^y$  y,x同类型                                 |
| tf.exp(x, name=None)        | 指数运算  $y=e^x$                                       |
| tf.log(x, name=None)        | 对数 $\log(x)$                                          |
| tf.ceil(x, name=None)       | 返回不小于x的元素方向最小整数  1.1 -->  2               |
| tf.floor(x, name=None)      | 返回不大于x的元素方向最大整数  1.1 --> 1                |
| tf.maximum(x, y, name=None) | 返回x和y的最大值                                        |
| tf.minimum(x, y, name=None) | 返回x和y的最小值                                        |
| tf.cos(x, name=None)        | 计算x元素的cos ，即： $\cos(x)$                         |
| tf.sin(x, name=None)        | 计算x元素的sin ，即： **$\sin(x)$**                     |

##### 矩阵数学函数：

| tf.表达式                                                    | 数学说明                           |
| ------------------------------------------------------------ | ---------------------------------- |
| tf.diag(diagonal, name=None)                                 | 返回具有给定对角线值的对角线张量。 |
| tf.transpose(a, perm=None, name='transpose')                 | 矩阵转置，prem=[]                  |
| tf.matmul(a, b, transpose_a=False, transpose_b=False, a_is_sparse=False, b_is_sparse=False, name=None) |                                    |
| tf.batch_matmul(x, y, adj_x=None, adj_y=None, name=None)     |                                    |
| tf.matrix_determinant(input, name=None)                      |                                    |
| tf.batch_matrix_determinant(input, name=None)                |                                    |
| tf.matrix_inverse(input, name=None)                          |                                    |
| tf.batch_matrix_inverse(input, name=None)                    |                                    |
| tf.cholesky(input, name=None)                                |                                    |
| tf.batch_cholesky(input, name=None)                          |                                    |

##### 复数函数：

tf.complex(real, imag, name=None)
tf.complex_abs(x, name=None)
tf.conj(in_, name=None)
tf.imag(in_, name=None)
tf.real(in_, name=None)

##### 减少：

tf.reduce_sum(input_tensor, reduction_indices=None, keep_dims=False, name=None)
tf.reduce_prod(input_tensor, reduction_indices=None, keep_dims=False, name=None)
tf.reduce_min(input_tensor, reduction_indices=None, keep_dims=False, name=None)
tf.reduce_max(input_tensor, reduction_indices=None, keep_dims=False, name=None)
tf.reduce_mean(input_tensor, reduction_indices=None, keep_dims=False, name=None)
tf.reduce_all(input_tensor, reduction_indices=None, keep_dims=False, name=None)
tf.reduce_any(input_tensor, reduction_indices=None, keep_dims=False, name=None)
tf.accumulate_n(inputs, shape=None, tensor_dtype=None, name=None)



##### 分割：

tf.segment_sum(data, segment_ids, name=None)
tf.segment_prod(data, segment_ids, name=None)
tf.segment_min(data, segment_ids, name=None)
tf.segment_max(data, segment_ids, name=None)
tf.segment_mean(data, segment_ids, name=None)
tf.unsorted_segment_sum(data, segment_ids, num_segments, name=None)
tf.sparse_segment_sum(data, indices, segment_ids, name=None)
tf.sparse_segment_mean(data, indices, segment_ids, name=None)





##### 序列比较和索引:

tf.argmin(input, dimension, name=None)
tf.argmax(input, dimension, name=None)
tf.listdiff(x, y, name=None)
tf.where(input, name=None)
tf.unique(x, name=None)
tf.edit_distance(hypothesis, truth, normalize=True, name='edit_distance')
tf.invert_permutation(x, name=None)