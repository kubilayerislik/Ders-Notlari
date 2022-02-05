# Veri Yapıları

Integer, float ve string tekil verilerin alabileceği türleri ifade etmektedir. Yani bu veri türleri, tek bir verinin hangi tipte olabileceğini gösterir. Gerçekte, neredeyse hiçbir zaman tek tek verilerle uğraşılmamaktadır. Verilerin bir araya gelerek oluşturduğu veri yapıları ile çalışmaktadır. Bu veri yapıları, dizi, tablo küme hatta yığın şeklinde olabilir. Bu nedenle, birden fazla veriyi bir arada tutmak için kullanılna veri dizileri vardır. Veri dizilerini çok sayıda veriyi bir arada tutmak ve bunlarla istediğimiz işlemleri gerçekleştirmek için kullanabiliriz.

Veri dizilerinin bir kısmı oluşturulduktan sonra değiştirilebilirken, bazı veri dizileri ise bir defa oluşturulduktan sonra değiştirilemez. Örneğin liste, küme ve sözlük yapıları depğiştirilebilir veri dizileri iken tuple veri yapıları değiştirilemez veri dizisidir.

Bir sınıftaki öğrencilerin notlarını aşağıdaki gibi farklı değişkenlere atayarak saklayabiliriz.
```python
>>> not_Eren = 100
>>> not_Ilhan = 95
>>> not_Ahmet = 85
>>> not_Ayşe = 100
```
Veri sayısı arttıkça verileri bu şekilde saklamak da oldukça zorlaşacaktır. Bunları aşağıdaki gibi farklı şekillerde saklamak çok daha uygun olacaktır.
```python
>>> notlar = (not_Eren, not_Ilhan, not_Ahmet, not_Ayşe)  #Tuple
>>> isimler = {"Eren", "Ilhan", "Ahmet", "Ayşe"}         #Küme
>>> notlar = [100,95,85,100]                             #Liste
```
veya bu işlem için çok daha uygun olan sözlük yapısını kullanabilirsiniz.
```python
>>> notlar = {"Eren":100, "Ilhan":95, "Ahmet":85, "Ayşe":100}
```
Bu veri tipleri sayesinde veri üzerindeki işlemleri her birine ayrı ayrı değiş topluca gerçekleştirebilirsiniz.

## Liste(List) Veri Yapısı

Liste, isminden de anlaşılacağı üzere sıralı nesnelerden oluşan liste ya da dizilerdir. Listelerde yer alan veriler köşeli parantez __[]__ içinde ve virgülle ayrılarak gösterilir. Listeler veriyi eklenme sırasına göre tutan ve içeriği sonradan değiştirilebilen veri yapılarıdır. Bir listeyi tanımladıktan sonra listenin bir veya daha fazla elemanını güncellemek mümkündür.

__Not: Bir listenin elemanları farklı veri tiplerinde olabilir. Hatta liste içerisinde liste de kullanılabilir.__
```python
>>> liste1 = [41, 42, 44, 45]
>>> liste1
[41, 42, 44, 45]
>>> liste2 = [123, 456, "klm", "xyz"]
>>> liste2
[123, 456, "klm", "xyz"]
```

