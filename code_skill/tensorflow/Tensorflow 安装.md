##Tensorflow 安装

首先安装anaconda里面 安装最新版本的anaconda
网址:  https://www.anaconda.com/download/
选择最新版本的下载即可
安装完成之后就可以使用, 在某个文件夹shift+鼠标右键,选择
打开cmd窗口, 输入 jupyter notebook 就可以进去
在anaconda navigator 里面安装 vscode, 可以非常方便的打开文档
进入anaconda prompt 然后创建新的环境和安装相应的模块

```
OS X 或 Linux
运行下列命令来配置开发环境

conda create -n tensorflow python=3.6
source activate tensorflow
conda install pandas matplotlib jupyter notebook scipy scikit-learn
conda install -c conda-forge tensorflow
```
```
Windows
Windows系统，在你的 console 或者 Anaconda shell 界面，运行

conda create -n tensorflow python=3.6
conda activate tensorflow
conda install pandas matplotlib jupyter notebook scipy scikit-learn
conda install -c conda-forge tensorflow
```
安装需要花点时间
如果下载的时候比较慢的话,可以使用蓝灯来进行加速.
测试  Hello, world!
在 Python console 下运行下列代码，检测 TensorFlow 是否正确安装。如果安装正确，Console 会打印出 "Hello, world!"。现在还不需要理解这段代码做了什么，你会在下一节学到。
```python
import tensorflow as tf

# Create TensorFlow object called tensor
hello_constant = tf.constant('Hello World!')

with tf.Session() as sess:
    # Run the tf.constant operation in the session
    output = sess.run(hello_constant)
    print(output)
```
在虚拟环境里面配置好,
在页面的时候如果要使用虚拟环境 
需要安装一个模块   conda install ipykernel  
需要找到jupyter notebook的配置文件
打开Anaconda安装目录下的etc文件如：D:\Anaconda\etc\jupyter  我的安装目录在D:\Anaconda,
再打开jupyter_notebook_config.json文件作如下修改即可： 

```javastrip
{
  "NotebookApp": {
    "nbserver_extensions": {
      "jupyterlab": true
    },
    "notebook_dir" : "D:\\Anaconda\\envs\\tensorflow"
  }
}
```
在需要使用jupyter notebook的文件夹 使用cmd进入虚拟环境之后, 进入jupyter notebook 就可以去如到浏览器里面,在浏览器上就会显示相关的虚拟环境,  下面是命令
``` 
cd ..目标目录
activate 虚拟环境的名字
jupyter notebook
```