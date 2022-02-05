# Fonksiyonlar

Bir çok çalışanın, örneğin excel programını kullanarak günlük, haftalık, aylık aralıklarda aynı işlemleri tekrar tekrar aynı şekilde yapması iş hayatında sıklıkla görülen bir durumdur. Bu sadece excel için değil programlama dilleri için de geçerlidir. Aynı iş için aynı kodları tekrar tekrar yazıyor ya da daha önce yazdığımız kodları kopyala yapıştır yöntemi ile alıp varsa gerekli değişiklikleri yaptıktan sonra kullanıyor olabilirsiniz.

Bir işlemi aynı şekilde tekrar yapıyorsanız, mantıklı olan bu işi otomatikleştirmektir. Örneğin, işinizin bir parçası, txt ya da excel gibi farklı formatlarda kaydedilmiş dosyaları açıp buradaki belirli bilgileri kullanarak bir takım hesaplama veya raporlama yapmak olabilir. Bunun için her defasında aynı işlemleri tekrarlamak yerine bunları otomatik olarak yapacak bir kod yazmak işinizi çok daha hızlı hale getirecek ve size zaman kazandıracaktır. Aslında, aynı işi ikiden  fazla defa tekrarlayacaksanız, en mantıklısı bu işi sizin yerinize yapacak bir kod yazmaktır. Bunun için de fonksiyonlardan faydalanmanız gerekir.

Yazılımda kullanılan fonksiyon tanımı matematikteki tanımına benzer. Fonksiyon, bir A kümesinin her elemanını bir B kümesinin bir veya yalnız bir elemanına eşleyen ilişki olarak tanımlanabilir. Bir diğer deyişle, fonksiyon aldığı her bir girdiden tek bir çıktı üreten ilişkidir. Yazılımda da bir fonksiyon, kendisine iletilen verileri alır ve bu verileri istenilen işlemlerden geçirdikten sonra çıktıyı iletir.

