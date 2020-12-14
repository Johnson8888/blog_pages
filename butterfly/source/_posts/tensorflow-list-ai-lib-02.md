---
title: 细数最流行的人工智能、深度学习常用框架，不止有TensorFlow，Java也可以进行人工智能开发
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2020-12-14 16:19:53
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_10_10_python_artificial_intelligence.png
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_10_10_python_artificial_intelligence.png
tags: 
    - 人工智能
    - Anaconda
    - conda
    - TensorFlow
categories:
keywords:
description: 人工智能是计算机科学的一个分支，它企图了解智能的实质，并生产出一种新的能以人类智能相似的方式做出反应的智能机器，该领域的研究包括机器人、语言识别、图像识别、自然语言处理和专家系统等。
photos:
fileName:
type:
---

作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)

###  人工智能
人工智能是计算机科学的一个分支，它企图了解智能的实质，并生产出一种新的能以人类智能相似的方式做出反应的智能机器，该领域的研究包括机器人、语言识别、图像识别、自然语言处理和专家系统等。人工智能从诞生以来，理论和技术日益成熟，应用领域也不断扩大，可以设想，未来人工智能带来的科技产品，将会是人类智慧的“容器”。人工智能可以对人的意识、思维的信息过程的模拟。人工智能不是人的智能，但能像人那样思考、也可能超过人的智能。那让我们来看一下都有哪些人工智能开发的框框。


