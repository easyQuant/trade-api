# 资金账号配置

环境配置好之后 需要使用zt-trade分配的账号和密码进行身份校验 以指定对应的资金账号进行交易

zt-trade账号相关可以加qq群 273896202 咨询

##### 1. 账号校验

在zt-trade/user.json下替换相关信息

```
{
    "path": "E:\\\\xxxxxx\\xiadan.exe",
    "account": "zt-trade账号",
    "password": "zt-trade密码",
    "brokerAccount": "券商资金账号",
    "brokerPassword": "券商资金密码"
}
```

##### 2. 启动本地接口服务

```
cd zt-trade && node server.js 启动本地接口server
```
