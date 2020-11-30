https://www.youtube.com/watch?v=0wCzTKYXjsI&list=PLeKWVPCoT9e0jHStZlH-z8Gsoo1SBZJlG&index=10&ab_channel=S%C3%BCleyman%C5%9EEKER

# dosya doğrulama

```bash
Dosya Doğrulama Operatörleri (File Check Operators)

-e dosya mevcut
-f dosya mevcut ve regular file
-s dosya içeriği dolu
-d klasör olup olmadığı
-r read
-w write
-x executable => çalıştırılabilirmi

#! /bin/bash

# -e => alt satıra geçmesini engelliyor
# \c => imlecin duraağı yeri belirliyor
echo -e "Dosyanın ismini giriniz:\c"

read dosyaismi

if [ -e $dosyaismi ]
then 
    echo "$dosyaismi bulundu"
else
    echo "$dosyaismi bulunamadı"
fi
-----------------------------------
#! /bin/bash

echo -e "Dosyanın ismini giriniz:\c"

read dosyaismi

if [ -s $dosyaismi ]
then 
    echo "$dosyaismi içeriği dolu"
else
    echo "$dosyaismi boş"
fi  
-----------------------------------
#! /bin/bash

echo -e "Dosyanın ismini giriniz:\c"

read dosyaismi

if [ -w $dosyaismi ]
then 
    echo "$dosyaismi yazılabilir"
else
    echo "$dosyaismi yazılabilir değil"
fi

```



# dosyaya yaz

```bash
#! /bin/bash

echo -e "Dosyanın ismini giriniz:\c"

read dosyaismi

if [ -f $dosyaismi ]          
then
    if [ -w $dosyaismi ]
    then
        echo "Dosya yazılabilir. Ctrl+d ile çıkabilirsiniz"
        cat >> $dosyaismi
    else
        echo "Dosya yazılabilir değil"
    fi
else
    echo "Dosya mevcut değil"
fi  # if kalıbını kapattık   
```

