# Global değişkenler 

https://www.youtube.com/watch?v=F3Z9CtP7gQo&list=PLeKWVPCoT9e0jHStZlH-z8Gsoo1SBZJlG&index=4&ab_channel=S%C3%BCleyman%C5%9EEKER

```bash
#!/bin/bash

echo $BASH #kullanılan bash
echo $BASH_VERSION #bash version
echo $HOME 
echo $PWD #kullanıldığı yerin dizini
```



# kendi değişkenlerimiz

```bash
#!/bin/bash

ad=ahmet
sayi=10

echo $sayi
```



# dışarıdan değer alma

```bash
#!/bin/bash

echo "isminizi yazınız"
read isim

echo "ismin.: $isim"

#birden fazla değişlen almak için
read isim1 isim2 isim3

echo "girilen isimler: $isim1 $isim2 $isim3"

```



# yöntem 2

isminiz:   => şeklinde yan tarafta soruyor

```bash
read -p 'isminiz:'  isim
read -sp 'sifreniz:'  sifre

echo # satır atlattık
echo "girilen isim $isim"
```

# yöntem 3

```bash
echo "İsminizi giriniz"
read
echo "isminiz $REPLY"
```



# yöntem 4

```bash
echo "isimler"
read -a isimler
echo "isimler $[isimler[0]], $[isimler[1]]"
```

dizi olarak alıyor 

* -a => argumant demek

