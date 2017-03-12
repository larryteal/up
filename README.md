# 操作系统 Centos 7
# 在git 中使用ssh提交代码
首先要在开发机器上生成公钥私钥，然后登陆到git服务器上配置SSH，把生成的公钥粘贴到key 字段中
#### 生成ssh密钥的命令是：ssh-keygen，（在.ssh目录中的id_rsa.pub是生成的公钥）
---
# express 的 body-parser
body-parser无法解析 enctype="multipart/form-data" 类型的表单，同样postman在提交数据时
数据类型要选则x-www-form-urlencoded，而不是form-data类型，如须上传文件数据，可以使用
formidable 中间件。
---
# session
session 分为两个部分 session id 和 session data 其中session id 保存到客户端的cookie中
而 session data 部分即可以保存到客户端cookie中也可以保存到服务器端的内存或数据库中，但是出于
安全考虑session data 一般放到后端服务器而不是客户端。（可以把session存储到Redis中）



