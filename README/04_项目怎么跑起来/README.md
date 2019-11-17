# 项目怎么跑起来
1. 首先打开AndroidManifest.xml文件
    ```
        <activity android:name=".HelloWorldActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    ```
    * 这段代码表示对于HelloWorldActivity这个活动进行注册,没有注册的活动不能使用
    * intent-filter中的两行代码表示这个activity是这个项目的主活动,就是点击图标首先启动的活动
    
2. 查看Activity java代码
    * MainActivity继承自AppCompatActivity,是一种向下兼容的Activity. 可以将各个系统版本中增加的特性和功能最低兼容到2.1系统
    * Activity是安卓系统的活动基类,所有活动必须继承他或他的子类才能有活动特性
    * onCreate()方法是一个活动被创建的时候必定要执行的方法

3. 布局文件
    * android程序的设计讲究逻辑和视图分离,因此不推荐在活动中直接编写界面
    * 更加通用的做法是,在布局文件编写界面,在活动中引入进来.使用setContentView()方法来给当前活动引入一个布局
        