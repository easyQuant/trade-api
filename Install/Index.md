# 安装
#### 环境要求
支持系统    windows

python版本  3.7 无需单独安装 程序包内已带

nodejs版本    8+

#### 配置环境

#### 安装前的准备

##### 下载cmder [windows下命令行工具]

https://cmder.net/ 选择完整版

##### 安装nodejs

https://nodejs.org/en/

##### <font color=#FF0000 >所有路径不要有中文</font>


#### 准备安装

##### 1. 下载券商客户端

http://download.95538.cn/download/software/hx/ths_order.exe

##### 2. 下载程序安装包

http://120.77.176.54:8000/zt-trade.zip

https://pan.baidu.com/s/1Mo1P-SD1jDjJjF_MUmXZJQ 百度网盘

##### 3. 使用命令行或者winrar解压zt-trade.zip

```
unzip zt-trade.zip
```

##### 4. 进入zt-trade

```
cd zt-trade
```

##### 5 安装 node 依赖

```
npm install -ddd
```

安装速度慢的话可以使用以下方案加速

```
npm --registry https://registry.npm.taobao.org install -ddd ## 临时使用淘宝源
```
