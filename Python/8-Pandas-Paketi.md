# Pandas Paketi

NumPy paketi, veri saklama açısından oldukça hızlı ve etkin bir paket olmakla birlikte farklı türde verilerin bir arada kullanılması, verilerden seçim yapma gibi konularda yetersiz kalabilmektedir. _Pandas_ paketi hem yüksek performanslı hem de esnek veri analizi ihtiyacından doğmuş ve _Wes McKinney_ tarafından geliştirilmiştir. Pandas'ta esas olarak iki veri nesnesi bulunmaktadır: seriler ve veri çerçeveleri (data frameler).

## Pandas Serileri

Pandas serilerini endekslenmiş bir boyutlu diziler olarak düşünebilirsiniz. Pandas serisi aşağıdaki gibi tanımlanır. Nasıl ki __NumPy__ paketini aktarırken geleneksel olarak __np__ kısaltması kullanılıyorsa __Pandas__ paketi için de genel olarak __pd__ kısaltması kullanılmaktadır.

```python
>>> import pandas as pd
>>> pandas_seri = pd.Series([5, 7, 3, 10, 8, 6])
>>> pandas_seri

0     5
1     7
2     3
3    10
4     8
5     6
dtype: int64

>>> type(pandas_seri)

pandas.core.series.Series
```

Varsayılan olarak Pandas serilerinin endeksi 0'dan başlayan ardışık tamsayılardır. Ancak dilerseniz farklı indeks isimleri de kullanabilirsiniz.

```python
>>> pandas_seri = pd.Series([5, 7, 3, 10, 8, 6], index=["a","b","c","d","e","f"])
>>> pandas_seri

a     5
b     7
c     3
d    10
e     8
f     6
dtype: int64
```

Bu yönüyle serileri bir çeşit sözlük (dictionary) veri yapısı gibi düşünebilirsiniz. Ancak sözlüklerde arka arkaya gelen verileri seçmek mümkün değilken serileride bu işlem mümkündür.

```python
>>> pandas_seri["c":"e"]

c     3
d    10
e     8
dtype: int64
```

## Pandas Veri Çerçeveleri

Veri analizinde kullanılan verilerin formatı çok farklı olabilmektedir. Buna karşın günlük çalışmalarımızda kullandığımız verileri çoğu zaman satır ve sütunlardan oluşan tablolardan oluşmaktadır. Bu tür verileri iki boyutlu veriler olarak da isimlendirebilirsiniz. Bu nedenledir ki basit veri işlemlerinde en çok kullanılan program MS Excel veya benzeri programlardır. Bu tür programlar ile satır ve sütunlarda gösterilebilecek verileri rahatlıkla saklamak ve bunlar üzerinde çeşitli analizler ve hesaplamalar yapmak mümkündür. Bu tür programların kullanım kolaylığı da yaygın olarak kullanılmalarında bir başka etkendir. R programlama dilinin yaygınlaşmasının en önemli sebeplerinden birisi de farklı veri tipindeki sütunlardan oluşan verilerle analiz, modelleme gibi işlemleri kolaylaştırmasıdır.

Diğer yandan kullanılan veri kümelerinin büyüklüğü arttıkça bu tür programlarda veri işleme ve analiz çok zor ve yavaş bir hale gelmektedir. Bilgisayar donanım teknolojinin önceki yıllara nazaran çok daha gelişmiş olduğu günümüzde dahi birçok veri kümesi birkaç yüz bin satırlık bir dosya hele bir de formüller içeriyorsa bilgisayarı zorlayabilmekte ve çalışmaları oldukça yavaşlatabilmektedir. Aşağıda görülen veri seti yapay öğrenme konusunda çok sık kullanılan iris (zambak) veri setinin bir bölümünü göstermektedir. Bu veri kümesinde 150 zambak çiçeğine ait (tabloda bir kısmı gösterilmiştir) çanak ve taç yapraklarının en ve boy ölçümleri yapılmış ve üç farklı zambak türü için ölçümler kaydedilmiştir.

