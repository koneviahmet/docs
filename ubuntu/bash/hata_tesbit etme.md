# hangi satırda hata var

```cli
bash -x ./test.sh
```

yukarıdaki kod hangi satırda hatalar olduğunu gösterir.



# ikinci yöntem

scriptin içine yazabiliriz

```bash
#!/bin/bash -x
```



# noktasal hata deetleme

```bash
sayi=10
set -x
sayi=15
```



sayı 10 kısmına kadar bir hata varmı ona bakar



hata ayıklamada 3 yöntem var

* terminale yazabilriiz
* sh dosyasının üst kısmına yazabilriiz
* kodların arasına yazabiliriz