
# 总核数 = 物理CPU个数 X 每颗物理CPU的核数 
# 总逻辑CPU数 = 物理CPU个数 X 每颗物理CPU的核数 X 超线程数

# 查看物理CPU个数
cat /proc/cpuinfo| grep "physical id"| sort| uniq| wc -l

# 查看每个物理CPU中core的个数(即核数)
cat /proc/cpuinfo| grep "cpu cores"| uniq

# 查看逻辑CPU的个数
cat /proc/cpuinfo| grep "processor"| wc -l

# 查看CPU信息（型号）
cat /proc/cpuinfo | grep name | cut -f2 -d: | uniq -c

# 查看内 存信息
 cat /proc/meminfo

生成日志
$ /usr/local/bin/goaccess -f /var/log/apache2/access.log -a > report.html

查看WEB服务器进程连接数：
netstat -antp | grep 80 | grep ESTABLISHED -c

http://www.laozuo.org/9107.html

https://www.cnblogs.com/itfenqing/p/6194051.html?utm_source=itdadao&utm_medium=referral

http://www.laozuo.org/9107.html

http://www.linuxidc.com/Linux/2015-04/116848.htm

https://www.fanhaobai.com/2017/06/go-access.html

http://blog.163.com/leijie131421@126/blog/static/4241114520112176194123/


服务器
https://zhuanlan.zhihu.com/p/28088863


 yum install ncurses-devel
./configure --enable-geoip --enable-utf8
 yum install glib2 glib2-devel GeoIP-devel  ncurses-devel zlib zlib-devel
 ./configure --enable-geoip --enable-utf8
 make && make install
 goaccess
 ln -s /usr/local/lib/libGeoIP.so* /lib64/
 
 
 安装goacess的一些支持库，如果后面操作出现问题，很有可能是因为某些库位安装，主要包括：glib2,glib2-devel,geoip,geoip-devel,ncurses-devel,zlib,zlib-devel,gcc。
 yum install glib2 glib2-devel GeoIP-devel  ncurses-devel zlib zlib-devel
 yum install gcc -y
 如果是一键安装，注意安装过程中的提示，哪些未安装成功，需要单独安装，比如我在本地操作时，ncurses-devle、zlib、zlib-devel默认已安装，geo-ip就未安装成功，需要单独安装。
 
 cd /usr/local/src
wget http://geolite.maxmind.com/download/geoip/api/c/GeoIP-1.4.6.tar.gz
wget http://geolite.maxmind.com/download/geoip/database/GeoLiteCountry/GeoIP.dat.gz

tar xzvf GeoIP-1.4.6.tar.gz
cd GeoIP-1.4.6
./configure && make && make install
cd ..
mv GeoIP.dat.gz /usr/local/share/GeoIP/
 
接下来我们就可以安装goaccess了，这里我是用的编译安装：
wget http://tar.goaccess.io/goaccess-0.8.1.tar.gz
tar xzvf goaccess-0.8.1.tar.gz
cd goaccess-0.8.1/
./configure --enable-geoip --enable-utf8
make && make install

运行goaccess命令查看是否安装成功，结果我在本地安装时提示下面错误：

32位系统使用下面命令解决：
ln -s /usr/local/lib/libGeoIP.so* /lib/

64位系统尝试使用下面命令解决：
ln -s /usr/local/lib/libGeoIP.so* /lib64/
goaccess使用：

找到日志文件access.log所在目录，最简单直接的使用方法：

goaccess -f access.log -c -a
接着会提示如下界面，使用上下方向键选择第三个，用空格键确认选择，然后回车确定即可。

当然也可以生成HTML报告，更为直观的查看数据。

当然也可以生成HTML报告，更为直观的查看数据。

goaccess -f access.log -a > report.html


https://linux.cn/article-5352-1.html


goaccess默认安装路径
/usr/local/bin/goaccess
/usr/local/bin/goaccess -f /var/log/access.log

epel源
https://www.cnblogs.com/imweihao/p/7357484.html


   /var/log/httpd/access_log：
   /var/log/httpd/error_log


 将Linux文件清空的几种方法
1、使用重定向的方法

[root@centos7 ~]# du -h test.txt 
4.0K    test.txt
[root@centos7 ~]# > test.txt 
[root@centos7 ~]# du -h test.txt 
0    test.txt

 
2、使用true命令重定向清空文件

[root@centos7 ~]# du -h test.txt 
4.0K    test.txt
[root@centos7 ~]# true > test.txt 
[root@centos7 ~]# du -h test.txt 
0    test.txt

 
3、使用cat/cp/dd命令及/dev/null设备来清空文件

[root@centos7 ~]# du -h test.txt 
4.0K    test.txt
[root@centos7 ~]# cat /dev/null >  test.txt 
[root@centos7 ~]# du -h test.txt 
0    test.txt
###################################################
[root@centos7 ~]# echo "Hello World" > test.txt 
[root@centos7 ~]# du -h test.txt 
4.0K    test.txt
[root@centos7 ~]# cp /dev/null test.txt 
cp：是否覆盖"test.txt"？ y
[root@centos7 ~]# du -h test.txt 
0    test.txt
##################################################
[root@centos7 ~]# echo "Hello World" > test.txt 
[root@centos7 ~]# du -h test.txt 
4.0K    test.txt
[root@centos7 ~]# dd if=/dev/null of=test.txt 
记录了0+0 的读入
记录了0+0 的写出
0字节(0 B)已复制，0.000266781 秒，0.0 kB/秒
[root@centos7 ~]# du -h test.txt 
0    test.txt


 
4、使用echo命令清空文件
[root@centos7 ~]# echo "Hello World" > test.txt 
[root@centos7 ~]# du -h test.txt 
4.0K    test.txt
[root@centos7 ~]# echo -n "" > test.txt    ==>要加上"-n"参数，默认情况下会"\n"，也就是回车符
[root@centos7 ~]# du -h test.txt  
0    test.txt

 
5、使用truncate命令清空文件
[root@centos7 ~]# du -h test.txt 
4.0K    test.txt
[root@centos7 ~]# truncate -s 0 test.txt   -s参数用来设定文件的大小，清空文件，就设定为0；
[root@centos7 ~]# du -h test.txt 
0    test.txt



goaccess的安装和使用
http://blog.itpub.net/21220384/viewspace-2139772/
https://www.cnblogs.com/imweihao/p/7357484.html
http://www.tianfeiyu.com/?p=585



时间设置
[root@localhost ~]# date;hwclock -r 
2012年 10月 19日 星期五 23:39:44 CST  
2012年10月19日 星期五 23时39分45秒  -0.317993 seconds 

date -s 20121019  

ntpdate time.windows.com && hwclock -w  

连网更新时间，如果成功，将系统时间，写入BOIS

hwclock -w 或 hwclock --systohc

可以做到crontab里

3、启动ntpd服务，开启后2就不能用了。
先用ntpdate更新一下，确保时间不至于差别太大
rpm -qa | grep ntp #查询一下可安装了
chkconfig --list | grep ntp #看下服务情况
chkconifg ntpd on
service ntpd start 或/etc/init.d/ntpd start
必要的话，设置一下/etc/ntp.conf，再把服务reload一下。


日志
https://www.cnblogs.com/cnlihao/p/7072932.html

$ /usr/local/bin/goaccess -f /var/log/apache2/access.log -a > report.html
