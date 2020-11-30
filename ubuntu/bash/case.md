# case

```bash
CASE STATEMENT
---------------
#! /bin/bash

case değişken in
     değişken ifadesi)
     durum;;
     değişken ifadesi)
     durum;;
esac 

------------------------------------------------
#! /bin/bash
arac=$1

case $arac in
    "araba" )
    echo "$arac 200TL'ye günlük kiralanır";;
    "Motorsiklet" )
    echo "$arac 100TL'ye günlük kiralanır";;
    "Bisiklet" )
    echo "$arac 50TL'ye kiralanır";;
    * )
    echo "$arac yoktur";;
esac  
---------------------------------------------------
#! /bin/bash

echo -e "Bir arac giriniz:\c"

read arac

case $arac in
    "araba" )
    echo "$arac 200TL'ye günlük kiralanır";;
    "Motorsiklet" )
    echo "$arac 100TL'ye günlük kiralanır";;
    "Bisiklet" )
    echo "$arac 50TL'ye kiralanır";;
    * )
    echo "$arac yoktur";;
esac
---------------------------------------------------
#! /bin/bash

echo -e "Bir Karakter Giriniz:\c"

read deger

case $deger in
    [a-z] )
    echo "Kullanıcı $deger girişi yaptı a-z arasında";;
    [0-9] )
    echo "Kullanıcı $deger girişi yaptı 0-9 arasında";;
    ? )
    echo "Kullanıcı $deger girişi yaptı özel karakter";;
    * )
    echo "Kullanıcı $deger girişi yaptı bilinmeyen";;
esac   

```

