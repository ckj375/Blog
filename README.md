# Android-Tech-Stack

基础工具相关
-------------------------------------------------------------------------------
Git相关
http://chenkaijian.com/2018/04/26/git/

Git Flow
https://www.cnblogs.com/hblflu/p/6494950.html
https://www.cnblogs.com/lcngu/p/5770288.html

Android相关
-------------------------------------------------------------------------------
Android SDK常用工具
DDMS，9-Patch，HierarchyViewer，Monkey，TraceView，ADB

Handler机制

Android程序运行时权限和文件系统权限区别

什么情况会导致Force Close ？如何避免？能否捕获导致其的异常？
运行时异常，如空指针，数组越界等；在可能出现异常的地方添加逻辑判断；捕获异常throws或trycatch

Activity生命周期

横竖屏切换时Activity生命周期
若未设置configChanges属性，则重走生命周期
竖屏启动：
onCreate -->onStart-->onResume
切换横屏：
onPause -->onSaveInstanceState -->onStop -->onDestroy -->onCreate-->onStart -->
onRestoreInstanceState-->onResume -->onPause -->onStop -->onDestroy 
若设置android:configChanges="orientation|keybordHidden|screenSize"则不会重走生命周期
竖屏启动：
onCreate -->onStart-->onResume
切换横屏：
onConfigurationChanged

Fragment生命周期
Activity的4种启动方式
如何将Activity设置成窗口样式
Intent的作用：启动Activity或Service，传递数据和事件
Service的启动和停止方式
IntentService是Service的子类，能处理耗时任务，当处理完所有Intent请求后会自动停止
广播注册方式及优缺点

UI布局适配
MVC模式原理，MVC，MVP和MVVM的区别
android 黄油计划相关改进

IPC是什么？有哪些方式？
Android进程间通信，方式：Intent/Bundle，文件共享，AIDL，Messenger，ContentProvider，Socket

AIDL：Android接口定义语言
通过定义 AIDL 接 口文件来定义 IPC 接口。Servier 端实现 IPC 接口，Client 端调用 IPC 接口本地代理
处理数据类型：java基本数据类型，String，CharSequence，List，Map，Parcelable
https://juejin.im/entry/579320241532bc0060c7e420

Android Binder机制
进程间通信的机制
https://www.cnblogs.com/xinmengwuheng/p/7070167.html

Android ClassLoader机制
https://juejin.im/post/59e73b3cf265da432e5b1b29

DVM和ART
https://www.jianshu.com/p/bdb6c29aca83

Android线程池原理及使用
https://www.jianshu.com/p/7b2da1d94b42

Android应用内存大小是否限定，如何增大内存大小
是的，android:largeHeap="true"

Android动画
补间动画，逐帧动画，属性动画

Android常见异常
NullPointerException，ClassCastException，ClassNotFoundException，ArrayIndexOutOfBoundsException，FileNotFoundException，ArithmeticException，IOException，SQLException，NoSuchMethodException，NumberFormatException，SecturityException

Android多渠道打包方式：
1.Flavor ＋ BuildType
2.美团多渠道打包方案
3.美团Walle瓦力

SQLite数据库文件如何和APK一起发布
将数据库文件放到assets或res/raw目录下，不会参与编译。res/raw目录下的文件会映射到R文件，且不允许有目录，而assets不会映射，且允许再建目录。

Android中touch事件分发机制并结合各种实例分析
https://github.com/Idtk/Blog/blob/master/Blog/11%E3%80%81TouchEvent.md

Android自定义View的流程及原理
https://www.jianshu.com/p/56006bc13dcf

A/B测试
有足够用户量，应用范围：单变量

Android编译流程

Android gradle混淆流程

开源库相关
-------------------------------------------------------------------------------------
Glide
https://muyangmin.github.io/glide-docs-cn/doc/download-setup.html
https://www.jianshu.com/p/791ee473a89b
https://blog.csdn.net/yulyu/article/details/55261439

Retrofit+OKHttp+RXJava
http://chenkaijian.com/2017/09/05/retrofit-okhttp-rxjava-guide/

Leakcanary实现原理
https://www.jianshu.com/p/261e70f3083f

Gson
https://www.jianshu.com/p/0444693c2639

Java基础知识
-------------------------------------------------------------------------------------

