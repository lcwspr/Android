# 安卓项目结构讲解
* 注意Android studio中的Android视图不是真正的安卓目录结构，而是为了快速开发，android studio生成的目录结构
* 查看真实的目录结构要使用Project视图

## 目录结构简述
1. .gradle/ 和 .idea/
    * 这两个目录放置的都是Android Studio自动生成的一些文件，不需要关心
2. app/
    * 项目中的代码，资源等等都是放置在这个目录下面的,后面详解
3. build/
    * 放置编译的时候自动生成的文件
4. gradle/
    * 包含了gradle wrapper的配置文件,使用gradle wrapper的方式不需要提前将gradle下载好,而是会根据本地的缓存情况决定是否需要联网下载gradle.(安卓默认关闭gradle wrapper方式,可以使用Android->File->Settings->Build Execution, Deployment->Gradle),进行配置
    
5. .gitignore
    * 用来将指定的目录或文件排除在版本控制之外
6. build.gradle
    * 项目全局的gradle构建脚本,通常这个文件中的内容不需要修改
7. gradle.properties
    * 全局gradle配置文件,会影响项目中所有的gradle编译脚本
8. gradlew和gradlew.bat
    * 用于命令行中执行gradle命令.(window&linux)
9. HelloWorld.iml
    * iml文件是IntelliJ IDEA项目都会生成的一个文件,标识这是IDEA项目
10. local.properties
    * 指定本机中Android SDK路径.除非本机Android SDK位置发生了改变
11. settings.gradle
    * 用于指定项目中所有引入的模块,通常模块的引入都是自动完成的
    
## app目录简述
1. build/
    * 和外层的build目录相似 也是包含一些编译时自动生成的文件 不过内容会更复杂
2. libs/
    * 如果你的项目使用到第三方jar包  就需要把jar包放在libs下  会被自动添加到构建路径
3. src/
    1. androidTest/
        * 用来编写Android Test测试用例
    2. main/
        1. java/
            * 存放java代码
        2. res/
            * 项目中所有的图片,布局,字符串等等资源都放在这个文件件
                * 图片放在drawable
                * 布局放在layout
                * 字符串放在values
        3. AndroidManifest.xml
            * android项目的配置文件,所有四大组件都需要在这个文件声明,还可以添加权限声明
    3. test/
        * 编写unit Test测试用例   对于项目自动化测试的另一种方式
    4. .gitignore
        * 用于将模块内的指定的目录或者文件排除在版本控制之外
    5. 001_firstandroid.iml
        * IntelIJ IDEA,自动生成-无须理会
    6. build.gradle
        * 模块内的gradle构建脚本,会指定很多项目构建相关的配置
    7. proguard-rules.pro
        * 用于指定项目代码的混淆规则,不希望破解,就会混淆代码
        