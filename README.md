
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

