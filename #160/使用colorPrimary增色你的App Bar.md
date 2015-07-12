app bar或者是action bar是Android App的一部分，有些时候，我们希望能够个性化我们的app：使用branding color来作为app bar的背景颜色。

color palette（AppCompat提供的直接的解决方法），在5.0中增加的material design中，Android 2.1设备中同样可以使用AppCompat这项技术。

如果你正在使用诸如：`Theme.AppCompat`，你需要添加**colorPrimary**属性：

```xml
<style name="AppTheme" parent="@style/Theme.AppCompat">
<item name="colorPrimary">@color/primary</item>
</style>
```
这样，App Bar会进行颜色的自适应。注意到的是，使用的是*colorPrimary*,而非*android:colorPrimary*,因为*android:colorPrimary*仅仅只能在android 5.0或者以上的设备中，但是AppCompat中提供的*colorPrimary*却不是。请确保你使用了正确的Theme，以保证text和icons具备足够的对比性：

- Theme.AppCompat->dark activity,dark app bar;
- Theme.AppCompat.Light->light activity,light app bar;
- Theme.AppCompat.Light.DarkActionBar->light activity,dark action bar.

但是，或许你已经早就使用了Toolbars（或许是使用了在Design Library's AppBarLayout)。如果正是如此，或许你正在使用*Theme.AppCompat.NoActionBar*或者*Theme.AppCompat.Light.NoActionBar*,并且早将这些元素写在了xml文件中。谢天谢地，我们仍旧可以通过**?attr/colorPrimary**使用：	

```xml
<android.support.v7.widget.Toolbar
android:background="?attr/colorPrimary" />
```
好了：**?attr/**这种样式允许你使用当前theme中任意的attribute，避免了在文件中寻找的麻烦。

介于并没有*Theme.AppCompat.Light.DarkActionBar.NoActionBar*的存在，我们将失去text color的自渲染。没关系，在xml中可以进行theme的**ThemeOverlay**，即是Theme的覆写。值得注意的是，不同于完整的theme的覆写，只会覆写当前的Theme，并改变那些我们希望改变的东西。举个例子，如果我们希望一个light theme，但是一个dark Toolbar,我们可以这样使用：

```xml
<android.support.v7.widget.Toolbar
android:background="?attr/colorPrimary"
android:theme="@style/ThemeOverlay.AppCompat.Dark.ActionBar"/>
```
这样，我们的text和icon将会成为白色。this is perfect for a dark Toolbar.

事实上，你可以找到许多你能够找到的颜色对你的5.0的设备的status bar的颜色进行渲染。比方说：**colorPrimaryDark**--使得status bar的背景色更深点，**colorAccent**--使得类如 FloatActionBar 的颜色与周围有着对比，这样看来，就真正的突出了。

现在开始，尽情的享受**colorPrimary**吧！

资料链接：		
[http://goo.gl/Meu1sE](http://goo.gl/Meu1sE)	
[https://goo.gl/EHaUMj](https://goo.gl/EHaUMj)	
[https://goo.gl/Wo1IBv](https://goo.gl/Wo1IBv)	
[https://www.youtube.com/watch?v=5Be2mJzP-Uw﻿](https://www.youtube.com/watch?v=5Be2mJzP-Uw﻿)

