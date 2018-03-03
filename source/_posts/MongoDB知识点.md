---
title: MongoDB知识点
date: 2017-10-23 19:17:16
tags: MongoDB
---
MongoDB 知识点总结
======================
1. **安装数据库**
    
        apt-get install mongodb
2. **配置远程登陆**

        默认的 mongod 命令为启动 mongodb 的命令， 但是在启动时不会加载config 文件
        
        mongod -f  /etc/mongo.conf
        
        可以强制使用mongo的conf文件
        配置远程连接的配置如下
        1. 使用 mongod 启动本地mongodb数据库
            >  mongod  
        2. 使用mongo 链接本地数据库，不加载配置文件的情况下默认不需要验证权限
            >  mongo 127.0.0.1:27017
        mongodb的默认端口为27017
        3. 增加user
            > use admin
            > db.addUser('root', '123456');
            >exit
        4. 更改配置文件内容
            bind_ip = 127.0.0.1 将此句话注释，则为监听所有ip
            > #bind_ip = 127.0.0.1
            增加登陆验证
            >auth = true
        5. 开放相应防火墙端口
            > iptables -A INPUT -p tcp -m state --state NEW -m tcp --dport 27017 -j ACCEPT
        5. 重启数据库
            > mongod -f /etc/mongo.conf
3. **图形化管理工具 MongoVUE**
        
        bing上有不少破解资源 