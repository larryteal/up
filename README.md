# 操作系统 Centos 7
# 在git 中使用ssh提交代码
首先要在开发机器上生成公钥私钥，然后登陆到git服务器上配置SSH，把生成的公钥粘贴到key 字段中
#### 生成ssh密钥的命令是：ssh-keygen，（在.ssh目录中的id_rsa.pub是生成的公钥

***
# express 的 body-parser
body-parser无法解析 enctype="multipart/form-data" 类型的表单，同样postman在提交数据时
数据类型要选则x-www-form-urlencoded，而不是form-data类型，如须上传文件数据，可以使用
formidable 中间件。

***
# session
session 分为两个部分 session id 和 session data 其中session id 保存到客户端的cookie中
而 session data 部分即可以保存到客户端cookie中也可以保存到服务器端的内存或数据库中，但是出于
安全考虑session data 一般放到后端服务器而不是客户端。（可以把session存储到Redis中）

***
# 跨域Ajax post 提交数据
## 客户端设置
    $.ajax({
        type: "post",
        url: "http://localhost:8082/captcha/check",
        xhrFields: { withCredentials: true },
        crossDomain: true,
        data : {"data":val},
        success: function(data){},
        error: function(){}
    });
## 服务器端设置 （使用了express库和cors库）
    var cors = require('cors');
    var cors_option = {
        "origin" : ["http://localhost:8089","http://localhost:8083"],
        "methods": "GET,POST",
        "credentials" : true
    };
    app.use(cors(cors_option));

***
# 验证码逻辑
## 获取验证码：
在数据库中建立邮箱/手机号与验证码的对应关系以 key --> value 的关系 存储。
## 校验验证码：
客户端需要提供申请验证码时的key和用户输入的验证码，服务器端根据获取的key来查找value，
并把value和用户输入的验证码进行比较。

（ 比对后用一个随机数覆盖掉原来的value值，也可以对key --> value 设置一个过期时间 ；
 浏览器图片验证码可以使用 session id 和 session data 来保存这种key --> value的对应关系；
 可以使 Redis 作为这种 key --> value 关系的存取数据库）

***
# 三级分销系统上下级关系表设计
user_id  parent_id_1 parent_id_2 parent_id_3 user_deep ...

```

graph TB
    A[roo] --> B((child 1))
    A --> C((child 2))
    A --> D((child 3))
    B --> E((child 4))
    B --> F((child 6))
    B --> G((child 6))
    B --> H((child 7))
    C --> I((child 8))
    D --> J((child 9))
    D --> K((child 10))
    D --> L((child 11))
    E --> M((child 12))
    E --> N((child 13))
    M --> O((child 14))
    M --> P((child 15))
    M --> Q((child 16))
    M --> R((child 17))

```





















