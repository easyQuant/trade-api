# 运行

##### 1. 启动本地接口服务

```
cd zt-trade && node server.js 启动本地接口server
```

##### 2. 登录成功后 启动浏览器 测试接口

```
http://127.0.0.1:3001/api/position 地址栏输入
```

##### 3. 简单但是完整的策略

```
import requests

## 在策略代码顶端添加本地server地址
REAL_URL = "http://127.0.0.1:3001"

## 获取持仓
handle_position ():
    return requests.get(REAL_URL + "/api/position").json()
    
## 下限价买单
handle_buy ():
    r = requests.get(REAL_URL + "/api/buy", params = {
        "stock": "000001",
        "price": 16.00,
        "amount": 100
    }).json()

position = handle_position()
cash = position['portfolio']['available_cash']

## 如果可用资金大于0 买入一手平安银行
if cash > 0:
    handle_buy()
```