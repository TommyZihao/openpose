<div align="center">
    <img src=".github/Logo_main_black.png", width="300">
</div>



> 为了便于中国软件开发者学习研究人体姿态识别、贡献代码，特翻译README文件。
>
> 向卡耐基梅隆大学大学的开发者以及本项目其他贡献者致敬。
>
> 英译汉：同济大学开源软件协会 Tommy
>
> In order to facilitate Chinese software developers to learn, use Openpose, make progress in human gesture recognition development and source code contributions, we translated README file into simplified Chinese.
>
> Salute to the developers in Carnegie Mellon university and the contributors to this project.
>
> translattor: Tommy in Tongji Univerisity Opensource Association 



------

| **`Linux`**                                                  |
| ------------------------------------------------------------ |
| [![Build Status](https://travis-ci.org/CMU-Perceptual-Computing-Lab/openpose.svg?branch=master)](https://travis-ci.org/CMU-Perceptual-Computing-Lab/openpose) |

[OpenPose](https://github.com/CMU-Perceptual-Computing-Lab/openpose) 是 **世界上首个在单张图片中识别人体躯干、手、脸部共135个关键点的多人实时识别系统**.

<p align="center">
    <img src="doc/media/pose_face_hands.gif", width="480">
</p>

## 特点

- **功能**:
  - **二维多人关键点实时识别**:
    - **15、18或 25个身体/脚部的关键点识别，运算时间与检测出的人数无关**。
    - **2*21个手部关键点识别。目前，运算时间取决于检测出的人数**。
    - **70个面部关键点的识别。目前，运算时间取决于检测出的人数**
  - **三维单关键点实时识别**:
    - 通过多个单一角度的视频进行三角测量。
    - 菲力尔品牌摄像机的视频同步处理。
    - 与Flir摄像机和Point Grey摄像机兼容，提供了C++语言的代码样本，用户可以自定义输入。
  - **校准工具**:
    - 能够对摄像机拍摄中出现的扭曲等内外参数进行简易评估。
  - 针对未来的加速优化和视觉流畅，增加了**单人位置追踪** 。
- **输入**: 图片、视频、网络摄像头的视频流、Flir或Point Grey和IP摄像机。项目提供了C++语言的代码样本，用户可以自定义输入。
- **输出**: 原有图片+关键点展示（PNG、JPG、AVI等格式），关键点数据存储文件（(JSON, XML, YML等格式）。
- **操作系统**: Ubuntu (14, 16), Windows (8, 10), Mac OSX, Nvidia TX2.
- **其它**:
  - 项目提供: 命令行测试、C++封装、C++ API接口。
  - CUDA (Nvidia GPU), OpenCL (AMD GPU), and CPU 版本。



## 最近更新

- Sep 2018: [**单人位置追踪测试**](doc/quick_start.md#tracking) 增加处理速度，观看体验更加流畅！
- Jun 2018: [**躯干、脚部联合检测的模型发布！速度加快40%，精确度增加5%**](doc/installation.md)!
- Jun 2018: [**Python API接口**](doc/modules/python_module.md)发布!
- Jun 2018: [**OpenCL/AMD 显卡版本**](doc/installation.md) 发布!
- Jun 2018: [**校准工具**](doc/modules/calibration_module.md) 发布!
- Jun 2018: [**Mac OSX 版本(CPU)**](doc/installation.md) 发布!
- Mar 2018: [**CPU 版本**](doc/installation.md#cpu-version)!
- Mar 2018: [**三维关键点重建模型**](doc/modules/3d_reconstruction_module.md) (从多个摄像机角度识别)!

更多信息可访问 [全部更新文档](doc/released_features.md) 以及 [版本更新记录](doc/release_notes.md).



## 效果

### 躯干、脚部识别

<p align="center">
    <img src="doc/media/dance_foot.gif", width="360">
</p>

### 躯干、脸部、手部识别

<p align="center">
    <img src="doc/media/pose_face.gif", width="360">
</p>

### 人体姿态三维重建

<p align="center">
    <img src="doc/media/openpose3d.gif", width="360">
</p>

### 身体、手指关键点识别

<p align="center">
    <img src="doc/media/pose_hands.gif", width="360">
</p>

### 身体识别

<p align="center">
    <img src="doc/media/dance.gif", width="360">
</p>



## 内容

1. [特点](#特点)
2. [最近更新](#最近更新)
3. [效果](#效果)
4. [安装、重装、卸载](#安装、重装、卸载)
5. [快速启动](#快速启动)
6. [输出](#输出)
7. [增加运算速度以及基准测试](#增加运算速度以及基准测试)
8. [向我们提供出错信息和反馈！](#向我们提供出错信息和反馈！)
9. [作者和项目贡献者](#作者和项目贡献者)
10. [引用](#引用)
11. [授权协议](#授权协议)



## 安装、重装、卸载

**Windows能用的版本**: 点击[所有版本](https://github.com/CMU-Perceptual-Computing-Lab/openpose/releases) 下载最新的版本即可。

或者，你也可以点击 [安装文档](doc/installation.md) 查看通过源代码编译安装的安装指南。



## 快速启动

大部分用户不需要调用OpenPose的C++和Python的开发接口，这些用户只需要运行OpenPose Demo即可

- **OpenPose Demo**: 为了便于处理图片、视频或者网络摄像头的视频流，并展示和后处理结果，你需要看[doc/demo_overview.md](doc/demo_overview.md). 例如，你可以直接通过以下命令在Ubuntu操作系统上处理一个视频。

```
# Ubuntu
./build/examples/openpose/openpose.bin --video examples/media/video.avi
:: Windows - Portable Demo
bin\OpenPoseDemo.exe --video examples\media\video.avi
```

- **校准工具**: 三维的OpenPose处理和其它立体视觉处理任务需要你便捷校准摄像机，可查看 [doc/modules/calibration_module.md](doc/modules/calibration_module.md)文档。
- **OpenPose C++ API**: 如果你想定制开发读取特定内容的接口、增加个性定制的后处理功能或者展示存储功能，点击这个链接查看C++的API接口，[examples/tutorial_api_cpp/](examples/tutorial_api_cpp/) 和 [doc/library_introduction.md](doc/library_introduction.md)。你可以增加自己的代码[examples/user_code/](examples/user_code/) 使用Cmake快速编译整个项目。快速增加自己定制的代码，看这个文档：[examples/user_code/README.md](examples/user_code/README.md) 
- **OpenPose Python API**: 类似C++的API接口，点击文档查看Python API的教程[examples/tutorial_api_python/](examples/tutorial_api_python/).
- **增加额外的模块**:查看 [doc/library_add_new_module.md](./doc/library_add_new_module.md).
- **独立的脸部和手指检测**:
  - **脸部** 不对身体关键点进行识别，**仅对**脸部关键点识别：如果你想加快处理速度（同时也会减少识别脸的个数），请看OpenCV脸部识别文档：[doc/standalone_face_or_hand_keypoint_detector.md](doc/standalone_face_or_hand_keypoint_detector.md).
  - **使用你自己的脸部和手部识别工具**: 与身体关键点识别不同，你可以使用你自己的脸部和手部识别工具。比方说，在手指能看清但身体看不清的时候使用（OpenPose的识别器不能正常工作）。查看文档[doc/standalone_face_or_hand_keypoint_detector.md](doc/standalone_face_or_hand_keypoint_detector.md).



## 输出

请点击这个文档，查看输出文件的格式、关键点数据结构等信息。[doc/output.md](doc/output.md).



## 增加运算速度以及基准测试

点击这个文档，查看增加运行速度、减少内存需求的提示 [doc/faq.md#speed-up-memory-reduction-and-benchmark](doc/faq.md#speed-up-memory-reduction-and-benchmark).



## 向我们提供出错信息和反馈！

我们的代码库面向以科学研究为目的开发者开源，我们希望持续不断地优化它！所以，如果出现了以下情况，请及时向我们反馈。

1. ... 你发现OpenPose处理图片或视频出错，请把识别失败的案例发到openposecmu@gmail.com邮箱中，我们会运用你提供的信息优化我们的算法。
2. ... 你发现了软件功能或者运行速度上的bug。
3. ... 你增加了一些我们可能吸纳到项目源代码中的函数、类或者其它子类。
4. ... 你知道如何针对本项目优化性能、提升检测速度。
5. ... 你发现本项目的一个潜在应用场景。
6. ... 其它问题.

你可以在Github上评论，或者pull request你的新代码，我们会尽快回复你的。如果你基于本项目做了有趣的开发或者录制了Youtube视频，请给我们发电子邮件。



## 作者和项目贡献者

Openpose项目由 [Gines Hidalgo](https://www.gineshidalgo.com/), [Zhe Cao](http://www.andrew.cmu.edu/user/zhecao), [Tomas Simon](http://www.cs.cmu.edu/~tsimon/), [Shih-En Wei](https://scholar.google.com/citations?user=sFQD3k4AAAAJ&hl=en), [Hanbyul Joo](http://www.cs.cmu.edu/~hanbyulj/), 和 [Yaser Sheikh](http://www.cs.cmu.edu/~yaser/)创造发起。 目前，这个项目由 [Gines Hidalgo](https://www.gineshidalgo.com/) 和 [Yaadhav Raaj](https://www.linkedin.com/in/yaadhavraaj)进行日常维护。  [original CVPR 2017 repo](https://github.com/ZheC/Multi-Person-Pose-Estimation) 包括了Matlab和Python版本，以及模型训练代码。人体姿态评估方面的工作是基于 [the original ECCV 2016 demo](https://github.com/CMU-Perceptual-Computing-Lab/caffe_rtpose)的。

除此之外，不可或缺的还有 [CMU Panoptic Studio dataset](http://domedb.perception.cs.cmu.edu/)。

我们还想感谢所有帮助过OpenPose项目的人，主要贡献者列在了这个文档里[doc/contributors.md](doc/contributors.md)。



## 引用

如果本项目帮助了你的研究，请在你发表的作品里注明引用出处（人脸关键点识别与[Simon et al. 2017]使用了同样的训练方法）。

```
@inproceedings{cao2017realtime,
  author = {Zhe Cao and Tomas Simon and Shih-En Wei and Yaser Sheikh},
  booktitle = {CVPR},
  title = {Realtime Multi-Person 2D Pose Estimation using Part Affinity Fields},
  year = {2017}
}

@inproceedings{simon2017hand,
  author = {Tomas Simon and Hanbyul Joo and Iain Matthews and Yaser Sheikh},
  booktitle = {CVPR},
  title = {Hand Keypoint Detection in Single Images using Multiview Bootstrapping},
  year = {2017}
}

@inproceedings{wei2016cpm,
  author = {Shih-En Wei and Varun Ramakrishna and Takeo Kanade and Yaser Sheikh},
  booktitle = {CVPR},
  title = {Convolutional pose machines},
  year = {2016}
}
```



## 授权协议

Openpose对于非商业化使用是免费的，而且仅限于这些情况。点击 [license](LICENSE)查看更多细节。[对商业使用的授权感兴趣？点我吧](https://flintbox.com/public/project/47343/)。咨询商业应用相关信息可以联系 [Yaser Sheikh](http://www.cs.cmu.edu/~yaser/).
