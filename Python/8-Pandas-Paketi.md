<div style="text-align: justify">

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

## Data Framelerde Seçim Yapma

Bir data framedeki herhangi bir sütunu seçmek a da görnmek için __dataframe["sutun_adı"]__ formatı kullanılır. Önce dataframein ismi ve yanında köşeli parantez içinde, tırnak ya da kesme işareti içinde görülmek istenen sütun ismi yazılır. Yukarıdaki iris veri setinde __Pedal_Length__ sütununu görmmek için __iris["Pedal_Length"] yazılmalıdır.

```python
>>> iris["Pedal_Length"]

0      1.4
1      1.4
2      1.3
3      1.5
4      1.4
      ... 
145    5.2
146    5.0
147    5.2
148    5.4
149    5.1
Name: Pedal_Length, Length: 150, dtype: float64
```

Data framein yanında tek köşeli paranmtez kullanırsak sütundaki veriyi bir boyutlu olarak indirir.. Bunu bir lites olarak da düşünebilirsiniz. Nitekim, bu şekilde çetiğimiz veririnin üğtürünü incelemek istediğimizde bir boyutlu bir Series veri tipi olduğunu görürüz.


```python
>>> type(iris["Pedal_Length"])

pandas.core.series.Series
```

Yukarıda da görüldüğü gibi data frameden çektiğimiz sütunun türü Series yani bir boyutlu bir dizidir. Eğer istediğimiz sütunun da data frame gibi davranmasını istiyorsak sütun ismini iki köşeli parantez içinde yazarsak aşağıdaki şekilde bir pandas data frame'i ile karşılaşırız.

```python
>>> iris[["Pedal_Length"]]


   Pedal_Length
0	1.4
1	1.4
2	1.3
3	1.5
4	1.4
...	...
145	5.2
146	5.0
147	5.2
148	5.4
149	5.1,

150 rows × 1 columns

>>> type(iris[["Pedal_Length"]])
pandas.core.frame.DataFrame
```

__Görüldüğü gibi data framedeki bir sütunu bir adet köşeli parantezle çekince bir boyutlu seri, iki adet köşeli parantez ile çekince DataFrame veri yapısı ile karşılaşıyorsunuz.__

Peki birden fazla sütunu çekmek istersek ne yapmamız gerekiyor? Sorgulamayı, bir adet köşeli parantezle yaptığımızda bir boyutlu seri üretildiğini söyledik. Bu nedenloe örneğin __iris["Sepal_Length","Sepal_Width"]__ şeklinde yazarsak hata mesajı ile karşılaşırsınız. Bu nedenle birden fazla değişkeni seçmek için iki adet köşeli parantez kullanmanız gerekmektedir.

```python
>>> iris[["Sepal_Length", "Sepal_Width"]]

	Sepal_Length	Sepal_Width
0	    5.1           3.5
1	    4.9           3.0
2	    4.7           3.2
3	    4.6           3.1
4	    5.0           3.6
...	    ...           ...
145	    6.7           3.0
146	    6.3           2.5
147	    6.5           3.0
148	    6.2           3.4
149	    5.9           3.0
150 rows × 2 columns
```

Sütunları nasıl seçeceğimizi gördük. Şimdi de satırları nasıl seçeceğimizi görelim. Yine iris dataframe'i ile deval edelim. Bir dataframede belirli satırları seçmek için istediğimiz satır numaralarını arada iki nokta olacak şekilde yazıyoruz. Burada iki noktayı hatırlatmak da fayda var. Python'da indeks numaraları sıfırdan başlıyor ve indeks sondaki sayıyı kapsamıyor. Yani [2:5] indeks numaraları yazıldığında, 2 indeks numasarus ile başlayan ve 4 indeks numarası ile biten satırlar seçilecek, 5 indeks numarasına sahip satır seçilmeyecektir. İndeks numaralarının sıfırdan başladığını düşünürsek yaptığımız seçim 3. sıradaki satırla başlayıp 5. satırla sona erecektir. Sonuç olarak __iris[2:5]__ yazdğımızda aşağıdaki sonuçlar karşımıza çıkacaktır.