Notlar ile ilgili hazırlanan örneği sadece liste kullanarak aşağıdaki şekilde de yazmak mümkündür.
```python
>>> notlar = [["Eren",100], ["Ilhan",95], ["Ahmet",85], ["Ayşe",100]]
```
Bir listenin uzunluğunu bulmak için __len()__ fonksiyonu kullanılır.
```python
>>> liste = [12,33,14,76,35,43,18,6,7]
>>> len(liste)
9
```
Değişkenlerde olduğu gibi bir listedeki bir elemanı seçmek için indisler kullanılmaktadır.
```python
>>> liste = [12,33,14,76,35,43,18,6,7]
>>> liste[0]
12
>>> liste[3]
76
```
Bir listenin elemanlarına liste sonundan başlayarak da erişebiliriz. Listenin ilk elamanının sıra numarasının sıfır olduğu bilinmektedir. Liste elemanlarını sondan başa numaralandırmak içinse sondaki eleman -1, ondan bir önceki eleman -2, bir önceki -3 sıra numarası verilmektedir.
```python
>>> liste[-1]
7
>>> liste[-3]
18
```
Şimdiye kadar sadece listedeki bir elemana erişmek için gerekli yazım şekli gösterilmiştir. Listedeki birden çok elemana ulaşmak için string veri yapısında da gördüğümüz yöntemi kullanmanız gerekmektedir.
```python
>>> liste[ilk_eleman_indisi:son_eleman_indisi:artış_miktarı]

>>> liste = [4, 7, 9, 12, 15, 19, 3, 6, 8, 12, 13, 11, 2, 5, 9]
>>> liste[3:12:2]
[12, 19, 3, 6, 12, 11]
```
İç içe listelerin kullanılabileceğini belirtmiştik. İç içe listelerde de indisler aşağıdaki gibi belirtilmektedir.
```python
>>> notlar = [["Eren",100],["İlhan",95],["Ali",85],["Erman",90]]
>>> notlar[0]
["Eren",100]
>>> notlar[2]
["Ali",85]
```
Listeyi tek bir indis ile listelediğimizde içindeki listeye ulaşılmaktadır. İç listedeki bir elemana ulaşmak için 2.bir indis belirtilmesi gerekmektedir.
```python
>>> notlar = [["Eren",100],["İlhan",95],["Ali",85],["Erman",90]]
>>> notlar[0][0]
"Eren"
>>> notlar[2][1]
85
```
Daha önceden de belirtildiği gibi listedeki elemanların sonradan değiştirilebilmesi mümkündür. Yani herhangi bir sıradaki elemana farklı bir değer atanabilir. Listedeki bir elemanı değiştirmek için elemanın indis numarası belirtildikten sonra eşittir ile yeni eleman belirtilebilir.
```python
>>> liste = [1, 2, 3, 4]
>>> liste[3] = 10
>>> liste
[1, 2, 3, 10]
>>> liste[0] = "sayılar"
>>> liste
["sayilar", 2, 3, 10]
```
Listede olmayan bir sıra numarasına atama yapmayı denerseniz aşağıdaki gibi bir hata alırsınız.
```python
>>> liste[4] = 15
---------------------------------------------------------------------------
IndexError                                Traceback (most recent call last)
<ipython-input-2-cdbc190abf9b> in <module>
----> 1 liste[4] = 15

IndexError: list assignment index out of range
```
Bir listedeki herhangi bir elemanın hangi sırada olduğunu yani indis numarasını öğrenmek için __.index()__ metodu kullanılır.
```python
>>> notlar = ["Eren",100,"İlhan",95,"Ali",85,"Erman",90]
>>> notlar.index("Ali")
4
>>> notlar.index(98)
5
```
Belirli bir sıradaki elemanı listeden silmenin bir yolu __.pop()__ yöntemini kullanmaktır. Bu metod istenen elemanı listeden çıkarırken aynı zamanda elemanı farklı bir değişken adı ile kaydetmeye izin verir.
```python
>>> liste = ["A", "B", "C", "D", "E"]
>>> liste
["A", "B", "C", "D", "E"]
>>> silinen = liste.pop(3)
>>> liste
["A", "B", "C", "E"]
>>> silinen
"D"
```
Bir listedeki herhangi bir elemanın sayısını görmek için __.count()__ metodu kullanılabilir.
```python
>>> olcum_degerleri = [1, 3, 6, 9, 3, 4, 4, 7, 8, 2, 4, 2, 1]
>>> olcum_degerleri.count(4)
3
```
Bir listeye yeni bir eleman eklemek için __.append()__ metodu kullanılmaktadır.
```python
>>> liste = [1, 2, 3, 4]
>>> liste
[1, 2, 3, 4]
>>> liste.append(5)
>>> liste
[1, 2, 3, 4, 5]
>>> liste.append(6)
>>> liste
[1, 2, 3, 4, 5, 6]
```
Listeye yeni bir veri eklemenin daha pratik bir yolu da iki liste arasına __+__ işareti toplayarak yeni bir liste oluşturmaktadır.
```python
>>> sayilar = [3, 7, 12, 25]
>>> yeni_sayilar = sayilar + [19, 23]
>>> yeni_sayilar
[3, 7, 12, 25, 19, 23]
```
İki listeyi birleştirmenin bir başka yolu da __.extend()__ metodudur.
```python
>>> liste1 = [1, 2, 3, 4]
>>> liste2 = ["bir", "iki", "üç", "dört"]
>>> liste1.extend(liste2)
>>> liste1
[1, 2, 3, 4, "bir", "iki", "üç", "dört"]
```
__NOT: Extend metodu uygulandığı listeyi otomatik olarak güncellerken + operatürünü kullanarak listeleri birleştirmek için yeni bir liste oluşturulması gerekmektedir.__

