---
permalink: why-flutter-1-1.html
title: 【Flutter 1-1】8个Flutter的优势以及为什么要在下一个项目中尝试Flutter
date: 2020-10-04 14:30:08
toc: true
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
categories: Flutter
tags: 
    - Flutter
---

让我们一起来了解Flutter与其他跨平台框架的优势，以及这些优势在开发流程中的作用。



- #### [Flutter是什么](#jump1)
- #### [Flutter的优势](#jump2)
    - ##### [1. 跨平台使用相同的UI和业务逻辑](#jump2_1)
    - ##### [2. 节省开发时间](#jump2_2)
    - ##### [3. 更快的迭代速度](#jump2_3)
    - ##### [4. 无限接近原生的交互体验](#jump2_4)
    - ##### [5. 丰富的UI动画](#jump2_5)
    - ##### [6. 独立的渲染引擎](#jump2_6)
    - ##### [7. 能够很容易与原生进行交互](#jump2_7)
    - ##### [8. 不只是能运行在移动端](#jump2_8)
- #### [从业务层来看，Flutter是一个好的选择吗？](#jump3)
- #### [为什么要尝试使用Fultter?](#jump4)

#### <span id="jump1">Flutter是什么</span>
就我目前的职业开发生涯中，目睹了太多太多项目不知道该选择哪种跨平台方案的例子。这些项目都是不同的，但是我们都希望这些项目能够运行在更多平台和更多设备上，常见的作法就是在不同的客户端招聘不同的开发人员来进行开发工作，比如手机端有iOS程序员和Android程序员等等。
我记得在2013年，我第一次看到了比较完善的跨平台游戏开发方案，那时候我就在想，为什么App端没有这种工具可以满足我们跨平台的需求呢？
但是，现在我们有了，它就是Flutter！我将在下面介绍我使用Flutter做了些什么，希望能对你有所帮助或启发。
我有过一些iOS开发经验，也有过一些游戏开发经验，可以说Flutter就是我一直在寻找的跨平台解决方案。它不仅使用简单，还能保持跨平台UI的一致性时，并且很容易的与原生进行交互。是非常好的体验。
<!--more-->

#### <span id="jump2">Flutter的优势</span>
你之前可能会了解到，所有的跨平台框架都会在节约开发时间上有所帮助。但是，Flutter在有些地方跟其他框架有很多不同，让我们来看看，究竟Flutter比其他跨平台框架在哪些地方做的更好。