```python
>>> iris[2:5]

       Sepal_Length	Sepal_Width	Pedal_Length	Pedal_Width	Species
2	  4.7	           3.2	     1.3	    0.2	 setosa
3	  4.6	           3.1	     1.5	    0.2	 setosa
4	  5.0	           3.6	     1.4	    0.2	 setosa
```

NumPy dizilerinde hem satır hem de sütunlarda seçim yapmak mümkündü. Yani belirli sütunların belirli satırlarını seçebiliyorduk. Ancak, yukarıdaki gösterdiğimiz seçim yöntemi hem satır hem de sütunda seçim yapmaya izin vermemektedir. Pandas paketinde satır ve sütunlardan kolayca seçim yapmak için __loc__ ve __iloc__ fonksiyonları geliştirilmiştir. Bunlardan loc, location (konum); iloc ise integer location (sayısal konum) ifadelerini temsil etmektedir.

Örnek olarak aşağıdaki şekilde görülen hisselerinm bir günlük açılış, en düşük, en yüksek ve kapanış fiyatlarını gösteren dataframeini dikkate alalım. Aşağıdaki dataframede satırların numaralarla değil hisse isimleri ile belirtildiğini görüyorsunuz. Bir dataframede satırları bu şekilde isimlendirmek mümkündür. Satır isimlendirme için __.index()__ metodu kullanılır. Aşağıdaki dataframein isminin hisseler olduğunu varsayalım. Bu durumda, satırları isimlendirmek için __hisseler.index = ["ABC", "DEF", "KLM", "XYZ", "IJK", "VYZ", "ERN", "HEA"]__ yazmak yeterlidir. Dataframeini bir csv dosyasından okutuyorsak ve satır isimleri de ilk sütunda ise bu durumda __.read_csv()__ metodunda dosya yolu ve isminden sonra ikinci bir argüman olarak __index_col()__ yazmanız gerekmektedir.

```python
>>> hisseler = pd.read_csv(dosya_yolu+"\hisseler.csv", index_col=0)
>>> hisseler


       Acilis	   En_Dusuk	 En_Yuksek	Kapanis
ABC	 3.25	     3.15	   3.50	  3.15
DEF	 5.48	     5.00	   6.00	  6.00
KLM	 15.75	     15.25	   16.75	  16.50
XYZ	 80.20	     75.00	   85.25	  84.30
IJK	 17.50	     16.00	   19.00	  18.20
VYZ	 25.70	     24.10	   27.50	  26.80
ERN	 95.00	     90.20	   99.50	  97.50
HEA	 55.00	     53.00	   57.40	  59.30
```

Şimdi önce ERN hissesine ait bilgileri görmek isteyelim. Satır isimleri ile seçim yapmak için __.loc[]__ fonksiyonunu kullanmanız gerekmektedir.

```python
>>> hisseler.loc["ERN"]

Acilis       95.0
En_Dusuk     90.2
En_Yuksek    99.5
Kapanis      97.5
Name: ERN, dtype: float64
```

Seçimi bir adet köşeli parantez kullanarak yaptığımız için sonuç değişik bir formatta geldi. Yine dataframe formatında gelmesini sağlamak için iki adet köşeli parantez kullanılması gerekmektedir.

```python
>>> hisseler.loc[["ERN"]]


       Acilis	  En_Dusuk	En_Yuksek	Kapanis
ERN	 95.0	    90.2	   99.5      	 97.5
```

Bu şekilde birden fazla satır seçmek de mümkündür.

```python
>>> hisseler.loc[["ERN","HEA"]]

	Acilis	   En_Dusuk	En_Yuksek	Kapanis
ERN	 95.0	     90.2	   99.5	  97.5
HEA	 55.0	     53.0	   57.4	  59.3
```