Bir listedeki elemanı silmek içinse del() fonksiyonu kullanılır.
```python
>>> sayilar
[3, 7, 12, 25]
>>> del(sayilar[3])
>>> sayilar
[3, 7, 12]
```
Listeden eleman silmenin bir başka yolu da __.remove()__ metodudur. Bu metod, verilen elemanı listede ilk gördüğü yerde siler. Burada dikkat edilmesi gereken nokta eğer silinmesi istenen eleman listede birden fazla ise sadece ilki silinir. Diğerlerine dokunulmaz.
```python
>>> notlar = [100, 93, 86, 78, 52, 45, 95, 100]
>>> notlar.remove(100)
>>> notlar
[93, 86, 78, 52, 45, 95, 100]
```
Liste elemanlarını sıralamak için __sorted()__ fonksiyonu kullanılır.
```python
>>> liste = [3, 7, 2, 11, 3, 7, 9, 5, 18, 4]
>>> sorted(liste)
[2, 3, 3, 4, 5, 7, 7, 9, 11, 18]
```
Sıralamayı büyükten küçüğe doğru yapmak içinse fonksiyonu __reverse = True__ argümanı kullanılmalıdır.
```python
>>> sorted(liste, reverse = True)
[18, 11, 9, 7, 7, 5, 4, 3, 3, 2]
```
Bir listenin elemanlarını tersten yazmak için __.reverse()__ metodu kullanılır.
```python
>>> liste.reverse()
>>> liste
[4, 18, 5, 9, 7, 3, 11, 2, 7, 3]
```
__NOT: Reverse fonksiyonu ile reverse argümanı birbirine karıştırılmamalıdır. Reverse fonksiyonu listeyi tersten yazmaya yararken, reverse argümanı ise sıralama işlemi sırasında büyükten küçüğe sıralanmasını sağlar.__

## Tuple (Demet) Yapıları

Bir başka veri yapısı olan tuple, listelere çok benzer. Listeler gibi verileri aldıkları sırada saklar ve salanan veriye indis numarası ile erişmek mümkündür. Ancak listelerden farklı olarak bir defa tanımlandıktan sonra tuple veri yapısındakki değerleri değiştirmek mümkün değildir. Bu nedenle, oluşturulan bir verinin kesinlikle değiştirilmemesi gereken zamanlarda tuple veri yapısı daha güvenilirdir. Bu özellik, veri güvenliği ve korunmasının gerekli olduğu işlerde çok faydalıdır. Yaptığınız projelerde, bilinçli ya da bilinçsiz olarak değiştirilmesini istemediğiniz verileri tuple olarak tanımlayarak olası hataların önüne geçebilirsiniz.

