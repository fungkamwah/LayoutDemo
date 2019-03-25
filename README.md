# LayoutDemo
Android上手练习6.常用布局
LinearLayout即线性布局，是Android界面开发中常用的布局方式之一。包括纵向的线性布局和横向的线性布局。


## 1 LinearLayout
## 1.1 
新建项目，选择【Empty Activity】，让AndroidStudio帮我们创建一个空的Activity，并会自动在AndroidManifest.xml配置好默认的Activity。
![image](http://po1d0nnr5.bkt.clouddn.com/QQ20190312-103114.png)

生成的是一个可以直接运行Android项目。
![image](http://po1d0nnr5.bkt.clouddn.com/QQ20190312-104251.png)

## 1.2 纵向LinearLayout
生成的layout_main使用的是ConstraintLayout 

```
<?xml version="1.0" encoding="utf-8"?>
<android.support.constraint.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello World!"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

</android.support.constraint.ConstraintLayout>
```

把它编辑为LinearLayout，并在其中添加几个子项。
```
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:gravity="center"
        android:text="text0"/>
    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:gravity="center"
        android:text="text1"/>

    <Button
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="button0"/>
    <Button
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="button1"/>

</LinearLayout>
```
通过设置属性orientation值为vertical，将LinearLayout设定为纵向的线性布局。
运行一下看效果，为子View纵向排列的效果。

![image](http://po1d0nnr5.bkt.clouddn.com/QQ20190312-112805.png)

## 1.3 横向的LinearLayout
设置属性orientation值为horizontal的LinearLayout为横向的线性布局。这里演示的是直接在上面的布局当中嵌套一个LinearLayout。
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <LinearLayout
        android:orientation="horizontal"
        android:layout_width="match_parent"
        android:layout_height="80dp">

        <Button
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="横向1"/>
        <Button
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="横向2"/>
        <Button
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="横向3"/>

    </LinearLayout>

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:gravity="center"
        android:text="text0"/>
    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:gravity="center"
        android:text="text1"/>

    <Button
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="button0"/>
    <Button
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="button1"/>

</LinearLayout>
```

运行效果

![image](http://po1d0nnr5.bkt.clouddn.com/QQ20190312-114219.png)

## 1.4 weight比重
线性布局中可通过设置weight来给子View分配空间。把刚刚的横向线性布局修改为
```
    <LinearLayout
        android:orientation="horizontal"
        android:layout_width="match_parent"
        android:weightSum="6"
        android:layout_height="80dp">

        <Button
            android:layout_width="0dp"
            android:layout_weight="1"
            android:layout_height="wrap_content"
            android:text="横向1"/>
        <Button
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="2"
            android:text="横向2"/>
        <Button
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="3"
            android:text="横向3"/>

    </LinearLayout>
```
LinearLayout设置属性weihtSum为6，三个Button分别设置layout_weight为1，2，3，即分别占据父布局空间的1/6，2/6，3/6，同时把把它们的 layout_width都设为0dp。运行看效果。

![image](http://po1d0nnr5.bkt.clouddn.com/QQ20190312-115407.png)


*更多关于LinearLayout的内容可参考：[http://www.runoob.com/w3cnote/android-tutorial-linearlayout.html](http://www.runoob.com/w3cnote/android-tutorial-linearlayout.html)*


## 2 RelativeLayout

使用相对布局可以减少View的嵌套，以及有利于屏幕适配。

新建Activity。
```
package net.gzchunxiang.layoutdemo;

import android.os.Bundle;
import android.support.annotation.Nullable;
import android.support.v7.app.AppCompatActivity;

public class RelativeActivity extends AppCompatActivity {

    @Override
    protected void onCreate(@Nullable Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_relative);
    }
}

```

新建布局文件activity_relative.xml。使用RelativeLayout

```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">


    <!--一个相对于父View水平居中的ImageView-->
    <ImageView
        android:id="@+id/imageView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="30dp"
        android:src="@mipmap/ic_launcher" />


    <!--imageView下方，父View右侧-->
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/imageView"
        android:layout_alignParentRight="true"
        android:text="text"
        android:textSize="20sp" />


    <!--相对父View 正居中的ImageView-->
    <ImageView
        android:id="@+id/centerImage"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerInParent="true"
        android:src="@mipmap/ic_launcher" />

    <!--centerImage上方的TextView-->
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_above="@id/centerImage"
        android:layout_centerInParent="true"
        android:text="上" />

    <!--centerImage内左上的TextView-->
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignLeft="@id/centerImage"
        android:layout_alignTop="@id/centerImage"
        android:text="内左上"
        android:textColor="#ffff00" />

    <!--centerImage外右下的TextView-->
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignBottom="@id/centerImage"
        android:layout_toRightOf="@id/centerImage"
        android:text="外右下"
        android:textColor="#ff0000" />


    <!--centerImage下方的Button-->
    <Button
        android:layout_width="200dp"
        android:layout_height="wrap_content"
        android:layout_below="@id/centerImage"
        android:layout_centerInParent="true"
        android:layout_marginTop="10dp"
        android:text="下" />

    <Button
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_alignParentBottom="true"
        android:text="相对父View底部的按钮" />


</RelativeLayout>
```

自行在MainActivity添加跳转到RelativeActivity，不要忘了在AndroidManifest.xml添加配置。
运行看效果：

![image](http://po1d0nnr5.bkt.clouddn.com/QQ20190321-142626.png)


## 3 FrameLayout
帧布局可以实现一些简单的堆叠布局。

示例：activity_frame.xml
```
<?xml version="1.0" encoding="utf-8"?>
<FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">
    
    
    <ImageView
        android:id="@+id/image"
        android:layout_width="match_parent"
        android:layout_height="400dp"
        android:src="@color/colorPrimary"/>
    
    
    <FrameLayout
        android:layout_width="200dp"
        android:layout_height="200dp"
        android:layout_gravity="center"
        android:background="#ffff00">
        
        <ImageView
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            android:layout_margin="10dp"
            android:src="@color/colorAccent"/>
        
        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_gravity="right"
            android:layout_margin="15dp"
            android:textColor="#ffffff"
            android:text="角标"/>
        
        <TextView
            android:layout_gravity="bottom"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:background="#66333333"
            android:textColor="#ffffff"
            android:gravity="center"
            android:text="标题XX"/>
        
    </FrameLayout>

</FrameLayout>
```

预览效果。

![image](http://po1d0nnr5.bkt.clouddn.com/QQ20190321-145530.png)


## 4 其他布局
以上是用得最多的几种布局方式。
其他的一些布局可以参考：

约束布局ConstraintLayout  [https://juejin.im/post/5c0bd6b05188257c3045dc50](https://juejin.im/post/5c0bd6b05188257c3045dc50)
