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

```python
>>> iris.index
RangeIndex(start=0, stop=150, step=1)

# Veri çerçevesinin boyutlarına yani kaç satır ve kaç sütundan oluştuğu aşağıdaki gibi incelenir.
>>> iris.shape
(150, 5)
```

Dataframe'e ait bilgileri alabileceğimiz bir diğer metod __.info()__ metodudur ancak bu metod istatistiksel özellikler yerine sütunların veri tipi, dataframedeki satır sayısını, her bir sütundaki veri sayısı gibi değerleri vermektedir.

```python
>>> iris.info()

<class 'pandas.core.frame.DataFrame'>
RangeIndex: 150 entries, 0 to 149
Data columns (total 5 columns):
 #   Column        Non-Null Count  Dtype
---  ------        --------------  -----
 0   Sepal_Length  150 non-null    float64
 1   Sepal_Width   150 non-null    float64
 2   Pedal_Length  150 non-null    float64
 3   Pedal_Width   150 non-null    float64
 4   Species       150 non-null    object
dtypes: float64(4), object(1)
memory usage: 6.0+ KB
```

Bir dataframe'i olduğu gibi başka bir veri çerçevesine aktarmak için __copy()__ metodu kullanılmaktadır.

```python
>>> iris_yeni = iris.copy()
```

Pandas paketinin, NumPy paketi üzerinde geliştirildiğini daha önce belirtmiştik. İstenirse bir pandas dataframe'ine __.values__ özelliğini kullanarak NumPy dizisine çevirebilirsiniz.

```python
>>> np_iris = iris.values
>>> np_iris

array([[5.1, 3.5, 1.4, 0.2, 'setosa'],
       [4.9, 3.0, 1.4, 0.2, 'setosa'],
       [4.7, 3.2, 1.3, 0.2, 'setosa'],
       [4.6, 3.1, 1.5, 0.2, 'setosa'],
       [5.0, 3.6, 1.4, 0.2, 'setosa'],
       ...
```
NumPy için geçerli olan metodları pandas dataframe'ine de uygulayabilirsiniz. Örneğin sayısal değerlerden oluşan bir dataframe'deki değerlerin doğal logaritmasını bulmak için NumPy paketindeki __.log()__ metodunu uygulayabilirsiniz.

```python
>>> import numpy as np

# Önce iris dataframe'inin sayısal sütunlarını seçelim.
>>> dizi = iris.iloc[:,[0,1,2,3]]
>>> dizi_log = np.log(dizi)
>>> dizi_log.head()

  Sepal_Length	Sepal_Width	Pedal_Length	Pedal_Width
0	  1.629241	    1.252763	   0.336472	   -1.609438
1	  1.589235	    1.098612	   0.336472	   -1.609438
2	  1.547563	    1.163151	   0.262364	   -1.609438
3	  1.526056	    1.131402	   0.405465	   -1.609438
4	  1.609438	    1.280934	   0.336472	   -1.609438
```

Şimdiye kadar gördüğümüz pandas serileri ve veri çerçeveleri esasen bir veya iki boyutlu veri yapılarıdır. Ancak, pandas üç ve daha fazla boyutlu veri yapılarına da izin vermektedir. Bunu pandas verilerinde çoklu indeks olarak ekleyerek yapabilirsiniz. Önce bir pandas serine çoklu indeks eklemeyi görelim. Aşağıdaki örnekte farklı hisse senetlerinin 2016 ve 2017 yılı kapanış fiyatlarını görüyorsunuz.

```python
>>> indeks = [("ABC", 2016),("ABC", 2017),
              ("DEF", 2016),("DEF", 2017),
              ("XYZ", 2016),("XYZ", 2017),
              ("KLM", 2016),("KLM", 2017)]

>>> fiyatlar = [32.5, 12.3, 24.7, 18.6, 20.3, 7.2, 51.9, 56.2]
>>> hisseler = pd.Series(fiyatlar, index = indeks)
>>> hisseler

(ABC, 2016)    32.5
(ABC, 2017)    12.3
(DEF, 2016)    24.7
(DEF, 2017)    18.6
(XYZ, 2016)    20.3
(XYZ, 2017)     7.2
(KLM, 2016)    51.9
(KLM, 2017)    56.2
dtype: float64
```

