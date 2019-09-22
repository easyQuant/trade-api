# Joinquant

#### 对接聚宽量化终端

##### 1. 下载量化终端
https://www.joinquant.com/default/index/jqclient

##### 2. 在研究内复制以下实盘相关文件
<a href="http://120.77.176.54:5000/real_api.py" >real_api.py</a>

##### 3. 新建策略 在头部引入实盘文件

```
from real_api import *
```

##### 4. 改动交易函数

###### 交易函数的相关改动

```
## Context对象, 存放有当前的账户/股票持仓信息
context => g.context

## 按数量买入
order(stock, amount) => g.order(stock, amount)

## 按价值买入
order_value(stock, value) => g.order_value(stock, value)

## 交易到指定数量
order_target(stock, amount) => g.order_target(stock, amount)

## 交易到指定价值
order_target_value(stock, value) => g.order_target_value(stock, value)

## 根据委托单号撤单
cancel_order(order_id) => g.cancel_order(order_id)

## 获取未成交委托列表
get_open_orders => g.get_open_orders
```

##### 5. 正常执行回测

##### 6. 使用刚刚创建的回测 创建本地模拟盘

