##tensorflow输入和训练

#####占位符

| tf表达式                                     | 使用说明                                   |
| -------------------------------------------- | ------------------------------------------ |
| tf.placeholder(dtype, shape=None, name=None) | 张量插入占位符。 后需要使用feed_dict={K:V} |

#####读：（这个还不知道怎么用的，类下面还有很多的方法）

| tf 表达式                        | 使用说明（一个类，下面还有很多方法）       |
| -------------------------------- | ------------------------------------------ |
| class tf.ReaderBase              | 不同Reader类型的基类，每步生成一条记录。   |
| class tf.TextLineReader          | 返回此阅读器已完成处理的工作单元数。       |
| class tf.WholeFileReader         | 一个Reader，它将文件的全部内容输出为值。   |
| class tf.IdentityReader          | 一个Reader，它将排队的工作作为键和值输出。 |
| class tf.TFRecordR               | 从TFRecords文件输出记录的Reader。          |
| class tf.FixedLengthRecordReader | 一个从文件中输出固定长度记录的Reader。     |

#####转换：

TensorFlow提供了几种操作，可用于将各种数据格式转换为张量。 

**records**：A `Tensor`型`string`。每个字符串都是csv中的记录/行，所有记录都应具有相同的格式。 <br />**record_defaults**：列表`Tensor`：对象与种类`float32`，`int32`，`int64`，`string`。输入记录的每列一个张量，具有该列的标量默认值，如果需要该列，则为空。  <br />**field_delim**：可选`string`。默认为`","`。用于分隔记录中字段的分隔符。  
**name**：操作的名称（可选）。

| tf 表达式                                                    | 使用说明                                  |
| ------------------------------------------------------------ | ----------------------------------------- |
| tf.decode_csv(records, record_defaults, field_delim=None, name=None) | 将CSV记录转换为张量。每列映射到一个张量。 |
| tf.decode_raw(bytes, out_type, little_endian=None, name=None) | 将字符串的字节重新解释为数字向量。        |

#####协议缓冲区示例

**serialized**：一个字符串列表，一批二进制序列化`Example` 原型。 

**names**：字符串列表，序列化protos的名称。  

**sparse_keys**：示例功能中的字符串键列表。这些键的结果将作为`SparseTensor`对象返回。 

 **sparse_types**：`DTypes`与长度相同的列表`sparse_keys`。仅支持`tf.float32`（`FloatList`），`tf.int64`（`Int64List`）和`tf.string`（`BytesList`）。  

**dense_keys**：示例功能中的字符串键列表。这些键的结果将作为`Tensor`s 返回  

**dense_types**：与长度相同的DType列表`dense_keys`。仅支持`tf.float32`（`FloatList`），`tf.int64`（`Int64List`）和`tf.string`（`BytesList`）。  

**dense_defaults**：将字符串键映射到`Tensor`s的dict 。dict的键必须与feature的dense_keys匹配。  

**dense_shapes**：与长度相同的元组列表`dense_keys`。每个密集特征的数据形状由引用`dense_keys`。  

**name**：此操作的名称（可选）

| tf 表达式                                                    | 使用说明            |
| ------------------------------------------------------------ | ------------------- |
| tf.parse_example(serialized, names=None, sparse_keys=None, sparse_types=None, dense_keys=None, dense_types=None, dense_defaults=None, dense_shapes=None, name='ParseExample') | 解析`Example`原型。 |
| tf.parse_single_example(serialized, names=None, sparse_keys=None, sparse_types=None, dense_keys=None, dense_types=None, dense_defaults=None, dense_shapes=None, name='ParseSingleExample') |                     |



#####队列：

| tf 表达式（也是一个类，需要后面在了解） | 使用说明                             |
| --------------------------------------- | ------------------------------------ |
| class tf.QueueBase                      | 队列实现的基类。                     |
| class tf.FIFOQueue                      | 以先进先出顺序使元素出列的队列实现。 |
| class tf.RandomShuffleQueue             | 以随机顺序使元素出列的队列实现。     |

#####处理文件系统

| tf 表达式                             | 使用说明                          |
| ------------------------------------- | --------------------------------- |
| tf.matching_files(pattern, name=None) | 返回与模式匹配的文件集。          |
| tf.read_file(filename, name=None)     | 读取并输出输入文件名的全部内容 。 |

####输入管道

#####输入管道的开头：

**limit**：int32标量张量。  

**num_epochs**：一个整数（可选）。如果指定，则在生成OutOfRange错误之前生成`range_input_producer` 每个整`num_epochs`数倍。如果未指定，则`range_input_producer`可以无限次循环整数。  

**shuffle**：布尔值。如果为真，则整数在每个时期内随机洗牌。  

**seed**：一个整数（可选）。如果shuffle == True，则使用种子。 

**capacity**：一个整数。设置队列容量。 

 **name**：操作的名称（可选）。

| tf 表达式                                                    | 使用说明                                         |
| ------------------------------------------------------------ | ------------------------------------------------ |
| tf.train.match_filenames_once(pattern, name=None)            | 保存匹配模式的文件列表，因此只计算一次。         |
| tf.train.limit_epochs(tensor, num_epochs=None, name=None)    | 返回张量num_epochs次数，然后引发OutOfRange错误。 |
| tf.train.range_input_producer(limit, num_epochs=None, shuffle=True, seed=None, capacity=32,name=None) | 生成队列中从0到限制1的整数                       |
| tf.train.slice_input_producer(tensor_list, num_epochs=None, shuffle=True, seed=None, capacity=32, name=None) | 在tensor_list中生成每个Tensor的切片。            |
| tf.train.string_input_producer(string_tensor, num_epochs=None, shuffle=True, seed=None, capacity=32, name=None) | 将字符串（例如文件名）输出到输入管道的队列。     |

#####在输入管道的末尾进行批处理

**tensor_list**：要排队的张量列表。

**batch_size**：从队列中提取新的批处理大小。

**capacity**：一个整数。队列中的最大元素数。

**min_after_dequeue**：出队后队列中的最小数字元素，用于确保元素的混合程度。

**num_threads**：排队的线程数`tensor_list`。

**seed**：种子用于队列中的随机混洗。

**enqueue_many**：每个张量是否`tensor_list`是一个例子。

**shapes**:(可选）每个示例的形状。默认为推断的形状`tensor_list`。

**name**:(可选）操作的名称。

| tf 表达式                                                    | 使用说明                               |
| ------------------------------------------------------------ | -------------------------------------- |
| tf.train.batch(tensor_list, batch_size, num_threads=1, capacity=32, enqueue_many=False, shapes=None, name=None) | 在中创建批量的张量`tensor_list`。      |
| tf.train.batch_join(tensor_list_list, batch_size, capacity=32, enqueue_many=False, shapes=None, name=None) | 运行张量列表以填充队列以创建批量示例。 |
| tf.train.shuffle_batch(tensor_list, batch_size, capacity, min_after_dequeue, num_threads=1, seed=None, enqueue_many=False, shapes=None, name=None) | 通过随机填充张量创建批次。             |
| tf.train.shuffle_batch_join(tensor_list_list, batch_size, capacity, min_after_dequeue, seed=None, enqueue_many=False, shapes=None, name=None) | 通过随机调整张量来创建批次。           |