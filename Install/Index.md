# 安装
#### 环境要求
支持系统    windows

python版本  3.6 3.7

node版本    8+

#### 配置环境

##### 1. 安装 node 环境

http://nodejs.cn/download/

##### 2. 安装 python3 环境

https://www.python.org/

##### 3. 安装 cmder 实现在windows下执行命令行操作 

https://cmder.net/

#### 下载程序安装包

http://120.77.176.54:4000

##### 1. 通过cmder进入安装包目录

cd zt-trade

##### 2. 安装 node 和 python 依赖

npm install -ddd

pip install -r requirements.txt

安装速度慢的话可以使用以下方案加速

npm --registry https://registry.npm.taobao.org install -ddd ## 临时使用淘宝源

pip install -i https://pypi.tuna.tsinghua.edu.cn/simple -r requirements.txt ## 临时使用国内源
