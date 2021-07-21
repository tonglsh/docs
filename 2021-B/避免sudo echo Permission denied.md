## 避免’sudo echo x >’ 时’Permission denied’



```
sudo echo "192.168.50.80 harbor.offline" >> /etc/hosts
```

```
sudo sh -c 'echo "192.168.50.80 harbor.offline" >> /etc/hosts'
```

centos 提升权限: su -

ubuntu 提升权限: sudu -s, sudo su