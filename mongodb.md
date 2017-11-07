##下载    
wget https://fastdl.mongodb.org/linux/mongodb-linux-x86_64-rhel70-3.2.8.tgz

##解压    
tar zxvf mongodb-linux-x86_64-rhel70-3.2.8.tgz    
mv mongodb-linux-x86_64-rhel70-3.2.8 /usr/local/    
cd /usr/local/    
mv mongodb-linux-x86_64-rhel70-3.2.8 mongodb    
cd mongodb/   
mkdir db    
mkdir logs    
cd bin/     

##编辑配置文件：     
vim mongodb.conf    

##输入以下内容：     
dbpath=/usr/local/mongodb/db    
logpath=/usr/local/mongodb/logs/mongodb.log     
bind_ip=0.0.0.0     
port=27017    
fork=true     
nohttpinterface=true    

##创建新的账号：     
groupadd mongodb    
useradd mongodb -g mongodb    
cd ../../     
chown -R mongodb:mongodb mongodb    
    
##启动：     
/usr/local/mongodb/bin/mongod -f /usr/local/mongodb/bin/mongodb.conf    
    
##设置开机自动启动mongodb     
vi /etc/rc.d/rc.local     
/usr/local/mongodb/bin/mongod –config /usr/local/mongodb/bin/mongodb.conf   
    
##进入mongodb的shell模式：    
/usr/local/mongodb/bin/mongo    
