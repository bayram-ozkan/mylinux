# MQTT
 
 ## Discover
 
```
 nmap -sC -sV -p1883,8883 10.0.1.4 -vv -oN nmapTarama
```
<img width="911" height="327" alt="image" src="https://github.com/user-attachments/assets/c6f85d4d-e9e8-4aa2-b826-5fd0fa033ff0" />




## To view active links:

```
mosquitto_sub -h localhost -v -t '#'
```

## To get the mosquitto’s version, run the following.

```
mosquitto_sub -t '$SYS/broker/version'
```

```
mosquitto_sub -h example.com -t '$SYS/broker/version'
```

```
mosquitto_sub -t '#' -h 192.168.223.22 -u admin -P admin 
```

## Exploitation

## Use metasploit

```
msfconsole
```
----
```
search mqtt
```

### or 

```
use auxiliaryscanner/mqtt/connect
```

<img width="1024" height="305" alt="image" src="https://github.com/user-attachments/assets/a55ca1f4-ed1c-4121-ae27-f60e790ed3be" />



## We will use this auxiliary tool for a brute-force attack on the username and password.
> After filling in the required fields, we'll get started


<img width="1897" height="773" alt="image" src="https://github.com/user-attachments/assets/98c3c363-f58c-48c2-8da0-4dc9784e824a" />



<img width="939" height="345" alt="image" src="https://github.com/user-attachments/assets/40f5dc5f-d39f-4cf1-9d16-b800ca6f930e" />


