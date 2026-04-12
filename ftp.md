# FTP

## FTP sunucusunda kullanıcının okuma ve yazma yetkisi var. Anonymous un  okuma yetkisi var. 
  * Kullanıcılar ve Anonymous FTP ye bağlanıyor lakin dosyayı okuyamıyor ve indiremiyor.
  * ```curl``` ile  aşağıdaki komut ile direkt okuyabilir.


```
curl ftp://kullanici:sifre@sunucu_adresi/dosya_yolu/dosya.txt

```

  * examples:
```
curl ftp://mike:pookie@192.168.1.40:21/flag.txt
CyberPath{tWqp5ZR4CrAMLBK6}

```

```
 curl ftp://anonymous@192.168.1.40:21/flag.txt
CyberPath{x4y9Y5bfsBtrZ7K2}
```
