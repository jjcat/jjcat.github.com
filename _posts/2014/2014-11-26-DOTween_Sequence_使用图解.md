---
    layout: post
    title: DOTween Sequence 使用图解
    tagline: 
    tags: [Unity3D, DOTween]
---

最近在使用[DOTween](http://dotween.demigiant.com/documentation.php)制作一些动画过渡的内容，发现非常好用，使用Sequence类可以方便的组织Tweens来制作复杂的过渡动画。Sequence的几个函数文档说明都比较简单，我列出每个函数调用后的Sequence变化以方便查阅。

下图表示调用函数前的Sequence。

![image](http://www.jjcat.me/image/2014/11/dotween1.png)

---

###Append(Tween tween)
Adds the given tween to the end of the Sequence.

在Sequence的最后添加一个tween。

![image](http://www.jjcat.me/image/2014/11/dotween2.png)

___


###AppendCallback(TweenCallback callback)
Adds the given callback to the end of the Sequence.

在Sequence的最后添加一个回调函数。

![image](http://www.jjcat.me/image/2014/11/dotween3.png)

___

###AppendInterval(float interval)
Adds the given interval to the end of the Sequence.

在Sequence的最后添加一段时间间隔。

![image](http://www.jjcat.me/image/2014/11/dotween4.png)

___


###Insert(float atPosition, Tween tween)
Inserts the given tween at the given time position, thus allowing you to overlap tweens instead than just placing them one after each other.

在给定的时间位置上放置一个tween，可以实现同时播放多个tween的效果，而不是一个接着一个播放。

![image](http://www.jjcat.me/image/2014/11/dotween5.png)

___


###InsertCallback(float atPosition, TweenCallback callback)
Inserts the given callback at the given time position.

在给定的时间位置上放置一个回调函数。

![image](http://www.jjcat.me/image/2014/11/dotween6.png)

___


###Join(Tween tween)
Inserts the given tween at the same time position of the last tween added to the Sequence.

在Sequence的最后一个tween的开始处放置一个tween。

![image](http://www.jjcat.me/image/2014/11/dotween7.png)

___

###Prepend(Tween tween)
Adds the given tween to the beginning of the Sequence, pushing forward in time the rest of the contents

在Sequence开始处插入一个tween，原先的内容根据时间往后移。

![image](http://www.jjcat.me/image/2014/11/dotween8.png)

___


###PrependCallback(TweenCallback callback)
Adds the given callback to the beginning of the Sequence.

在Sequence开始处插入一个回调函数。

![image](http://www.jjcat.me/image/2014/11/dotween9.png)

___


###PrependInterval(float interval)
Adds the given interval to the beginning of the Sequence, pushing forward in time the rest of the contents.

在Sequence开始处插入一段时间间隔，原先的内容根据时间往后移。

![image](http://www.jjcat.me/image/2014/11/dotween10.png)

