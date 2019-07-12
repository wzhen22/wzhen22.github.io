---
layout: post
title: "Ruby环境常使参考"
date: 2019-07-12   
tag: 技术工具教程
---

###Mac 环境下Ruby相关解释

* Homebrew是Mac OSX上的软件包管理工具，能在Mac中方便的安装软件或者卸载软件

```
安装Homebrew
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

- RVM:用于帮你安装Ruby环境，帮你管理多个Ruby环境，Ruby环境不仅仅是Ruby本身，还包括依赖的第三方Ruby插件。都由RVM管理

```
安装rvm
$ curl -L https://get.rvm.io | bash -s stable
可以通过rvm list 查看当前安装了哪些ruby版本
切换使用指定版本的ruby：rvm use 指定版本号（如2.0.0）
```

- Ruby是一种简单的面向对象编程语言,mac OSX系统自带ruby2.3.7。

```
1:rvm 安装
  rvm install 2.0.0
2:使用brew安装
  brew update
  brew install ruby
```

- RubyGems：是Ruby的一个包管理器，提供了分发Ruby程序和函式库的标准格式“gem”，旨在方便地管理gem安装的工具，以及用于分发gem的服务器。从Ruby 1.9版起成为Ruby标准库的一部分。类似于Python的pip。

- gem install:安装gem包，这种安装是通过RubyGems这个包管理工具来安装的

- 使用bundle install 之前需要安装bundler组件，bundler可以从gem上面下載。bundler主要针对项目安装的各gem依赖问题。

- bundle install: 
  首先，你要在你应用根目录下一个叫Gemfile文件里声明这些依赖，它看起来是这个样子的：

```
source "https://rubygems.org"

gem 'fastlane'
gem "cocoapods"
```

它告诉了 bundler 默认是在Gemfile里指定的https://rubygems.org 上来下载 指定gem。 当下载完成后会生成对应的Gemfile.lock。Gemfile.lock保存着所有gem的一个版本快照。将来使用Bundle会根据Gemfile.lock来决定Gemfile是否有修改来进行gem的更新。

### gem镜像源设置

```
sudo gem update --system
终端输入如下命令（把Ruby镜像指向taobao，避免被墙，你懂得）
gem sources --remove https://rubygems.org/ 
gem sources -a https://ruby.taobao.org/ 
gem sources -l  （用来检查使用替换镜像位置成功）
更新镜像源
gem sources --add https://gems.ruby-china.org/ --remove https://rubygems.org/
这里说明一下因域名备案问题，.org域名无法继续提供RubyGems镜像服务，现提供.com 代替
https://gems.ruby-china.com/
```

### 安装CocoaPods

```
终端输入：sudo gem install cocoapods 
备注：苹果系统升级 OS X EL Capitan 后改为$sudo gem install -n /usr/local/bin cocoapods
$pod setup
```

pod setup命令执行后原理是将**Spec**项目复制到当前用户的**.cocoapods\master**目录下,以后的查找、安装使用都是基于该本地目录的。安装成功后，就可以尝试使用了,**以后更新新版本的Spec项目只需要再次执行pod setup即可**

### Ruby的管理工具

**rbenv**和**RVM**

rvm的使用--[参考教程](https://www.jianshu.com/p/a703135682a3)

[rbenv 使用指南](https://ruby-china.org/wiki/rbenv-guide)

[rbenv与rvm的区别](https://www.jianshu.com/p/85c5f49d737b)

### JekyII安装教程

[JekyII on macOS](https://jekyllrb.com/docs/installation/macos/)  官方提供的参考网址