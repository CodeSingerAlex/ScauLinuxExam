```python
# xinetd开机自启动
systemctl enable xinetd.service
# 开启xineted服务
systemctl start xinetd.service
# 查看xinetd服务是否开启
service xinetd status
# telnet监听端口
netstat -tnl |grep 23
# 防火墙没开,不用专门开一个端口
# 查看端口监听状态
netstat -ntlp | grep 23
# 重启xinetd
server xinet drestart
# 启动telnet服务
systemctl start telnet.socket
systemctl enable telnet.socket
```

