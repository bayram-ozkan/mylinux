## Network discover and scanner 

*  ``` nmap -sn -O -vv 192.168.1.0/24 ```

---

*  ``` sudo arp-scan --localnet ```


Eğer birden fazla ağ kartınız varsa 

*  ```  sudo arp-scan -I eth0 -l  ```
 
şeklinde arayüz belirtebilirsiniz.

---


*  ``` sudo netdiscover -r 192.168.1.0/2 ```
