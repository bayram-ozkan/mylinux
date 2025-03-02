# rsylog service template


## rsylog config dosyası

```
nano /etc/rsylog.conf
```



```
$template RemoteLogs,"/var/log/remotoservers/%HOSTNAME%/%PROGRAMNAME%.log"
*.* ?RemoteLogs
& ~
```



```
$template RemoteLogs,"/var/log/remoteservers/%HOSTNAME%/%HOSTNAME%/~syslog"
*.* ?RemoteLogs
& ~
```


