# Joinquant-local

#### 客户端对接

##### 1. 安装聚宽金融终端
https://www.joinquant.com/default/index/jqclient

##### 2. 下载并复制py文件到研究
<a href="http://120.77.176.54:5000/real_zt_api.py" >real_zt_api.py</a>

##### 3. 编写一个简单的策略

```
### 聚宽客户端 进行本地实盘交易的demo ###

# 导入函数库
from jqdata import *
from real_zt_api import *

# 初始化函数，设定基准等等
def initialize(context):

    # 初始化此策略
    # 设置我们要操作的股票池
    g.stocks = ['601398.XSHG']

    # 设定沪深300作为基准
    set_benchmark('000300.XSHG')

    # 开启动态复权模式(真实价格)
    set_option('use_real_price', True)
    
    ## 运行函数（reference_security为运行时间的参考标的；传入的标的只做种类区分，因此传入'000300.XSHG'或'510300.XSHG'是一样的）
    # 开盘前运行
    run_daily(before_market_open, time='before_open', reference_security='000300.XSHG') 

    # 收盘后运行
    run_daily(after_market_close, time='after_close', reference_security='000300.XSHG')

    ### 实盘相关配置 ###
    # 初始化实盘跟单函数
    init(g, context, order, order_target, order_value, order_target_value, get_open_orders, cancel_order, LimitOrderStyle, False)
    g.current_data = get_current_data()
    
## 开盘前运行函数     
def before_market_open(context):
    pass
    
def handle_data(context, data):

    # 循环每只股票
    for security in g.stocks:

        # 得到上一时间点股票收盘价
        price = data[security].close
        g.get_current_total_value(g, context)

        # 得到当前资金余额
        cash = context.portfolio.available_cash

        # 如果持有该股票同时可卖数量大于0则卖出
        if security in context.portfolio.positions and context.portfolio.positions[security].closeable_amount > 0:

            # 下限价卖出单 卖出100股
            log.info(' # 下卖单 市价卖出100股 ')
            g.order(security, -100, g.LimitOrderStyle(price))

            # 记录这次买入
            log.info("Selling %s" % (security))

        # 否则有现金余额则买入
        elif cash > 0:

            # 下市价买单 买入600的价值
            log.info(' # 下买单 市价买入600价值的股票 ')
            g.order_value(security, 600)

            # 记录这次买入
            log.info("Buying %s" % (security))

## 收盘后运行函数  
def after_market_close(context):
    pass

```