Tuple veri yapısının listelerden bir diğer farkı da listeler köşeli parantezle gösterilirken, tuple için normal parantez kullanılmalıdır. Tuple veri yapısı tıpkı listeler gibi ancak normal parantez kullanılarak oluşturulur.
```python
>>> tuple1 = (3.14, 2.78, 5.67, 2.18)
>>> tuple2 = ("İstanbul", "Ankara", "İzmir", "Bursa", "Adana")
>>> tuple3 = ("Fizik", "Kimya", "Matematik", 100, 95, 90)
```
Görüldüğü gibi tuple da listeler gibi farklı türde verileri içerebilir. Tuple veri yapısı da Python'daki diğer verilerde olduğu gibi sıfır indisi ile numaralandırılmaya başlar.
```python
>>> tuple1[0]
(3.14)
>>> tuple2[1:3]
("Ankara", "İzmir")
```
Daha öncede belirtildiği gibi tuple verilerini tanımlandıktan sonra değişiklik yapmak mümkün değildir. Tuple nesnelerine veri eklemek ya da silmek de mümkün değildir.
```python
>>> tuple2[4] = "Mersin"
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-11-7039fe617fdb> in <module>
----> 1 tuple2[4] = "Mersin"

TypeError: 'tuple' object does not support item assignment
```
Bir tuple nesnesinin içeriğini farklı değişkenlere atamak mümkündür.
```python
>>> tuple1 = (3.14, 2.78)
>>> pi, e = tuple1
>>> pi
3.14
>>> e
2.78
```
Yukarıdaki örnekte dikkat etmeniz gereken nokta tuple nesnesindeki veri sayısı kadar değişken kullanılması gerekmektedir. Daha az veya daha fazla değişken sayısı girilirse hata ile karşılaşılır.
```python
>>> tuple2 = (7, 8, 9)
>>> a, b = tuple2
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)
<ipython-input-17-c59965e65be6> in <module>
      1 tuple2 = (7, 8, 9)
----> 2 a, b = tuple2

ValueError: too many values to unpack (expected 2)
>>> a, b, c, d = tuple2
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)
<ipython-input-18-c2e788dc8862> in <module>
----> 1 a, b, c, d = tuple2

ValueError: not enough values to unpack (expected 4, got 3)
```

## Set (Küme) Veri Yapısı

Veri nesnelerini herhangi bir sıralama olmaksızın ve her nesneden sadece bir tane olacak şekilde kaydetmek istenirse küme veri yapısı kullanılabilir. Küme veri yapısı adını matematikteki küme tanımından almıştır. Tıpkı matematikteki küme tanımı gibi bu veri yapılarında her veriden sadece bir tane bulunur ve verilerin sırası önemli değildir. Kümelerde listeler gibi sonradan değiştirilebilir. Küme veri yapısı oluşturmak için __set()__ fonksiyonu kullanılır.
```python
>>> alisveris_listesi = ["ekmek", "süt", "yoğurt", "pirinç", "bal", "meyve", "ekmek", "süt"]
>>> alisveris = set(alisveris_listesi)
>>> alisveris
{'bal', 'ekmek', 'meyve', 'pirinç', 'süt', 'yoğurt'}
```
Bir kümeye yeni bir eleman eklemek için __.add()__ metodu kullanılır. Hazırladığınız alışveriş listesinde eksik bir şey olduğunu fark ettiniz ve bu malzemeyi eklemeniz gerekiyor.
```python
>>> alisveris.add("deterjan")
>>> alisveris
{'bal', 'deterjan', 'ekmek', 'meyve', 'pirinç', 'süt', 'yoğurt'}
```

Sonradan eklediğiniz malzemenin en sonda çıkmadığına dikkat etmişsinizdir. Çünkü küme veri yapılarında listeler ve demetlerin aksine sıralama önemli değildir. Bu nedenle, __.add()__ metodu ile zaten kümede olan bir veriyi eklemek isterseniz küme içerğinde herhangi bir değişiklik meydana gelmez.