Switch能否用String做参数？
在 Java 7 之前， switch 只能支持 byte 、 short 、 char 、 int 或者其对应的封装类以及 Enum 类型。在 Java 7 中， String 支持被加上了
equals与==的区别
==是判断两个变量或实例是不是指向同一个内存空间 equals是判断两个变量或实例所指向的内存空间的值是不是相同
String、StringBuffer与StringBuilder的区别
String 类型和 StringBuffer 类型的主要性能区别其实在于 String 是不可变的对象 StringBuffer和StringBuilder底层是 char[]数组实现的 StringBuffer是线程安全的，而StringBuilder是线程不安全的
Override和Overload区别
抽象类和接口的区别
垃圾回收是什么？
释放不再持有引用的对象的内存
HashMap和 HashTable 的区别
HashTable比较老，是基于Dictionary 类实现的，HashTable 则是基于 Map接口实现的 HashTable 是线程安全的， HashMap 则是线程不安全的 HashMap可以让你将空值作为一个表的条目的key或value
堆和栈的区别
基本数据类型比变量和对象的引用都是在栈分配的，堆内存用来存放由new创建的对象和数组
ArrayList、LinkedList、Vector的区别
ArrayList 和Vector底层是采用数组方式存储数据，Vector由于使用了synchronized方法（线程安全）所以性能上比ArrayList要差，LinkedList使用双向链表实现存储，随机存取比较慢
Arraylist和linkedlist区别-->为啥链表比数组更适合增删操作
1.ArrayList是实现了基于动态数组的数据结构，LinkedList是基于链表结构。
2.对于随机访问的get和set方法，ArrayList要优于LinkedList，因为LinkedList要移动指针。
3.对于新增和删除操作add和remove，LinkedList比较占优势，因为ArrayList要移动数据。
解析XML的几种方式的原理与特点：DOM、SAX、PULL
DOM：消耗内存：先把xml文档都读到内存中，然后再用DOM API来访问树形结构，并获取数据。这个写起来很简单，但是很消耗内存。要是数据过大，手机不够牛逼，可能手机直接死机
SAX：解析效率高，占用内存少，基于事件驱动的：更加简单地说就是对文档进行顺序扫描，当扫描到文档(document)开始与结束、元素(element)开始与结束、文档(document)结束等地方时通知事件处理函数，由事件处理函数做相应动作，然后继续同样的扫描，直至文档结束。
PULL：与 SAX 类似，也是基于事件驱动，我们可以调用它的next（）方法，来获取下一个解析事件（就是开始文档，结束文档，开始标签，结束标签），当处于某个元素时可以调用XmlPullParser的getAttributte()方法来获取属性的值，也可调用它的nextText()获取本节点的值。
wait()和sleep()的区别
sleep来自Thread类，和wait来自Object类
调用sleep()方法的过程中，线程不会释放对象锁。而 调用 wait 方法线程会释放对象锁
sleep睡眠后不出让系统资源，wait让出系统资源其他线程可以占用CPU
sleep(milliseconds)需要指定一个睡眠时间，时间一到会自动唤醒
生产者消费者模式

JVM工作原理和流程
https://www.cnblogs.com/lishun1005/p/6019678.html
http://liuwangshu.cn/tags/Java%E8%99%9A%E6%8B%9F%E6%9C%BA/

冒泡排序
for(int i=0;i<arr.length-1;i++){//外层循环控制排序趟数
　　for(int j=0;j<arr.length-1-i;j++){//内层循环控制每一趟排序多少次
　　　　if(arr[j]>arr[j+1]){
　　　　int temp=arr[j];
　　　　arr[j]=arr[j+1];
　　　　arr[j+1]=temp;
　　　　}
　　}
}

快速排序
https://www.cnblogs.com/MOBIN/p/4681369.html
public static void quickSort(int arr[],int _left,int _right){
        int left = _left;
        int right = _right;
        int temp = 0;
        if(left <= right){   //待排序的元素至少有两个的情况
            temp = arr[left];  //待排序的第一个元素作为基准元素
            while(left != right){   //从左右两边交替扫描，直到left = right

                while(right > left && arr[right] >= temp)  
                     right --;        //从右往左扫描，找到第一个比基准元素小的元素
                  arr[left] = arr[right];  //找到这种元素arr[right]后与arr[left]交换

                while(left < right && arr[left] <= temp)
                     left ++;         //从左往右扫描，找到第一个比基准元素大的元素
                  arr[right] = arr[left];  //找到这种元素arr[left]后，与arr[right]交换
            }
            arr[right] = temp;    //基准元素归位
            quickSort(arr,_left,left-1);  //对基准元素左边的元素进行递归排序
            quickSort(arr, right+1,_right);  //对基准元素右边的进行递归排序
        }        
    }

