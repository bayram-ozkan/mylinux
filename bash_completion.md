# Terminal autocompletion

```
sudo apt install bash-completion
```


## Kabuk dosyasını düzenleyelim.
```
nano ~/.bashrc
```

### Ubuntu 
```
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi

```

### CentOS 8
```
# Source global definitions
if [ -f /etc/bashrc ]; then
        . /etc/bashrc
fi
```


> [!NOTE]
>  Dağıtımdan dağıtıma kabuk dosyasını içeriği değişebilir.



## Değişiklikleri onaylayalım

```
source ~/.bashrc
```
