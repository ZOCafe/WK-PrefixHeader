# Prefix-Header
Prefix Header for Objective-C project

1. cd到当前目录

```
$ cd WKPrefixHeader
```

2.创建一个podspec文件,命令:

```
$ pod spec create WKPrefixHeader
```

3.编辑 podspec文件，这里是用vim打开的，命令：

```
$ open WKPrefixHeader.podspec
```

4.创建之后会自动生成一个模板，里面会有详细的注释，我们只需要按需要修改这个文件即可，下边这个是测试的时候我编辑的 （如果需要更更多的配置 可以参考别的开源项目的podspec文件）：

```
Pod::Spec.new do |s|
  s.name         = "WKPrefixHeader"
  s.version      = "0.0.2"
  s.summary      = "something about prefix header of WKPrefixHeader."
  # s.description  = <<-DESC
  #                  DESC

  s.homepage     = "https://github.com/OComme/WK-Prefix-Header"
  s.license      = "MIT"

  s.author             = { "OComme" => "a163913692@icloud.com" }
  s.platform     = :ios, "8.0"
  s.requires_arc = true
  s.source       = { :git => "https://github.com/OComme/WK-Prefix-Header.git", :tag => "#{s.version}" }
  s.source_files = "WKPrefixHeader/*"
end
```
5.创建tag，并推送到git,依次执行以下命令：
```
$ git tag 0.0.1
$ git push --tags
```

6.验证podspec文件 
```
$ pod spec lint WKPrefixHeader.podspec
```

7.如果验证不通过，会有详细的ERROR和WARING提示，根据提示依次解决，然后回到第6步重新来一遍。
注意：在重新开始之前，我们要删除远程库的tag和本地的tag，命令如下：
```
$ git tag -d 0.0.1                   //删除本地tag
$ git push origin :refs/tags/0.0.1  // 删除远程库tag
```

8.验证通过后，提交到CocoaPods或私有Specs。
```
$ pod trunk push WKPrefixHeader.podspec          //提交到CocoaPods
$ pod repo push WKSpecs WKPrefixHeader.podspec   //提交到私有Specs
```
9.如果是第一次提交，需要先执行这个命令：
```
$ pod trunk register 这里写邮箱 '这里起个名字' --description=' 这里写描述'
```
执行完成之后，会给你的邮箱里发一封邮件，去邮箱点击链接之后，再重新执行第8步即可！
