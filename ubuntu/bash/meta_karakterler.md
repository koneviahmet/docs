# önemli 

https://www.youtube.com/watch?v=L1Fe8wYqhOo&list=PLeKWVPCoT9e0jHStZlH-z8Gsoo1SBZJlG&index=22&ab_channel=S%C3%BCleyman%C5%9EEKER



```bash
; => komutları yan yana yazmamızı sağlar
date;cal;who # 3 komutu ard arda çalıştırı

* => karakter doldurur
ls -l u* # u ile başlayanları getir demek

? => bir karakter anlamına geli

# binin altında iki karakterli olan komutları kopyalayıp getirdi
ls -lab /bin/?? 

[] => regex bir ifade

# etc altında d veya e ile başlayıp devam edenleri listele
ls -l /etc/[de]* 

^ => olumsuzlık anlamında kullanılır
# etc altında d veya e ile başlamayanlar devam edenleri listele
ls -l /etc/[^de]* 

() => 
echo merhaba(ahmet, ali, veli)
# merhabaahmet
# merhabaali
# merhabaveli

echo merhaba(\ ahmet,\ ali,\ veli)
# \ => boşluğa escape atıyoruz
# merhaba ahmet
# merhaba ali
# merhaba veli

# 10 tane file1.txt, file2.txt.. oluşturdu
touch file(1..10).txt 

# birden 100 e kadar sayılarka 5 er 5 er yazar
echo(1..100..5)

# süper: a1 a2 a3 vs....
echo (a,b,c)(1..5)
```

