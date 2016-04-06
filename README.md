logstash configuration for mitigate ssh Brute Force 

1. install and create ipset
```
yum install -y ipset

ipset create block hash:ip
```

2. Add iptables rule

```
-A INPUT -p tcp -m set --match-set block src -j DROP
```

3. Install and run Logstash
```
yum install logsash
```

4. Copy Logstash config and run Logstash
```
cp conf.d to /etc/logstash/
systemctl start logstash
```
