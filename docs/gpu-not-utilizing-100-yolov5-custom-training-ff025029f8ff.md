# GPU 未利用 100%的内存(YOLOv5 定制培训)

> 原文：<https://medium.com/nerd-for-tech/gpu-not-utilizing-100-yolov5-custom-training-ff025029f8ff?source=collection_archive---------1----------------------->

在 *之前的(5–10)年，出现了许多新的物体检测模型，每个模型都有自己的优缺点，但直到现在在速度&准确性方面最好的物体检测模型包括 yolov4、yolov5。*

![](img/3cf035908d12dccb2ebe189150669680.png)

**YOLOv5 物体探测**

> 在这篇文章中，我们将集中讨论在 yolov5 的安装和使用中所面临的不同问题，在使用中可以发现许多问题，但我们将讨论下面提到的一些基本问题和大多数用户面临的问题。

```
a) GPU Utilization
b) PyTorch installation
c) No labels found
```

**GPU 利用率:**当我们在定制数据上训练对象检测模型时，我们需要 GPU 来加速训练过程。在 yolov5 的自定义训练中，很多用户都面临着 GPU 利用率的问题。

![](img/fb7b78d9837b2b8299fc11aefe619643.png)

当我们开始培训时，GPU 利用率达到 100%，但在 2-3 分钟后，它下降到 0%。当 CPU (workers)没有正确加载数据集时，就会出现这个问题。在 CPU 加载数据集并将其传递给 GPU 之前，GPU 不会被利用。

> 这个问题的解决方案是，在训练命令中使用(— workers = (cpu 内核)*2)，如果您有 SSD，那么将数据集移动到 SSD，这将更好地利用 gpu。
> 
> 如果你使用的是 windows，使用 num-workers 可能会导致崩溃，问题是多进程 python 将如何在使用 pytorch/Cuda 的 windows 上工作。python 进程每次导入 pytorch 时，都会加载几个包含大量数据的 dll，Windows 甚至会保留未使用的内存。

**PyTorch 安装:** Yolov5 需要一个 PyTorch 来训练/推断定制数据。可以用 yolo V5(requirements . txt)文件安装 torch，但是很多时候不会工作或者只使用 CPU 进行训练/推理。为了更好地利用整个 GPU，您可以从[**py torch**](https://pytorch.org/)**网站安装 torch。**

****未找到标签:**此错误主要出现在 python 脚本无法访问数据文件夹时。您可以通过尝试下面提到的步骤来解决此错误。**

```
if you are giving path to train directory, replace it with second method by creating train.txt file (which includes all training images path) & move all labels inside images folder 
```

**标注时也会出现上述错误。不会为新的定型删除缓存，因为代码将检查(标签。缓存)已经存在于 training 文件夹中，则它不会创建新文件。所以如果你的训练在 label 创建后被打断。缓存文件然后在开始新的训练之前删除它。**

> ****注:**以上是许多人面临的一些重要而普遍的问题。尽管如此，还是有很多问题可以在不同的场景中找到，你可以直接在 [yolov5 问题论坛](https://github.com/ultralytics/yolov5/issues)上发表你的问题。**

****关于我:****

**我有超过 1 年的软件开发工作经验。目前，我是一名软件工程师，通过使用零售分析、建立大数据分析工具、创建和维护模型以及加入引人注目的新数据集，为我们的客户改进产品和服务。之前，我是 Spark 基金会的计算机视觉实习生，在那里我体验了来自不同开源平台(如 kaggle、google images、open images 等)的视觉数据分析。)，并在该数据上训练不同的深度学习模型。**

*   **[*在 LinkedIn 上和我联系*](https://www.linkedin.com/in/muhammadrizwanmunawar/)**
*   **[*与我协商*](https://www.upwork.com/services/product/consultation-1477666319161577472?ref=project_share)**
*   **[*我的 yolov5 服务*](https://www.upwork.com/services/product/you-will-get-image-classification-projects-using-machine-learning-with-python-1323963101029052416?ref=project_share)**

*****如有任何问题，欢迎在下方评论*****