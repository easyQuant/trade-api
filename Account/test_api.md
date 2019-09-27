# 交易API

#### 在python代码中调用本地http api 实现实盘

```
import requests

## 在策略代码顶端添加本地server地址
REAL_URL = "http://127.0.0.1:3001"
```

#### 获取持仓信息

##### 请求方式
```
r = requests.get(REAL_URL + "/api/position")
```

##### 返回数据示例

```
{
    ## 账户信息
	"portfolio": { 

        ## 总的权益, 包括现金, 仓位(股票)的总价值, 可用来计算收益
		"total_value": 7999.68, 

        ## 可用资金, 可用来购买证券的资金
		"available_cash": 7240.68, 

        ## 可取资金, 即可以提现的资金, 不包括今日卖出证券所得资金
		"transferable_cash": 7240.68, 

        ## 挂单锁住资金
		"locked_cash": 0, 

        ## 持仓价值
		"positions_value": 759, 

        ## 总权益的累计收益
		"returns": 0
	},

    ## 具体持仓信息
    "positions": {

        ## 标的代码
        "002503": {

            ## 标的名称
            "security_name": "搜于特",

            ## 标的代码
            "security": "002503",

            ## 当前价格
            "price": 2.53,

            ## 成本价格
            "acc_avg_cost": 2.48,

            ## 成本均价
            "avg_cost": 2.48,

            ## 冻结数量
            "locked_amount": null,

            ## 市值
            "value": 759,

            ## 可卖出的仓位
            "closeable_amount": 300,

            ## 总数量
            "total_amount": 300,

            ## 累计收益
            "returns": 14.95,

            ## 当前价格
            "current_value": 14.95,

            ## 当日收益
            "current_returns": 2.016
        }
    }
	
}
``` 

#### 下限价买单

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

#### 当日委托列表

##### 请求方式
```
r = requests.get(REAL_URL + "/api/today_entrusts")
```

##### 请求返回
```
[
    {
        ## 合同编号
        "entrust_no": "827",

        ## 标的代码
        "security": "002503",

        ## 标的名称
        "security_name": "搜于特",

        ## 委托类型
        "order_type": "证券卖出",

        ## 成交状态
        "state": "未报",

        ## 委托价格
        "order_price": 2.7,

        ## 委托时间
        "order_date": "21:08:45",

        ## 委托数量
        "transaction_amount": 100,

        ## 委托金额
        "transaction_value": 270,

        ## 委托价格
        "transaction_price": 2.7
    }
]
```


#### 当日成交列表

##### 请求方式
```
r = requests.get(REAL_URL + "/api/today_trades")
```

##### 请求返回
```
[
    {
        ## 合同编号
        entrust_no: "827",

        ## 标的代码
        security: "002503",

        ## 标的名称
        security_name: "搜于特",

        ## 成交类型
        trade_type: "证券卖出",

        ## 成交时间
        trade_date: "21:08:45",

        ## 成交均价
        transaction_price: "2.7",

        ## 成交数量
        transaction_amount: "100",

        ## 成交金额
        transaction_value: 270
    }
]
```

#### 当日撤单列表

##### 请求方式
```
r = requests.get(REAL_URL + "/api/cancel_entrusts")
```

##### 请求返回
```
[
    {
        ## 合同编号
        "entrust_no": "827",

        ## 标的代码
        "security": "002503",

        ## 标的名称
        "security_name": "搜于特",

        ## 委托类型
        "order_type": "证券卖出",

        ## 委托状态
        "state": "未报",

        ## 撤单日期
        "trade_date": 20190923,

        ## 委托价格
        "transaction_price": 2.7,

        ## 委托数量
        "transaction_amount": 100,

        ## 委托金额
        "transaction_value": 270
    }
]
```