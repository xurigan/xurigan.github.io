# 使用cocoapods创建库工程，并将库提供给他人使用

参考链接：

https://guides.cocoapods.org/making/using-pod-lib-create.html

https://github.com/AFNetworking/AFNetworking

https://www.jianshu.com/p/d6a592d6fced

> 打个比方：假如我要开发一个网络请求库XFNetworking，别人只需要在Podfile文件中
>
> ```ruby
> pod 'XFNetworking', '~> 3.0'
> ```
>
> 就可以使用我的库了，同时我的代码也要在github上管理

上面就是这篇文章要做的事情了

## 在github上创建两个仓库

这里用A、B来做区分

A仓库：用来保存我的代码，进行代码管理和协同开发

https://github.com/xurigan/XFNetworking.git

B仓库：用来发布

https://github.com/xurigan/PodSpecRepos

## 创建pod

其实使用pod的命令创建一个工程用于开发

在终端中cd到想要创建工程的目录（我这里使用Desktop），输入

```ruby
pod lib create XFNetworking
```

终端输出

```ruby
Cloning `https://github.com/CocoaPods/pod-template.git` into `XFNetworking`.
Configuring XFNetworking template.

------------------------------

To get you started we need to ask a few questions, this should only take a minute.

If this is your first time we recommend running through with the guide: 
 - https://guides.cocoapods.org/making/using-pod-lib-create.html
 ( hold cmd and double click links to open in a browser. )
```

之后会让你在终端中回答几个问题,以下是我的回答

```ruby
What platform do you want to use?? [ iOS / macOS ]
 > iOS

What language do you want to use?? [ Swift / ObjC ]
 > ObjC

Would you like to include a demo application with your library? [ Yes / No ]
 > Yes

Which testing frameworks will you use? [ Specta / Kiwi / None ]
 > None

Would you like to do view based testing? [ Yes / No ]
 > No

What is your class prefix?
 > XF
 
```

终端输出

```ruby
Running pod install on your new library.

Analyzing dependencies
Fetching podspec for `XFNetworking` from `../`
Downloading dependencies
Installing XFNetworking (0.1.0)
Generating Pods project
Integrating client project

[!] Please close any current Xcode sessions and use `XFNetworking.xcworkspace` for this project from now on.
Sending stats
Pod installation complete! There is 1 dependency from the Podfile and 1 total pod installed.

 Ace! you're ready to go!
 We will start you off by opening your project in Xcode
  open 'XFNetworking/Example/XFNetworking.xcworkspace'

To learn more about the template see `https://github.com/CocoaPods/pod-template.git`.
To learn more about creating a new pod, see `http://guides.cocoapods.org/making/making-a-cocoapod`.

```

xcworkspace工程会直接打开，文明暂时先关闭它

cd到XFNetworking/Example/目录下，输入

```ruby
pod install
```

终端输出

```ruby
Analyzing dependencies
Fetching podspec for `XFNetworking` from `../`
Downloading dependencies
Using XFNetworking (0.1.0)
Generating Pods project
Integrating client project
Sending stats
Pod installation complete! There is 1 dependency from the Podfile and 1 total pod installed.
```

现在我们可以去打开xcworkspace工程了,目录结构如下

```ruby
XFNetworking
├── Example
│   ├── Podfile
│   ├── Podfile.lock
│   ├── Pods
│   ├── Tests
│   ├── XFNetworking
│   ├── XFNetworking.xcodeproj
│   └── XFNetworking.xcworkspace
├── LICENSE
├── README.md
├── XFNetworking
│   ├── Assets
│   └── Classes
├── XFNetworking.podspec
└── _Pods.xcodeproj -> Example/Pods/Pods.xcodeproj
```

![](/Users/xurigan/Documents/GitHub/xurigan.github.io/resource/Snip20190520_1.png)











---

关键词：静态库开发 动态库开发 