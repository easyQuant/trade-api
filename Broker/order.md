# 下单

#### 限价买单

##### 请求方式
```
r = requests.get(REAL_URL + "/api/buy", params = {

    ## 股票代码
    "stock": "002503",

    ## 要下单的价格
    "price": 2.62,

    ## 下单数量
    "amount": 100
})
```

##### 返回数据示例

```
{
    ## 合同编号
    "entrust_no":"821"
}

```

#### 限价卖单

##### 请求方式
```
r = requests.get(REAL_URL + "/api/sell", params = {

    ## 股票代码
    "stock": "002503",

    ## 要下单的价格
    "price": 2.62,

    ## 下单数量
    "amount": 100
})
```

##### 请求返回

```
{
    ## 合同编号
    "entrust_no":"827"
}
```

#### 市价买单

##### 请求方式
```
r = requests.get(REAL_URL + "/api/market_buy", params = {

    ## 股票代码
    "stock": "002503",

    ## 当前价格
    "price": 2.62,

    ## 下单数量
    "amount": 100
})
```

##### 请求返回

```
{   
    ## 合同编号
    "entrust_no": 100
}
```

#### 市价卖单

##### 请求方式
```
r = requests.get(REAL_URL + "/api/market_sell", params = {
    
    ## 股票代码
    "stock": "002503",

    ## 当前价格
    "price": 2.62,

    ## 下单数量
    "amount": 100
})
```

##### 请求返回

```
## 委托成功
{
    ## 合同编号
    "entrust_no": "100"
}
```

#### 根据委托单号撤单

##### 请求方式
```
r = requests.get(REAL_URL + "/api/cancel_entrust", params = {

    ## 合同编号
    "entrust_no": "100"
})
```

##### 请求返回

```
## 委托成功
{
    "message":"您的撤单委托已成功提交，合同编号：829。"
}
```

#### 申请新股

##### 请求方式

```
r = requests.get(REAL_URL + "/api/auto_ipo")
```

##### 请求返回

```
{
    "message":"您的新股申请已成功"
}
```