---
layout:            post
title:             "8.21 CGC Meeting Record"
menutitle:         "8.21 CGC Meeting Record"
category:          Meeting Record
author:            LabbyY
tags:              meetingrecord
cover:             /media/img/universe1.jpg
---

### 重新做一遍todo-list

#### Model 和 DB

- rails目录的组织架构、重要的文件和文件夹
- 要添加用户信息，`rails new`,修改`Gemfile`中的gem source后，新加一个用来加密的包：

  ```Ruby
  #加密密码
  gem 'bcrypt', '~>3.1.7'
  ```
- 新建一个migration

   ```Ruby
   #单词首字母大写、结尾是复数
   rails generate migration CreateTodos
   ```
- 在db->migration下的文件中加入字段,并创建数据库、表、model

  ```ruby
  rake db:create
  rake db:migrate
  #然后在model中新建一个todo.rb;
  class Todo < ApplicationRecord

  end
  #todo的命名也是约定，必须是数据库表的单数形式，因为它表示的是单张表
  rake c
  rake console #or
  #进入rails的控制台（与irb类似），新建并插入一条数据
  todo = Todo.new(title: 'title name', finished: false)
  todo.save
  #新建一个migration，保存一些默认值
  rails generate migration ChangeTodosFinishedDefault
  #表名，字段名，类型，默认值
  change_column :todos, :finished, :boolean, default: false
  #新建一张user表
  rails generate migration CreateUsers
  #表中的字段
  t.string :nickname
  t.string :email
  t.string :password_digest
  #上面安装的加密包只识别password_digest字段并将它加密
  #为了满足一对多的用户-list模型，需要新加一张给todolist添加userid的表
  rails generate migration AddUserIdToUsers
  #↓
  add_column :todos, :user_id, :integer
  add_index :todos, :user_id
  #执行migration
  rake db:migrate
  #在user和todo的model中加入对映关系和安全密码

  class User < ApplicationRecord
    has_secure_password
    has_many :todos
  end

  class Todo < ApplicationRecord
    belongs_to :user
  end

  #在控制台里，用authenticate方法验证密码的正确性，正确返回user对象，错误返回false
  u = User.new
  u.nickname = "Labby"
  u.email = "e@163.com"
  u.password = "rrrttt"
  u.authenticate("rrrttt")
  ```

  #### 创建前端页面

  - 使用`rake routes`查看 get与controller中方法的映射关系
  - form 表单可以发送post请求
  - 修改routes.rb，添加sessions资源
