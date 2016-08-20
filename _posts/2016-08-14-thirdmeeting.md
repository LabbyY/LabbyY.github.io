---
layout:            post
title:             "8.14 CGC Meeting Record"
menutitle:         "8.14 CGC Meeting Record"
category:          Meeting Record
author:            LabbyY
tags:              meetingrecord
cover:             /media/img/universe1.jpg
---

### 上周回顾

- 部分人不太懂第八章存取器
- 部分人不太懂与块相关的内容
- 3~4人进行了线上Coursera课程，1人完成

### 难点讲解

- 作用域和存取器

  属性是封装在类中的，因此需要存取器来对属性进行存取操作

- 鸭子类型

  ruby不会对数据的具体类型进行区分，如果某方法需要对传递进来的参数进行处理，那么只要该参数能够进行该项处理，就可以执行程序，而不必对传参类型进行区分。
  使用`method.respond_to?(:method_name)`来判断某对象是否实现了该方法。

- 块

  是任何方法的隐藏参数（因此即使不使用也可以传进去）
  它一定要依附于方法才可以使用。
  使用`yield`关键字增加了灵活度，在需要执行某方法的时候才把它取出来。

  在 module、class、def等关键字构建的作用域（封闭的空间）中：
    - 块为这些封闭空间中的属性提供了穿越空间的可能
    - 块扩展了这些封闭空间，以便随时能在`yield`关键字处执行任何代码块


- gem：Ruby软件包管理工具

  为代码共享提供了统一标准

### Rails 简介

- 是一个web开发框架（参考汉东发的pdf）
- 全栈
- 是一个MVC框架
    - 模型 - 处理逻辑业务
    - 控制器 - 处理路由页面跳转
    - 视图 - 生成html
- Restful
- 通过`rails new alias`新建一个rails项目
- 通过`rails console`运行
- conifg => routes.rb 中指定了路由方法。
- app=>controllers中指定了响应的controller.
    - 使用routes => resources 中的匹配路径名命名：route_controller
- db下的文件定义了数据表的形式

  ```ruby
    rails generate migration table_name #生成一个解析表原型的文件
    rake db:migrate #创建数据表
  ```
- 对象关系模型
    - module下的类为映射类（只要声明类名即可）
    - 数据表映射出了一个类，由该类的实例来完成数据表的增删改查
- -b 0.0.0.0 vm


### To-Do list

  - 读汉东发的pdf，了解元编程、gem、ruby的应用领域
  - 继续学习Coursera
  - 根据栗子制作一个可以增删改的 to-do list Web 应用

### 问题

  - View中的标签怎么查询？<%= %>和<% %>有什么区别？
  - View中的类是什么类？比如box
  - controller中edit空方法的意义是什么？
  - 以下在TodosController方法中的`:todo`是从哪来的？
    ```ruby
    def todo_params
      todo_params = params[:todo]
      todo_params ? todo_params.permit(:title, :remark, :is_finished) : {}
    end
    ```
  - `_form.html.erb`命名前的下划线是什么样的约定？
  - `resource.rb`下的`resources :todos`是用来干什么的？
  - index 和 form 中的 @todos 与 @todo 有什么关系吗？
  - 以下方法中的`@todo`是新建了一个变量后修改变量中的attribute还是直接修改params中的数据？`.new`的意义何在？
      ```ruby
    def build_todo
      @todo ||= todo_scope.new
      @todo.attributes = todo_params
    end
      ```

  - View 和 Controller如何交互的？以delete为例

      `<%= link_to "Delete", todo_path(todo.id), method: :delete %>`

    ```ruby
    def destroy
      @todo.destroy
      respond_to do |format|
        format.html { redirect_to todos_url, notice: '删除成功' }
      end
    end
    ```
  - build_todo方法有什么作用？？
    ```ruby
    def build_todo
      @todo ||= todo_scope.new
      @todo.attributes = todo_params
    end
    ```
  - update 方法和 edit 方法有什么区别？
  - controller 私有方法改写失败
