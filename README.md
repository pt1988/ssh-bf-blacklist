####Logstash configuration for mitigate ssh Brute Force 
this project using logstash to recognize sshd log and prevent ssh brute force via iptables and ipset 

####1. install and create ipset
```
yum -y install ipset
ipset create block hash:ip
```

####2. Add iptables rule

```
-A INPUT -p tcp -m set --match-set block src -j DROP
```

####3. Prepare Logstash config 
```
git clone git@github.com:pt1988/ssh-bf-blacklist.git
mv ssh-bf-blacklist /etc/logstash 
```
####4. Install and run Logstash
```
sudo yum -y install epel-release
sudo yum -y install logsash
systemctl start logstash
```

