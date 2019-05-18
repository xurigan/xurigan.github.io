

https://guides.cocoapods.org/

# CocoaPods使用

## 一、入门

### 1.Cocoapods简介

> CocoaPods manages library dependencies for your Xcode projects.
>
> The dependencies for your projects are specified in a single text file called a Podfile. CocoaPods will resolve dependencies between libraries, fetch the resulting source code, then link it together in an Xcode workspace to build your project.
>
> Ultimately the goal is to improve discoverability of, and engagement in, third party open-source libraries by creating a more centralised ecosystem.

CocoaPods是用来管理Xcode工程中依赖的库，一般是第三方的公开库或者自己制作的私有库，比如AFNetworking

这些库是声明在一个叫**Podfile**的文件中的，CocoaPods会解析这个Podfile文件，将所有的库进行统一的管理，在Xcode workspace中编译到你的工程/项目。

[YouTube上的介绍](https://www.youtube.com/watch?v=iEAjvNRdZa0&spfreload=10)

### 2.基础操作

#### 2.1.安装

CocoaPods是用的[Ruby](https://www.ruby-lang.org/zh_cn/)来构建的，macOS上已经提供了标准的Ruby了，建议使用最新版本的macOS，比如我现在是10.14.4

打开终端，输入

```ruby
sudo gem install cocoapods
```

然后回车，然后可能会要求你输入开机密码，输入密码之后回车即可

#### 2.2.更新

在终端中输入

```ruby
sudo gem install cocoapods
```

回车后输入密码再次回车

下面这个是我本次更新在终端显示的日志

```ruby
Fetching: cocoapods-core-1.6.2.gem (100%)
Successfully installed cocoapods-core-1.6.2
Fetching: cocoapods-1.6.2.gem (100%)
Successfully installed cocoapods-1.6.2
Parsing documentation for cocoapods-core-1.6.2
Installing ri documentation for cocoapods-core-1.6.2
Parsing documentation for cocoapods-1.6.2
Installing ri documentation for cocoapods-1.6.2
Done installing documentation for cocoapods-core, cocoapods after 5 seconds
2 gems installed
```

### 3.在Xcode工程中使用pods

#### 3.1.在已有的项目中使用pods

我这里新建一个Xcode工程作为示例，你也可以先在新工程里试一试，掌握之后再在你的项目中使用

我在桌面上创建一个工程叫testCocoaPods

![](/Users/xurigan/Documents/GitHub/xurigan.github.io/resource/Snip20190518_4.png)

打开终端

cd到testCocoaPods目录下

```ruby
cd Desktop/testCocoaPods/
```

输入

```ruby
touch Podfile
```

会在文件夹中创建一个Podfile的文件，双击打开Podfile文件，粘贴如下代码并保存

```ruby
target 'testCocoaPods' do
  pod 'AFNetworking'
end
```

cd到testCocoaPods目录下，ls一下确认已经有Podfile文件

```ruby
Podfile			testCocoaPods		testCocoaPods.xcodeproj
```

继续输入

```ruby
pod install
```

回车后，终端中输入如下信息

```ruby
Analyzing dependencies
Downloading dependencies
Installing AFNetworking (3.2.1)
Generating Pods project
Integrating client project

[!] Please close any current Xcode sessions and use `testCocoaPods.xcworkspace` for this project from now on.
Sending stats
Pod installation complete! There is 1 dependency from the Podfile and 1 total pod installed.

[!] Automatically assigning platform `ios` with version `12.2` on target `testCocoaPods` because no platform was specified. Please specify a platform for this target in your Podfile. See `https://guides.cocoapods.org/syntax/podfile.html#platform`.
```

同时查看testCocoaPods文件夹

![](/Users/xurigan/Documents/GitHub/xurigan.github.io/resource/Snip20190518_8.png)

多出了几个文件和文件夹

双击'testCocoaPods.xcworkspace'来打开工程，之后都将使用这个**xcworkspace**来进行开发，不再使用'testCocoaPods.xcodeproj'了

**(如果刚才创建testCocoaPods.xcodeproj后xcode没有关闭这个项目记得先关闭再打开testCocoaPods.xcworkspace)**

![](/Users/xurigan/Documents/GitHub/xurigan.github.io/resource/Snip20190518_11.png)

之后就可以在熟悉的AppDelegate.m、ViewController.m或者其他喜欢的地方

```objective-c
#import <AFNetworking.h>
```

#### 3.2.使用pods创建新的项目

我们也可以用cocoapods创建一个新的项目

像往常一样在Xcode中创建一个新项，比如名字叫MyApp

在终端cd到MyApp目录

```ruby
cd Desktop/MyApp/
```

```ruby
pod init
```

这会在MyApp目录下创建Podfile文件，双击打开Podfile文件，可以看到

```ruby
# Uncomment the next line to define a global platform for your project
# platform :ios, '9.0'

target 'MyApp' do
  # Uncomment the next line if you're using Swift or would like to use dynamic frameworks
  # use_frameworks!

  # Pods for MyApp

end
```

[^]: #后面的都是注释

打开第二行的注释，来制定平台和版本

```ruby
platform :ios, '9.0'
```

target后面指定的就是工程名

do和end之间来添加cocoapod

比如AFNetworking，也可以指定AFNetworking的版本

```
pod 'AFNetworking', '~> 3.0'
```

编辑完Podfile文件之后就可以在终端里

```ruby
pod install	
```

```ruby
Analyzing dependencies
Downloading dependencies
Installing AFNetworking (3.2.1)
Generating Pods project
Integrating client project

[!] Please close any current Xcode sessions and use `MyApp.xcworkspace` for this project from now on.
Sending stats
Pod installation complete! There is 1 dependency from the Podfile and 1 total pod installed.
```

可以看到使用的AFNetworking版本是3.2.1而不是3.0，这是因为

~> 3.0代表3.0到4.0之间(不包括4.0)的最高的一个版本

也可以使用其他的运算符

> - `'> 0.1'` Any version higher than 0.1
> - `'>= 0.1'` Version 0.1 and any higher version
> - `'< 0.1'` Any version lower than 0.1
> - `'<= 0.1'` Version 0.1 and any lower version

或者

> - `'~> 0.1.2'` Version 0.1.2 and the versions up to 0.2, not including 0.2 and higher
> - `'~> 0.1'` Version 0.1 and the versions up to 1.0, not including 1.0 and higher
> - `'~> 0'` Version 0 and higher, this is basically the same as not having it.



---

关键词：cocoapods ruby 库管理 第三方库 lib .a .framework enter password 逻辑运算符















