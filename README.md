# ShadowProxy

MinerProxy, ShadowMiner Proxy, 矿池代理, 加密代理, 免费, 无抽水, 支持任意币种与矿池, 支持SSL/TLS代理及更安全的SSL/TLS+二次加密代理，支持Windows及Ubuntu系统

<img width="1120" height="480" src="https://github.com/ShadowTools/ShadowProxy/blob/main/ShadowProxyWin.JPG?raw=true"/> 

#### 配套软件:
* 代理: <a href="https://github.com/ShadowTools/ShadowProxy">https://github.com/ShadowTools/ShadowProxy</a>
* 矿工: <a href="https://github.com/ShadowTools/ShadowMiner">https://github.com/ShadowTools/ShadowMiner</a>
* 群控: <a href="https://github.com/ShadowTools/ShadowProxy">https://github.com/ShadowTools/ShadowMonitor</a>

## 功能:
* 支持Windows以及Ubuntu系统
* 支持任意币种/矿池
* 支持使用本地证书
* 支持周期性自生成SSL/TLS证书
* 支持SSL/TLS证书周期性更新
* 支持最大用户数限制
* 支持多进程, 提升多核服务器性能
* 支持两种代理模式
  1. 传统的SSL/TLS代理模式
  2. 更高安全性的SSL/TLS+二次加密代理模式
  
### Note:
* 二次加密代理优势:
  * 传统的SSL/TLS代理模式容易受到中间人攻击, 导致数据泄露
  * 基于私有口令的二次认证与加密, 提供极高数据安全性
  * 加密并转发矿工端内核抽水地址与数据，避免因矿工内核抽水导致的信息泄露
  * 在矿工端即可灵活修改目标矿池地址，配合ShadowMiner使用

* SSL/TLS证书自更新优势:
  * 周期更新自生成证书, 避免证书指纹一致带来的问题
  * 无需繁琐的证书申请与替换流程


## 费率
无抽水, 提供100%转发
### Note:
判断是否抽水:
1. 对比本地与矿池24小时份额
2. 监测异常的TCP连接
3. 不需设置币种信息一般无抽水


## 使用说明

### Windows版本:
* 在出入站规则中开放所需的出入站端口(二次加密模式建议打开所有出站端口)
* 在Windows系统的允许应用通过防火墙中，添加ShadowProxyWin
* 为防止系统误删软件, 建议ShadowProxyWin目录添加到信任列表
* 解压后运行ShadowProxyWin.exe
* 添加代理, 输入本地端口, 转发模式, 口令, 目标矿池, 证书等信息, 详情见软件
* 点击启动即可
* SSL/TLS代理模式, 推荐使用ShadowMiner中的TCPing功能测试连接/延迟(本地-代理)等信息
* 二次加密代理模式, 推荐使用ShadowMiner中的Ping功能测试连接/延迟(本地-代理|代理-矿池)/证书/负载等信息

### Ubuntu版本:
#### Note:
Ubuntu版本对硬件要求更低, 建议熟悉Linux环境的人使用

* 在出入站规则中开放所需的出入站端口(二次加密模式建议打开所有出站端口)
* 修改启动脚本中的信息,比如端口号, 矿池地址等
* 启动脚本或者使用推荐命令启动
* 若端口被占用, 可以杀死所有ShadowProxy进程后, 再启动ShadowProxy
* SSL/TLS代理模式, 推荐使用ShadowMiner中的TCPing功能测试连接/延迟(本地-代理)等信息
* 二次加密代理模式, 推荐使用ShadowMiner中的Ping功能测试连接/延迟(本地-代理|代理-矿池)/证书/负载等信息

| 脚本 | 功能 |
| ------------- | ------------- |
| run_proxy_without_crypto_forward.sh | 以SSL/TLS代理模式启动 |
| run_proxy_with_crypto_forward.sh |以SSL/TLS+二次加密代理模式启动 |
| kill_all_proxy.sh | 杀死所有ShadowProxy进程 |
| check_port_available.sh | 检查指定端口是否占用 |
| check_proxy_thread.sh | 检查代理是否运行 |

##### 推荐命令:
* SSL/TLS代理模式:
  * nohup ./ShadowProxyCmd.bin -crypto 0 -local_port 443 -pool PoolAddress -port PoolPort -ssl 0 -force 1 -every 30 > out.log 2>&1 &
* SSL/TLS+二次加密代理模式
  * nohup ./ShadowProxyCmd.bin -crypto 1 -key YourKey -local_port 8008 -force 1 -every 30 > out.log 2>&1 &

##### 命令说明:
usage: ShadowProxyCmd.bin [-h] [-crypto CRYPTO] [-key KEY] [-pool POOL] [-port PORT] [-ssl SSL] [-local_port LOCAL_PORT] [-force FORCE] [-every EVERY] [-limit LIMIT]

options:
| Parameter |	Description |
| ------------- | ------------- |
| -h, --help | show this help message and exit |
|  -crypto CRYPTO | use crypto forward 1/0 |
|  -key KEY     | crypto key string |
|  -pool POOL   | target pool string when not use crypto forward(-c 0) |
|  -port PORT   | target pool port int |
|  -ssl SSL     | target pool ssl 1/0 |
|  -local_port  | local port int |
|  -force FORCE | force generate new Cert file at start |
|  -every EVERY | generate new Cert file every number of days |
|  -limit LIMIT | limit number of connections, 0 means no limit |


* 联系我们: Telegram: https://t.me/+5yaCgLEEmmszZWY1 Mail: shadowtools8@gmail.com
----------------------------------------------------------------------------------------------
