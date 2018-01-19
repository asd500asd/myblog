# 项目结构
- models: 存放操作数据库的文件
- public: 存放静态文件，如样式、图片等
- routes: 存放路由文件
- views: 存放模板文件
- index.js: 程序主文件
- package.json: 存储项目名、描述、作者、依赖等等信息

# 项目初始依赖模块
- express: web 框架
- express-session: session 中间件
- connect-mongo: 将 session 存储于 mongodb，结合 express-session 使用
- connect-flash: 页面通知的中间件，基于 session 实现
- ejs: 模板
- express-formidable: 接收表单及文件上传的中间件
- config-lite: 读取配置文件
- marked: markdown 解析
- moment: 时间格式化
- mongolass: mongodb 驱动
- objectid-to-timestamp: 根据 ObjectId 生成时间戳
- sha1: sha1 加密，用于密码加密
- winston: 日志
- express-winston: express 的 winston 日志中间件

# 会话
- 由于 HTTP 协议是无状态的协议，所以服务端需要记录用户的状态时，就需要用某种机制来识别具体的用户，这个机制就是会话（Session）。

- cookie 与 session 的区别

- cookie 存储在浏览器（有大小限制），session 存储在服务端（没有大小限制）
通常 session 的实现是基于 cookie 的，session id 存储于 cookie 中
session 更安全，cookie 可以直接在浏览器查看甚至编辑

- connect-flash 是基于 session 实现的，它的原理很简单：设置初始值 req.session.flash={}，通过 req.flash(name, value) 设置这个对象下的字段和值，通过 req.flash(name) 获取这个对象下的值，同时删除这个字段，实现了只显示一次刷新后消失的功能。
