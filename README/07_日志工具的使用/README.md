# 日志工具的使用

## 使用Android的日志工具Log
1. 安卓的日志工具类是Log(android.util.Log),类中提供了5个方法来供我们打印日志
    1. Log.v(): 最为琐碎意义最小的日志信息(verbose)
    2. Log.d(): 调试信息(debug)
    3. Log.i(): 比较重要的数据，非常想看到的(info)
    4. Log.w(): 用于打印一些警告信息，提示潜在风险(warn)
    5. Log.e(): 用于打印错误信息，比如程序进入catch语句中。
2. 使用Log.d(tag,mess)打印日志
    * tag: 一般传入当前类名，用于对信息进行过滤
    * msg: 想要打印的信息
3. System.out.println打印日志？
    * 日志打印不可控制，打印时间无法确定，不能添加过滤器，日志没有级别区分
4. 自动一过滤器
    * logcat edit filter configuration
    