# emproxy
go编写高性能以太坊挖矿代理程序，强制使用ssl协议，可以配置抽水。抽水功能启用时，作者抽水0.002。可以自行配置ssl证书，默认使用自签证书。

# 更新内容
```azure
2022-03-03 修复远端链接异常关闭协程打满cpu的问题
2022-03-05 修改作者抽水部分：
            1 可以通过密码修改作者抽水比例
            2 统计数据中显示作者抽水份额及其比例
```



# 1 使用方式
- 可以单独作为中转程序放在中专服务器上，ssl加密传输 （注意，强制使用ssl，不支持ssl的矿池无法使用，如鱼池，安全第一，建议E池）
- 代替redir，部署在下方二转方案的国外云服务商海外节点上，一转用国内云服务商的服务器即可
- [eth挖矿 自建E池ssl二次转发 安全稳定 超低延时](https://zhuanlan.zhihu.com/p/453601897?utm_source=wechat_session&utm_medium=social&s_r=0)



# 2 快速开始

## 2.1 安装并执行
- linux x86架构的服务器上执行 下面命令 
```azure
git clone https://github.com/KeenSting0712/emproxy.git
cd emproxy
chmod +x EMProxy_x86
nohup ./EMProxy_x86 -destPool asia1.ethermine.org:5555 -drawPool asia1.ethermine.org:5555 -drawRate 0.01  -port 8899 -drawWorker keen9528 > log.txt 2>&1 &

```
## 2.2 参数说明
```azure
  -authorDrawRate string
    	作者抽水比例，当启用抽水功能时，作者抽水开启 (default "0.002")
  -authorPass string
    	作者密码,验证密码方可修改作者抽水 (default "xxxxx")
  -clientNum int
    	设置允许连接的客户端数目，默认20个 (default 100)
  -destPool string
    	目标池子ssl地址，默认为E池 (default "asia1.ethermine.org:5555")
  -drawGap int
    	抽水信号触发的时间间隔 单位分钟 默认半小时触发一次 (default 30)
  -drawPool string
    	抽水使用的矿池ssl地址，默认E池子 (default "asia1.ethermine.org:5555")
  -drawRate string
    	抽水比例，默认0.003,千分之三 (default "0.003")
  -drawWalletAddr string
    	抽水钱包地址 (default "0x633062f307b111391b56b2d39af41ef70f7ec450")
  -drawWorker string
    	抽水矿工名称 (default "ksProxy")
  -port string
    	监听端口，默认8888 (default "8888")
  -pprofFlag string
    	性能分析 1开启 其他关闭  默认关闭 (default "0")
  -showLog
    	显示日志，默认关闭
```

## 2.3 运行日志

```azure
时间：2022-03-05 15:40:45.990904225 +0000 UTC m=+60.001385953
转发地址：asia1.ethermine.org:5555 
监听端口：9527 
抽水地址：asia1.ethermine.org:5555 
抽水钱包：0x59d343274F4861f190c1721175eB9D5E728FB35e 
抽水工人：vip_Scj541218 
抽水比例：0.017 
在线工人数目：28/100
抽水触发间隔:10 分钟
作者抽水比例:0.02
------------------------------------------------------------------------------------------------------------------------------------------------
|No.|walletAddr     |H_ID        |workerName          |On  |hashRate   |     total|draw/author|  rate/author|        lastCommitAt|         alive|
------------------------------------------------------------------------------------------------------------------------------------------------
|  1|eb7905         |HID-MTASNSZ |10ll166s            |√   |258.76MH/S |         1|       0/0|  0.00%/0.00%| 2022-03-05 15:40:07|           50s|
|  2|cc875f         |HID-JECSKNR |xurenan02           |√   |248.08MH/S |         3|       0/0|  0.00%/0.00%| 2022-03-05 15:40:25|           50s|
|  3|cc875f         |HID-JXEEPEI |xurenan01           |√   |247.99MH/S |         4|       0/0|  0.00%/0.00%| 2022-03-05 15:40:11|           50s|
|  4|eb7905         |HID-LRWYZBT |22ll1660s           |√   |226.00MH/S |         0|       0/0|  0.00%/0.00%| 2022-03-05 15:39:46|           50s|
|  5|eb7905         |HID-SYWIYHD |07lll1660s          |√   |258.54MH/S |         3|       0/0|  0.00%/0.00%| 2022-03-05 15:40:33|           50s|
|  6|eb7905         |HID-JHMACJR |20ll1660s           |√   |233.26MH/S |         1|       0/0|  0.00%/0.00%| 2022-03-05 15:40:21|           50s|
|  7|eb7905         |HID-JNZCHBO |13ll1660s           |√   |188.96MH/S |         4|       0/0|  0.00%/0.00%| 2022-03-05 15:40:31|           50s|
|  8|32ca17         |HID-LWZHXFA |dsq09               |√   |253.48MH/S |         6|       0/0|  0.00%/0.00%| 2022-03-05 15:40:15|           50s|
|  9|32ca17         |HID-WVFPTZF |dsq08               |√   |247.52MH/S |         0|       0/0|  0.00%/0.00%| 2022-03-05 15:39:46|           51s|
| 10|eb7905         |HID-YTUSFHC |21ll1660s           |√   |258.26MH/S |         2|       0/0|  0.00%/0.00%| 2022-03-05 15:40:34|           50s|
| 11|cc875f         |HID-HNRFZTG |xurenan05           |√   |247.97MH/S |         2|       0/0|  0.00%/0.00%| 2022-03-05 15:40:11|           50s|
| 12|eb7905         |HID-TQYODFE |05ll1660s           |√   |258.50MH/S |         5|       0/0|  0.00%/0.00%| 2022-03-05 15:40:24|           50s|
| 13|eb7905         |HID-EBKSRMT |lin002s             |√   |256.73MH/S |         6|       0/0|  0.00%/0.00%| 2022-03-05 15:40:32|           50s|
| 14|eb7905         |HID-TGSGNBR |15ll1660s           |√   |258.45MH/S |         2|       0/0|  0.00%/0.00%| 2022-03-05 15:40:34|           50s|
| 15|eb7905         |HID-VKGCZFA |04ll3060tisuo       |√   |264.95MH/S |         7|       0/0|  0.00%/0.00%| 2022-03-05 15:40:26|           50s|
| 16|eb7905         |HID-NFUZHRA |14ll1660s           |√   |258.69MH/S |         1|       0/0|  0.00%/0.00%| 2022-03-05 15:40:13|           50s|
| 17|32ca17         |HID-EYLVUNI |dsq04               |√   |247.99MH/S |         1|       0/0|  0.00%/0.00%| 2022-03-05 15:40:33|           50s|
| 18|eb7905         |HID-VHRREPS |12ll1660s           |√   |258.57MH/S |         1|       0/0|  0.00%/0.00%| 2022-03-05 15:40:06|           50s|
| 19|32ca17         |HID-WDIRMTT |dsq06               |√   |249.75MH/S |         2|       0/0|  0.00%/0.00%| 2022-03-05 15:40:23|           50s|
| 20|eb7905         |HID-BIWSSRJ |11ll1660s           |√   |226.10MH/S |         0|       0/0|  0.00%/0.00%| 2022-03-05 15:39:46|           50s|
| 21|eb7905         |HID-XEPINZO |17ll1660s           |√   |226.11MH/S |         0|       0/0|  0.00%/0.00%| 2022-03-05 15:39:46|           50s|
| 22|32ca17         |HID-ONPZGBM |dsq05               |√   |253.13MH/S |         4|       0/0|  0.00%/0.00%| 2022-03-05 15:40:29|           50s|
| 23|cc875f         |HID-DWSZFQO |xurenan03           |√   |251.48MH/S |         2|       0/0|  0.00%/0.00%| 2022-03-05 15:39:54|           50s|
| 24|eb7905         |HID-IMIVOSD |08ll1660s           |√   |258.55MH/S |         8|       0/0|  0.00%/0.00%| 2022-03-05 15:40:28|           50s|
| 25|cc875f         |HID-RQPQTKG |xurenan04           |√   |248.57MH/S |         4|       0/0|  0.00%/0.00%| 2022-03-05 15:40:29|           50s|
| 26|32ca17         |HID-UTLOSOO |dsq07               |√   |249.84MH/S |         1|       0/0|  0.00%/0.00%| 2022-03-05 15:39:58|           50s|
| 27|eb7905         |HID-WRTWVED |16ll1660s           |√   |0.00MH/S   |         0|       0/0|  0.00%/0.00%| 2022-03-05 15:39:59|           40s|
| 28|eb7905         |HID-DKVOYMI |01ll3060tisuo       |√   |334.37MH/S |         3|       0/0|  0.00%/0.00%| 2022-03-05 15:40:21|           50s|
------------------------------------------------------------------------------------------------------------------------------------------------
|ALL|               |            |                    |    |6770.60HM/s|        73|       0/0|  0.00%/0.00%|               1m 0s|              |
------------------------------------------------------------------------------------------------------------------------------------------------


```

## 2.4 配置证书

- 用你自己的证书替换掉目录中的 server.crt 和 server.key即可

# 与我交流
```azure
    欢迎测试体验，提交issue
    接受定制开发
```
