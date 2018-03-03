---
title: Node.js常用知识点
date: 2017-10-23 19:17:57
tags: Nodejs
---
Node.JS 常用知识点总结
=================
1. 常用第三方

        1. bodyParser :解析POST请求
        2. cookies :操作 cookie
        3. swing  :模板解析引擎
        4. mongoose :操作 mongoDB
        5. markdown :解析 MarkDown
 2. nodejs 项目文件目录
        
        1. db ：数据库存储
        2. models ：数据库模型文件
        3. schemas ：数据库结构文件目录
        4. views ：模板视图文件目录
        5. app.js ：应用入口文件
        6. public ：公共文件目录
        7.routers ：路由目录
     
 3. app.js 内容
 
        1.  模块的划分
            app.use('route',function)
 
 4. 登陆 moongoDB
    
        如果数据库开启了验证机制，则在连接时需要提供验证
        
        > mongoose.connect("mongodb://root:123456@123.207.72.192:27017/Nodejs?authSource=admin" ,function(err){});
        
        这里的 err 中包含了  连接错误的信息，对于admin以外的数据库，需要指明用户登陆验证所使用的数据库，即 ?authSource=admin