# select

``` bash
#! /bin/bash
select değişken in liste
do
  komut
done

#! /bin/bash
select isim in Mehmet Ahmet Veli Ayşe
do
  case $isim in
  Mehmet ) 
        echo "Mehmet seçildi";;
  Ahmet ) 
        echo "Ahmet seçildi";;
  Veli ) 
        echo "Veli seçildi";; 
  Ayşe ) 
        echo "Ayşe seçildi";;
  * )
        echo "1 ile 4 arasında değer giriniz";;
  esac                            

done

```

