# 资金账号配置

环境配置好之后 需要使用zt-trade分配的账号和密码进行身份校验 以指定对应的资金账号进行交易

zt-trade账号相关可以加qq群 273896202 咨询

##### 1. 账号校验

在zt-trade/user.json下替换相关信息

```
{
    "path": "替换券商客户端的路径", // 例如: E:\\\\zt\\xiadan.exe 不要有中文
    "account": "zt-trade账号",
    "password": "zt-trade密码",
    "brokerAccount": "券商资金账号",
    "brokerPassword": "券商资金密码"
}
```