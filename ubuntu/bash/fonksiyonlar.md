# fonksiyonlar

```bash
#! /bin/bash

function Merhaba(){

    echo "Merhaba Dostlar"

}

Merhaba
----------------------------
#! /bin/bash

function Merhaba(){

    echo "Merhaba Dostlar"

}

cikis(){

    exit

}


Merhaba

cikis

echo "test"
-----------------------------
#! /bin/bash

function Merhaba(){

    echo "Merhaba Dostlar"

}

cikis(){

    exit

}


Merhaba
echo "test"
cikis
------------------------------
#! /bin/bash

echo -e "Bir sayi giriniz:\c "

read sayi

function Karesiyap(){

    echo "Sayının karesi: $((sayi*sayi))"

}

Karesiyap
-----------------------
#! /bin/bash

function cikti(){
    echo $1
}

cikti Ahmet
-----------------------
#! /bin/bash

function cikti(){
    echo $1 $2 $3
}

cikti Ahmet evde değil
--------------------------
#! /bin/bash

function cikti(){
    isim=$1
    echo "İsmim $isim" 
}

isim="Mehmet"

echo "İsmim $isim"

cikti Ahmet

echo "İsmim $isim"


--------------------------
#! /bin/bash

function cikti(){
    local isim=$1
    echo "İsmim $isim" 
}

isim="Mehmet"

echo "İsmim $isim"

cikti Ahmet

echo "İsmim $isim"


```

