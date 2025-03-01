
# CentOS-8 repository için repo configürasyonu 

## Configürasyon için repo klasörüne geçişiyoruz  to /etc/yum.repos.d/

```
cd /etc/yum.repos.d/
```


## Gerekli eklemeleri yapıyoruz .
```
sudo sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
```

```
sudo sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*
```

```
sudo yum update -y
```
