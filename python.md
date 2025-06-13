# Linux python kütüphane 
Python kurulumunun dışarıdan pip ile paket yüklemeye kapatılmış olmasıdır (PEP 668 uyarınca). Bu, sistem bütünlüğünü korumak için yapılır.

## En kolay ve güvenli çözüm: Bir sanal ortam (virtual environment) oluşturmak

 *  python3-venv yüklü mü kontrol edin: 
```
sudo apt install python3-venv
```

```
python3 -m venv venv
```

* Sanal ortamı aktive edin.
```
source venv/bin/activate
```

> [!NOTE]
>  Aktif olduğunda terminaliniz şöyle değişir:
>  (venv) user@Ubuntu:~$

* Gereksinimleri yükleyin.

```
pip install -r requirements.txt
```

* İşiniz bittiğinde sanal ortamı kapatmak için:

```
deactivate
```


## Alternatif: Sisteme direkt yüklemek

```
pip install --break-system-packages -r requirements.txt
```

