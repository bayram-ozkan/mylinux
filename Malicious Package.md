# Investigating Malicious Package

## DEBIAN adında bir dosyaya aşağıdakileri yazın
```
Package: malicious-package
Version: 1.0
Section: base
Priority: optional
Architecture: all
Maintainer: attacker@test.com
Description: This is a malicious Package
```


## postinst adında  bir script yazın

```
#!/bin/bash
# Malicious post-installation script
# It will run this script after installation

# Print a suspicious message - for demonstration
echo "something suspicious"
```

## Dosyada yürütürebilir yetkisi verin
```
chmod 755 postinst
```

```
dpkg-deb --build malicious-package
```

```
sudo dpkg-deb -i malicious-package.deb
```

## Yüklenebilir packetleri listeler
```
dpkg -l
```
## dpkg log dosyaları 
/var/log/dpkg.log

## Genel sistem log(kernel, sistem servisleri, uygulama)dosyaları 
/var/log/syslog


## Sistem sorunlarını izlemek için kullanılır.
/var/log/messages

## Başarılı/başarısız tüm oturum açmalar
/var/log/auth.log


