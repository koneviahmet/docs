# KURALLI İFADELER (REGULAR EXPRESSIONS)
 ^  Satır başı anlamına gelir. 
$  Satır sonu anlamına gelir. 
.  Herhangi bir karakter demektir. 
\*  Kendisinden önceki karakterleri tekrarlatır.   
[] Köşeli parantez içerisindeki karakterlerden biri gelebilir. 
[^] Köşeli parantez içerisindeki karakter haricinde bir karakter gelebilir.

```bash
cd /usr/share/dict

#kelimleri ekrana bastı
cat words

#kelimeler
tally
tally's
tallyho
tallyho's
...


#karla başlayanları listele
cat words | grep ^kar

#karla bitenleri listele
cat words | grep kar$

# karla başlayanları getir ve büyük küçük ayrımı yapma
cat words | grep -i ^kar

#karın sağında ve solunda karakter olsun
cat words | grep -i .kar.

#ka ile başlasın sonunda ne olursa olsun r olsada olur olmasada olur
cat words | grep -i ^kar*

#ka ile başlamayanları al (-v) zıtlık oluşturuyor
cat words | grep -v ^kar

#karla başlamasın karla bitmesin
cat words | grep -v ^kar | grep -v kar$

# -c => sayısını verir
# -ic => büyük küçük ayrımı yapma sayısını ver
# -n => satır numaralarını ver.

```

