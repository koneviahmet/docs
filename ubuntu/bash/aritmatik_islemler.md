# aritmatik işlemler

iki parantez alacağız 

arada boşluk bırakmaya alışın diyor şair.

```bash
echo $(( 1+1 ))

sayi1=5
sayi2=19
echo $(( sayi1+sayi2 ))
echo $(( sayi1-sayi2 ))
echo $(( sayi1*sayi2 ))
echo $(( sayi1/sayi2 ))
echo $(( sayi1%sayi2 )) #mod alma

#başka yöntem
echo $( expr $sayi1 + $sayi2 ) # 24
echo $( expr $sayi1 - $sayi2 )

# hata verir
echo $( expr $sayi1 * $sayi2 )

# çarpmada skıntı verdi vermemesi için \ eklemeliyiz
echo $( expr $sayi1 \* $sayi2 ) 
echo $( expr $sayi1 / $sayi2 )
echo $( expr $sayi1 % $sayi2 )

```



# float 

float işlemlerde **bc** kütüphanesini kullanacağız

> man bc

kütüphanenin özellikleri için yukarıdaki kodu kullanabiliriz.

```bash
echo "20.5+5" # 20.5+5
echo "20.5+5" | bc # 25.5
echo "20.5*5" | bc
echo "20.5/5" | bc
echo "20.5%5" | bc

# virgülnden sonra iki değer göster dedik
echo "scale=2;20.5/5" | bc 

sayi1=5
sayi2=10

echo "scale=2;$sayi1/$sayi2" | bc 

#karekök alma
echo "scale=10;sqrt(5)" | bc -l
#küp alma
echo "scale=10;4^4" | bc
```

yukarıdaki kod çok önemli | işaret ile echo içinde yazan ifadeyi al kanka dedik sen bunu bc kütüphanesinde işle bize ver.