##### <span id="jump2_1">1. 跨平台使用相同的UI和业务逻辑</span>
我们知道，基本上所有的跨平台框架都提供了一种在目标平台之间共享代码的实现方式。但是没有任何一个平台像Flutter这样允许共享UI代码以及UI本身。
为了说明这一点，下面我们来看一下其中一个跨平台框架UI的实现逻辑：
![2020_09_30_other_paltform](https://raw.githubusercontent.com/Johnson8888/blog_pages/master/images/2020_09_30_other_paltform.png)
React Navite 的渲染过程看起来像是在每个平台上都很简单。但是从图中我们不难发现，这种渲染过程需要依然各个平台原生组件来进行渲染，React Native 就是帮我们实现了对各个平台应用层UI控件的映射。这就需要将每个动画每个UI映射到各个平台的动画和UI上，显然这比较繁琐。
相比之下，Flutter不需要依赖热任何平台的UI组件就能生成UI界面。Flutter唯一需要的就是一个画布，也就是我们常说的Canvas。
下面是Flutter的渲染过程:
![2020_09_30_flutter_canvas](https://raw.githubusercontent.com/Johnson8888/blog_pages/master/images/2020_09_30_flutter_canvas.png)
Flutter能够在任何平台上构建完全一模一样的的UI，这种独特的渲染方式是它脱颖而出的关键。
简而言之，使用Flutter来实现UI和业务逻辑能够节省时间和精力，并且同时不影响最终产品的性能。原来iOS、Android需要每个平台都要配备相应的程序员，使用Flutter只需要一组程序员就可以了，还节省了程序员！
##### <span id="jump2_2">2. 节省开发时间</span>
依据我个人的开发经验，从编译到运行一个Android App至少需要40秒的时间。同时，在调试UI的过程中需要不停的编译和运行，这就需要消耗大量的时间。诚然，Android Studio是具有布局预览功能的，但是总有一点不足的是：Android Studio 不能每次都像预期那样运行，特别是在自定义View的时候。
Flutter的 “热重载”功能可以让我们实时看到应用的变化，并且不会丢失当前应用程序的状态。这就是使用Flutter节省开发时间的根本原因。
此外，Flutter团体还付出了很多努力来提供各种控件。这些控件大多数都可以自定义，这就在构建UI上给我们节省了不少时间。除了众多的核心控件外，Flutter还提供了大量的Material(Android风格)和Cupertino(iOS风格)的控件可以满足不同的设计风格。
如下图：
![2020_09_30_services](https://raw.githubusercontent.com/Johnson8888/blog_pages/master/images/2020_09_30_services.png)
总而言之，使用Flutter来开发，我们可以绕过几个程序开发过程中比较耗时的步骤，这样使整个开发过程更快，更简单且更省心。

##### <span id="jump2_3">3. 更快的迭代速度</span>
使用Flutter来开发迭代产品会更快。在大多数情况下，我们研发一个App需要Android端和iOS端都需要进行开发和维护，而Flutter只要一组人员就可以完成这个任务。在开发时间上至少节省了一倍。原因很简单，我们只需要编写一套代码就可以得到在各个应用平台相同的交互效果。任何基于2D的UI都可以在Flutter中实现，且不需要调用原生代码。
除此之外，Flutter使用声明式语法构建UI，根据我的经验，它可以显著提高开发速度。当涉及到UI效果调整时这是最明显的。
##### <span id="jump2_4">4. 无限接近原生的交互体验</span>
我们知道，App的性能是好的用户体验的关键。
尽管很难说出确切的数字，但是可以肯定地说，在大多数情况下，Flutter应用程序的性能与本机应用程序没有区别，甚至在复杂的UI动画场景中表现的更好。
为什么呢？与大多数跨平台框架不同的是，Flutter不依赖任何中间代码做映射。Flutter应用直接调用了底层代码，这就极大的提高了性能。
我们同样可以使用Flutter完全编译和发布应用程序。
##### <span id="jump2_5">5. 丰富的UI动画</span>
Flutter的一个最大的优势就是可以随时修改屏幕上的任何控件，无论这个控件有多复杂。同样也支持直接使用原生控件来做UI动画。
下面是一个简单的自定义动画的示例：
![2020_09_30_animate](https://raw.githubusercontent.com/Johnson8888/blog_pages/master/images/2020_09_30_animate.png)
同样的，使用Flutter生成动画更加灵活和通用，并且不会额外增加工作量。过渡动画、圆角、颜色、阴影、变换等，Flutter都能轻松实现。
[这里](https://itsallwidgets.com/)给大家提供更多的Demo。让我们更好的熟悉这些动画。
##### <span id="jump2_6">6. 独立的渲染引擎</span>
与其他框架相比，Flutter应有更多的能力。显然，这需要框架本身非常强大，且需要框架本身是一个高性能的框架。
Flutter是使用[Skia](https://github.com/google/skia)作为底层的渲染引擎。有了Skia的支持，UI层可以在任何平台上进行渲染，且保持一致性。换句话说，我们不需要调整任何代码就可以将UI呈现在其他平台上，这极大的简化了开发过程。
##### <span id="jump2_7">7. 能够很容易与原生进行交互</span>
除了UI之外，我们还有很多功能需要依赖原生的支持，比如获取GPS信息，蓝牙通信，传感器，照相机，相册等等。这些功能都可以通过Flutter的插件来实现。
当然有些时候这些插件也是不足以满足我们的需求。但是不用担心，Flutter使用的开发语言（Dart语言）与原生代码通信非常简单。只需要几行代码我们就可以实现原生与Flutter之间的交互，就可以实现任何你想调用原生功能的需求。
交互流程如下图：
![2020_09_30_channel](https://raw.githubusercontent.com/Johnson8888/blog_pages/master/images/2020_09_30_channel.png)
##### <span id="jump2_8">8. 不只是能运行在移动端</span>
Flutter不仅是可以在移动设备上使用，还支持Web端和桌面端。在2018年的I / O会议上，Google展示了Flutter Web的技术，这使得在浏览器中运行纯Flutter应用程序成为可能，且不需要修改任何源代码。
下面是演示视频：

{% raw %}

<div style="position: relative; width: 100%; height: 0; padding-bottom: 75%;">
    <iframe src="//player.bilibili.com/player.html?aid=927277621&bvid=BV1iT4y1c71E&cid=241986005&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true" style="position: absolute; width: 100%; height: 100%; left: 0; top: 0;">
    </iframe>
</div>

{% endraw %}

不能打开视频的可以点击[这里](https://www.bilibili.com/video/BV1iT4y1c71E/)查看
官方的这一操作，意味着Flutter从移动开发框架升级到了全平台开发框架的行列。
如果我们不需要在移动端做部署和使用，技术娴熟的Flutter程序员可以让Flutter在热门平台上运行，包括但不限于Android、iOS、Web浏览器、Windows、macOS、Linux甚至是嵌入式设备。同样的代码可以在这些任何平台上运行，且不需要修改任何Dart代码。


#### <span id="jump3">从业务层来看，Flutter是一个好的选择吗？</span>
是的！是的！是的！
软件产品能保证性能和稳定性、人员容易招聘、产品能够快速的迭代和开发这些优势都能够给企业带来巨大的价值。一旦技术方案出现缺陷和存在任何方面的问题，都会给企业带来直接或间接的损失。
从这个角度来看，Flutter都是可以降低我们的风险的：
- 目前Google正在研发[Fuchsia OS](https://www.techradar.com/news/google-fuchsia)(与Flutter配合使用)，因此Flutter会继续投入研发人员维护和升级，不会中断。
- 使用Flutter的门槛并不高，因为社区中已经有了很多的人气很高的Android开发人员都在提倡和使用Flutter。
- 已经有很多大公司在使用，例如：阿里巴巴，Google Ads，AppTree，Reflectly和My Leaf等等，这是Flutter实力的证明。



#### <span id="jump4">为什么要尝试使用Fultter?</span>
让我们总结一下Flutter的最突出优点：
- UI和业务逻辑代码在各个平台呈现效果一直
- 更快的开发速度
- 更快的迭代速度和更快的上线速度
- 无限接近原生的交互体验
- 更容易的自定UI和动画功能
- 独立的渲染引擎
- 不依赖于任何平台的UI组件
- 适用于更多的平台
- 商业风险控制在最小

所以说，想开发跨平台的，性能优良的应用，Flutter是不二选择。Flutter正式成为最终的跨平台UI框架只是时间问题。