Bir sütun ve satırdaki değeri almak için sütun ve satır isimlerini sırayla köşeli parantez içinde aşağıda görüldüğü gibi belirtmek mümkündür. Önce sütun daha sonra satır ismi belirttiğimize dikkat edin.

```python
>>> hisseler["Acilis"]["ERN"]

95.0
```

Aynı seçimi aşağıdaki şekilde de yapabilirsiniz. 

```python
>>> hisseler.Acilis["ERN"]

95.0
```

Şimdi de birden fazla satır ve sütun ismi kullanılarak seçim yapmayı görelim. Bu tür seçimlerde __.loc__ özelliğini kullanırsınız. Bunun için de istediğimiz satır ve sütunları virgülle ayrılmış iki ayrı liste olarak istemeniz gerekmektedir.

```python
>>> hisseler.loc[["ERN","HEA"], ["En_Dusuk", "En_Yuksek"]]

	En_Dusuk	En_Yuksek
ERN	  90.2	         99.5
HEA	  53.0	         57.4
```

Yukarıdaki seçimi bir adet satır ve sütun için de yapabileceğinizi unutmayın.

```python
>>> hisseler.loc[["ERN"],["Acilis"]]

       Acilis
ERN	95.0
```

Belirli değişkenlere ait tüm satırları seçtirmek için satır ismi yazmayıp bunun yerine : yazmanız yeterlidir.

```python
>>> hisseler.loc[:,["En_Dusuk", "En_Yuksek"]]

       En_Dusuk	En_Yuksek
ABC	  3.15	         3.50
DEF	  5.00	         6.00
KLM	  15.25	  16.75
XYZ	  75.00	  85.25
IJK	  16.00	  19.00
VYZ	  24.10	  27.50
ERN	  90.20	  99.50
HEA	  53.00	  57.40
```

__NOT:__ Yukarıda tüm satırlar için mutlaka : kullanmamız gerektiğine dikkat edin. Bunun yerine sadece __hisseler.loc[["En_Dusuk", "En_Yuksek"]]__ yazarsanız __*hata mesajı*__ ile karşılaşırsınız.

Satır ve sütun isimleri yerine indeks numaraları ile seçim yapmak için iloc fonksiyonu kullanılır. Bu kullanım şeklinde tek fark satır ve sütunların isimleri yerine indeks numaralarını kullanmanız gerekmektedir.

```python
>>> hisseler.iloc[1]

Acilis       5.48
En_Dusuk     5.00
En_Yuksek    6.00
Kapanis      6.00
Name: DEF, dtype: float64

>>> hisseler.iloc[[1]]


       Acilis   En_Dusuk	En_Yuksek	Kapanis
DEF	5.48	    5.0	   6.0          6.0


>>> hisseler.iloc[0:6]

      Acilis   En_Dusuk	En_Yuksek	Kapanis
ABC	3.25	   3.15	   3.50	 3.15
DEF	5.48	   5.00	   6.00	 6.00
KLM	15.75	   15.25	   16.75	 16.50
XYZ	80.20	   75.00	   85.25	 84.30
IJK	17.50	   16.00	   19.00	 18.20
VYZ	25.70	   24.10	   27.50	 26.80

>>> hisseler.iloc[[1,2,3]]


       Acilis	   En_Dusuk	En_Yuksek	Kapanis
DEF	5.48	     5.00	   6.00	  6.0
KLM	15.75	     15.25	   16.75	  16.5
XYZ	80.20	     75.00	   85.25	  84.3
```

Yine iki adet köşeli parantez kullandığımıza dikkat edin. Bir tane köşeli parantez kullanmamız halinde Dizi şeklinde sonuç alınmaktadır.

Birden fazla satır ve sütunda seçim yağmak için yine loc fonsiyonunda olduğu şekilde ama bu defa satır ve sütun indeks numaralarını belirterek yazılması gerekmektedir.

```python
>>> hisseler.iloc[[1,2,3],[2,3]]


       En_Yuksek	Kapanis
DEF	  6.00	         6.0
KLM	  16.75	  16.5
XYZ	  85.25	  84.3
```

