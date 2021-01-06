# JWanandroid

## 介绍
Java版Wanandroid客户端，主体使用MVPArms，利用 MVP + RxJava + Retrofit + Glide + EventBus等框架开发。

## 开放API

感谢无私的[wanandroid](https://wanandroid.com/)站长[鸿洋](https://me.csdn.net/lmj623565791)提供的[开放API](https://wanandroid.com/blog/show/2)

## 开源框架

- [JessYanCoding/MVPArms](https://github.com/JessYanCoding/MVPArms)
  - 
- [square/dagger](https://github.com/square/dagger)
  - 
- [ReactiveX/RxJava](https://github.com/ReactiveX/RxJava)
  - 
- [square/retrofit](https://github.com/square/retrofit)
  - 
- [tbruyelle/RxPermissions](https://github.com/tbruyelle/RxPermissions)
  - 
- [bumptech/glide](https://github.com/bumptech/glide)
  - 
- [scwang90/SmartRefreshLayout](https://github.com/scwang90/SmartRefreshLayout)
  - 下拉刷新框架
- [youth5201314/banner](https://github.com/youth5201314/banner)
  - 
- [CymChad/BaseRecyclerViewAdapterHelper](https://github.com/CymChad/BaseRecyclerViewAdapterHelper)
  - 
- [goweii/AnyLayer](https://github.com/goweii/AnyLayer)
  - 
- [H07000223/FlycoTabLayout](https://github.com/H07000223/FlycoTabLayout)
  - 
- [jd-alexander/LikeButton](https://github.com/jd-alexander/LikeButton)
  - 
- [Kennyc1012/MultiStateView](https://github.com/Kennyc1012/MultiStateView)
  - 
- [JakeWharton/timber](https://github.com/JakeWharton/timber)
  - log库，有log输出开关，统一Log输出形式，存储到文件、数据库、以及网络传输。

+ [yangchong211/YCWebView](https://github.com/yangchong211/YCWebView)
  + WebView库

+ [didi/DoraemonKit](https://github.com/didi/DoraemonKit)
  + 开发测试工具，可以检测性能，查看app信息等。在debug版本上用，辅助开发测试。

### 项目中出现的类：

#### AppLifecycles，AppDelegate

MVPArms中的接口类，AppDelegate实现该接口，代理application的生命周期方法（onCreate(),onTerminate(),attachBaseContext()）。

MVPArms需要做一些初始化工作，在application的对应生命周期方法中调用这些生命周期方法，让MVPArms执行自己的逻辑。

这个项目里可以直接继承MVPArms的BaseApplication,通过ConfigModule来扩展生命周期方法，做自己的事情。



#### WanComponent





#### BaseApp（自己的类）

继承application，实现Application.ActivityLifecycleCallbacks接口）。

> ActivityLifecycleCallbacks：
>
> 所有activity的生命周期函数被回调的时候，也会回调到该callback。



#### APP接口

只有一个方法，getAppComponent()，在AppDelegate中重写了该方法，并提供AppComponent的实现类，该实现类内部通过Dagger2管理app的全局单例对象。如application对象，okHttpClient对象，ImagerLoader对象，Gson对象。



#### WanComponent

只有一个接口方法appconfig(),看起来只是用来做配置用的。

有一个DaggerWanComponent实现类（这个类是编译生成的），使用Dagger管理对象。内部Builder要传入wanModule对象（内部提供AppConfig的单例）。

就是用来获取一个appConfig的单例对象。还不知道这里这么做有什么好处？