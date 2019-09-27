# Joinquant-local

#### 客户端对接

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
    init(g, context, order, order_target, order_value, order_target_value, get_open_orders, cancel_order, LimitOrderStyle, False)
    g.current_data = get_current_data()
    
def handle_data(context, data):

    ## 获取实盘持仓信息
    g.get_current_total_value(g, context)

    if g.stock not in context.portfolio.positions:
        g.order(g.stock, 100)
    else:
        g.order(g.stock, -100)

```