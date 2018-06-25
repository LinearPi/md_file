##matplotlib使用

```python
import matplotlib.pyplot as plt
plt.subplot(231)     #（nrows*ncols*plot_number ) = (2*3*[1 - 6])  2和3 就是现实的小图的每层的数量
plt.imshow(x_train[0], cmap=plt.get_cmap('gray'))

plt.imshow(输入层, cmap=plt.get_cmap('gray'))
```



