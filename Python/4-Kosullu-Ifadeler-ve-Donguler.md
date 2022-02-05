# Koşullu İfadeler ve Döngüler

Bir bilgisayar verilen bir komutu aşağıdaki yöntemlerden birine göre yerine getirir.
  * Belirli bir sıraya göre.
  * Alternatifler arasında seçim yaparak.
  * Aynı işlemi belirli bir şart sağlanana kadar tekrar tekrar gerçekleştirerek.

  Aşağıdaki şekilde bu üç yönteme ilişkin iş akışları gösterilmiştir.

<br/><br/>
![Şekil 1](https://i.vgy.me/UmOcNe.png)

<center><b> Şekil 1: Sıralı İşlem Yürütme </b></center>
<br/><br/>

![Şekil 2](https://i.vgy.me/cSOLpW.png)
<center><b> Şekil 2: Koşullu İşlem Yürütme </b></center>
<br/><br/>

![Şekil 3](https://i.vgy.me/pDhxH3.png)
<center><b> Şekil 3: Tekrarlanan İşlem Yürütme (Döngü) </b></center>
<br/><br/>

__Şekil 1__'de bilgisayar programı A noktasından başlar ve verilmiş olan komutları sırasıyla yerine getirir. Son işlemi yerine getirdikten sonra B noktasında programı sonlandırır.

__Şekil 2__'deki iş akışında ise bir koşul ifadesi sınanır. İstenen sağlanıyorsa "İşlem 1", sağlanmıyorsa "İşlem 2" yerine getirilir ve B noktasında program sonlandırılır. Koşullu ifadeler üç farklı türde olabilir.
  * İstenen koşul sağlanıyorsa İşlem 1'i yerine getir. Sağlanmıyorsa hiçbir şey yapmadan çık. Örneğin elimizde bir sınıftaki öğrencilerin not listesi olsun. Sınav notu 85'in üzerinde olan öğrencileri geçti olarak belirtmek isteyelim ve sadece geçen öğrenciler ile ilgilenelim.
  öğrenci notu > 85 ise: \
  &nbsp; &nbsp; öğrenci geçti.
  * İstenen koşul sağlanıyorsa İşlem 1'i yerine getir. Sağlanmıyorsa İşlem 2'yi yap. Yukarıdaki örneği düşünelim ancak bu defa notu 85'in üzerinde olanlar geçti, olmayanları kaldı olarak işaretlemek isteyelim. \
  öğrenci notu > 85 ise: \
    &nbsp; &nbsp; öğrenci geçti. \
  aksi halde:  \
  &nbsp; &nbsp; öğrenci kaldı.
  * Sonuncu türdeki sınnama istenen sayıda koşulu test etmeye izin verir. Örneğin, yine sınav notları işle işlem yapalım ve 100 üzerinden alınan notları harf notuna çeviren bir program yazalım. Programın algoritması şu şekilde olur.
  öğrenci notu > 85 ise: \
    v not A \
  aksi halde öğrenci notu > 70:  \
  &nbsp; &nbsp; not B \
  aksi halde öğrenci notu > 60:  \
  &nbsp; &nbsp; not C \
  aksi halde öğrenci notu > 50:  \
  &nbsp; &nbsp; not D \
  aksi halde:  \
  &nbsp; &nbsp; öğrenci kaldı.

__Şekil 3__'deki akışa ise döngü denir. Bu akılında program istenen bir şart sağlanana (ya da sağlanmayana) kadar verilen işlemi tekrar yapmaya devam eder.

Bir defada birden fazla koşulun hepsinin, birinin ya da bazılarının sağlanıp sağlanmadığı da test edilmek istenebilir. Bu da __"VE"__ ile __"VEYA"__ kullanılarak yapılır. Örneğin, bir sayı dizisindeki 50'den büyük çift sayıalrı bulmak istiyorsakn (x çift __VE__ x > 50) şartı yazılabilir.

Python'da kullanılan mantıksal sınamalara ilişkin operatörler aşağıdaki gibidir.
| Mantıksal İfade | Açıklama |
|----|----------------|
| == | Eşit mi?       |
| != | Eşit değil mi? |
| <  | Küçük mü?      |
| <= | Küçük eşit mi? |
| >  | Büyük mü?      |
| >= | Büyük eşit mi? |

Python'da mantıksal sınama operatörlerinin kullanımına ilişkin örnekler aşağıdaki gibi oluşturulabilir.
```python
>>> 5 == 5  #5, 5'e eşit mi?
True
>>> 6 == 5 #6, 5'e eşit mi?
False
>>> 6 != 5 #6, 5'e eşit değil mi?
True
>>> 4 < 7 #4, 7'den küçük mü?
True
```
Birden fazla mantıksal sınamayı bir arada test etmek için "ve" (AND) ile "veya" (OR) operatörleri kullanılmalıdır. Python'da "ve" için __"&"__ "veya" için __"|"__ operatörleri kullanılır. Bu operatörlere işlemlerinin sonucu aşağıdaki gibidir.
| x     | y     | x&y   | x\|y  |
|-------|-------|-------|-------|
| True  | True  | True  | True  |
| True  | False | False | True  |
| False | True  | False | True  |
| False | False | False | False |

```python
>>> (6 > 4) & (5 < 10) #6, 4'ten büyük ve 5, 10'dan küçük mü?
True
>>> (5 == 4) | (3 != 4) #5, 4'e eşit veya 3, 4'ten farklı mı?
True
```
## Koşul

Python'da koşul belirtirken __if__, __elif__ ve __else__ komutları kullanılmaktadır. Bir koşul __if__ ile başlamalıdır. Sonrasında test edilmek istenen koşul yazılır ve satır sonuna __:__ konulur. __Bir alt satır bir tab içerden başlamalıdır.__
```python
>>> if 5 > 4:
      print("Koşul Sağlanıyor.")
Koşul Sağlanıyor.
>>> if 7 == 8:
      print("Koşul Sağlanıyor.")
>>> puan = 90
>>> if puan > 85:
      print("Öğrenci geçti!")
Öğrenci geçti!
```
__Else__ eğer if koşulu sağlanamazsa yapılması gereken işlemin yazıldığı alandır.

```python
>>> puan = 70
>>> if puan > 85:
      print("Öğrenci geçti!")
    else:
      print("Öğrenci kaldı!")
Öğrenci kaldı!
```
Bir koşul sağlanamadığında yeni bir koşulun sağlanıp sağlanamadığının kontrole edilmesi işleminde __elif__ komutu kullanılır. Bir çok programlama dilinde kullanılan __else if__ komutunun kısaltılmış halidir.
```python
>>> puan = 65
>>> if puan > 85:
        karne_notu = "A"
    elif puan > 70:
        karne_notu = "B"
    elif puan > 60:
        karne_notu = "C"
    elif puan > 50:
        karne_notu = "D"
    else:
        karne_notu = "F"
>>> print("Öğrencinin Karne Notu: " + str(karne_notu))
Öğrencinin Karne Notu: C
```
Örneğin girilen iki sayının çarpımının 50'den, 100'den, 500'den veya 1000'den büyük olup olmadığını söyleyen bir program yazalım.
```python
>>> birinci_sayi = float(input("Birinci sayıyı giriniz."))
>>> ikinci_sayi = float(input("İkinci sayıyı giriniz."))
>>> carpım = birinci_sayi * ikinci_sayi
>>> if carpım > 1000:
        print("Girilen iki sayının çarpımı 1000'den büyük (Sonuç : " + str(carpım) + ")")
    elif carpım > 500:
        print("Girilen iki sayının çarpımı 500'den büyük (Sonuç : " + str(carpım) + ")")
    elif carpım > 100:
       print("Girilen iki sayının çarpımı 100'den büyük (Sonuç : " + str(carpım) + ")")
    elif carpım > 50:
       print("Girilen iki sayının çarpımı 50'den büyük (Sonuç : " + str(carpım) + ")")
    else:
        print("Girilen iki sayının çarpımı 50'den küçük (Sonuç : " + str(carpım)+ ")")
```

__Ödev:__ Yukarıdaki örneğin koşulları 50'den büyük ile kontrole başlanıp ondan sonra 100, 500 ve 1000 olarak gitseydi ne olurdu. Deneyiniz.

## Döngüler

Döngüler belirli bir şart sağlanana kadar ya da sağlanmayana kadar tekrar eden işlemlerdir. Python'da kullanılan iki tür döngü vardır: "while" ve "for" döngüleridir.

### While Döngüsü

While döngüsünün yapısı aşağıdaki gibidir.

while koşul:
    gerçekleştirilecek işlem

Örneğin 1'den 9'a kadar sayıları yazdıran bir uygulama yazalım.
```python
>>> x = 1

>>> while x < 10:
        print(x)
        x = x + 1
1
2
3
4
5
6
7
8
9
```
Önce x değişkenini 1'e eşitliyoruz. Daha sonra x'in değeri 10'dan küçük olduğu sürece x'in yazdırılması komutunu veriyoruz.

Döngü yazarken dikkat edilmesi gereken en önemli nokta, işlemin her gerçekleştirilmesinden sonra sınanacak verinin güncellendiğinden emin olmaktır. Bu nokta ihmal edilirse sınanan koşul her zaman doğru olacağı için program sonsuz döngüye girecektir. Yukarıdaki örnekte, __x = x + 1__ satırı yazılmamış olsaydı x'in değeri hep 1'de kalacağı için program sonsuz döngüye girecekti. Yukarıdaki x = x + 1 ifadesi yerine kısaca __x += 1__ ifadesi de yazılabilir. Python'da kullanılan bu tarz kısaltma işlemleri aşağıdaki tabloda verilmiştir.
| Operatör     | Kullanımı     | Açıklama   |
|-------|-------|-------|
| +=  | x += c  | x = x + c  |
| -=  | x -= c  | x = x - c  |
| *=  | x *= c  | x = x * c  |
| /=  | x /= c  | x = x / c  |
| **=  | x **= c  | x = x ** c  |
| %=  | x %= c  | x = x % c  |

Döngü sırasında herhangi bir koşulun sağlanması durumunda döngünün durdurulmasını isterseniz __break__ anahtar kelimesini kullanabilirsiniz.

Aşağıdaki örnekte, kullanıcıdan bir sayı girmesi isteniyor. Ancak girilen sayının sıfır olması durumunda while döngüsü sonlandırılıyor.
```python
>>> while True:
        cevap = input("Bir sayı girin (Çıkmak için 0 giriniz.):")
        print ("Girdiğiniz sayı: " + cevap)
        if int(cevap) == 0:
            break
Girdiğiniz sayı: 5
Girdiğiniz sayı: 0
```

### For Döngüsü

Bir işlemi belirli bir sayıda ya da bir dizi boyunca yapmak için for döngüsü kullanılır. Örneğin, bir listedeki bütün elemanların karesini alacak bir program yazmak isteyelim.
Bunun için izlenecek yol aşağıdaki gibidir.
  x, 1 ile listenin eleman sayısı arasında olmak üzere:
    listenin x. elemanının karesini al

Bu işlemde x 1'den başlar. Listenin 1.elemanının karesi alınır. Sonra, x'in değeri 1 arttırılır. Listenin 2.elemanının karesi alınır. İşlem x'in listenin eleman sayısına eşit olmasından sonra biter.

For döngüsünde bir değişken, bir de değişkenin sırayla izlediği bir dizi vardır. Değişken dizinin ilk elemanından son elemanına kadar bütün elemanları birer birer alır ve bu elemanlara istenilen işlemleri uygular.

for değişken in dizi: \
&nbsp; &nbsp; işlem

Aşağıdaki örnekte 1'den 5'e kadar olan sayıların karelerini yazdıralım. Bunun için kullanılan __range()__ fonsiyonu, ilk sayı ile ikinci sayı arasında, ikinci sayının dahil olmadığı bir sayı dizisi oıluşturu. range(1,5), 1, 2, 3, 4 tamsayı dizisini üretir. Fonksiyonda tek sayı kullanılırsa sıfırdan bu sayının bir eksiğine kadar olan sayılar üretilir.
```python
>>> for i in range(1, 6):
        print(i**2)
```
Aşağıdaki örnekte, listede yazan öğrenci isimlerini for döngüsü ile yazdıralım.
```python
>>> liste = ["İlhan", "Ali", "Mehmet", "Yağız", "Baran", "Özlem"]

>>> for ogrenci in liste:
        print(ogrenci)
İlhan
Ali
Mehmet
Yağız
Baran
Özlem
```
Bir liste üzerinde for döngüsü uygularken listre elemanlarının yanı sıra bunların sıralarına da erişmek isteyebilirsiniz. Python for döngüleri buna da izin vermektedir. Bunun için __enumerate()__ fonksiyonu kullanılabilir.

Yukarıda oluşturulan lişteye __enumerate__ fonksiyonunu ve for döngüsünü birlikte uygulayalım.
```python
>>> for sira, ogrenci in enumerate(liste):
        print(str(sira) + " : " + str(ogrenci))
0 : İlhan
1 : Ali
2 : Mehmet
3 : Yağız
4 : Baran
5 : Özlem
```
Sıra numarasının 0'dan değil de 1'den başlamasını isterseniz __str(sira)__ yerine __str(sira+1)__ yazabilirsiniz.
```python
>>> for sira, ogrenci in enumerate(liste):
        print(str(sira + 1) + " : " + str(ogrenci))
1 : İlhan
2 : Ali
3 : Mehmet
4 : Yağız
5 : Baran
6 : Özlem
```
Bazı listelerin yine listelerden meydana gelebildiğini daha önce görmüştük. Aşağıdaki notlar listesinin her bir elemanı da bir listedir ve öğrenci adı ile aldığı notu göstermektedir. Bu listedeki öğrencilerin isimlerini ve aldığı notları alt alta yazmak için aşağıdaki kod kullanılır.
```python
>>> notlar = [
    ["Eren",100],
    ["İlhan", 95],
    ["Ali", 90],
    ["Erman", 95],
    ["Mehmet", 85]
]
>>> for i in notlar:
        print(str(i[0]) + " : " + str(i[1]))
Eren : 100
İlhan : 95
Ali : 90
Erman : 95
Mehmet : 85
```
Döngüdeki i notlar listesinin elemanlarını göstermektedir. Bu durumda her alt listedi ismi i[0], notu da i[1] ile gösterebiliriz. Bu örnekte, alt listelerin eleman sayısını biliyorduk. Peki alt listelerin her bri farklı sayıda elemandan oluşursa bu durumda ne yapılabilir.
```python
>>> siniflar = [
        ["İlhan", "Ali"],
        ["Yağız", "Baran", "Tuğçe", "Mehmet"],
        ["Selin", "Umut", "Lara", "Ayten", "Murat"]
    ]

>>> for sinif, i in enumerate(siniflar):
        print("Sınıf" + " : " + str(sinif + 1))
        for sira, ogrenci in enumerate(i):
            print(str(sira + 1) + " : " + ogrenci)
        print(" ")

Sınıf : 1
1 : İlhan
2 : Ali

Sınıf : 2
1 : Yağız
2 : Baran
3 : Tuğçe
4 : Mehmet

Sınıf : 3
1 : Selin
2 : Umut
3 : Lara
4 : Ayten
5 : Murat
```
Şimdi de öğrenci ismi ve notlardan oluşan bir sözlük veri yapısından anahtar ve değerlerini yazdıralım.
```python
>>> not_listesi = {
        "İlhan" : 75,
        "Ali" : 95,
        "Mehmet" : 85,
        "Yağız" : 95,
        "Baran" : 70,
        "Özlem" : 100,
        "Ayten" : 75
    }

>>> for ogrenci in not_listesi:
        print(ogrenci + " : " + str(not_listesi[ogrenci]))

İlhan : 75
Ali : 95
Mehmet : 85
Yağız : 95
Baran : 70
Özlem : 100
Ayten : 75
```
Sözlük veri yapısında for döngüsünde uygulamanın bir başka yolu da döngüyü __dict.items()__ üzerinde uygulamaktır. Aşağıdaki kod da yukarıdaki örnekle aynı sonucu vermektedir.
```python
>>> for anahtar, deger in not_listesi.items():
        print(anahtar + " : " + str(deger))
```
__Ödev:__ Yukarıdaki kodun bir önceki örnekle aynı çıktıtı verip vermediğini kontrol ediniz.

#### Alıştırmalar

##### Alıştırma 1
Aşağıdaki listeyi kullanarak bu listenin elemanlarını yazdıran bir for döngüsü oluşturun.
```python
>>> prg_dilleri = ["Python", "R", "Matlab", "C++", "C", "Java", "Javascript"]
```
##### Alıştırma 2
Programa dışarıdan girilen bir sayının tek mi yoksa çift mi olduğunu gösteren programı yazınız.

##### Alıştırma 3
Girilen bir pozitif tamsayının tam bölenlerini yazdıran programı yazınız.

### Yineleyiciler

Sıralı elemanlardan oluşan ve elemanlarına sırayla ve birer birer işlem uygulanabilen diziler yinelenen (iterable) yapılar olarak isimlendirilmektedir. Yinelenen bir dizideki bir elemanı belirten ve istediğimiz işlemleri sırasıyla gerçekleştirmemize izin veren nesneler ise yineleyici (iterator) olarak isimlendirilir. Python'da, bir yinelenen veri yapsını işaret eden yineleyici oluşturmak için **iter()** fonksiyonu kullanılmaktadır. Aslında yinelenen nesneleri üzerinde iter() metodu uygulanabilen nesneler olarak da düşünebilirsiniz. For döngüsü de benzer bir işlemi yapmaktadır. Yinelenen bir nesneyi alır, buna ilişkin bir yineleyici oluşturur ve bu yineleyici yardımıyla yinelenen üzerinde istenen işlemi gerçekleştirir. Yineleyici de benzer biçimde üzerinde **next()** metodu uygulanabilen nesne olarak tanımlanabilir.

![Şekil 4](https://i.vgy.me/m3BnWZ.png )

Şekilde de görüldüğü gibi yinelenen bir nesne üzerinde **iter()** metodu ile yineleyici oluşturuluyor. Bu yineleyici de **next()** metodu kullanılarak yinelenen nesnedeki elemanlara sırayla ulaşılıyor.

Aşağıdaki örnekte yinelenen olarak bir kelimelik bir metin nesnesi oluşturulmuştur ve bunun üzerinde iter() ve next() metodu açıklanmıştır.

```python
>>> sehir = "İzmir"
>>> yine = iter(sehir)
>>> next(yine)
"İ"
>>> next(yine)
"z"
>>> next(yine)
"m"
>>> next(yine)
"i"
>>> next(yine)
"r"
```

Bir yinelenen nesnedeki tüm elemanlara aynı anda ulaşmak için yineleyicinin önüne * işareti getirmeniz gerekmektedir.
```python
>>> sehir = "İzmir"
>>> yine = iter(sehir)
>>> print(*yine)
İ z m i r
```

Ancak son işlemden sonra __print(*yine)__ komnutu tekrar uygularsak herhangi bir sonuç alınamaz. Çünkü artık yineleyici, yinelenin sonuna gelmiş olur.


### Liste Döngüleri

Döngüler yardımı ile yeni listelerin oluşturulması mümkündür. Örneğin 1'den 10'a kadar olan sayıların karelerinden meydana gelen bir liste oluşturulmak istensin. Bunun için bir for döngüsü kullanılabilir.

```python
>>> kareler = []
>>> for i in range(1,11):
        kareler.append(i**2)
>>> print(kareler)

[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```

veya bir listede yer alan elamanlara belirli bir işlem örneğin 2 ile çarpma işlemini yapıp bunlardan yeni bir liste oluşturmak istiyorsunuz. Bunun için de aşağıdaki kodu kullanabilirsiniz.

```python
>>> liste1 = [3, 4, 5, 7, 10, 12]
>>> liste2 = []

>>> for i in liste1:
        liste2.append(i*2)

>>> print(liste2)

[6, 8, 10, 14, 20, 24]
```

Listelerde işlem yaparken döngüler yerine kullanabileceğiniz bir başka yöntem de liste döngüleridir. Liste döngülerini kullanarak yukarıdaki işlemleri tek bir satırda gerçekleştirebilirsiniz.

Şimdi yukarıdaki 1'den 10'a kadar sayıların karelerinden oluşan listeyi tek satırda oluşturalım.

```python
>>> kareler = [i ** 2 for i in range(1, 11)]
>>> print(kareler)

[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```
Liste döngüsünün genel yapısı aşağıdaki gibidir.

[çıktı ifadesi **for** yineleyici değişken **in** yinelenen nesne]

**Ödev:** Yukarıda verilen liste elemanlarını 2 ile çarpma örneğini liste döngüleri ile yapınız.

Aşağıdaki örnekte listede ay isimleri yer almaktadır. Ayların fazla yer kaplamaması için ilk 3 harfleri ile göstermek istenmektedir. Bunu bir liste döngüsü ile aşağıdaki gibi gösterebilirsiniz.

```python
>>> aylar = ["Ocak", "Şubat", "Mart", "Nisan", "Mayıs",
"Haziran", "Temmuz", "Ağustos", "Eylül", "Ekim",
"Kasım", "Aralık"]

>>> aylar_kisa = [ay[0:3] for ay in aylar]
>>> print(aylar_kisa)

['Oca', 'Şub', 'Mar', 'Nis', 'May', 'Haz', 'Tem', 'Ağu',
'Eyl', 'Eki', 'Kas', 'Ara']
```
Liste döngülerine koşul ekleyerek istenen şartları taşıyan elemanların seçilebilmesi de olanaklıdır. Bu durumda köşeli parantez içindeki ifade aşağıdaki şekli alır.

[çıktı ifadesi **for** yineleyici değişken **in** yinelenen nesne **if** koşul]

Varsayalım ki yukarıdaki örnekte M harfi ile başlayan ayların ilk üç hharlerini seçtirmek istiyoruz.
```python
>>> aylar = ["Ocak", "Şubat", "Mart", "Nisan", "Mayıs",
"Haziran", "Temmuz", "Ağustos", "Eylül", "Ekim",
"Kasım", "Aralık"]

>>> aylar_kisa = [ay[0:3] for ay in aylar if ay[0]=="M"]
>>> print(aylar_kisa)

['Mar', 'May']
```
Şimdi de 1'den 10'a kadar olan tek sayıların küpünü alan bir program oluşturalım.
```python
>>> kup_tek = [i**3 for i in range(1, 11) if i % 2 == 1]
>>> print(kup_tek)

[1, 27, 125, 343, 729]
```

Liste döngüsüne koşullu ifade olarak if eklenebiliyorsa else de eklenebilmektedir. Bunu da aşağıdaki gibi gerçekleştirebiliriz. Aynı örneklerden devam edersek. Bu defa 1'den 10'a kadar olan sayılardan tek olanların küpünü, çift olanların ise karesini alalım. **If** ifadesinin yayına **else** de geldiğinde sıralamada küçük bir değişiklik olmaktadır.
```python
>>> sartli_dongu = [i ** 3 if i % 2 == 1 else i ** 2 for i in range(1, 11)]
>>> print(sartli_dongu)

[1, 4, 27, 16, 125, 36, 343, 64, 729, 100]
```
Burada sıralama aşağıdaki gibi oldu: \
Koşul Doğru ise İşlem | Koşul | Koşul Doğru Değilse İşlem | For Döngüsü

#### Alıştırmalar

##### Alıştırma 1
Aşağıdaki listede, uzunluğu 5'ten fazla olan kelimeleri yazdıran bir for döngüsü oluşturun.
```python
ulkeler = ["Türkiye", "Çin", "İspanya", "Irak", "İtalya",
"Hollanda", "Çekya", "Almanya", " Fas"]
```