二分查找
static int binarySerach(int[] array, int key) {
    int left = 0;
    int right = array.length - 1;
    while (left <= right) {
        int mid = (left + right) / 2;
        if (array[mid] == key) {
            return mid;
        }
        else if (array[mid] < key) {
            left = mid + 1;
        }
        else {
            right = mid - 1;
        }
    }
    return -1;
}

设计模式
-------------------------------------------------------------------------------------
单例模式
饿汉式，懒汉式，双重锁式
https://www.cnblogs.com/zhangqie/p/6408388.html

工厂模式，建造者模式，适配器模式，代理模式，观察者模式

网络协议相关

HTTP 中Get 和 Post 方法的区别
GET参数通过URL传递，POST放在Request body中

Http协议详解
https://www.cnblogs.com/sunny-sl/p/6529830.html
https://www.cnblogs.com/jackson0714/p/HTTP1.html

TCP/IP协议
https://blog.csdn.net/e_kunt/article/details/52623614

https://juejin.im/post/5aa721936fb9a028d4443d8b

#### Java进阶
设计模式  
https://www.cnblogs.com/snow-flower/p/6110403.html  

#### Android基础
事件分发机制  
http://www.jianshu.com/p/e99b5e8bd67b  
自定义View  
http://hencoder.com/ui-1-1/  
Android Handler机制  
https://segmentfault.com/a/1190000004866028  
https://www.jianshu.com/p/f70ee1765a61  
Android线程与线程池  
https://blog.csdn.net/weixin_36244867/article/details/72832632  

#### Android进阶
Ant教程  
https://www.w3cschool.cn/ant/  
Maven教程  
https://www.w3cschool.cn/maven/u7oe1ht0.html  
Gradle基础教程  
http://www.cnblogs.com/davenkin/p/gradle-learning-1.html  
Android项目中Gradle详解  
http://blog.csdn.net/wqc_CSDN/article/details/53572921  
Groovy教程  
http://blog.csdn.net/iamzgx/article/details/72972255教程  
多渠道打包：productFlavors  
http://chenkaijian.com/2018/01/12/android-gradle-productflavors/  
多渠道打包：AndroidMultiChannelBuildTool  
https://github.com/GavinCT/AndroidMultiChannelBuildTool  
多渠道打包：walle  
https://github.com/Meituan-Dianping/walle  
内存泄露  
http://chenkaijian.com/2016/05/10/Android%E5%86%85%E5%AD%98%E6%B3%84%E9%9C%B2%E6%80%BB%E7%BB%93/  
Android Binder机制  
https://juejin.im/post/5acccf845188255c3201100f  
AIDL  
https://juejin.im/post/58d39de6a22b9d00644eb60b  
Android类加载机制  
https://www.jianshu.com/p/7193600024e7  
Android组件化  
https://blog.csdn.net/asddavid/article/details/53436848  
反编译教程  
http://www.jianshu.com/p/b3bb4da64dc7  

#### Android开源库
网络请求：OKHttp,Retrofit,Volley  
https://github.com/square/okhttp  
https://github.com/square/retrofit  
https://github.com/google/volley  
响应式编程：RxJava  
https://github.com/ReactiveX/RxJava/  
图片加载相关：Universal-Image-Loader,Picasso,Glide,Fresco  
https://github.com/bumptech/glide  
https://mrfu.me/2016/02/27/Glide_Thumbnails/  
性能优化：LeakCanary  
https://github.com/square/leakcanary/  
JSON解析：Gson,FastJson,jackson  
https://github.com/google/gson  
Html解析：Jsoup  
https://github.com/jhy/jsoup  
Log框架：Logger  
https://github.com/orhanobut/logger  
调试框架：stetho  
https://github.com/facebook/stetho  
依赖注入：ButterKnife,Dagger2  
https://github.com/google/dagger/  
热修复框架：AndFix,Tinker  
https://github.com/Tencent/tinker  
事件总线：EventBus  
https://github.com/greenrobot/EventBus/  
Android模块间通信  
https://github.com/alibaba/ARouter  

### 工具资源
Wireshark网络抓包  
http://chenkaijian.com/2017/12/20/android-debug-wireshark/  
Fiddler网络抓包  
http://blog.csdn.net/lyd135364/article/details/78384285  
在线工具  
https://tool.lu/  
在线图标库  
http://www.iconfont.cn/  
在线颜色选择器|RGB颜色查询对照表  
http://www.atool.org/colorpicker.php  
Git教程  
http://chenkaijian.com/2018/04/26/git/  
