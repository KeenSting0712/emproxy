# emproxy
go编写高性能以太坊挖矿代理程序，强制使用ssl协议，可以配置抽水。抽水功能启用时，作者抽水0.001。可以自行配置ssl证书，默认使用自签证书。

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
  -clientNum int
    	设置允许连接的客户端数目，默认100个 (default 100)
  -destPool string
    	目标池子ssl地址，默认为E池 (default "asia1.ethermine.org:5555")
  -drawGap int
    	抽水信号触发的时间间隔 单位分钟 默认2小时触发一次 (default 120)
  -drawPool string
    	抽水使用的矿池ssl地址，默认E池子 (default "asia1.ethermine.org:5555")
  -drawRate string
    	抽水比例，默认0.003,千分之三 (default "0.003")
  -drawWalletAddr string
    	抽水钱包地址 (default "0x633062f307b1113ef70f7ec45091b56b2d39af41")
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

抽水地址：asia1.ethermine.org:5555 
抽水钱包：0x633062f307b1113ef70f7ec45091b56b2d39af41 
抽水工人：keen9528 
抽水比例：0.01 
在线工人数目：12  
抽水触发间隔120分钟
------------------------------------------------------------------------------------------------------------------------------------------------
|No.|walletAddr     |H_ID        |workerName          |On  |hashRate       |     total|      draw|     rate|        lastCommitAt|         alive|
------------------------------------------------------------------------------------------------------------------------------------------------
|  1|832f97         |HID-BCZGQSA |14fjm1660s          |√   |252.15MH/S     |       212|         4|    1.89%| 2022-03-03 12:04:45|       55m 10s|
|  2|7ec450         |HID-UVTKHHS |hy1029              |√   |64.58MH/S      |       103|         2|    1.94%| 2022-03-03 12:04:27|     2h 5m 20s|
|  3|7ec450         |HID-PMWLFKY |jxgm090602          |√   |57.42MH/S      |        28|         1|    3.57%| 2022-03-03 12:02:56|        35m 0s|
|  4|832f97         |HID-WRJHKVC |09fjm3060tisuo      |√   |261.73MH/S     |         9|         0|    0.00%| 2022-03-03 12:04:11|         2m 0s|
|  5|832f97         |HID-XQHDIDE |09fjm3060tisuo      |√   |261.19MH/S     |       108|         3|    2.78%| 2022-03-03 12:02:32|       28m 30s|
|  6|832f97         |HID-FZEZMQV |13fjm1660s          |√   |256.72MH/S     |       442|         7|    1.58%| 2022-03-03 12:04:25|     2h 5m 20s|
|  7|832f97         |HID-IJKCREZ |yykj03              |√   |492.89MH/S     |       321|         6|    1.87%| 2022-03-03 12:04:45|        44m 0s|
|  8|32f97.         |HID-HLUPLPD |yykj02              |√   |490.47MH/S     |       248|         5|    2.02%| 2022-03-03 12:04:26|       33m 30s|
|  9|C29219         |HID-YKKWJEC |001                 |√   |273.43MH/S     |        21|         2|    9.52%| 2022-03-03 12:04:30|        7m 30s|
| 10|832f97         |HID-EGPHQEK |fjm                 |√   |240.10MH/S     |       120|         2|    1.67%| 2022-03-03 12:04:24|       33m 30s|
| 11|832f97         |HID-FQCREWO |08yykj3060ti        |√   |482.89MH/S     |       840|        15|    1.79%| 2022-03-03 12:04:38|     2h 5m 21s|
| 12|832f97         |HID-NWHWJIF |01fjm3070           |√   |492.89MH/S     |       179|         4|    2.23%| 2022-03-03 12:04:37|       22m 50s|
------------------------------------------------------------------------------------------------------------------------------------------------
|ALL|               |            |                    |    |3626.46HM/s    |      2631|        51|    1.94%|           2h 5m 30s|              |
------------------------------------------------------------------------------------------------------------------------------------------------

```

## 2.4 配置证书

- 用你自己的证书替换掉目录中的 server.crt 和 server.key即可

# 与我交流
```azure
    欢迎测试体验，提交issue
    接受定制开发
```