Centos7安装nodejs

tar -zxvf node-v14.16.0-linux-x64.tar.gz -C /usr/local/

export NODE_HOME=/usr/local/node-v14.16.0-linux-x64
export PATH=$NODE_HOME/bin:$PATH


一 nodejs安装

1. 下载nodejs

wget https://nodejs.org/dist/latest-v10.x/node-v10.19.0-linux-x64.tar.gz
2. 解压

tar -zxvf node-v10.19.0-linux-x64.tar.gz -C /usr/local/
cd /usr/local
mv node-v10.19.0-linux-x64/ node
3. vim /etc/profile 增加环境变量

export NODE_HOME=/usr/local/node-v14.16.0-linux-x64
export PATH=$NODE_HOME/bin:$PATH
eg:



4. source /etc/profile

source /etc/profile
5. 查看版本

[root@izbp1845cet96se1qmb5ekz ~]# node -v
v10.19.0
[root@izbp1845cet96se1qmb5ekz ~]# npm -v
6.13.4
5. 设置淘宝镜像源

npm config set registry https://registry.npm.taobao.org

[root@izbp1845cet96se1qmb5ekz ~]# npm config get registry https://registry.npmjs.org/
[root@izbp1845cet96se1qmb5ekz ~]# npm config set registry https://registry.npm.taobao.org
[root@izbp1845cet96se1qmb5ekz ~]# npm config get registry https://registry.npm.taobao.org/
[root@izbp1845cet96se1qmb5ekz ~]#

6. which node  、 whereis node   查看有无 node、npm等命令

[root@izbp1845cet96se1qmb5ekz ~]# which node
/usr/local/node/bin/node
[root@izbp1845cet96se1qmb5ekz ~]# whereis node
node: /usr/local/node /usr/local/node/bin/node
[root@izbp1845cet96se1qmb5ekz ~]# which npm
/usr/local/node/bin/npm
[root@izbp1845cet96se1qmb5ekz ~]# whereis npm
npm: /usr/local/node/bin/npm
[root@izbp1845cet96se1qmb5ekz ~]#
7 安装全局 pm2

npm install -g pm2
8. 查看 有无 pm2命令 ， pm2 版本

[root@izbp1845cet96se1qmb5ekz ~]# which pm2
/usr/local/node/bin/pm2
[root@izbp1845cet96se1qmb5ekz ~]# whereis pm2
pm2: /usr/local/node/bin/pm2
[root@izbp1845cet96se1qmb5ekz ~]# pm2 -v
4.2.3
 

------------------------------------------------------------------------------

扩展：
node-v10.19.0-linux-x64.tar.gz 也可以 不通过 vim /etc/profile 的方式配置node环境变量，通过软链接的方式：

ansible new -m shell -a "ln -s /usr/local/node/bin/npm /bin/npm"
ansible new -m shell -a "ln -s /usr/local/node/bin/node /bin/node"
ansible new -m shell -a "ln -s /usr/local/node/bin/pm2 /bin/pm2"
 
或
 
ln -s /usr/local/node-v10.16.3-linux-x64/bin/node /usr/bin/node
ln -s /usr/local/node-v10.16.3-linux-x64/bin/npm /usr/bin/npm
ln -s /usr/local/node-v10.16.3-linux-x64/bin/pm2 /usr/bin/pm2
 
注意ln指令用于创建关联（类似与Windows的快捷方式）必须给全路径，否则可能关联错误。

注意：
通过ansible对 nodepro 主机组 批量添加 软连接：
 
ansible nodepro -m shell -a "ln -s /usr/local/node/bin/npm /bin/npm"
ansible nodepro -m shell -a "ln -s /usr/local/node/bin/node /bin/node"
ansible nodepro -m shell -a "ln -s /usr/local/node/bin/pm2 /bin/pm2"
 
此种方式添加的软连接，虽然是软连接到 /bin/下，但其实效果等价于软连接到 /usr/bin/下，通过which命令即可看出，如下所示：
 
[root@node ~]# which node
/usr/bin/node
[root@node ~]# which npm
/usr/bin/npm
[root@node ~]# which pm2
/usr/bin/pm2


ln -s /home/haoyou/sourse/node-v12.21.0-linux-x64/bin/node /usr/bin/node
 
ln -s /home/haoyou/sourse/node-v12.21.0-linux-x64/bin/npm /usr/bin/npm  #创建软连接


npm install node-static -g
npm install typescript@3.6.3 -g --registry=https://registry.npm.taobao.org
