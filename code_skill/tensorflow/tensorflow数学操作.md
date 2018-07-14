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
| tf.abs(x, name=None)        | 计算张量的绝对值。  即：$y=                             |
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

| tf.表达式                                                    | 数学说明                                                     |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| tf.diag(diagonal, name=None)                                 | 返回具有给定对角线值的对角线张量。                           |
| tf.transpose(a, perm=None, name='transpose')                 | 矩阵转置，prem=[]转置                                        |
| tf.matmul(a, b, transpose_a=False, transpose_b=False, a_is_sparse=False, b_is_sparse=False, name=None) | ab点乘，注意ab的shape大小                                    |
| tf.batch_matmul(x, y, adj_x=None, adj_y=None, name=None)     | 将批量的两个张量相互叠加， x和y的大小一致                    |
| tf.matrix_determinant(input, name=None)                      | 计算方阵的行列式。 $D=\left|   \begin{array}{lcr}    a_1 & b_1 \\    a_2 & b_2 \end{array}     \right|=a_1b_2-a_2b_1$ |
| tf.batch_matrix_determinant(input, name=None)                | 计算一批方阵的行列式。                                       |
| tf.matrix_inverse(input, name=None)                          | 计算平方可逆矩阵的倒数。检查可逆性。                         |
| tf.batch_matrix_inverse(input, name=None)                    | 计算平方可逆矩阵的逆。检查可逆性。                           |
| tf.cholesky(input, name=None)                                | 计算方阵的Cholesky分解。                                     |
| tf.batch_cholesky(input, name=None)                          | 计算一批方阵的Cholesky分解。                                 |

##### 复数函数：

| Tf.表达式                         | 数学说明                        |
| --------------------------------- | ------------------------------- |
| tf.complex(real, imag, name=None) | 将两个实数转换为复数            |
| tf.complex_abs(x, name=None)      | $a+bj$ , $\sqrt{a^2+b^2}$       |
| tf.conj(in_, name=None)           | 返回复数的复共轭  $a+bj>>a-bj $ |
| tf.imag(in_, name=None)           | 返回复数的虚部。                |
| tf.real(in_, name=None            | 返回复数的实部。                |

##### 减少：

 TensorFlow提供了几个操作，您可以使用这些操作执行常见的数学计算，从而减少张量的各个维度。 

| tf表达式                                                     | 数学说明                                                     |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| tf.reduce_sum(input_tensor, reduction_indices=None, keep_dims=False, name=None) <br /> **reduction_indices**：要减少的尺寸 <br /> **keep_dims**：如果为true | 计算张量维度的元素总和 <br />x= [[1, 1, 1]],[1, 1, 1]] <br />tf.reduce_sum(x) ==> 6<br />tf.reduce_sum(x, 0) ==> [2, 2, 2] <br />tf.reduce_sum(x, 1) ==> [3, 3] <br />tf.reduce_sum(x, 1, keep_dims=True) ==> [[3], [3]] tf.reduce_sum(x, [0, 1]) ==> 6 |
| tf.reduce_prod(input_tensor, reduction_indices=None, keep_dims=False, name=None) | 计算跨张量尺寸的元素乘积。                                   |
| tf.reduce_min(input_tensor, reduction_indices=None, keep_dims=False, name=None) | 计算张量维度的最小元素。                                     |
| tf.reduce_max(input_tensor, reduction_indices=None, keep_dims=False, name=None) | 计算张量维度的元素最大值。                                   |
| tf.reduce_mean(input_tensor, reduction_indices=None, keep_dims=False, name=None) | 计算张量维度的元素平均值。                                   |
| tf.reduce_all(input_tensor, reduction_indices=None, keep_dims=False, name=None) | 计算张量维度的元素的“逻辑和”。                               |
| tf.reduce_any(input_tensor, reduction_indices=None, keep_dims=False, name=None) | 计算张量维度的“逻辑或”元素。                                 |
| tf.accumulate_n(inputs, shape=None, tensor_dtype=None, name=None) | 返回张量列表的元素和。                                       |

##### 分割：

TensorFlow提供了几个可用于在张量段上执行常见数学计算的操作。这里，分割是沿着第一维度的张量的分割，即，它定义从第一维度到第一维度的映射 `segment_ids`。的`segment_ids`张量应该是第一尺寸的大小，`d0`与在范围内的连续的ID `0`到`k`，在那里`k<d0`。特别地，矩阵张量的分段是行到段的映射。 

![SegmentSum](images\SegmentSum.png)

| tf表达式                                                     | 数学说明                   |
| ------------------------------------------------------------ | -------------------------- |
| tf.segment_sum(data, segment_ids, name=None)                 | 计算张量段的总和 。        |
| tf.segment_prod(data, segment_ids, name=None)                | 计算张量段乘积。           |
| tf.segment_min(data, segment_ids, name=None)                 | 计算张量段的最小值。       |
| tf.segment_max(data, segment_ids, name=None)                 | 计算张量段的最大值 。      |
| tf.segment_mean(data, segment_ids, name=None)                | 计算张量段的平均值。       |
| tf.unsorted_segment_sum(data, segment_ids, num_segments, name=None) | 计算张量段的总和。         |
| tf.sparse_segment_sum(data, indices, segment_ids, name=None) | 计算张量的稀疏段的总和。   |
| tf.sparse_segment_mean(data, indices, segment_ids, name=None) | 计算张量的稀疏段的平均值。 |

##### 序列比较和索引:

| tf表达式                                                     | 数学说明                          |
| ------------------------------------------------------------ | --------------------------------- |
| tf.argmin(input, dimension(尺寸), name=None)                 | 返回张量维度中具有最小值的索引。  |
| tf.argmax(input, dimension, name=None)                       | 返回张量维度上具有最大值的索引 。 |
| tf.listdiff(x, y, name=None)                                 | 计算两个数字列表之间的差异。      |
| tf.where(input, name=None)                                   | 返回布尔张量中的真值的位置。      |
| tf.unique(x, name=None)                                      | 在1-D张量中找到独特的元素。       |
| tf.edit_distance(hypothesis, truth, normalize=True, name='edit_distance') | 计算序列之间的Levenshtein距离。   |
| tf.invert_permutation(x, name=None)                          | 计算张量的逆置换。                |

