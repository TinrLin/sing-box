# **说明**
- **脚本使用sing-box、Juicity内核。**
- **脚本支持IPV6单栈机。**
- **脚本支持 CentOS 8+、Debian 10+、Ubuntu 20+ 操作系统。**
- **脚本支持 warp 解锁 ChatGPT、Netflix、Disney+。**
- **脚本所有协议均支持自签证书（NaiveProxy除外）。**
- **脚本支持多用户。**
- **脚本支持所有协议共存。**
- **脚本支持自动续签证书。**
- **脚本支持生成Clash客户端配置文件，需要配合Meta内核。**
- **脚本支持生成sing-box客户端配置文件。**
- **电脑端使用方法：下载生成的win_client.json文件====>>V2rayN客户端添加自定义配置服务器====>>地址加载生成的win_client.json文件====>>Core类型选sing_box====>>Socks端口1080。**
- **手机端使用方法：下载生成的phone_client.json文件====>>手机下载sing-box官方客户端====>>Profiles点击New profile====>>name自己命名====>>Source选择Import====>>点击Import File====>>选择下载的phone_client.json文件。**

# **安装**
- **Debian&&Ubuntu使用以下命令安装依赖**
```
apt update && apt -y install curl wget tar socat jq git openssl uuid-runtime build-essential zlib1g-dev libssl-dev libevent-dev dnsutils
```
- **CentOS使用以下命令安装依赖**
```
yum update && yum -y install curl wget tar socat jq git openssl util-linux gcc-c++ zlib-devel openssl-devel libevent-devel bind-utils
```
- **使用以下命令运行脚本**
```
wget -N -O /root/singbox.sh https://raw.githubusercontent.com/TinrLin/sing-box/main/Install.sh && chmod +x /root/singbox.sh && ln -sf /root/singbox.sh /usr/local/bin/singbox && bash /root/singbox.sh
```
# **Hysteria端口跳跃**
```
# Debian&&Ubuntu

## 安装iptables-persistent
apt install iptables-persistent

## 清空默认规则
iptables -F

## 清空自定义规则
iptables -X

## 允许本地访问
iptables -A INPUT -i lo -j ACCEPT

## 开放SSH端口（假设SSH端口为22）
iptables -A INPUT -p tcp --dport 22 -j ACCEPT

## 开放HTTP端口
iptables -A INPUT -p tcp --dport 80 -j ACCEPT

## 开放UDP端口（10010替换为节点的监听端口）
iptables -A INPUT -p udp --dport 10010 -j ACCEPT

## 开放UDP端口范围（假设UDP端口范围为20000-40000）
iptables -A INPUT -p udp --dport 20000:40000 -j ACCEPT

## 允许接受本机请求之后的返回数据
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

## 其他入站一律禁止
iptables -P INPUT DROP

## 允许所有出站
iptables -P OUTPUT ACCEPT

## 查看开放的端口
iptables -L

## 添加NAT规则，20000:40000替换为你设置端口跳跃的范围，10010替换为你节点的监听端口
iptables -t nat -A PREROUTING -p udp --dport 20000:40000 -j DNAT --to-destination :10010

## 查看NAT规则
iptables -t nat -nL --line

## 保存iptables规则
netfilter-persistent save
```
```
# CentOS
## 安装iptables-service
yum install iptables-services

## 启用iptables服务
systemctl enable iptables

## 启动iptables服务
systemctl start iptables

## 清空默认规则
iptables -F

## 清空自定义规则
iptables -X

## 允许本地访问
iptables -A INPUT -i lo -j ACCEPT

## 开放SSH端口（假设SSH端口为22）
iptables -A INPUT -p tcp --dport 22 -j ACCEPT

## 开放HTTP端口
iptables -A INPUT -p tcp --dport 80 -j ACCEPT

## 开放UDP端口（10010替换为节点的监听端口）
iptables -A INPUT -p udp --dport 10010 -j ACCEPT

## 开放UDP端口范围（假设UDP端口范围为20000-40000）
iptables -A INPUT -p udp --dport 20000:40000 -j ACCEPT

## 允许接受本机请求之后的返回数据
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

## 其他入站一律禁止
iptables -P INPUT DROP

## 允许所有出站
iptables -P OUTPUT ACCEPT

## 查看开放的端口
iptables -L

## 添加NAT规则，20000:40000替换为你设置端口跳跃的范围，10010替换为你节点的监听端口
iptables -t nat -A PREROUTING -p udp --dport 20000:40000 -j DNAT --to-destination :10010

## 查看NAT规则
iptables -t nat -nL --line

## 保存iptables规则
service iptables save
```

# **脚本支持的节点类型**
- **Socks**
- **TUIC V5**
- **juicity**
- **WireGuard--解锁 ChatGPT、Netflix、Disney+**
- **Hysteria2**
- **VLESS+tcp**
- **VLESS+ws**
- **VLESS+gRPC**
- **VLESS+vision+Reality**
- **VLESS+h2+Reality**
- **VLESS+gRPC+Reality**
- **Direct--sing-box版任意门**
- **Trojan+tcp**
- **Trojan+ws**
- **Trojan+gRPC**
- **Trojan+tcp+tls**
- **Trojan+H2C+tls**
- **Trojan+gRPC+tls**
- **Trojan+ws+tls**
- **Hysteria**
- **ShadowTLS V3**
- **NaiveProxy**
- **Shadowsocks**
- **Vmess+tcp**
- **Vmess+ws**
- **Vmess+grpc**   
- **Vmess+tcp+tls**
- **Vmess+ws+tls** 
- **Vmess+h2+tls**
- **Vmess+grpc+tls** 

