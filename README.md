# TBDialogLibrary
地址：https://github.com/tongzhenggang/TBDialogLibrary
对Android的底部弹窗、顶部弹窗菜单及自定义界面的使用封装。

----------
## 一、配置
 
1. Add it in your root build.gradle ：
 ```java
 allprojects {
     repositories {
         ...
         maven {
             url 'https://jitpack.io'
 
         }
 
 }
 ```
 
2. Add the dependency
```java
dependencies {
	 compile 'com.github.tongzhenggang:TBDialogLibrary:1.0'
}
```

3. 忽略com.android.support:appcompat-v7:25.3.1配置引用方法（一般情况不需要使用该方式）
```java
    compile('com.github.tongzhenggang:TBDialogLibrary:1.0') {
        exclude(group: 'com.android.support', module: 'appcompat-v7')
    }
```

---

## 二、使用方法

    PopWindow popWindow = new PopWindow.Builder(this)
                .setStyle(PopWindow.PopWindowStyle.PopUp)
                .setTitle("注意")
                .setMessage("今天天气不错")
                .addItemAction(new PopItemAction("选项1"))
                .addItemAction(new PopItemAction("选项2", PopItemAction.PopItemStyle.Normal))
                .addItemAction(new PopItemAction("选项3", PopItemAction.PopItemStyle.Normal, new PopItemAction.OnClickListener() {
                    @Override
                    public void onClick() {
                        Toast.makeText(MainActivity.this, "选项3", Toast.LENGTH_SHORT).show();
                    }
                }))
                .addItemAction(new PopItemAction("确定", PopItemAction.PopItemStyle.Warning, new PopItemAction.OnClickListener() {
                    @Override
                    public void onClick() {
                        Toast.makeText(MainActivity.this, "确定", Toast.LENGTH_SHORT).show();
                    }
                }))
                .addItemAction(new PopItemAction("取消", PopItemAction.PopItemStyle.Cancel))
                .create();
        popWindow.show();

  效果图：
 ![](https://github.com/tongzhenggang/TBDialogLibrary/blob/master/other/show1.png)



说明：封装基于HMY314的PopWindow

