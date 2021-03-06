# SlideMenuLayout
## 简介
一个支持左右滑动并带有视差滑动效果的安卓滑动菜单控件。   
[![Platform](https://img.shields.io/badge/platform-android-green.svg)](http://developer.android.com/index.html)
<img src="https://img.shields.io/badge/license-Apache 2.0-green.svg?style=flat">
[![SDK](https://img.shields.io/badge/API-12%2B-green.svg?style=flat)](https://android-arsenal.com/api?level=11)

## 演示
  封装不同场景下的滑动嵌套  
<img src="/gif/demo.gif" width="280px"/>

## 特性
- [x] **支持滑动方向的配置**  
- [x] **直接作为控件使用**  
- [x] **处理各个场景下的滑动冲突**  
- [x] **侧滑菜单打开时候点击主体布局关闭侧滑菜单（可配置）**
- [x] **侧滑菜单打开/关闭的时候主体布局暗度自动变化（可配置）**
- [x] **支持滑动视差效果（可配置）**

## 最新版本
|模块|slideMenuLayout|
|---|---|
|最新版本|![Download](https://api.bintray.com/packages/jkb/maven/slidemenu/images/download.svg)|

## 集成
#### Maven集成
```xml
<dependency>
  <groupId>com.justkiddingbaby</groupId>
  <artifactId>slidemenu</artifactId>
  <version>最新版本</version>
  <type>pom</type>
</dependency>
```
#### JCenter集成
第一步 在项目build.gradle中添加
```gradle
repositories {
    jcenter()
}
```
第一步 在module的build.gradle中添加
```gradle
compile 'com.justkiddingbaby:slidemenu:最新版本'
```

## 属性说明
|属性|说明|值|
|---|---|---|
|[slideMode](/slidemenu/src/main/res/values/attrs.xml)|滑动模式|left right both none|
|[slidePadding](/slidemenu/src/main/res/values/attrs.xml)|滑动菜单打开时候主视图预留边界|dimension|
|[slideTime](/slidemenu/src/main/res/values/attrs.xml)|滑动菜单单开的时间，默认800ms|integer|
|[parallax](/slidemenu/src/main/res/values/attrs.xml)|是否允許滑动视差效果，默认true|boolean|
|[contentAlpha](/slidemenu/src/main/res/values/attrs.xml)|设置侧滑菜单打开时候ContentView的阴影透明度（范围0<alpha<=1.0），默认0.5f|float|
|[contentShadowColor](/slidemenu/src/main/res/values/attrs.xml)|设置侧滑菜单打开时候ContentView的阴影颜色，默认色值#000000|color|
|[contentToggle](/slidemenu/src/main/res/values/attrs.xml)|设置是否允许侧滑菜单打开时候点击ContentView关闭侧滑菜单，默认false|boolean|

## 方法说明
|返回值|方法|说明|
|---|---|---|
|void|[setSlideMode(int slideMode)](/slidemenu/src/main/java/com/jkb/slidemenu/SlideMenuAction.java)|设置滑动模式|
|void|[setSlidePadding(int slidePadding)](/slidemenu/src/main/java/com/jkb/slidemenu/SlideMenuAction.java)|设置滑动边界|
|void|[setSlideTime(int slideTime)](/slidemenu/src/main/java/com/jkb/slidemenu/SlideMenuAction.java)|设置滑动菜单打开的时间|
|View|[getSlideLeftView()](/slidemenu/src/main/java/com/jkb/slidemenu/SlideMenuAction.java)|返回左滑菜单|
|View|[getSlideRightView()](/slidemenu/src/main/java/com/jkb/slidemenu/SlideMenuAction.java)|返回右滑菜单|
|View|[getSlideContentView()](/slidemenu/src/main/java/com/jkb/slidemenu/SlideMenuAction.java)|返回主视图|
|void|[toggleLeftSlide()](/slidemenu/src/main/java/com/jkb/slidemenu/SlideMenuAction.java)|打开/关闭左滑菜单|
|void|[openLeftSlide()](/slidemenu/src/main/java/com/jkb/slidemenu/SlideMenuAction.java)|打开左滑菜单|
|void|[closeLeftSlide()](/slidemenu/src/main/java/com/jkb/slidemenu/SlideMenuAction.java)|关闭左滑此单|
|boolean|[isLeftSlideOpen()](/slidemenu/src/main/java/com/jkb/slidemenu/SlideMenuAction.java)|左滑菜单是否打开|
|void|[toggleRightSlide()](/slidemenu/src/main/java/com/jkb/slidemenu/SlideMenuAction.java)|打开/关闭右滑菜单|
|void|[openRightSlide()](/slidemenu/src/main/java/com/jkb/slidemenu/SlideMenuAction.java)|打开右滑菜单|
|void|[closeRightSlide()](/slidemenu/src/main/java/com/jkb/slidemenu/SlideMenuAction.java)|关闭右滑菜单|
|boolean|[isRightSlideOpen()](/slidemenu/src/main/java/com/jkb/slidemenu/SlideMenuAction.java)|右滑菜单是否打开|
|void|[setParallaxSwitch(boolean parallax)](/slidemenu/src/main/java/com/jkb/slidemenu/SlideMenuAction.java)|设置是否允许滑动视差效果|
|void|[setContentAlpha(float contentAlpha)](/slidemenu/src/main/java/com/jkb/slidemenu/SlideMenuAction.java)|设置在侧滑菜单打开时候的ContentView的透明度，`该值为1.0时表示滑动过程中无阴影`|
|void|[setContentShadowColor(int color)](/slidemenu/src/main/java/com/jkb/slidemenu/SlideMenuAction.java)|设置ContentView在滑动过程中的阴影颜色|
|void|[setContentToggle(boolean contentToggle)](/slidemenu/src/main/java/com/jkb/slidemenu/SlideMenuAction.java)|设置ContentView是否在侧滑菜单打开时候点击关闭侧滑菜单.默认false|

## 使用方式
#### 布局中使用
```xml
 <com.jkb.slidemenu.SlideMenuLayout
        android:id="@+id/mainSlideMenu"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:background="@color/white"
        app:slideMode="both">
        <include layout="@layout/content_menu_left" />
        <include layout="@layout/content_menu_right" />
        <include layout="@layout/content_menu_content" />
 </com.jkb.slidemenu.SlideMenuLayout>
 ```
 #### 注意
 **[SlideMenuLayout](/slidemenu/src/main/java/com/jkb/slidemenu/SlideMenuLayout.java)中布局的顺序是侧滑菜单布局在前，主体内容在后(为了防止右滑菜单重叠问题)。**   
 要是slideMode为both时，则SlideMenuLayout必须要有三个子视图，否则会抛出异常。
 
## 发布历史
#### v1.0.1(2017/6/9)
1、修改最低版本SDK为12.
#### v1.0.0(2017/6/8)
1、发布SlideMenuLayout，处理各个场景下的滑动冲突。  
2、封装demo。

## License
![](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f8/License_icon-mit-88x31-2.svg/128px-License_icon-mit-88x31-2.svg.png)

RollingLayout遵循MIT开源协议. 浏览[LICENSE](https://opensource.org/licenses/MIT)查看更多信息.