Verileri bu şekilde indeksleyerek seride seçim de yapabilirsiniz.

```python
>>> hisseler[("XYZ",2016):("KLM",2017)]

(XYZ, 2016)    20.3
(XYZ, 2017)     7.2
(KLM, 2016)    51.9
(KLM, 2017)    56.2
dtype: float64
```

Yukarıdaki gibi çoklu indeks kullanmanın daha etkin bir yöntemi ise pandas MultiIndex kullanmaktır.
```python
>>> indeks  = pd.MultiIndex.from_tuples(indeks)
>>> indeks

MultiIndex([('ABC', 2016),
            ('ABC', 2017),
            ('DEF', 2016),
            ('DEF', 2017),
            ('XYZ', 2016),
            ('XYZ', 2017),
            ('KLM', 2016),
            ('KLM', 2017)],
           )

>>> hisseler = pd.Series(fiyatlar, index=indeks)
>>> hisseler

ABC  2016    32.5
     2017    12.3
DEF  2016    24.7
     2017    18.6
XYZ  2016    20.3
     2017     7.2
KLM  2016    51.9
     2017    56.2
dtype: float64

# Hisseleri isimlendirmek de mümkündür.
>>> hisseler.index.names = ["Hisse", "Yıl"]
>>> hisseler

Hisse  Yıl
ABC    2016    32.5
       2017    12.3
DEF    2016    24.7
       2017    18.6
XYZ    2016    20.3
       2017     7.2
KLM    2016    51.9
       2017    56.2
dtype: float64
```

Yukarıdaki hisseler verisi bir boyutlu pandas verisi ancak ilk iki sütunda belirtilen iki indeksle gösteriliyor. Bu seriyi pandas modülündeki __.unstack()__  metodunu kullanarak dataframe'e çevirebilirsiniz.

```python
>>> hisseler.unstack()
Yıl	     2016	2017
Hisse
ABC	     32.5	12.3
DEF	     24.7	18.6
KLM	     51.9	56.2
XYZ   	 20.3	7.2
```

Bir dataframe'i de __.stack()__ metodu ile eski haline çevirebilirsiniz. MultiIndex ile çoklu indeks oluşturmanın üç farklı yöntemi vardır.

Nasıl ki satırlar için  çoklu indeks oluşturabiliyorsakj sütunlar için de aynı şekilde çoklu indeks oluşturabiliriz. Çoklu indeks kullanımı özellikle panel verilerle yapılan çalışmalarda faydalıdır. Şimdi yukarıdaki hisse senedi tablosuna sütunlarına her çeyrek için kapanış fiyatı ve hacim bilgisini ekleyeblim.

```python
>>> indeks = pd.MultiIndex.from_product([["ABC","DEF","KLM"], [2016, 2017]])
>>> sutunlar = pd.MultiIndex.from_product([["Q1", "Q2", "Q3", "Q4"],["Hacim","Kapanis"]])

>>> veri = np.array([10762, 32.5, 12638, 33.5, 13689, 35.2, 18414, 37.4,
                     10688, 12.3, 14348, 13.2, 15924, 15.3, 15243, 17.9,
                     14841, 24.7, 14966, 22.1, 13098, 19.3, 17439, 15.4,
                     15607, 18.6, 16166, 13.4, 10627, 15.1, 13396, 15.3,
                     12565, 20.3, 17469, 21.4, 18964, 22.5, 15187, 23.6,
                     13203, 7.2, 10629, 7.2, 15239, 8.2, 18307, 9])

>>> veri = np.reshape(veri, (6,8))
>>> hisseler = pd.DataFrame(veri, index = indeks, columns=sutunlar)
>>> hisseler
```
![vgy.me](https://i.vgy.me/VkDOLO.png)
