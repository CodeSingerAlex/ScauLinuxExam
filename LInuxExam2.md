```css
#(实时)追踪文件改动
tail -f [path]

#追加头13行head -13
head -13 /etc/passwd >> exam2.txt

#Xshell复制快捷键
ctrl + insert
#粘贴快捷键
shift + insert

#将某个目录下的所有文件和字目录的内容以长格式的方式追加到文件中
ls -laR ../myshare/ >> exam2.txt

#直接使用user + 用户名 创建用户会导致用户没有密码，也没有权限(不会再/home中创建同名用户)
#应使用user -m 用户名 或者 adduser 用户名 创建

#Linux中root对所有文件可操作,其他用户只对自己所属文件可操作
#把 myshare目录及其目录下的所有文件和子目录的拥有者设置为用户test，组改为mail
	#../
chown -R test:mail ../myshare/
#查看文件所有者及权限
ls -l [文件夹]
[root@Linux myshare]# ls -l 
total 8
drwxr-xr-x. 2 test mail   22 Mar 28 10:54 202125330220
-rw-r--r--. 1 test mail 1090 Mar 28 11:06 exam2.txt
-rwxr-x--x. 1 test mail   86 Mar 28 10:53 hello.sh
1位 d(directory文件夹) -(其他)
234位 拥有者rwx读写执行权限 rw读写权限
567位 组群r-x读与执行权限 r--只读权限
89TEN位 其他人r--只读权限 --x只执行权限
#赋权:每个权限都有唯一的数值。
    #读:4,写:2,执行:1。数字相加表示权限总和。三个数字依次表示拥有者、组群和其他人权限。
    #下面例子中751表示,拥有者可读写执行、组群可写执行、其他人可执行。
    #特别的:0表示没有权限。
chomod 751 file/direction

# ../direction -- 当前文件夹本身 相当于cd..回退上一级后 对direction进行操作
    
#递归删除文件夹(文件夹非空时)
rm -rf [文件夹]
```

