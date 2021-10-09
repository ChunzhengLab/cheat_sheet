

````bash
#查看账户磁盘配额
quota -uvs username
````

````bash
#查看磁盘占用
du -sh 只显示总和的大小
````

````bash
#保持ssh不断联客户机操作
sudo vim /etc/ssh/ssh_config
#写入
ServerAliveInterval 30
ServerAliveCountMax 100

#原理：本地 ssh 客户端每隔 30s 向服务器端 sshd 发送 keep-alive 数据包，如果连续发送 10 次，server 无回应，则断开连接。这样同时规避了网络闪断的问题。
````

````bash
#tar 用法
tar -cf #建立压缩档案
tar -xf #解压
tar -tf #查看内容
tar -rf #向压缩归档文件末尾追加文件
tar -uf #更新原压缩包中的文件
#这五个是独立的命令，压缩解压都要用到其中一个，可以和别的命令连用但只能用其中一个。下面的参数是根据需要在压缩或解压档案时可选的
-f 是必须的，接档案名，这个参数是最后一个参数，后面只能接档案名。
#-z：有gzip属性的
#-j：有bz2属性的
#-Z：有compress属性的
#-v：显示所有过程
#-O：将文件解开到标准输出

#总结
# *.tar 用 tar -xvf 解压
# *.gz 用 gzip -d或者gunzip 解压
# *.tar.gz和.tgz 用 tar -xzf 解压
# *.bz2 用 bzip2 -d或者用bunzip2 解压
# *.tar.bz2用tar -xjf 解压
# *.Z 用 uncompress 解压
# *.tar.Z 用tar -xZf 解压
# *.rar 用 unrar e解压
# *.zip 用 unzip 解压
````

```bash
find   path   -option   [   -print ]   [ -exec   -ok   command ]   {} \;

#将当前目录及其子目录下所有文件后缀为 .c 的文件列出来:
find . -nabashme "*.c"
#将目前目录其其下子目录中所有一般文件列出
find . -type f
#将当前目录及其子目录下所有最近 20 天内更新过的文件列出:
find . -ctime -20
#查找 /var/log 目录中更改时间在 7 日以前的普通文件，并在删除之前询问它们：
find /var/log -type f -mtime +7 -ok rm {} \;
#查找当前目录中文件属主具有读、写权限，并且文件所属组的用户和其他用户具有读权限的文件：
find . -type f -perm 644 -exec ls -l {} \;
#查找系统中所有文件长度为 0 的普通文件，并列出它们的完整路径：
find / -type f -size 0 -exec ls -l {} \;
```

```bash
#列出cpu信息
lscpu
```

