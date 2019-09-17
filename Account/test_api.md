# 测试HTTP接口

##### 在python代码中调用本地http api 实现实盘

```
## 获取持仓信息
import requests
REAL_URL = 'http://127.0.0.1:3001'

r = requests.get(REAL_URL + '/api/position')

## 持仓信息
print(r.json()['data'])

```