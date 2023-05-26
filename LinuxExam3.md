##### 启动ngnix

```
/usr/local/nginx/sbin/nginx -c /usr/local/nginx/conf/nginx.conf
```

##### 查看监听端口

```
netstat -unltp |grep fdfs
```

##### 用tail查看日志

```
tail
命令格式: tail[必要参数][选择参数][文件]
-f 循环读取
-q 不显示处理信息
-v 显示详细的处理信息
-c<数目> 显示的字节数
-n<行数> 显示行数
-q, --quiet, --silent 从不输出给出文件名的首部
-s, --sleep-interval=S 与-f合用,表示在每次反复的间隔休眠S秒
```

```
tail  -n  10   test.log   查询日志尾部最后10行的日志;
tail  -n +10   test.log   查询10行之后的所有日志;
tail  -fn 10   test.log   循环实时查看最后1000行记录(最常用的)
```

```java
//关键,循环读取日志文件且显示行号
tail -fn 1000 test.log | grep '关键字'
```

```
tail -n 4700  aa.log |more -1000 可以进行多屏显示(ctrl + f 或者 空格键可以快捷键)
```