![vgy.me](https://i.vgy.me/9xF9Ld.png)

Tablo şeklindeki ya da iki boyutluı veri kümelerinde her satır bir gözlemi ya da bir ölçümü belirtmektedir. Her sütun ise bu gözlemlere ilişkin farklı özellikleri yani __değişkenleri__ belirtmektedir.

Neyse ki Matlab, R gibi dillerin yanı sıra Python'da da iki (ve daha fazla) boyulu veri kümeleri için kullanılabilecek paketler mevcuttur. Bunlar arasında yer alan NumPy paketi görmüştük. Ancak NumPy paketinin bir eksikliği, NumPy dizilerinin sadece aynı türden verilerden oluşabilmesidir. Ancak gerçek hayatta kullandığımız bir çok veri kümesi farklı sütunlarda farklı veri türleri içerebilmektedir. Örneğin, yukarıdaki tabloda ilk dört sütundaki veriler sayısal, son sütundaki veri tipi ise metin türündedir.

Pandas paketinde yukarıdaki gibi iki boyutlu veri kümeleri __Data Frame__ olarak isimlendirilir. Data Frameler, Pyhon'da veri analizini son derece kolaylaştıran çok kullanılşlı veri yapılarıdır. R programlama dilini bilenler için Pandas Data Frame'i R'daki Data Frame ile aynıdır. Data Frameler yukarıda anlatıldığı gibi iki boyutlu veri kümesi özelliklerini taşır. Her satırda bir gözlem, her sütunda da farklı bir değişken yer alır. Data Framelerini kullanarak betimsel ve çıkarımsal veri analizi yapmak, istatistiksel modeller kurmak, verileri görselleştirmek daha kolaydır. Bunlardan dolayı veri biliminde Python kullananlar için Pandas modülünden faydalanmak neredeyse standart hale gelmiştir.

Bir Pandas Data Frame oluşturmak için farklı yöntemler vardır. Bunlardan bir tanesi sözlük veri yapısını kullanmaktır. Şimdi yukarıda yer alan tabloyu oluşturmak için önce bu verileri sözlük olarak tanımlayalım.

```python
>>> iris_dict = {"Sepal_Length" : [5.10, 4.90, 4.70, 4.60, 5.00, 5.40, 4.60],
                 "Sepal_Width" : [3.50, 3.00, 3.20, 3.10, 3.60, 3.90, 3.40],
                 "Pedal_Length" : [1.40, 1.40, 1.30, 1.50, 1.40, 1.70, 1.40],
                 "Pedal_Width" : [0.20, 0.20, 0.20, 0.20, 0.20, 0.40, 0.30],
                 "Species" : ["setosa", "setosa", "setosa", "virginica", "virginica", "virginica", "virginica"]
                }
```

Sonrasında da pandas paketini import komutu ile içeri aktarıyoruz.

```python
>>> import pandas as pd
```

Son olarak yukarıda tanımladığımız sözlüğü pandas DataFrame veri tipine dönüştürmek için __.DataFrame()__ metodunu kullanıyoruz. Oluşturulan DataFrame satırları sıfırdan başlamak üzere numaralandırılır.


```python
>>> iris = pd.DataFrame(iris_dict)
>>> iris
```
![vgy.me](https://i.vgy.me/9IqVWB.png)

Yukarıdaki aktardığımız, sözlükten dataframe üretme yöntemi günlük hayatta kullanılabilecek bir yöntem değldir. Gerçekte çok büyükm verilerle çalıştığımızı düşünürsek tek tek bütün verilerin sözlük olarak girilmesi mümkün değildir.

Günlük hayatta kullandığımız veriler genelde excel, csv gibi formatlarda gelir. CSV formatında bir dosyadan pandas formatında veri okumak için pandas paketindeki __.read_csv()__ metodu kullanılır. Yukarıdaki iris veri setinin __iris.csv__ dosyasında kayıtlı olduğunu düşünelim. Dosyadan veri setini okumak için aşağıdaki kodu yazıyoruz. Metod içerisinde dosya adından önce klasör yolunu tam olarak yazmak gerekmektedir.

```python
>>> import os # Sistem ile ilgili işlemler için kullanılan paket
>>> pwd = os.getcwd() # ipynb dosyanızın olduğu klasör yolunu bulmaya yarayan kod
>>> iris = pd.read_csv(pwd+"\iris.csv")
>>> iris
```

![vgy.me](https://i.vgy.me/NBQ164.png)

Dataframe'in hangi sütunlardan oluştuğunu görmek için __.columns__ özelliğini kullanabilirsiniz.

```python
>>> iris.columns

Index(['Sepal_Length', 'Sepal_Width', 'Pedal_Length', 'Pedal_Width',
       'Species'],
      dtype='object')
```

Aynı şekilde bir dataframedeki sütun isimlerini değiştirmek de mümkündür.

```python
>>> iris.columns = ["Taç Boy", "Taç En", "Çanak Boy", "Çanak En", "Tür"]
>>> iris
```
![vgy.me](https://i.vgy.me/fpixUa.png)

İris dataframenin genel yapısını incelemek için __.head()__ metodunu kullanabilirsiniz. Bu metod da argüman olarak görmek istediğiniz satır satıyını iletebilirsiniz.

```python
>>> iris.head(10)
```
![vgy.me](https://i.vgy.me/S0OlCq.png)

Benzer şekilde, dataframedeki son satırları görmek için de __.tail()__ metodu kullanılır. Bu metoda da aynı biçimde sondan kaç satırı görmek istediğinizi belirtebilirsiniz.

```python
>>> iris.tail(4)
```
![vgy.me](https://i.vgy.me/ZpFeo1.png)

Dataframe sütunları veri türüne baktığımızda Pandas içinde tanımlanmış olan Index veri türünde olduğunu görürüz. Bu tanımlama sayesinde Pandas dataframelerde arama, sıralama vb. işlemleri çok hızlı bir şekilde yapabilmektedir. Benzer şekilde satırlar da indeklenmektedir. Iris dataframe indeksine bakalım:
