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