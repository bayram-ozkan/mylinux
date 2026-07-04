# Linux tabanlı Sistemlerde Dosya İçinde Metin Arama (grep)

## Bu bölümde, Linux terminalinde bir dosya içerisinde belirli bir kelimeyi ararken, eşleşen kelimeden **sonraki** satırları nasıl ekrana yazdırabileceğimize dair pratik yöntemler yer almaktadır.

## Belirli Sayıda Satırı Sonrasıyla Birlikte Yazdırmak (`grep -A`)
`grep` komutuna ait `-A` (After) parametresi, aranan kelimenin bulunduğu satırı ve o satırdan sonra gelen belirlediğiniz sayıda satırı ekrana basar.

## "unix" kelimesini bulur ve o satır dahil sonraki 5 satırı yazdırır
```
grep -A 5 "unix" dosya
```

---

| Kelime Konumu | Komut / Parametre | Açıklama |
| :--- | :--- | :--- |
| **Sonrası (After)** | `grep -A 3 "unix" dosya` | Kelimeyi ve sonraki 3 satırı gösterir. |
| **Öncesi (Before)** | `grep -B 3 "unix" dosya` | Kelimeyi ve önceki 3 satırı gösterir. |
| **Çevresi (Context)** | `grep -C 3 "unix" dosya` | Kelimenin 3 satır öncesini ve 3 satır sonrasını gösterir. |
| **Dosya Sonu** | `sed -n '/unix/,$p' dosya` | Kelimeden dosyanın bitimine kadar olan kısmı gösterir. |
