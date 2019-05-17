# Mac 防止误触电源键，而关闭显示器

最近使用公司配的MacBook Pro，发现想按delete键时很容易不小心按到Power键关闭显示器，delete键的使用是很高频的，但是总按到power给我带来很多不便

![](/Users/xurigan/Desktop/Snip20190517_1.png)

启动终端，输入如下命令：

```Ruby
defaults write com.apple.loginwindow PowerButtonSleepsSystem -bool no
```

然后回车就可以了

现在如果点按电源按钮是没有任何反应的，只有长按才会出现

![](/Users/xurigan/Documents/GitHub/xurigan.github.io/resource/Snip20190517_3.png)

如果想恢复原来的设置 no 改成 yes就可以了

```ruby
defaults write com.apple.loginwindow PowerButtonSleepsSystem -bool yes
```

---

关键字keywords：delete power key button 回退 删除 按钮 电源 按键 误触 误点 不小心 按到 关屏 息屏 显示器 

[https://xurigan.github.io/](https://xurigan.github.io/)

