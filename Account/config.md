# 资金账号配置

环境配置好之后 需要使用zt-trade分配的账号和密码进行身份校验 以指定对应的资金账号进行交易

zt-trade账号相关可以加qq群 123456 咨询

##### 1. 账号校验

在zt-trade/server.js下输入系统和资金账号

```
// 1. 引入实盘函数
let brokerService = require('./common').brokerService

// 2. 初始化系统
brokerService('zhongtai', 'init', null, async (res) => {

    // 3. 远程校验zt-trade权限
    let info = await brokerService('zhongtai', 'check', {
        account: 'zttrade1',
        password: 'zttrade1',
        brokerAccount: '123456' 
    })

    console.log('info => ', await info)

    if (info.data.status) {

        // 4. 进程启动完成开始登录
        // 输入安装路径
        // 资金账号
        // 资金密码
        await brokerService('zhongtai', 'login', {
            path: `E:\\\xiadan\\xiadan.exe`,
            account: '资金账号',
            password: '资金密码'
        })
    }
})

```

##### 2. 启动本地接口服务
cd zt-trade && node server.js 启动本地接口server