Sütun ismi ve indek numaralarını bir arada kullanmak da mümkündür. Örneğin, ilk 4 sıradaki hissenin kapanış fiyatlarını görelim:

```python
>>> hisseler["Kapanis"][0:4]

ABC     3.15
DEF     6.00
KLM    16.50
XYZ    84.30
Name: Kapanis, dtype: float64
```

Satır seçimine 0:4 yazdığımızda 0,1,2 ve 3. sıradaki yani ilk dört sıradaki verileri çektiğimize dikkat edin. ":" işaretini satır veya sütun isimleriyle de kullanabilirsiniz.

```python
>>> hisseler.loc["ABC":"KLM","En_Dusuk":"Kapanis"]

	En_Dusuk	En_Yuksek	Kapanis
ABC	3.15	         3.50	         3.15
DEF	5.00	         6.00	         6.00
KLM	15.25	         16.75	  16.50
```

Satır ya da sütunları ters sırada yazdırmak da mümkündür. 

```python
>>> hisseler.loc["KLM":"ABC":-1]

	Acilis	   En_Dusuk	  En_Yuksek	Kapanis
KLM	 15.75	   15.25	  16.75	16.50
DEF	 5.48	   5.00	  6.00	        6.00
ABC	 3.25	   3.15	  3.50	        3.15
```

Yukarıda anlatılan satır ve sütun seçim yöntemleri aşağıdaki tabloda özetlenmiştir. 

