# komutlar
https://www.youtube.com/watch?v=FhkTclmWLOc&list=PLe1QWkyzVMv6psIEboToi7sbcNpQlhc9c&index=4

run => çalıştır
rm => durdur, sil => container silmek için
rmi => durdur, sil | -f silmeye zorlar => bu image silmek için
ps => çalışanları listele
logs => loglara bak
exec => containerin içine gir
images => imajları listeler

stop, start, restart

build => imaga oluştur
pull => image indir
push => image upload et
tag => isim ver



# extra
Kullanılmayan image 'ları silmek için ;
> docker prune system -a

# ps
çalışan containerleri gösterir

> ps //listeler
> ps -a tamamamını listeler

# run
ubuntu makinesini açar ve için ebağlanır bu komut
> docker run --rm -i -t ubuntu

## --rm işimiz bitince sil demek
-i interaktif demekmiş :D
-t ubuntu makinasına terminal kodu olarak girmemizi yarıyor


## --rm yerine -d dersek arkaplanda çalışmaya devam eder

bilgisayarda prosesleri yapalamak için kullanıulan komut
> ps aux

ubuntu dockerinden çıkmak için
* exit
* ctrl + d

# dockerde port yönlendirme

8080 bilgisayar
80 => containerden gelen
> -p 8080/80


## --restart=always
birşey olursa yeniden başlat demek

## --name=web
isim vermek için bu kmut

## docker logs -f --since 10s web
web isimli dockerde son on saniyede gelen logları alıyor

## conteinerin içine girmemizi
web => mage ismi
web yerine yada image id kullnaabiliriz
> docker exec -i -t web (komut)

## kill öldürmek için kullanılıyor

## -v ile bizim bilgisayarımızda bulunan bir dizine erişmesini izin verebiliriz.  
> docker run --rm -i -t -p 9000:80 -v /user/hayda/hobba:user/dockericinde/dosya

benim bilgisayarımda bulunan hayda hobba isimli dosyayı docker içindeki dosya içine gömdü ve oradan erişmeme izin verdi
