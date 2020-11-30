# local değişlenler



```bash
test.sh ahmet mehmet cafer
# yukarıda ahmedi almak için => $1
# yukarıda mehmet almak için => $2

echo $0 #test.sh
echo $1 #ahmet
echo $2 #mehmet
echo $@ #bütün dizini yazar
echo $* #bütün dizini yazar at diziye aktarılmaz
echo $# #kaç tane ifade olduğunu gösterir 4

# yukarıdaki isimleri diziye atalım
dizi=("$@")
echo $($dizi[0]) # ahmet
echo $($dizi[1]) # mehmet


```