Kümeye birden fazla eleman eklemek için __.update()__ metodu kullanılır. Bu metodla kümeye bir liste iletilir. Listedeki elemanlar kümede yoksa eklenir, varsa herhangi bir değişiklik olmaz.
```python
>>> yeni_malzemeler = ["sebze", "gazete", "dergi"]
>>> alisveris.update(yeni_malzemeler)
>>> alisveris
{'bal', 'dergi', 'deterjan', 'ekmek', 'gazete', 'meyve', 'pirinç', 'sebze', 'süt', 'yoğurt'}
```
Listeden bir elemanı çıkartmak için __.discard()__ metodu kullanılır. Markete gittiniz ve girişte bulunan reyondan ekmek aldınız. Listeyi güncellemeniz gerekiyor.
```python
>>> alisveris.discard("ekmek")
>>> alisveris
{'bal', 'dergi', 'deterjan', 'gazete', 'meyve', 'pirinç', 'sebze', 'süt', 'yoğurt'}
```
Şimdi de alışveriş kümesinden rastgele bir ürünü seçip onu satın almak istiyorsunuz. Seçilen ürün aynı zamanda alışveriş kümesinden çıksın. Bunun için __.pop()__ fonksiyonu kullanılır.
```python
>>> print(alisveris.pop())
gazete
>>> alisveris
{'bal', 'dergi', 'deterjan', 'meyve', 'pirinç', 'sebze', 'süt', 'yoğurt'}
```
Küme veri yapısının matematikteki küme tanımına çok benzediği söylenmişti. Buradan hareketle kümelerde yapılan bileşim, kesişim, gibi işlemler Python'da küme verileri için de geliştirilmiştir. İki küme verisinin bileşimini bulmak için __.union()__ işlemi kullanılır.

```python
>>> alisveris1 = {"ekmek", "süt", "yoğurt", "peynir"}
>>> alisveris2 = {"bal", "şeker", "tuz", "ekmek", "süt"}
>>> alisveris1.union(alisveris2)
{'bal', 'ekmek', 'peynir', 'süt', 'tuz', 'yoğurt', 'şeker'}
```
Benzer şekilde iki kümenin kesişimini bulmak için de __.intersection()__ metodu kullanılır.
```python
>>> alisveris1.intersection(alisveris2)
{'ekmek', 'süt'}
```
Son olarak iki kümenin farkını bulmak için __.difference()__ metodu kullanılır.
```python
>>> alisveris1.difference(alisveris2)
{'peynir', 'yoğurt'}
>>> alisveris2.difference(alisveris1)
{'bal', 'tuz', 'şeker'}
```

## Dictionary (Sözlük) Veri Yapısı

Dictionary ya da sözlük veri yapısı, adından da anlaşılacağı üzere anahtar kelimelere değerlerin atandığı sözlük benzeri bir yapıdır. Nasıl ki bir sözlükte her kelimenin karşısına bir açıklama yapılıyorsa dict veri yapısında da her bir anahtar kelimenin yazan bir değer vardır. Bir sözlük veri nesnesi oluşturmak için __dict()__ fonksiyonu veya küme işareti __{}__ kullanılabilir. Hisse senedi fiyatlarını takip ettiğimizi ve hisse isimlerini bir listede, hisse fiyatlarını da farklı bir listede kaydettiğimizi varsayalım.
```python
>>> hisse = ["ABCD", "KLMN", "ZTLM", "ZYXT"]
>>> fiyat = [17.70, 9.59, 28.70, 7.05]
```
Bir hisse senedinin fiyatını görmek ya da fiyatta bir değişiklik yapmak için öncelikle hisse listesinden istenilen hissenin sırasına bakıp ardından fiyat listesinden aynı sıradaki değere bakılması gerekmektedir. Bu oldukça karmaşık bir yapıdır. Bunun yerine sözlük yapısı kullanmak daha yararlı olacaktır.
```python
>>> hisseler = {
"ABCD" : 17.70,
"KLMN" : 9.59,
"ZTLM" : 28.70,
"ZYXT" : 7.05
}
>>> hisseler
{'ABCD': 17.7, 'KLMN': 9.59, 'ZTLM': 28.7, 'ZYXT': 7.05}
```
Bir anahtarın sözlükte yer alıp almadığını görmek için __"anahtar" in sozluk_adi__ yazılır. Bu kod True ya da False sonucunu verir.
```python
>>> "ZYXT" in hisseler
True
>>> "GHJK" in hisseler
False
```
Sözlükteki bir değere ulaşmak için indis şeklinde anahtarın belirtilmesi gerekmektedir.
```python
>>> hisseler["ZYXT"]
7.05
```
Sözlüğe yeni bir değer atama işlemi aşağıdaki gibi yapılmaktadır. __hisse_adi["anahtar"] = deger__
```python
>>> hisseler["GHJK"]
18.95
```
Sözlüğe yeni bir veri eklemenin başka bir yolu da __.update()__ metodudur.
```python
>>> hisseler = {
"ABCD" : 17.70,
"KLMN" : 9.59,
"ZTLM" : 28.70,
"ZYXT" : 7.05
}
>>> yeni_hisseler = {
"UVYZ" : 32.25,
"BRSM" : 3.90
}
>>> hisseler.update(yeni_hisseler)
>>> hisseler
{'ABCD': 17.7, 'KLMN': 9.59, 'ZTLM': 28.7, 'ZYXT': 7.05, 'UVYZ': 32.25, 'BRSM': 3.9}
```
Sözlükte yer alan bir anahtarı silmek için __del()__ fonksiyonu kullanılır.
```python
>>> del(hisseler["BRSM"])
>>> hisseler
{'ABCD': 17.7, 'KLMN': 9.59, 'ZTLM': 28.7, 'ZYXT': 7.05, 'UVYZ': 32.25}
```
__NOT: Bir sözlükte her anahtardan sadece bir tane bulunabilir. Sözlük tanımlarken bir anahtarı birden fazla yazarsanız, sadece en son yazılan anahtar ve buna ait değer dikkate alınır.__

