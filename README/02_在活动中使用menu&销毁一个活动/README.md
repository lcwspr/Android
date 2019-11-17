# 在活动中使用Menu
* 手机空间十分有限，所以充分利用屏幕空间在手机界面设计中十分重要，如果活动中有大量菜单需要显示，那么界面显示就会很尴尬，Android给我们提供了一种方式，能够让所有菜单都能够展示的同时，还不不占用任何屏幕空间
* 使用
    1. 在res目录下新建一个menu文件夹
    2. 新建一个名称为main的菜单文件
        * New -> Menu resource file
    3. 添加菜单代码
        ```
        <menu xmlns:android="http://schemas.android.com/apk/res/android">
            <item
                android:title="Add"
                android:id="@+id/add_item"/>
            <item
                android:title="Remove"
                android:id="@+id/remove_item"/>
        </menu>
        ```
        1. 创建两个菜单项目，其中item标签就是用来创建具体的某一个菜单项
            * 然后通过android:id给这个菜单指定一个唯一的标识符
            * 通过android:title给菜单项指定一个名称
        2. 接着回到FirtActivity来重写`onCreateOptionsMenu()`,重写方法可以使用Ctrl + o快捷键
        3. 在选项菜单创建方法中，填充选项菜单
            ```
            public boolean onCreateOptionsMenu(Menu menu){
                getMenuInflater().inflate(R.menu.main, menu);
                return true;
            }
            ```
            * 通过getMenuInflater()方法能够得到MenuInflater对象，能够使用他的inflate()方法给当前活动创建菜单
            * inflate方法接受两个参数
                1. 通过那个资源文件创建菜单
                2. 将菜单项添加到哪一个Menu对象中
            * 方法的返回值用于指定菜单是否显现出来
  
## 监听菜单的点击事件
* 在活动中，重写onOptionsItemSelected()方法      
    ```
    public boolean onOptionsItemSelected(MenuItem item){
        switch(item.getItemId()){
        
        }
    }
    ```
        
## 销毁一个活动
* 其实只要按一下Back按钮就可以销毁当前活动了，不过如果想要通过代码来销毁活动那么也是可以的，Activity类提供了一个finish()方法，我们调用finish就能够销毁当前活动了 
              