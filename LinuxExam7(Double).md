#### 利用虚拟机新增一个磁盘，然后把新磁盘挂载到Linux的目录树下。

##### 虚拟机添加磁盘

1.打开虚拟机设置,点击"添加硬盘"按钮,选择"创建新虚拟磁盘":磁盘类型为SCSI,磁盘大小为”8.0GB”。

2.进入Linux虚拟机fdisk -l查看是否有新添加的硬盘。

##### 磁盘分区

3.使用fdisk分区工具对/dev/sdb磁盘进行分区,命令为fdisk /dev/sdb,输入n新建分区,选择分区类型为Linux(83),分区大小使用默认的全部空间,一直点击下一步直到完成。

4.输入w命令保存修改并退出fdisk。

##### 磁盘格式化

5.使用mkfs -t ext4 /dev/sdb1将分区格式化为ext4文件系统:

##### 磁盘挂载

6.创建文件夹mkdir /root/newdev, mount /dev/sdb /root/newdev挂载, df -h查看是否挂载成功。
注:Linux文件系统为以"/"为根的文件树,只有挂载点以及挂载点的子树可以使用磁盘空间。

7.打开/etc/fstad文件在最后一行添加 /dev/sdb /root/newdev ext4 defaults 0 0实现永久挂载。

