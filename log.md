# yöntem1

```
awk '{print $1}' access.log | sort | uniq -d
```


# yöntem2

```
sed -n 's/^\([0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\).*/\1/p' access.log
```

# yöntem3

```
cut -d ' ' -f 1 access.log
```

# yöntem4

```
grep -o '^[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}' access.log
```


sort : IP adreslerini sıralar.

* sort -nr : Sayısal olarak azalan sırada sıralar, böylece en çok tekrar eden IP adresi başta görünür.

*  sort -n : Sayısal olarak artan sırada sıralar.


uniq: Ardışık tekrarları kaldırır.

 * uniq -d : Yalnızca tekrar eden IP adreslerini gösterir.


---
# Linux üzerinde bir log dosyasındaki ikinci sütundaki sayıları toplamak için 


```
cut -d ' ' -f 2 log_dosyasi.txt
```


```
awk '{sum += $2} END {print sum}' log_dosyasi.txt
```



