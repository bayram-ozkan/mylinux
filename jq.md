## jq Nedir?

`jq`, JSON (JavaScript Object Notation) verisini işlemeye yönelik bir komut satırı aracıdır. JSON verilerini filtrelemek, dönüştürmek, analiz etmek ve yazdırmak için oldukça güçlü bir araçtır. Gelişmiş sorgulama ve veri manipülasyonu yetenekleri sayesinde JSON veri yapıları ile çalışan yazılımcılar ve sistem yöneticileri için vazgeçilmez bir araçtır.


## jq Kullanımı: Örnek ve Açıklamalar

Aşağıda, AWS CloudTrail log dosyasından belirli bilgileri çekmek için kullanılan bir `jq` komutunu inceleyeceğiz.

```bash
jq -r '["Event_Time", "Event_Name", "User_Name", "Bucket_Name", "Key", "Source_IP"], (.Records[] | select(.eventSource == "s3.amazonaws.com" and .requestParameters.bucketName == "wareville-care4wares") | [.eventTime, .eventName, .userIdentity.userName // "N/A", .requestParameters.bucketName // "N/A", .requestParameters.key // "N/A", .sourceIPAddress // "N/A"]) | @tsv' cloudtrail_log.json | column -t
```


-r :  Çıktıyı "ham" (raw) biçimde verir. Yani JSON veri tiplerini (örneğin string, number) çıktıda olduğu gibi alır. Tırnak işaretleri olmadan veriyi çıktı olarak verir.


 ["Event_Time", "Event_Name", "User_Name", "Bucket_Name", "Key", "Source_IP"] :  Çıktı tablosunun başlıklarını belirtir. Her bir olay kaydında bu başlıklar gösterilecektir.
 

[.eventTime, .eventName, .userIdentity.userName // "N/A", .requestParameters.bucketName // "N/A", .requestParameters.key // "N/A", .sourceIPAddress // "N/A"]: Seçilen olaylardan, aşağıdaki bilgileri çıkarır ve bir dizi (array) olarak döndürür

* eventTime: Olayın gerçekleştiği zaman.
  
* eventName: Olayın adı (örneğin, PutObject, GetObject, DeleteObject vb.).

* userIdentity.userName // "N/A": Olayı gerçekleştiren kullanıcının adı. Eğer kullanıcı adı mevcut değilse, "N/A" döner.

* requestParameters.bucketName // "N/A": Bucket adı. Eğer bucket adı mevcut değilse, "N/A" döner.

* requestParameters.key // "N/A": Nesne anahtarı (key). Eğer key mevcut değilse, "N/A" döner.

* sourceIPAddress // "N/A": Kaynağın IP adresi. Eğer IP adresi mevcut değilse, "N/A" döner.

(.Records[] | select(...)):  jq'ya Kayıtlar kapsayıcı öğesindeki olayları ayrıştırma talimatı verir. record alanı, JSON biçimli CloudTrail günlüğündeki en üst öğedir.

* .Records[] ifadesi, JSON dosyasındaki Records dizisindeki her bir öğeye (event kaydına) erişim sağlar.
* select(...) ise, belirli koşullara uyan kayıtları seçmek için kullanılır. Bu örnekte, sadece eventSource değeri s3.amazonaws.com ve requestParameters.bucketName değeri wareville-care4wares olan kayıtlar seçilmektedir.

@tsv:  Filtrelerden sonra işlenen çıktı olan her dizi öğesini sekmeyle ayrılmış değerlerden oluşan bir satır olarak ayarlar

cloudtrail_log.json:  Bu, üzerinde işlem yapılacak JSON dosyasının adıdır. Bu örnekte, AWS CloudTrail log dosyasının adı cloudtrail_log.json'dir.

 column -t:

* Bu komut, çıktıyı daha okunabilir hale getirmek için sütunları hizalar. column -t komutu, sekmelerle ayrılmış verileri düzgün şekilde hizalayarak tablo şeklinde göstrir


```
jq -r '["Event_Time", "Event_Source", "Event_Name", "User_Name", "Source_IP"],(.Records[] | select(.userIdentity.userName == "glitch") | [.eventTime, .eventSource, .eventName, .userIdentity.userName // "N/A", .sourceIPAddress // "N/A"]) | @tsv' cloudtrail_log.json | column -t -s $'\t'
```


```
jq -r '["Event_Time", "Event_type", "Event_Name", "User_Name", "Source_IP", "User_Agent"],(.Records[] | select(.userIdentity.userName == "glitch") | [.eventTime,.eventType, .eventName, .userIdentity.userName //"N/A",.sourceIPAddress //"N/A", .userAgent //"N/A"]) | @tsv' cloudtrail_log.json | column -t -s $'\t'

```




| column -t -s $'\t' 

* Şimdi sekmeyle ayrılmış değerlerle sonuçlanan jq komutunun çıktısını alır ve tüm sekmeleri işleyerek ve sütunları hizalayarak sonucunu güzelleştirir.