### Theano
![2020_12_14_list_ai_theano](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_12_14_list_ai_theano.jpg)
早在2007加拿大的蒙特利尔大学就开始了[Theano](https://github.com/Theano/Theano)的开发，它最初是为了用于学术研究而设计的。虽然出身于学术界，但是在过去很长一段时间里面，Theano都是深度学习开发与研究的行业标准。
Theano其实是一个比较底层的库，它比较适合数值计算和优化。支持自动函数梯度计算，支持Python接口，并且集成了Numpy。它并不只是专门用来做深度学习的，可以说Theano是Python的一个数值计算库。它也有缺点，就是不支持GPU和水平扩展。
由于TensorFlow在谷歌的支持下强势崛起，Theano可以说是日渐式微，这里面的有个标志性的事件就是Theano创始人之一Ian Goodfellow，他放弃了Theano转去Google开发TensorFlow。


### Caffe
![2020_11_14_list_ai_caffe](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_11_14_list_ai_caffe.png)
[Caffe](https://github.com/facebookarchive/caffe2)是由就读于加州大学伯克利分校的中国籍博士生**贾扬清**在2013年创建的，是一个老牌框架。
贾扬清本科和硕士都是清华毕业，他对两个深度学习的框架都有贡献，一个是TensorFlow，他以前是在Google工作。在2016年贾扬清加入到Facebook，开始了Caffe框架的开发。
Caffe的全称是"Convolution Architecture For Feature Extraction"，意思是能用于特征提取的卷积架构，它的设计初衷其实是为了针对计算机视觉。缺点是灵活性不足的问题，为了做模型调整会用到C++和CUDA。
在2017年4月，Facebook发布了Caffe2，这标志着Caffe有了一个很大的发展。我们可以把它看作是对Caffe更细粒度的重构，在实用的基础上增加了扩展性和灵活性。随着时间的发展，Facebook最后把Caffe2合并到了PyTorch上面了。

### PyTorch 
![2020_12_14_list_ai_pytorch](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_12_14_list_ai_pytorch.png)
说[PyTorch](https://pytorch.org/)之前，我们得先说一说Torch。Torch是一个非主流的深度学习框架，它是基于Lua语言的。而现在主流的深度学习框架使用的语言基本都是Python，所以用Torch就会显得很非主流。但是Facebook的人工智能研究所使用的就是Torch，Torch非常适用于卷积神经网络，同时它的灵活度也很高。  
有一个特点就是：它是命令式的，支持动态模型。大多数的机器学习框架都是支持静态图模型，也就是说在进行调试时，我们需要先把模型定义好，然后再进行运行和计算。而Torch它的灵活度更高，它可以在运行的过程中更改图模型，这就叫做支持动态的图模型。在2017年初，Facebook在Torch的基础上，发布了一个全新的机器学习框架叫PyTorch。PyTorch可以说是Torch的Python版，增加了很多特性。
2018年4月Facebook宣布将Caffe2并入PyTorch，所以说Caffe2就以PyTorch的形式存在。

### MXNet 
![2020_11_14_list_ai_mxnet](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_11_14_list_ai_mxnet.png)
[MXNet](https://mxnet.apache.org/versions/1.7.0/)是亚马逊它支持的深度学习框架。MXNet尝试把两种模式无缝的结合起来，一种是在命令式编程上提供张量运算，一种是在声明式的编程支持符号表达式。这样用户就可以自由的混合来实现他们自己的想法。也就是说，它结合了静态定义计算图和动态定义计算图的优势。另外MXNet支持的语言种类也比较多，除了常见的想Python还有C++，关键的他对R语音也支持的很好，对Go也有支持。但是它的学习曲线会比较高。

### CNTK
![2020_11_14_list_ai_cntk](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_11_14_list_ai_cntk.png)
[CNTK](https://github.com/microsoft/CNTK)又名：Microsoft Cognitive Toolkit。在2016年的微软宣布在给github上开源CNTK(computational Network ToolKit)。CNTK对语音和图像支持特别好，语音识别和图像识别也比较快。它还有着更为强大的可扩展性，开发者可以使用多台计算机去实现GPU的扩展，从而能够更加灵活地应对大规模的实验。当然它也支持支持C#语言。

### Keras 
![2020_11_14_list_ai_keras](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_11_14_list_ai_keras.png)
[Keras](https://keras.io/)是一个高级封装的库，同样也非常的受欢迎。它可以跟Theano、CNTK、TensorFlow结合起来工作。它相当于架设在这些框架上的更高一层，因为更高一层，这使得它的使用非常的简单。Keras强调的就是极简主义，你只需要几行代码就能构建一个神经网络。同样它号称为支持快速实验而生，能够把你的想法的迅速转换成为结果。它的语法的也比较明细，文档的也提供的非常好。当然了，它也是支持Python的。

### DL4J
![2020_11_14_list_ai_dl4j](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_11_14_list_ai_dl4j.png)
[DJF4](https://github.com/deeplearning4j)是一个基于JVM，聚焦行业应用，而且提供商业支持的分布式的深度学习框架。它的宗旨就是：在合理的时间里去解决各类涉及大量数据的问题。
从它的名字上不难看出，它其实是 Deep Learning For Java 的缩写，它对Java的支持是它最大的特点。它对使用Java作为开发语言的开发者来说非常友好，它可以与Hadoop和Spark很好的结合起来，也可以使用任意数量的GPU或者CPU运行。

### Chainer 
![2020_11_14_list_ai_chainer](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_11_14_list_ai_chainer.png)
[Chainer](https://chainer.org/)的是一个专门为高效研究和开发深度学习算法而设计的开源框架，它也是基于Python的深度学习框架。Chanier在"实时"使构件计算图，"边运行边定义"的方法使得构建深度学习网络的变得很灵活。也就是说，Chanier是支持动态图定义的。那这种方法可以让用户在每次迭代的时候可以根据条件去更改计算图，也很容易使用标准的调试器和分析器来调试和重构。

### PaddlePaddle
![2020_11_14_list_ai_paddle](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_11_14_list_ai_paddle.jpg)
[PaddlePaddle](https://www.paddlepaddle.org.cn/)是百度旗下的深度学习开源平台，它支持并行分布式深度学习。在2016年9月1日百度世界大会上，当时百度的首席科学家吴恩达宣布：百度的深度学习平台将对外开放，命名为PaddlePaddle。吴恩达认为PaddlePaddle比一个PaddleP要更容易让人记住，事实上也是，PaddlePaddle 比 Paddle更容易上口。百度的资深科学家，PaddlePaddle的研发负责人徐伟介绍：在PaddlePaddle的帮助下，深度学习模型的设计如同编写伪代码一样容易，工程师只需要关注模型的高层结构，而无需担心任何琐碎的底层问题。

### TensorFlow
![2020_11_14_list_ai_tensorflow](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_11_14_list_ai_tensorflow.jpg)
[TensorFlow](https://github.com/tensorflow/tensorflow)A machine learning platform for everyone to solve real problems。对每个人来解决现实问题的机器学习平台，这也是TensorFlow存在的宗旨。它不但在上层支持神经网络，它还很全面的支持别的机器学习的算法，像K-Means，决策树，向量积等等。它对语言的支持也很多，Python、C++、Java。在硬件层面，它也可以利用CPU，GPU进行计算。
另外的谷歌还出了专门的处理器，叫TPU，也就是Tensor处理器，另外它也支持在移动端使用。还提供了一个叫[TensorBoard](https://www.tensorflow.org/tensorboard?hl=zh-cn)的可视化工具。这个工具非常强大，它可以基于运行的一些日志和文件，可视化得把模型训练和结果展现出来。  
TensorFlow提供了不同层次的接口，从低层到高层。越低的层次越灵活，越容易去控制，越高层次是越容易使用。
TensorFlow支持的语言也非常多：Go、Python、C++、Java、Swift、R语音、C#、js等。
还有运行在Web端的TensorFlow.js，我们可以使用Javascript在网页端进行机器学习的训练和使用。在移动端同样提供支持的是TensorFlowLite，我们可以把在服务器端训练好的模型下发到移动端(Android、iOS、树莓派等)，在移动端通过TensorFlowLite来使用。


***
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)