| **Kullanım**                             	| **Sonuç**                                                                                             	|
|------------------------------------------	|-------------------------------------------------------------------------------------------------------	|
| hisseler["Kapanis"]                      	| Sütunu bir boyutlu veri dizisi olarak alır.                                                           	|
| hisseler[["Kapanis"]]                    	| Sütunu pandas dataframe'i olarak alır.                                                                	|
| hisseler[["En_Yuksek", "Kapanis"]]       	| Sütunları pandas dataframe'i olarak alır.                                                             	|
| hisseler[2:5]                            	| 3.satırdan (indeks no:2) başlayarak 5.satır<br><br>(indeks no:4) dahil olacak şekilde satırları alır. 	|
| hisseler.loc["ERN"]                      	| Satırı bir boyutlu veri dizisi olarak alır.                                                           	|
| hisseler.loc[["ERN"]]                    	| Satırı pandas dataframe'i olarak alır.                                                                	|
| hisseler.loc[["ERN","HEA"]]              	| Satırları pandas dataframe'i olarak alır.                                                             	|
| hissler.loc[["ERN","HEA"],["En_Yuksek"]] 	| Satır ve sütunları pandas dataframe'i olarak alır.                                                    	|
| hisseler.loc[:,["En_Dusuk,"En_Yuksek"]]  	| İstenen sütuınların tüm satırlarını alır.                                                             	|
| hisseler.iloc[[1]]                       	| İndeks numarası 1 olan (2.sıradaki] satırı alır.                                                      	|
| hisseler.iloc[[1,2,3],[2,3]              	| İndeks numarası 1,2 ve 3 olan satırları ve 2,3 olan<br>alır                                           	|                                   |


Bir dataframe'e for döngüsü uygulanırsa ne olur? Yukarıda kullanılan hisseler dataframe'e for döngüsü uygulayalım. 

```python
>>> for i in hisseler:
       print(i)


Acilis
En_Dusuk
En_Yuksek
Kapanis
```

Görüldüğü gibi sadece değişken isimleri yazdırılıyor. Bir dataframedeki bilgilere erişmek için pandas paketinde yer alan _.iterrows()__ metodu kullanılır. Şimdi bu metodu kullanarak bir for döngüsü yazalım.

```python
>>> for hisse, satir in hisseler.iterrows():
       print(hisse)
       print(satir)


ABC
Acilis       3.25
En_Dusuk     3.15
En_Yuksek    3.50
Kapanis      3.15
Name: ABC, dtype: float64
DEF
Acilis       5.48
En_Dusuk     5.00
En_Yuksek    6.00
Kapanis      6.00
Name: DEF, dtype: float64
KLM
Acilis       15.75
En_Dusuk     15.25
En_Yuksek    16.75
Kapanis      16.50
Name: KLM, dtype: float64
XYZ
Acilis       80.20
En_Dusuk     75.00
En_Yuksek    85.25
Kapanis      84.30
Name: XYZ, dtype: float64
IJK
...
En_Dusuk     53.0
En_Yuksek    57.4
Kapanis      59.3
Name: HEA, dtype: float64
```

Diyelim ki hewr defasında sadace belirli bir sütundaki verilere erişmek istiyoruz.

```python
>>> for hisse, satir in hisseler.iterrows():
        print(hisse + ":" + str(satir["Kapanis"]))

ABC:3.15
DEF:6.0
KLM:16.5
XYZ:84.3
IJK:18.2
VYZ:26.8
ERN:97.5
HEA:59.3
```

For döngüsü kullanarak dataframe'e yeni bir sütun da ekleyebiliriz. Şimdi her bir hissenin günlük açılış fiyatı ile kapanış fiyatı arasıondaki farkı alarak __günlük_fark__ isminde bir sütun oluşturmak istediğimizi düşünelim. Bunu aşağıdaki şekilde kolayca gerçekleştirebilirsiniz.

```python
>>> for hisse, satir in hisseler.iterrows():
       hisseler.loc[hisse, "gunluk_fark"] = satir["Kapanis"] - satir["Acilis"]
    print(hisseler)

     Acilis  En_Dusuk  En_Yuksek  Kapanis  gunluk_fark
ABC    3.25      3.15       3.50     3.15        -0.10
DEF    5.48      5.00       6.00     6.00         0.52
KLM   15.75     15.25      16.75    16.50         0.75
XYZ   80.20     75.00      85.25    84.30         4.10
IJK   17.50     16.00      19.00    18.20         0.70
VYZ   25.70     24.10      27.50    26.80         1.10
ERN   95.00     90.20      99.50    97.50         2.50
HEA   55.00     53.00      57.40    59.30         4.30
```

Aslında yukarıdaki for döngüsünü, dataframelerinde döngülerin nasıl çalıştığını görmek için yazdık. Ama yeni bir sütun eklemenin çok daha kolay ve hızlı bir yolu vardır. Aşağıdaki kod da yukarıdaki sonucun aynısını çok daha kısa bir sürede verecektir.

```python
>>> hisseler["Gunluk_Fark"] = hisseler["Kapanis"] - hisseler["Acilis"]
>>> hisseler

	Acilis	  En_Dusuk	En_Yuksek	Kapanis	gunluk_fark	Gunluk_Fark
ABC	3.25	    3.15	  3.50	        3.15	          -0.10	-0.10
DEF	5.48	    5.00	  6.00	        6.00	          0.52	0.52
KLM	15.75	    15.25	  16.75	 16.50	          0.75	0.75
XYZ	80.20	    75.00	  85.25	 84.30	          4.10	4.10
IJK	17.50	    16.00	  19.00	 18.20	          0.70	0.70
VYZ	25.70	    24.10	  27.50	 26.80	          1.10	1.10
ERN	95.00	    90.20	  99.50	 97.50	          2.50	2.50
HEA	55.00	    53.00	  57.40	 59.30	          4.30	4.30
```

## Pandas ile Veri Analizi

Bir veri kümesi ile çalışmaya başlamadan önce ilk olarak verilerin özelliklerine bakılır. Bu özellikler de genelde minimum, maksimum, ortalama, standart sapma, medyan, ve kartiller gibi değerlerdir. Pandas modülünde bu özelliklerin hepsini bir arada gösteren __.describe()__ metodu mevcuttur. Şimdi yine iris veri setinin bu metodunu kulllanarak inceleyelim.

```python
>>> import pandas as pd
>>> import os
>>> pwd = os.getcwd()
>>> iris = pd.read_csv(pwd+"\iris.csv")
>>> iris.describe()

	Sepal_Length	Sepal_Width	Pedal_Length	Pedal_Width
count	150.000000	150.000000	150.000000	150.000000
mean	5.843333	3.054000	3.758667	1.198667
std	0.828066	0.433594	1.764420	0.763161
min	4.300000	2.000000	1.000000	0.100000
25%	5.100000	2.800000	1.600000	0.300000
50%	5.800000	3.000000	4.350000	1.300000
75%	6.400000	3.300000	5.100000	1.800000
max	7.900000	4.400000	6.900000	2.500000
```

Her bir sütun için yukarıdan aşağıya sırayla count (veri sayısı), mean (ortalama), std (standart sapma), min (en düşük değer), %25 (1.kartil), %50 (medyan), %75 (3.kartil) ve max (en büyük değer) görülmektedir.

Yukarıdaki tabloda sadece sayısal verilere ilişkin özet bilgileri görüyoruz. Ancak iris veri setinde bir de Species yani tür bilgisini içeren bir sütun bulunmaktadır. Bu sütuna ait özellik bilgileri de __.describe()__ metodu ile görebilirsiniz. Aşağıda yer alan sonucu incelediğinizde bu sütunda 3 farklı değer olduğunu anlıyoruz. Bunlardan en sık görülenin versicolor türü olduğu belirtilmiştir.  Tablodaki top (mod), freq (moda ait frekans) bilgilsini belirtmektedir.

```python
>>> iris["Species"].describe()

count            150
unique             3
top       versicolor
freq              50
Name: Species, dtype: object
```

Bir sütunda hangi kategorik değişkenlerin yer aldığını görmek için __.unique()__ metodunu kullabilirsiniz. Bu metod, özellikle çok büyük veri setlerinde oldukça kullanışlı olabilir.

```python
>>> iris["Species"].unique()

array(['setosa', 'versicolor', 'virginica'], dtype=object)
```

Sayısal bilgilere ilişkin ortalama, standart sapma vb. özet değerleri ayrı ayrı hesaplamak için Pandas metodları bulunmaktadır.

```python
>>> iris.count()

Sepal_Length    150
Sepal_Width     150
Pedal_Length    150
Pedal_Width     150
Species         150
dtype: int64
```

Sadece istediğimiz sütunları seçerek bunlara ilişkin değerleri de görebilirsiz. Örneğin, __Pedal_Length__ ve __Pedal_Width__ sütunlarının veri sayısını görmek istiyorsak __iris[["Pedal_Length","Pedal_Width"]].count()__ yazmanız gerekmektedir. 

__NOT: Buradaki çift köşeli parantez yapısına dikkat edilmelidir. Çünkü istediğimiz sütunları liste olarak iletiyoruz.__

.count() gözlem sayısı için, .mean() ortalama için, .std() standart sapma için, .median() medyan için ve .quantile() yüzdelik dilim için kullanılabilir.

Gösterilen metodlar arasında __.quantile()__ metodunu açıklamak gerekmektedir. Bu metodu kullanırken, hangi yüzdelik dilimi istediğimizi, ondalık sayı şeklinde belirtmemiz gerekmektedir. Örneğin 1.kartili hesaplamak için __.quantile(0.25)__ yazmanız gerekmektedir.

Şimdiye kadar gördüğümüz metodları, sütunların yanı sıra satırlara da uygulayabiliriz. Yani satır bazıdna minimum, maksimum, ortalama vb. gibi değerleir hesaplatabiliriz. Bunun için uygulamız metod içinde __axis="columns"__ argümanını belirtmemiz gerekmektedir.

```python
>>> iris.mean(axis="columns")

0      2.550
1      2.375
2      2.350
3      2.350
4      2.550
       ...  
145    4.300
146    3.925
147    4.175
148    4.325
149    3.950
Length: 150, dtype: float64
```