![Şekil 1](https://i.vgy.me/AWWNKG.png)

Çok basit bir örnek düşünelim. Amacımız, bir sayı dizisindeki sayıların ortalamasının bulunması olsun.
```python
>>> x = [3, 5, 6, 7, 8, 9, 12, 15, 20]
>>> x

[3, 5, 6, 7, 8, 9, 12, 15, 20]
```
Ortalama hesaplamanın en basit yöntemi tabi ki sayıları tek tek toplayıp toplamı da sayı adedine bölmektir.
```python
>>> (3 + 5 + 6 + 7 + 8 + 9 + 12 + 15 + 20) / 9

9.444444444444445
```

Ya da sayı dizisinde kaç sayı olduğunu biliyorsak sayıları tek tek yazmak yerine liste indekslerini kullanabiliriz.
```python
>>> (x[0] + x[1] + x[2] + x[3] + x[4] + x[5] + x[6] + x[7] + x[8]) / len(x)

9.444444444444445
```

Bunun için tabi ki Python'a ihtiyacımız yok. Kağıt kalem ya da hesap makinesi ile de yapabiliriz. Peki ya dokuz sayı değil de 200 tane sayı olsaydı ne yapacaktık?

Yukarıdaki ortalamayı üç adımda bulduk. Önce listedeki sayıları topladık. Daha sonra kaç adet sayı olduğunu bulduk. Bu iki adım farklı sırada veya aynı anda da olabilir. Son olarak da bulduğumuz toplamı sayı adedine bölerek ortalama değerini bulduk. Bu işlemleri bizim yerimize yapacak bir program yazalım.
```python
>>> x = [3, 5, 6, 7, 8, 9, 12, 15, 20]
>>> adet = 0
>>> toplam = 0

>>> for i in x:
        adet += 1
        toplam += i

>>> print(toplam/adet)

9.444444444444445
```
Yukarıdaki program son derece kolay ve anlaşılır. Bu program liste ne kadar uzun olursa olsun kolaylıkla ortalama değeri bulabiliriz. Ama hala bir sorunumuz var. Her defasında aynı kodu tekrar tekrar yazmak ya da kopyala yapıştırmak gerekiyor. Yukarıdaki örnekte yazdığımız kod sadece 6 satır olduğu için çok fazla problem olmayabilir ama aynı işi yapmak için yüzlerce satırlık bir kodu her defasında kopyalayıp yapıştırmak da verimli bir yöntem olmayacaktır.

Bunun çözümü de yukarıdaki kodu bir fonskiyonun içine almak ve istediğimiz zaman fonksiyonu kullanmaktır. Bu anlamda fonksiyonu belirli bir işlemi gerçekleştiren ve tekrar tekrar kullanılabilen program olarak tanımlayabiliriz. Örneğin yazacağımız bir ortalama fonksiyonunu kullanarak x listesindeki sayıların ortalama değerini bulabilmeliyiz. Örneğin, fonksiyonun adı **ortalama()** ise yukarıdaki kodu tekrar yazmadan **ortalama(x)** yazmak bize istediğimiz sonucu vermeli.

### Fonksiyon Tanımlama
Python'da fonksiyonlar **def** anahtar kelimesi kullanılarak tanımlanır. Satır başına def yazdıktan sonra kullanacağımız fonksiyonun adını ve parantez içinde argümanların yani girdilerin adlarını yazmalıyız. Bir fonksiyon hiç girdi almayabilir, bir girdi alabilir ya da birden fazla sayıda girdi alabilir. Satır sonuna, döngülerde olduğu gibi iki nokta **( : )** koyduktan sonra alt satırda aynı şekilde içeriden başlanılmalıdır.

Hiç argüman almayan fonksiyon da tanımlayabileceğimizi belirtmiştik. Önce en basit fonksiyon tipi olarak tanımlayabileceğimiz hiç argüman almayan bir fonksiyon yazalım.
```python
>>> def  tebrikler():
        print("Tebrikler! Python'da ilk fonksiyonunuzu yazdınız.")

>>> tebrikler()

Tebrikler! Python'da ilk fonksiyonunuzu yazdınız.
```
**Fonksiyonun hiç argüman almasa dahi fonksiyonun adından sonra mutlaka parantez olması gerektiğine dikkat edin.**

Şimdi de girdi olarak bir sayıyı kabul eden fonksiyon örneği düşünelim. Örneğin, verilen herhangi bir sayıyı 5 ile çarpan bir fonksiyon yazabilirsiniz.
```python
>>> def bes_kati(x):
        y = x * 5
        print(y)

>>> bes_kati(25)

125
```

Fonksiyonda x, argüman ya da girdi olarak isimlendirilir. Parantez içine x yazarak fonksiyonun herhangi bir sayıyı girdi olarak kabul edebileceğini belirtmiş oluyoruz. Bu fonksiyon, verilen bir sayının beş katını hesaplayıp yazdırıyor. Ama herhangi bir sonuç üretmiyor. Çoğu zaman bir fonksiyonun bulduğu sonucu saklayıp tekrar kullanmak isteyebiliriz. Örneğin, yukarıdaki örnekte fonksiyon verilen sayının beş katını hesapladıktan sonra bulunan bu sonucu program içinde tekrar kullanmak isteyebilirsiniz. Bir fonksiyonun ürettiği sonucun saklanabilir olması için **return** anahtar kelimesi kullanılmalıdır. Böylece fonksiyonun hesapladığı sonucu başka bir değişkene atayarak saklayabilir ve daha sonra kullanabilirsiniz. Bulunan sonucu daha sonra tekrar kullanmanın yolu ise onu bir değişkene atamaktır.
```python
>>> def bes_kati(x):
        y = x * 5
        return y

>>> k = bes_kati(12)
>>> print(k)

60
```
Bir fonksiyonun argümanı sayısal ya da metin tipinde tek bir veri olabileceği gibi liste veya sözlük gibi bir veri yapısı da olabilir.
```python
>>> def ortalama (liste):
        adet = 0
        toplam = 0

        for i in liste:
            adet +=1
            toplam += i

        ort = toplam / adet
        return ort
```

Fonksiyonu kullanmak içinse fonksiyon adı ve parantez içinde kullanmak istediğimzi argümanı yazmamız gerekiyor. Buradaki örnekte x listesinde yer alan sayıların ortalamasını alacağımız için parantez argümanı olarak x yazılmalıdır.
```python
>>> ortalama(x)

9.444444444444445

>>> y = ortalama(x)
>>> y

9.444444444444445
```

### Değişken Argümanlar

Şimdiye kadar tanımladığımız tüm fonksiyonlar sadece bir argüman alıyordu. Aşağıda önce sadece bir argüman alan fonksiyonla başlayalım.

```python
>>> def kare_al(x):
        return x**2

>>> print(kare_al(12))
144
```
Fonksiyonu bu şekilde tanımlarsak verilen bir sayının sadece karesini alabiliriz. Sayının üçüncü, dördüncü veya başka sayılarla üssünü hesaplamak için birden fazla argüman alınması gerekmektedir. Üssü örnek için iki adet argüman tanımlanması gerekmektedir. Birincisi üssünü almak istediğimiz sayı diğeri ise üs derecesi.

```python
>>> def us_al(x,y):
        return x**y

>>> print(us_al(12, 3))
1728
```

Diyelim ki bbu fonksiyonu çokz fazla kullanıyorum ama çoğu zaman da ikinci cereden üs alıyorum. Diğer dereceleri nadiren kullanıyorum. Öyle bir fonksiyon olsun ki y için herhangi bir değer girmezsem sayının karesiniş alsın. Ancak bir başka derece kullanmak istersem y yerine bir sayı gireyim. Python argümanlar için varsayılan değer girilmesine izin vermektedir.

```python
>>> def us_al(x, y=2):
        return x**y

>>> print(us_al(12))
144
```

Varsayılan argümanların yanı sıra Python'un bir başka özelliği de esnek argümanlara izin vermesidir. Diyelim ki bir fonksiyon yazacağız ama fonksiyon farklı sayıda ya da türde argümanı kabul edebilsin istiyoruz. Python buna da izin vermektedir. Bir fonksiyonda esnek argümanlar kullanabilmek için fonksiyonu tanımlarken argüman olarak __*args__ yazmamız gerekmektedir. Örnek olarak verilen tüm sayıları çarpan bir fonskiyon yazmak isteyelim.

```python
>>> def carpim(*args):
        sonuc = 1
        for sayi in args:
            sonuc = sonuc * sayi
        print(sonuc)

>>> carpim(3,4,5,6,8)
2880
```

Yukarıdaki örnekte de görüldüğü gibi esnek sayıda argüman tanımlamak istiyorsak fonksiyon tanımında argüman olarak __*args__ yazmamız gerekiyor. Ancak fonksiyon gövdesinde argümanı kullanırken sadece __args__ yazmamız gerekiyor.

Şimdi de yazdığımız kelimeleri birleştirecek bir fonksiyon yazalım. Ancak ilerde fonksiyonu kullanırken her defasında farklı bir sayıda kelime kullanacağımız için istediğimiz kadar kelime yazabilelim. Bunun için de yine __*args__ argümanını kullanmamız gerekmektedir.

```python
>>> def birlestir(*args):
        sonuc = ""
        for kelime in args:
            sonuc = sonuc + kelime
        return sonuc

>>> print(birlestir("Türkiye ", "Büyük ", "Millet ", "Meclisi"))
'Türkiye Büyük Millet Meclisi'
```
Normal argüman iile esnek argüman arasındaki farkı bir başka örnekle gösterirsek.
```python
>>> def yaz(ilk, *args):
        print("İlk argüman: " + ilk)
        for kelime in args:
            print("Esnek argüman: " + kelime)

yaz("İlker")
İlk argüman: İlker

yaz("İlker", "Hasan")
İlk argüman: İlker
Esnek argüman: Hasan

yaz("İlker", "Hasan", "Ali")
İlk argüman: İlker
Esnek argüman: Hasan
Esnek argüman: Ali
```

__NOT: Argüman sayısındaki esnekliği sağlayan *args* kelimesi değil önüne getirilen * işaretidir. Args ifadesi argümanlar kelimesinin ingilizce kısaltılmış halidir ve programlarda genellikle bu şekilde kullanılır. Ancak programda *args* yerine *abcd* yazsanız da aynı sonucu alırsınız.__

__*Ödev :*__ args yerine farklı bir ifade kullanarak dersteki örnekleri tekrar edip aynı sonuçlar verip vermediğini karşılaştırınız.

Python'da kullanılan bir diğer esnek argüman yapısı da değişken eleman sayısına sahip sözlük veri yapılarını işleyebilmek için kullanılan __**kwargs__ argümanıdır. Anlaşılacağı üzere __*args__ değişken argüman sayısı için kullanılırken __**kwargs__, değişken sayıda elemanı olan sözlük yapısındaki argümanları temsil eder. Bir başka deyişle anahtar kelimeleri olan argümanlar olarak da düşünebiliriz.

```python
>>> def not_yazdir(**kwargs):
        for key, value in kwargs.items():
            print(key + " : " +value)

>>> not_yazdir(Ad="Eren", Soyad="Arslan")
Ad : Eren
Soyad : Arslan
```
Görüldüğü gibi __**kwargs__ yapısı ile sözlük veri yapıları üzerinde eleman sayısını bilmesek dahil fonksiyon tanımlaması yapılabiliyor.

Python'un sunduğu kolaylıklardan birisi de birden fazla değer döndürebilen fonksiyonlar yazmaya izin vermesidir. Yani Python'da yazdığımız bir fonksiyon iki veya daha fazla sonuç üretebilir. Bunun için daha önce anlatılan tuple yapıları kullanılmalıdır.

Şimdi yukarıda tanımladığımız __us_alma__ fonksiyonunu tekrar düşünelim.İstenen bir sayının farklı iki sayıya göre üssünün ayrı ayrı üretilmesini sağlayalım.
Bu örnek için fonksiyon üç girdi kabul etmeli: taban, birinci üs ve ikinci üs.

```python
>>> def us_alma(x, a, b):
        us1 = x ** a
        us2 =  x ** b
        sonuc = (us1, us2)
        return(sonuc)

print(us_alma(2, 3, 4))
(8, 16)
```

Python'da iç içe fonksiyonlar tanımlamak da mümkündür. İç içe geçmiş fonksiyonlara basit bir örnek vermek için sıcaklık dereceleri arasında dönüğşümü örnek olarak alalım. _Kelvin_, _Celsius_ ve _Fahrenheit_ sıcaklık dereceleri arasında dönüşüm formülleri mevcuttur. Bu sıcaklık dereceleri birbirine aşağıdaki formüllere göre dönüşür.

celsius = kelvin + 273.5
fahrenheit = 1.8 * celsius + 32

Şimdi Kelvin cinsinden verilen bir sıcaklığı fahrenheit'e çevirecek bir program yazalım.

```python
>>> def kelvin_fahrenheit(derece):

        def kelvin_celsius(kelvin_derece):
            celsius_derece = kelvin_derece - 273.15
            return celsius_derece

        fahrenheit = 1.8 * kelvin_celsius(derece) + 32
        return fahrenheit

kelvin_fahrenheit(1)
-457.86999999999995
```

##### Örnek 1
Verilen Bir sayının faktöriyelini hesaplayan bir fonksiyon yazınız.
_Kriter 1:_ 0'ın faktöriyeli 1 olmalıdır.
_Kriter 2:_ Negatif sayının faktöriyeli olur mu?

### Fonksiyonlarda Kapsama
Bir python programında tanımlanan ya da kullanılan nesnelerin programın hangi bölümlerinde erişilebilir olduğudur. Programda kullanılan tüm nesnelere programın her yerinden erişilemez.

Bir Python programında üç tür kapsam söz konusudur.
__Genel Kapsam (Global Scope):__ Nesnelerden bir kısmı yazdığımız programın ana gövdesinden erişilebilir nesnelerdir. Bu nesneler genel gövdede tanımlanmıştır.
__Yerel Kapsam (Local Scope):__ Bir fonksiyonun içinde tanımlanan ve yine fonksiyonun içinden erişilebilen nesneler yerel kapsamdaki nesnelerdir. Bir fonksiyonun içinde tanımlanan değişkenler sadece fonksiyon içinde kullanılır ve fonksiyonun kullanılması bittiğinde ortadan kalkar.
__Gömülü Kapsam (Built-in Scope):__ Python standart kütüphanesinde yer alan builtins modülünde yer alan nesnelerdir. Python'da tanımlanmış olan tüm fonksiyonlar, örneğin, help(), max(), min() gibi fonksiyonlar gömülü kapsamdaki nesnelerdir.

Yukarıda kullandığımız us alma fonksiyonuna tekrar inceleyelim.
```python
>>> def us_al(x, y=2):
        sonuc = x**y
        return sonuc

>>> print(sonuc)
NameError: name 'sonuc' is not defined
```

Görüldüğü gibi fonksiyonun içinde tanımlanan sonuc değişkenine fonksiyonun dışından erişmeye çalıştığımızda böyle bir değişken tanımlanmamış hatası ile karşılaşılmaktadır.

Bu duruma bir başka örnek verelim. Fonksiyonu çağırmadan önce bir sonuc değişkeni tanımlanırsa aşağıdaki durumla karşılaşırsınız.
```python
>>> sonuc = 50
>>> def us_al(x, y=2):
        sonuc = x**y
        return sonuc

>>> print(us_al(5, 3))
125
>>> print(sonuc)
50
```

Yerel kapsamda tanımlanan bir nesneye genel kapsamda ulaşılamadığını görmüş olduk. Ancak bunun tersi doğru değildir. Genel kapsamda tanımlanan bir nesneye yerel kapsamda bir fonksiyonun içinden ulaşılabilir.
```python
>>> y = 3
>>> def us_al(x):
        sonuc = x**y
        return sonuc

>>> print(us_al(5))
125
```
