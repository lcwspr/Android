# 项目中的资源文件

## 资源文件夹简介
1. 打开res目录看一下，其实里面的东西挺多的(主要由于mipmap,drawable为了更好的兼容各种设备，提供不同分辨率的图片。程序运行时会根据运行设备分辨率自动加载图片)
    1. 所有以drawable开头的文件夹都是放图片的
    2. 所有以mipmap开头的文件夹都是用来放应用图标的
    3. 所有以values开头的文件夹都是用来放字符串，样式，颜色等配置的
    4. layout文件夹是用来放布局文件的
* 但是一般情况下，美工只会给我们一份图片，那么就都放在drawable-xxhdpi文件夹就好了

## 资源的引用
1. 如下资源
    ```xml
       <resources>
           <string name="app_name">HelloWorld</string>
       </resources>
    ```
2. 引用方式
    1. 在代码中通过`R.string.app_name`获得字符串的引用
    2. 在XML中通过`@string/app_name`可以获得字符串的引用

3. 说明
    * 其中string部分时可以替换的，如果引用的是图片资源就可以替换成drawable
    * 引用图标可以替换成mipmap
    * 引用布局替换成layout

4. 操作
    * 在AndroidManifest.xml,应用图标就是通过android:icon属性指定的，应用名称通过android:label属性指定的
