---
layout: post
title: "隐藏Android应用的ActionBar"
date:   2023-02-27
tags: [Andorid, Java, ActionBar]
comments: true
author: Arnold
toc: true
---


ActionBar是在Active内显示的一个工具栏，它可以包含一些常用的信息与操作，如：标题、图标、菜单等。
有时，我们可能会想要隐藏ActionBar，比如在一个全屏的游戏中，ActionBar会占用一部分屏幕空间，影响游戏的体验。本文将介绍隐藏ActionBar的几种方法。

<!-- more -->

## 1. 在样式文件中全局隐藏
如果想在整个应用中隐藏ActionBar，包括在所有的Activity和fragment内，你可以使用这种方式。

一般，样式文件名称为`styles.xml`或`themes.xml`，位于`res/values/`内。你可以修改样式文件的`parent`为`~.NoActionBar`，例如，将下面代码中的`DarkActionBar`修改为`NoActionBar`。
``` xml
<resources> 
    <!---Base application theme. -->
    <style name="AppTheme" parent="Theme.AppCompat.Light.DarkActionBar"> 
    <!--> 
        修改为: <style name="AppTheme" parent="Theme.AppCompat.Light.NoActionBar">
    <-->
        <!---Customize your theme here.-->
        <item name="colorPrimary">@color/colorPrimary</item> 
        <item name="colorPrimaryDark">@color/colorPrimaryDark</item> 
        <item name="colorAccent">@color/colorAccent</item> 
    </style> 
</resources>
```

## 2. 在特定Activity中隐藏
如果你只想在某个Activity中隐藏ActionBar，你可以在Activity的`onCreate`方法中添加以下代码：
``` java
...
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);

    ...
    // 隐藏ActionBar
    ActionBar actionBar = getSupportActionBar();
    if (actionBar != null) {
        actionBar.hide();
    }
}
```

## 3. 在特定Activity中隐藏，使用Windows Manager
还有一种方式是，通过`Windows Manager`设置`Windows Flag`为全屏模式，这种方式可以隐藏ActionBar，也可以隐藏状态栏，但是会导致Activity的布局被拉伸，因为布局的高度会被设置为全屏的高度。需要注意的是，以下代码需要插入到`setContentView`之前。
``` java
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    ...
    // 隐藏ActionBar
    getWindow().setFlags(WindowManager.LayoutParams.FLAG_FULLSCREEN,
            WindowManager.LayoutParams.FLAG_FULLSCREEN);
    setContentView(R.layout.activity_main);
    ...
    setContentView(R.layout.activity_main);
}
```

此文就到此结束啦！欢迎大家在评论区留言哦ヾ(^▽^*)))  
Ciallo～(∠・ω< )⌒☆​  
写文不易，如果你觉得我的文章对你有帮助，欢迎[打赏](https://arnold117.github.io/likes/)！