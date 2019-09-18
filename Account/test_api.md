# 交易API

#### 在python代码中调用本地http api 实现实盘

```
import requests

## 在策略代码顶端添加本地server地址
REAL_URL = 'http://127.0.0.1:3001'
```

#### 获取持仓信息

```
r = requests.get(REAL_URL + '/api/position')

## 持仓信息
print(r.json()['data'])

```

#### 限价买单

```
r = requests.get(REAL_URL + '/api/buy', param = {
    stock: '002503',
    price: 2.62,
    amount: 100
})
```

##### 请求返回

```
## 委托成功
{
    data: {
        order_id: '100'
    }
}

## 委托异常
{
    data: {
        message: '异常信息'
    }
}
```

#### 限价卖单

```
r = requests.get(REAL_URL + '/api/sell', param = {
    stock: '002503',
    price: 2.62,
    amount: 100
})
```

##### 请求返回

```
## 委托成功
{
    data: {
        order_id: '100'
    }
}

## 委托异常
{
    data: {
        message: '异常信息'
    }
}
```

#### 市价买单

```
r = requests.get(REAL_URL + '/api/market_buy', param = {
    stock: '002503',
    price: 2.62,
    amount: 100
})
```

##### 请求返回

```
## 委托成功
{
    data: {
        order_id: '100'
    }
}

## 委托异常
{
    data: {
        message: '异常信息'
    }
}
```

#### 市价卖单

```
r = requests.get(REAL_URL + '/api/market_sell', param = {
    stock: '002503',
    price: 2.62,
    amount: 100
})
```

##### 请求返回

```
## 委托成功
{
    data: {
        order_id: '100'
    }
}

## 委托异常
{
    data: {
        message: '异常信息'
    }
}
```

#### 根据委托单号撤单

```
r = requests.get(REAL_URL + '/api/cancel_entrust', param = {
    order_id: '要撤单的委托单号'
})
```

##### 请求返回
```
## 委托成功
{
    data: {
        order_id: '100'
    }
}

## 委托异常
{
    data: {
        message: '异常信息'
    }
}
```

```
## 获取当日委托列表
r = requests.get(REAL_URL + '/api/today_entrusts')

## 当日委托列表
print(r.json()['data'])

```

```
## 获取当日成交列表
r = requests.get(REAL_URL + '/api/today_trades')

## 当日成交列表
print(r.json()['data'])

```

```
## 获取当日撤单列表
r = requests.get(REAL_URL + '/api/cancel_entrusts')

## 当日成交列表
print(r.json()['data'])

```