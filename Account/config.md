# 资金账号配置

环境配置好之后 需要使用zt-trade分配的账号和密码进行身份校验 以指定对应的资金账号进行交易

zt-trade账号相关可以加qq群 123456 咨询

##### 1. 账号校验

在zt-trade/server.js下输入系统和资金账号

```
// 1. 引入实盘函数
let brokerService = require('./common').brokerService

// 2. 远程校验zt-trade权限
let info = brokerService('zhongtai', 'check', {
    account: 'zt-trade的账号',
    password: 'zt-trade的密码',
    brokerAccount: '对应的资金账号' 
})

// 3. 身份校验没问题后 初始化系统
brokerService('zhongtai', 'init')

// 4. 执行资金账号登录操作
brokerService('zhongtai', 'login', {
    account: '券商资金账号',
    password: '券商资金密码'
})
```

##### 2. 启动本地接口服务
cd zt-trade && node server.js 启动本地接口server