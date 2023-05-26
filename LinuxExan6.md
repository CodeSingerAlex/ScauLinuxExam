##### 正确地记录命令结果与引用结果创建文件夹

```shell
pinfo=$(ps -ef | gred vsftpd | head -n 1) #不能存在空格
echo $pinfo
date=$(date '+%Y-%m-%d')
echo $date
echo $pinfo>/var/ftp/$date.log # 没有会自己创建, 存在则覆盖。
echo $pinfo>>/var/ftp/$date.log # 不存在则报错
```

##### 对命令行运行成功与否的判断

```shell
systemctl stop vsftpd
if [ $? -ne 0];then # 要注意if判断语句的空格不能缺失
	echo "stop ftp erro" | mail -s "Stop ftp error" root
```

##### 提交crontab

```shell
指定shell路径可以定期执行shell程序
```

