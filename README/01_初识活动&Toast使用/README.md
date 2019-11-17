# 初识活动

## 活动是什么
1. 活动(Activity)是最容易吸引用户的地方，是一种可以包含用户界面的组件，用于和用户交互。一个应用可以包含0个或多个活动，但是不包含活动的程序很少

## 活动的基本用法
1. 手动创建Activity(新建项目选择，选择Add No Activity)
    1. 手动创建Activity
        1. 右键包名，并填写主活动名，不要勾选Generate Layout File和Launcher Activity
            * 勾选Generate Layout 会自动生成布局文件
            * 勾选Launcher Activity会自动设置为当前项目的主活动
        2. 勾选Backwards Compatibility: 启用向下兼容模式
        3. 需要知道，项目中的任何活动都应该重写Activity的onCreate()
        
    2. 手动创建布局文件
        1. 安卓程序讲究逻辑和视图分离，所以最好每一个活动都能对应一个布局文件
        2. 在app/src/main/res中新家layout目录，然后右键新建Layout resource file.命名布局文件
            * 属性说明
                1. android:id : 给当前的元素定义一个唯一的标识符，方便在代码中操作
                    * 如果在xml中引用一个id使用`@id/id_name`
                    * 如果在xml中定义一个id使用`@+id/id_name`
                2. android:layout_width : 指定当前元素宽度
                    * match_parent : 和父亲一样宽
                    * wrap_content : 和内容一样宽
                3. android:layout_height : 指定元素高度
                4. android:text : 元素中文字内容
        3. 在主活动中加载布局
            * `setContentView(R.layout.first_layout)`
    
    3. 在AndroidManifest文件中注册
        1. 所有的活动都需要在AndroidManifest.xml中进行注册
        2. 活动的声明要放在<application>标签内，使用activity标签进行注册，我们使用android:name来指定具体注册哪一个活动
            * 因为最外层使用package属性指定了程序包名，所以可以直接使用.FirstActivity进行注册
        3. 配置主活动声明(activity中)
            ```
                <intent-filter>
                    <action android:name="android.intent.action.MAIN" />
                    <category android:name="android:intent.category.LAUNCHER" />
                </intent-filter>
            ```
            * 还可以使用android:label指定活动中标题栏的内容，显示在活动最顶部(activity标签属性)
                * `android:label="This is FirstActivity"`
                * 注意： 主活动指定的label不仅会成为标题栏中的内容，还会成为启动器中程序名称
        
## 活动中使用Toast
* android中提供了一种很好的提醒方式，可以将一些短小的信息通知给用户，一段时间会自动消失，不会占用空间
* 例如我们让点击按钮时，弹出一个Toast提示框(Activity的onCreate中添加按钮监听)
    ```
    Button btn = findViewById(R.id.button_1);
    btn.setOnClickListener(new View.OnClickListener() {
        @Override
        public void onClick(View v) {
            Toast.makeText(FirstActivity.this,"hello" ,Toast.LENGTH_SHORT).show();
            Log.d(TAG, "onClick: " + this);
            Log.d(TAG, "onClick: " + FirstActivity.this);
        }
    });
    ```
    * 在活动中，可以通过findViewByID方法获取到布局文件中定义的元素，R.id.btn,这个值时刚才在xml布局文件中指定的
    * 得到按钮的实例以后，我们调用setOnClickListener()方法为按钮注册一个监听器，点击按钮就会执行监听器中的onClick方法
    * 用法
        * `Toast.makeToast(context, msg, Toast.LENGTH_SHORT).show()`
    
* java 基础回顾
    1. 类名.class
       * 我们知道在java中，一个类在被加载的时候虚拟机就会自动的生成一个这个类的一个Class类型的“类对象”，每个类都对应着一个这样的类对象，通过这个Class类型的类对象，我们就能够使用“内省与反射”机制，访问一个类的信息，比如：对应类中的方法有哪些，成员域有哪些等等；获取一个类的“类对象”的方法之一就是通过使用   类名.class  这个方式返回一个Class类型的对象，其他的获取这个Class对象的方法如下：
            1. 利用对象调用getClass()方法获取该对象的Class实例
            2. 使用Class的静态方法forName()，用类的名字获取一个Class实例
            3. 运用.calss的方式获取Class实例，对基本数据类型的封装类，还可以采用.TYPE来获取对应的基本数据类型的Class实例。
    
    2. 类名.this详解(这个语法主要有两个方面)
        1. 当在一个类的内部类中，如果需要访问外部类的方法或者成员域的时候，如果使用  this.成员域(与 内部类.this.成员域 没有分别) 调用的显然是内部类的域 ， 如果我们想要访问外部类的域的时候，就要必须使用  外部类.this.成员域
        2. 还有一个使用情况，那就是在是使用意图更加的清楚，在Android开发中我们经常要在一些地方使用 Context 类型的参数， 而这个参数我们往往使用this
            * 其实这里面其实有一种隐含的逻辑，这说明我们创建的Intent(Toast)等 对象是与MainActivity这个类型的对象是有关联的，也就是说这个Intent是由MainActivity对象发出的，这说明有些情况下虽然使用 类名.this  和 直接使用this 没有分别，但是使用  类名.this  却能够清楚的显示出一种关联性，因此值得提倡
            * 与此同时如果我们创建的Intent在一个匿名内部类中创建的话，但是我们想让这个在Intent对象在逻辑上和外部类对象关联起来的话，我们就必须使用  外部类名.this  了
