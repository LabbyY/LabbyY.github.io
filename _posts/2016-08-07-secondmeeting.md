---
layout:            post
title:             "8.7 CGC Meeting Record"
menutitle:         "8.7 CGC Meeting Record"
category:          Meeting Record
author:            LabbyY
tags:              meetingrecord
cover:             /media/img/universe1.jpg
---
### 上周回顾

- 大家普遍反映《Ruby基础教程》中第三章关于文件IO的内容难以理解。
- 代码小作业[计算小程序][]，一名学员完成
- Coursera 第一周课程，全部学员完成

### Marks

- 使用 [Gist][] 可以上传并分享 script
- 使用 [Lantern][] 翻越 GFW

### 本节课相关代码/命令

#### Git部分

```ruby
git clone git@github.com:CocaColaCat/SZCGC2016.git alias #从指定地址下载repo并起一个别名
#Fork the Repository, 然后
git remote add alias.checker git@github.com:LabbyY/SZCGC2016.git # 添加一个新的远程repo并将该别名的checker引用至新repo
git push alias.checker master
#Pull Request, 然后就可以在原始reop的pull request list中看到该request
```

#### 计算小程序部分

- 去掉换行符：
    - (Kernal.gets()方法得到的输入值都有换行符，因此在运算和输出时要将换行符去掉)
    
    `attr = gets.chomp`


- [一些关于字符串的语法糖]

  ```ruby
  #以下代码新建字符串数组limit，并检查该数组中是否包含attr
  limit = %w(plus cut multi div)
  limit.include?(attr)
  ```

- 查看原型

    `attr.inspect`

- [send][]:通过符号调用方法

  [to_sym][]:返回symbol对应的object

    `c.send :add op.to_sym`

- 当需要直接访问外部连接时：

  ```ruby
  require 'open-uri' # open-uri API
  open('http://link') # 使用方法与file相同
  ```

- split方法将str按照空格符分隔为一个数组

  `str.split(" ")`

- 代码块可以将自身传递给方法

  `arr.inject(0){|sum,i| sum +=1 if i.match(/UCanUup/); sum}`


### To-Do List
- Install [zshell][]  √
- Read Go Pro Git

[一些关于字符串的语法糖]:https://ruby-china.org/topics/18512
[计算小程序]:https://tower.im/projects/d59c4198d1b84822aa345bb363566d25/docs/dcacfe724a5d438cb81061dd43dc0434/
[send]:http://ruby-doc.org/core-1.8.7/Object.html#method-i-send
[to_sym]:http://ruby-doc.org/core-2.2.3/Symbol.html#method-i-to_sym
[zshell]:https://github.com/robbyrussell/oh-my-zsh
[Gist]:https://gist.github.com/LabbyY/1bd09259564ca496e8cfc79cb642d5ee
[Lantern]:https://github.com/getlantern/lantern



[^1]: Some footnote
[^2]: Another footnote
[^3]: Last footnote