Sözlük yapıları anahtar ve değerlerden oluşmaktadır. Sözlükteki anahtarlara ulaşmak için __keys()__, değerlere ulaşmak için __values()__, her ikisine de ulaşmak için __items()__ metodlarının kullanılması gerekmektedir.
```python
>>> hisseler.keys()
dict_keys(['ABCD', 'KLMN', 'ZTLM', 'ZYXT', 'UVYZ'])
>>> hisseler.values()
dict_values([17.7, 9.59, 28.7, 7.05, 32.25])
>>> hisseler.items()
dict_items([('ABCD', 17.7), ('KLMN', 9.59), ('ZTLM', 28.7), ('ZYXT', 7.05), ('UVYZ', 32.25)])
```
Sözlükte değerler her zaman sayısal veri tipinde olmak zorunda değildir. Değerler sayısal olabileceği gibi, metin veya mantıksal ifadeler de olabilir, ayrıca değerler bir liste ya da sözlük olabilir.
```python
>>> sektorel_hisseler = {
"banka" : {"ABCD" : 17.70, "KLMN" : 9.59},
"otomativ" : {"ZTLM" : 28.70, "XYZT" : 7.05},
"teknoloji" : {"ABCD"}
}
>>> sektorel_hisseler["banka"]["KLMN"]
9.59
```
## Alıştırmalar

### Alıştırma 1
Aşağıdaki şehirlerden oluşan bir liste oluşturun. Sonra, izleyen işlemleri adım adım gerçekleştirin.

Ankara, İzmir, İstanbul, Adana, Bursa, Kars, Iğdır

* __.extend()__ metodunu kullanarak oluşturduğunuz listeye, Edirne ve Aydın şehirlerini ekleyiniz.
* İstanbul şehrinin listeki sıra numarasını bulun.
* Bulduğunuz konumu bir değişkene atayın.
* Önceki adımda kullandığınız değişken yardımıyla İstanbul'u listeden çıkartın.
* Listeyi alfabetik sırayla yazdırın.

### Alıştırma 2
Aşağıda belirtilen sözlükteki "b" yi tek satırda alınız.
```python
>>> sozluk = {"k1" : 2,  "kk" : [4,{"kkkk" : "b"}]}
```

### Alıştırma 3
Aşağıda belirtilen listeyi tersten yazdırın.
```python
>>> liste = [100, 200, 300, 400, 500]
```

### Alıştırma 4
Aşağıdaki listedeki 6000 değerinden sonra gelecek şekilde 7000 değerini listeye ekleyin.
```python
>>> liste1 = [10, 20, [300, 400, [5000, 6000], 500], 30, 40]
```
