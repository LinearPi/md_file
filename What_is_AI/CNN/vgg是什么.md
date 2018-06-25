##vgg是什么

VGG-Net同样也是一种CNN，它来自 Andrew Zisserman 教授的组 (Oxford)，VGG-Net 在2014年的 ILSVRC localization and classification 两个问题上分别取得了第一名和第二名，VGG-Net不同于AlexNet的地方是：VGG-Net使用更多的层，通常有16－19层，而AlexNet只有8层。另外一个不同的地方是：VGG-Net的所有 convolutional layer 使用同样大小的 convolutional filter，大小为 3 x 3。



基本结构A：

Input（224,224,3）→64F（3,3,3,1）→max-p(2,2)→128F（3,3,64,1）→max-p(2,2) →256F（3,3,128,1）→256F（3,3,256,1）→max-p(2,2)→512F（3,3,256,1）→512F（3,3,512,1）→max-p(2,2)→512F（3,3,256,1）→512F（3,3,512,1）→max-p(2,2)→4096fc→4096fc→1000softmax



