# React 服务端渲染

## 使用

### 1、启动前端工程:
前端开发目录为：client/
```
npm i
npm start
// 浏览器打开 http://localhost:8000/
```

### 2、启动服务端：
客户端开发及部署在根目录

```
npm i pm2 -g
npm i
npm start
// 浏览器打开 http://localhost:3000/
```

### 3、启动 Mysql：
- 先搭建 mysql 环境：官网下载mysql
- 安装一个 mysql 的可视化工具，我选择的是：Navicat Premium

启动mysql后，打开 mysql 可视化工具 Navicat Premium，
- 连接数据库，账号密码在 `server/config/db.json`
- 建表，本仓库提供了一份数据可以将 `mysql/user.sql` 直接导入


Done!



### 数据库如何操作？

建立连接
Sequelize会在初始化时设置一个连接池，这样你应该为每个数据库创建一个实例：
```
var sequelize = new Sequelize('database', 'username', 'password', {
  host: 'localhost',
  dialect: 'mysql'|'mariadb'|'sqlite'|'postgres'|'mssql',
  pool: {
    max: 5,
    min: 0,
    idle: 10000
  },

  // 仅 SQLite 适用
  storage: 'path/to/database.sqlite'
});

// 或者可以简单的使用一个连接 uri
var sequelize = new Sequelize('postgres://user:pass@example.com:5432/dbname');
```



## 查看服务器日志
```
pm2 log
```

## 项目结构
```
├── client 前端目录
|
├── mysql 数据库（第一次使用可以直接导入到本地）
|
├── public 服务器静态资源
|
└── server 后端目录
    ├── auth 权限验证 存放用户验证部分
    ├── config 数据库 配置文件 Sequelize（可以对多种数据库进行操作）
    ├── controllers 后端控制层 C 层的代码存放目录
    ├── models 操作 数据库 代码逻辑
    ├── routes 后端路由
    └── view 后端页面
```

### ps:
- server/models
Model相当于数据库中表，有时它也会被称为“模型”或“工厂”。`Model`不能通过构造函数创建，而只能通过`sequlize.define`方法来定义或通过`sequlize.import`导入。通过`define`定义一个`Model`，就相当于定义了一种模型与数据表之间的映射关系，通过模型可以实现对表记录的增、删、改、查等操作。

## License

MIT
