# Joinquant-local

#### 客户端对接

聚宽的金融终端可以在本地创建模拟交易 下面的教程使用聚宽模拟盘和zt-trade实现本地实盘交易

可以先去聚宽学习下简单语法 https://www.joinquant.com/help/api/help?name=api

##### 1. 安装聚宽金融终端
https://www.joinquant.com/default/index/jqclient

##### 2. 下载并复制py文件到研究
<a href="http://120.77.176.54:5000/real_zt_api.py" >real_zt_api.py</a>

##### 3. 编写一个简单但是完整的策略

```
# 导入函数库
from jqdata import *
from real_zt_api import *

# 初始化函数，设定基准等等
def initialize(context):
    # 设置我们要操作的股票
    g.stock = '601398.XSHG'
    ### 实盘相关配置 ###
    # 初始化实盘跟单函数
    init(g, context, order, order_target, order_value, order_target_value, 
    get_open_orders, cancel_order, LimitOrderStyle, False)
    g.current_data = get_current_data()
    
def handle_data(context, data):
    ## 获取实盘持仓信息
    g.get_current_total_value(g, context)

    if g.stock not in context.portfolio.positions:
        g.order(g.stock, 100)
    else:
        g.order(g.stock, -100)

```

##### 4. 实盘和模拟盘函数的编写差异

实盘函数和聚宽的模拟盘函数基本一致 可以同时兼容在本地回测和模拟盘

```
# 按股数下单[市价]
order(stock, amount) =>  g.order(stock, amount)

# 按股数下单
order(stock, amount, LimitOrderStyle(price)) =>  g.order(stock, amount, g.LimitOrderStyle(price))

# 目标股数下单
order_target(stock, amount, LimitOrderStyle(price)) =>  g.order_target(stock, amount, g.LimitOrderStyle(price))

# 按价值下单
order_value(stock, amount, LimitOrderStyle(price)) =>  g.order_value(stock, amount, g.LimitOrderStyle(price))

# 目标价值下单
order_target_value(stock, amount, LimitOrderStyle(price)) =>  g.order_target_value(stock, amount, g.LimitOrderStyle(price))

# 撤单
cancel_order(order) => g.cancel_order(order_id)

# 获取未完成订单信息
get_open_orders() => g.real_get_open_orders(g, context)

# 获取订单信息
get_orders() => g.real_get_orders(g, context)

# 获取成交信息
get_trades() => g.real_get_trades(g, context)
```