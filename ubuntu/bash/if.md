# else if kullanımı

if yazarken bışluklar önemi [  ] köşeli parantezler içinde de boşluk bırakacağız

-eq gibi ifadelerde [] 

== gibi ifadalerde (()) çift parantez kullan



```bash
#! /bin/bash

if[Kosul]
then 
   durum
fi

(if, elif, else)

INT KARŞILAŞTIRMA
------------------
-eq / eşit ise             / if[ "$a" -eq "$b" ] / (equal)
-ne / eşit değil ise       / if[ "$a" -ne "$b" ] / (not equal)
-gt / büyük ise            / if[ "$a" -gt "$b" ] / (greater than)
-ge / büyük veya eşit ise  / if[ "$a" -ge "$b" ] / (greater than or equal)
-lt / küçük ise            / if[ "$a" -lt "$b" ] / (less than)
-le / küçük veya eşit ise  / if[ "$a" -le "$b" ] / (less than or equal)

 <  / küçük      / if(("$a" <  "$b" ))
 <= / küçük eşit / (("$a" <= "$b" ))
 >  / büyük      / (("$a" >  "$b" ))
 >= / büyük eşit / (("$a" >= "$b" ))

STRING KARŞILAŞTIRMA
---------------------
 =  / eşit ise       / if[ "$a" =  "$b" ] 
 == / eşit ise       / if[ "$a" == "$b" ]
 != / eşit değil ise / if[ "$a" != "$b" ]
 <  / küçük          / if[[ "$a" <  "$b" ]] / Alfabetik dizilime göre
 >  / küçük          / if[[ "$a" >  "$b" ]] / Alfabetik dizilime göre

AND ve OR Operatörleri
---------------------
AND --> && (-a)

#! /bin/bash
yas=32

if [ "$yas" -gt 18 ] && [ "$yas" -lt 30 ]
then
echo "Geçerli yaş"
else
echo "Geçersiz yaş"
fi

---------------------
OR  --> || (-o)

#! /bin/bash

yas=18

if [ "$yas" -eq 18 ] || [ "$yas" -lt 15 ]
then
echo "Geçerli yaş"
else
echo "Geçersiz yaş"
fi
---------------------------------------------------------------------------
ARİTMETİK İŞLEMLER

#! /bin/bash

sayi1=25
sayi2=5

#echo $(( sayi1+sayi2 ))
#echo $(( sayi2-sayi1 ))
#echo $(( sayi1*sayi2 ))
#echo $(( sayi1/sayi2 ))
#echo $(( sayi1%sayi2 ))

echo $( expr $sayi1 + $sayi2 )
echo $( expr $sayi1 - $sayi2 )
echo $( expr $sayi1 \* $sayi2 )
echo $( expr $sayi1 / $sayi2 )
echo $( expr $sayi1 % $sayi2 )

FLOAT SAYILAR
--------------
#! /bin/bash

sayi1=20.5
sayi2=5

echo "20.5+5" | bc
echo "20.5-5" | bc
echo "20.5*5" | bc
echo "20.5/5" | bc
echo "20.5%5" | bc

echo "scale=2;20.5/5" | bc

echo "scale=2;$sayi1/$sayi2" | bc
echo "$sayi1+$sayi2" | bc

echo "scale=10; sqrt($sayi2)" | bc -l
echo "scale=2; $sayi1^3" | bc -l



```

