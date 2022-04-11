<div style="text-align: justify">

# Pandas Paketi

NumPy paketi, veri saklama açısından oldukça hızlı ve etkin bir paket olmakla birlikte farklı türde verilerin bir arada kullanılması, verilerden seçim yapma gibi konularda yetersiz kalabilmektedir. _Pandas_ paketi hem yüksek performanslı hem de esnek veri analizi ihtiyacından doğmuş ve _Wes McKinney_ tarafından geliştirilmiştir. Pandas'ta esas olarak iki veri nesnesi bulunmaktadır: seriler ve veri çerçeveleri (data frameler).

## Pandas Serileri

Pandas serilerini endekslenmiş bir boyutlu diziler olarak düşünebilirsiniz. Pandas serisi aşağıdaki gibi tanımlanır. Nasıl ki **NumPy** paketini aktarırken geleneksel olarak **np** kısaltması kullanılıyorsa **Pandas** paketi için de genel olarak **pd** kısaltması kullanılmaktadır.

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

Tablo şeklindeki ya da iki boyutluı veri kümelerinde her satır bir gözlemi ya da bir ölçümü belirtmektedir. Her sütun ise bu gözlemlere ilişkin farklı özellikleri yani **değişkenleri** belirtmektedir.

Neyse ki Matlab, R gibi dillerin yanı sıra Python'da da iki (ve daha fazla) boyulu veri kümeleri için kullanılabilecek paketler mevcuttur. Bunlar arasında yer alan NumPy paketi görmüştük. Ancak NumPy paketinin bir eksikliği, NumPy dizilerinin sadece aynı türden verilerden oluşabilmesidir. Ancak gerçek hayatta kullandığımız bir çok veri kümesi farklı sütunlarda farklı veri türleri içerebilmektedir. Örneğin, yukarıdaki tabloda ilk dört sütundaki veriler sayısal, son sütundaki veri tipi ise metin türündedir.

Pandas paketinde yukarıdaki gibi iki boyutlu veri kümeleri **Data Frame** olarak isimlendirilir. Data Frameler, Pyhon'da veri analizini son derece kolaylaştıran çok kullanılşlı veri yapılarıdır. R programlama dilini bilenler için Pandas Data Frame'i R'daki Data Frame ile aynıdır. Data Frameler yukarıda anlatıldığı gibi iki boyutlu veri kümesi özelliklerini taşır. Her satırda bir gözlem, her sütunda da farklı bir değişken yer alır. Data Framelerini kullanarak betimsel ve çıkarımsal veri analizi yapmak, istatistiksel modeller kurmak, verileri görselleştirmek daha kolaydır. Bunlardan dolayı veri biliminde Python kullananlar için Pandas modülünden faydalanmak neredeyse standart hale gelmiştir.

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

Son olarak yukarıda tanımladığımız sözlüğü pandas DataFrame veri tipine dönüştürmek için **.DataFrame()** metodunu kullanıyoruz. Oluşturulan DataFrame satırları sıfırdan başlamak üzere numaralandırılır.

```python
>>> iris = pd.DataFrame(iris_dict)
>>> iris
```

![vgy.me](https://i.vgy.me/9IqVWB.png)

Yukarıdaki aktardığımız, sözlükten dataframe üretme yöntemi günlük hayatta kullanılabilecek bir yöntem değldir. Gerçekte çok büyükm verilerle çalıştığımızı düşünürsek tek tek bütün verilerin sözlük olarak girilmesi mümkün değildir.

Günlük hayatta kullandığımız veriler genelde excel, csv gibi formatlarda gelir. CSV formatında bir dosyadan pandas formatında veri okumak için pandas paketindeki **.read_csv()** metodu kullanılır. Yukarıdaki iris veri setinin **iris.csv** dosyasında kayıtlı olduğunu düşünelim. Dosyadan veri setini okumak için aşağıdaki kodu yazıyoruz. Metod içerisinde dosya adından önce klasör yolunu tam olarak yazmak gerekmektedir.

```python
>>> import os # Sistem ile ilgili işlemler için kullanılan paket
>>> pwd = os.getcwd() # ipynb dosyanızın olduğu klasör yolunu bulmaya yarayan kod
>>> iris = pd.read_csv(pwd+"\iris.csv")
>>> iris
```

![vgy.me](https://i.vgy.me/NBQ164.png)

Dataframe'in hangi sütunlardan oluştuğunu görmek için **.columns** özelliğini kullanabilirsiniz.

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

İris dataframenin genel yapısını incelemek için **.head()** metodunu kullanabilirsiniz. Bu metod da argüman olarak görmek istediğiniz satır satıyını iletebilirsiniz.

```python
>>> iris.head(10)
```

![vgy.me](https://i.vgy.me/S0OlCq.png)

Benzer şekilde, dataframedeki son satırları görmek için de **.tail()** metodu kullanılır. Bu metoda da aynı biçimde sondan kaç satırı görmek istediğinizi belirtebilirsiniz.

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

Dataframe'e ait bilgileri alabileceğimiz bir diğer metod **.info()** metodudur ancak bu metod istatistiksel özellikler yerine sütunların veri tipi, dataframedeki satır sayısını, her bir sütundaki veri sayısı gibi değerleri vermektedir.

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

Bir dataframe'i olduğu gibi başka bir veri çerçevesine aktarmak için **copy()** metodu kullanılmaktadır.

```python
>>> iris_yeni = iris.copy()
```

Pandas paketinin, NumPy paketi üzerinde geliştirildiğini daha önce belirtmiştik. İstenirse bir pandas dataframe'ine **.values** özelliğini kullanarak NumPy dizisine çevirebilirsiniz.

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

NumPy için geçerli olan metodları pandas dataframe'ine de uygulayabilirsiniz. Örneğin sayısal değerlerden oluşan bir dataframe'deki değerlerin doğal logaritmasını bulmak için NumPy paketindeki **.log()** metodunu uygulayabilirsiniz.

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

Yukarıdaki hisseler verisi bir boyutlu pandas verisi ancak ilk iki sütunda belirtilen iki indeksle gösteriliyor. Bu seriyi pandas modülündeki **.unstack()** metodunu kullanarak dataframe'e çevirebilirsiniz.

```python
>>> hisseler.unstack()
Yıl	     2016	2017
Hisse
ABC	     32.5	12.3
DEF	     24.7	18.6
KLM	     51.9	56.2
XYZ   	 20.3	7.2
```

Bir dataframe'i de **.stack()** metodu ile eski haline çevirebilirsiniz. MultiIndex ile çoklu indeks oluşturmanın üç farklı yöntemi vardır.

Nasıl ki satırlar için çoklu indeks oluşturabiliyorsakj sütunlar için de aynı şekilde çoklu indeks oluşturabiliriz. Çoklu indeks kullanımı özellikle panel verilerle yapılan çalışmalarda faydalıdır. Şimdi yukarıdaki hisse senedi tablosuna sütunlarına her çeyrek için kapanış fiyatı ve hacim bilgisini ekleyeblim.

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

Bir data framedeki herhangi bir sütunu seçmek a da görnmek için **dataframe["sutun_adı"]** formatı kullanılır. Önce dataframein ismi ve yanında köşeli parantez içinde, tırnak ya da kesme işareti içinde görülmek istenen sütun ismi yazılır. Yukarıdaki iris veri setinde **Pedal_Length** sütununu görmmek için **iris["Pedal_Length"]** yazılmalıdır.

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

**Görüldüğü gibi data framedeki bir sütunu bir adet köşeli parantezle çekince bir boyutlu seri, iki adet köşeli parantez ile çekince DataFrame veri yapısı ile karşılaşıyorsunuz.**

Peki birden fazla sütunu çekmek istersek ne yapmamız gerekiyor? Sorgulamayı, bir adet köşeli parantezle yaptığımızda bir boyutlu seri üretildiğini söyledik. Bu nedenloe örneğin **iris["Sepal_Length","Sepal_Width"]** şeklinde yazarsak hata mesajı ile karşılaşırsınız. Bu nedenle birden fazla değişkeni seçmek için iki adet köşeli parantez kullanmanız gerekmektedir.

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

Sütunları nasıl seçeceğimizi gördük. Şimdi de satırları nasıl seçeceğimizi görelim. Yine iris dataframe'i ile deval edelim. Bir dataframede belirli satırları seçmek için istediğimiz satır numaralarını arada iki nokta olacak şekilde yazıyoruz. Burada iki noktayı hatırlatmak da fayda var. Python'da indeks numaraları sıfırdan başlıyor ve indeks sondaki sayıyı kapsamıyor. Yani [2:5] indeks numaraları yazıldığında, 2 indeks numasarus ile başlayan ve 4 indeks numarası ile biten satırlar seçilecek, 5 indeks numarasına sahip satır seçilmeyecektir. İndeks numaralarının sıfırdan başladığını düşünürsek yaptığımız seçim 3. sıradaki satırla başlayıp 5. satırla sona erecektir. Sonuç olarak **iris[2:5]** yazdğımızda aşağıdaki sonuçlar karşımıza çıkacaktır.

```python
>>> iris[2:5]

       Sepal_Length	Sepal_Width	Pedal_Length	Pedal_Width	Species
2	  4.7	           3.2	     1.3	    0.2	 setosa
3	  4.6	           3.1	     1.5	    0.2	 setosa
4	  5.0	           3.6	     1.4	    0.2	 setosa
```

NumPy dizilerinde hem satır hem de sütunlarda seçim yapmak mümkündü. Yani belirli sütunların belirli satırlarını seçebiliyorduk. Ancak, yukarıdaki gösterdiğimiz seçim yöntemi hem satır hem de sütunda seçim yapmaya izin vermemektedir. Pandas paketinde satır ve sütunlardan kolayca seçim yapmak için **loc** ve **iloc** fonksiyonları geliştirilmiştir. Bunlardan loc, location (konum); iloc ise integer location (sayısal konum) ifadelerini temsil etmektedir.

Örnek olarak aşağıdaki şekilde görülen hisselerinm bir günlük açılış, en düşük, en yüksek ve kapanış fiyatlarını gösteren dataframeini dikkate alalım. Aşağıdaki dataframede satırların numaralarla değil hisse isimleri ile belirtildiğini görüyorsunuz. Bir dataframede satırları bu şekilde isimlendirmek mümkündür. Satır isimlendirme için **.index()** metodu kullanılır. Aşağıdaki dataframein isminin hisseler olduğunu varsayalım. Bu durumda, satırları isimlendirmek için **hisseler.index = ["ABC", "DEF", "KLM", "XYZ", "IJK", "VYZ", "ERN", "HEA"]** yazmak yeterlidir. Dataframeini bir csv dosyasından okutuyorsak ve satır isimleri de ilk sütunda ise bu durumda **.read_csv()** metodunda dosya yolu ve isminden sonra ikinci bir argüman olarak **index_col()** yazmanız gerekmektedir.

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

Şimdi önce ERN hissesine ait bilgileri görmek isteyelim. Satır isimleri ile seçim yapmak için **.loc[]** fonksiyonunu kullanmanız gerekmektedir.

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

Bir sütun ve satırdaki değeri almak için sütun ve satır isimlerini sırayla köşeli parantez içinde aşağıda görüldüğü gibi belirtmek mümkündür. Önce **sütun** daha sonra **satır** ismi belirttiğimize dikkat edin.

```python
>>> hisseler["Acilis"]["ERN"]

95.0
```

Aynı seçimi aşağıdaki şekilde de yapabilirsiniz.

```python
>>> hisseler.Acilis["ERN"]

95.0
```

Şimdi de birden fazla satır ve sütun ismi kullanılarak seçim yapmayı görelim. Bu tür seçimlerde **.loc** özelliğini kullanırsınız. Bunun için de istediğimiz **satır** ve **sütunları** **virgülle ayrılmış iki ayrı liste** olarak istemeniz gerekmektedir.

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

**NOT:** Yukarıda tüm satırlar için mutlaka : kullanmamız gerektiğine dikkat edin. Bunun yerine sadece **hisseler.loc[["En_Dusuk", "En_Yuksek"]]** yazarsanız **_hata mesajı_** ile karşılaşırsınız.

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

| **Kullanım**                             | **Sonuç**                                                                                             |
| ---------------------------------------- | ----------------------------------------------------------------------------------------------------- | --- |
| hisseler["Kapanis"]                      | Sütunu bir boyutlu veri dizisi olarak alır.                                                           |
| hisseler[["Kapanis"]]                    | Sütunu pandas dataframe'i olarak alır.                                                                |
| hisseler[["En_Yuksek", "Kapanis"]]       | Sütunları pandas dataframe'i olarak alır.                                                             |
| hisseler[2:5]                            | 3.satırdan (indeks no:2) başlayarak 5.satır<br><br>(indeks no:4) dahil olacak şekilde satırları alır. |
| hisseler.loc["ERN"]                      | Satırı bir boyutlu veri dizisi olarak alır.                                                           |
| hisseler.loc[["ERN"]]                    | Satırı pandas dataframe'i olarak alır.                                                                |
| hisseler.loc[["ERN","HEA"]]              | Satırları pandas dataframe'i olarak alır.                                                             |
| hissler.loc[["ERN","HEA"],["En_Yuksek"]] | Satır ve sütunları pandas dataframe'i olarak alır.                                                    |
| hisseler.loc[:,["En_Dusuk,"En_Yuksek"]]  | İstenen sütuınların tüm satırlarını alır.                                                             |
| hisseler.iloc[[1]]                       | İndeks numarası 1 olan (2.sıradaki] satırı alır.                                                      |
| hisseler.iloc[[1,2,3],[2,3]              | İndeks numarası 1,2 ve 3 olan satırları ve 2,3 olan<br>alır                                           |     |

Bir dataframe'e for döngüsü uygulanırsa ne olur? Yukarıda kullanılan hisseler dataframe'e for döngüsü uygulayalım.

```python
>>> for i in hisseler:
       print(i)


Acilis
En_Dusuk
En_Yuksek
Kapanis
```

Görüldüğü gibi sadece değişken isimleri yazdırılıyor. Bir dataframedeki bilgilere erişmek için pandas paketinde yer alan \_.iterrows()\_\_ metodu kullanılır. Şimdi bu metodu kullanarak bir for döngüsü yazalım.

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

For döngüsü kullanarak dataframe'e yeni bir sütun da ekleyebiliriz. Şimdi her bir hissenin günlük açılış fiyatı ile kapanış fiyatı arasıondaki farkı alarak **günlük_fark** isminde bir sütun oluşturmak istediğimizi düşünelim. Bunu aşağıdaki şekilde kolayca gerçekleştirebilirsiniz.

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

Bir veri kümesi ile çalışmaya başlamadan önce ilk olarak verilerin özelliklerine bakılır. Bu özellikler de genelde minimum, maksimum, ortalama, standart sapma, medyan, ve kartiller gibi değerlerdir. Pandas modülünde bu özelliklerin hepsini bir arada gösteren **.describe()** metodu mevcuttur. Şimdi yine iris veri setinin bu metodunu kulllanarak inceleyelim.

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

Yukarıdaki tabloda sadece sayısal verilere ilişkin özet bilgileri görüyoruz. Ancak iris veri setinde bir de Species yani tür bilgisini içeren bir sütun bulunmaktadır. Bu sütuna ait özellik bilgileri de **.describe()** metodu ile görebilirsiniz. Aşağıda yer alan sonucu incelediğinizde bu sütunda 3 farklı değer olduğunu anlıyoruz. Bunlardan en sık görülenin versicolor türü olduğu belirtilmiştir. Tablodaki top (mod), freq (moda ait frekans) bilgilsini belirtmektedir.

```python
>>> iris["Species"].describe()

count            150
unique             3
top       versicolor
freq              50
Name: Species, dtype: object
```

Bir sütunda hangi kategorik değişkenlerin yer aldığını görmek için **.unique()** metodunu kullabilirsiniz. Bu metod, özellikle çok büyük veri setlerinde oldukça kullanışlı olabilir.

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

Sadece istediğimiz sütunları seçerek bunlara ilişkin değerleri de görebilirsiz. Örneğin, **Pedal_Length** ve **Pedal_Width** sütunlarının veri sayısını görmek istiyorsak **iris[["Pedal_Length","Pedal_Width"]].count()** yazmanız gerekmektedir.

**NOT: Buradaki çift köşeli parantez yapısına dikkat edilmelidir. Çünkü istediğimiz sütunları liste olarak iletiyoruz.**

.count() gözlem sayısı için, .mean() ortalama için, .std() standart sapma için, .median() medyan için ve .quantile() yüzdelik dilim için kullanılabilir.

Gösterilen metodlar arasında **.quantile()** metodunu açıklamak gerekmektedir. Bu metodu kullanırken, hangi yüzdelik dilimi istediğimizi, ondalık sayı şeklinde belirtmemiz gerekmektedir. Örneğin 1.kartili hesaplamak için **.quantile(0.25)** yazmanız gerekmektedir.

Şimdiye kadar gördüğümüz metodları, sütunların yanı sıra satırlara da uygulayabiliriz. Yani satır bazında minimum, maksimum, ortalama vb. gibi değerleir hesaplatabiliriz. Bunun için uygulamız metod içinde **axis="columns"** argümanını belirtmemiz gerekmektedir.

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

Iris veri setinin üç farklı türe ait gözlemlerden meydana geldiğini daha önce belirtmiştik. Şimdiye kadar verdiğimiz örneklerde her üç türe ait gözlemleri bir arada değerlendirdik ve tür farklılıklarını dikkate almadık. Peki ya her bir türe ait istatistiksel değerleri ayrı ayrı hesaplamak istersek ne yapacağız. Bunu için mantıksal seçim kurallarını uygulayabiliriz. Varsayalım ki versicolor türüne ait özet bilgileri görmek istiyoruz. Öncelikle versicolor türüne ait gözlemleri seçip sonra da yaptığımız seçime istediğimiz metod uygulanabilir.

```python
>>> kosul = iris["species"] == "versicolor"
>>> type(kosul)

pandas.core.series.Series

>>> kosul

0      False
1      False
2      False
3      False
4      False
5      False
```

Şimdi, bu koşul değerini kullanarak iris veri çerşevesinde sadece versicolor türlerinin olduğu satırları seçtirebiliriz.

```python
>>> versicolor = iris.loc[kosul, :]

sepal_length	sepal_width	pedal_length	pedal_width	species
50	          7.0	            3.2	    4.7	  1.4	versicolor
51	          6.4	            3.2	    4.5	  1.5	versicolor
52	          6.9	            3.1	    4.9	  1.5	versicolor
53	          5.5	            2.3	    4.0	  1.3	versicolor
54	          6.5	            2.8	    4.6	  1.5	versicolor

>>> versicolor.describe()

	sepal_length	sepal_width	pedal_length	pedal_width
count	50.000000	50.000000	50.000000	50.000000
mean	5.936000	2.770000	4.260000	1.326000
std	0.516171	0.313798	0.469911	0.197753
min	4.900000	2.000000	3.000000	1.000000
25%	5.600000	2.525000	4.000000	1.200000
50%	5.900000	2.800000	4.350000	1.300000
75%	6.300000	3.000000	4.600000	1.500000
max	7.000000	3.400000	5.100000	1.800000
```

Yukarıdaki işlemin anlaşılması kolay olması için iki ayrı satıra ayırdır ancak bu işlem tek bir satırda da gerçekleştirilebilir.

```python
>>> iris[iris["species"]=="virginica"].describe()

	sepal_length	sepal_width	pedal_length	pedal_width
count	50.00000	50.000000	50.000000	50.00000
mean	6.58800	2.974000	5.552000	2.02600
std	0.63588	0.322497	0.551895	0.27465
min	4.90000	2.200000	4.500000	1.40000
25%	6.22500	2.800000	5.100000	1.80000
50%	6.50000	3.000000	5.550000	2.00000
75%	6.90000	3.175000	5.875000	2.30000
max	7.90000	3.800000	6.900000	2.50000
```

Burada iris veri seti içinde (iris[]) species sütununun değeri "virginica" olanları (iris["species"] == "virginica") seçiyoruz.

Metin tipi sütunlarda koşullu seçim yapmanın bir diğer yolu da **.str** metodunu uygulamaktadır.

```python
>>> kosul = iris["species"].str.contains("setosa")
>>> setosa = iris[kosul]
>>> setosa.head()


       sepal_length	sepal_width	pedal_length	pedal_width	species
0	    5.1	      3.5	    1.4	    0.2	setosa
1	    4.9	      3.0	    1.4	    0.2	setosa
2	    4.7	      3.2	    1.3	    0.2	setosa
3	    4.6	      3.1	    1.5	    0.2	setosa
4	    5.0	      3.6	    1.4	    0.2	setosa
```

Yukarıdaki kodda üçüncü satırda yer alan **.str.contains()** yapısına dikkat ediniz. Burada önce **.str** metodunu ardından da **.contains()** (yani içerir) metodunu kullanıyoruzz.

Şimdi farklı bir örnek görelim: \_\_Sepal_Length değeri 7,5'ten büyük olan kayıtları seçelim.

```python
>>> iris[iris.sepal_length > 7.5]

       sepal_length	sepal_width	pedal_length	pedal_width	species
105	     7.6	    3.0	    6.6	     2.1	virginica
117	     7.7	    3.8	    6.7	     2.2	virginica
118	     7.7	    2.6	    6.9	     2.3	virginica
122	     7.7	    2.8	    6.7	     2.0	virginica
131	     7.9	    3.8	    6.4	     2.0	virginica
135	     7.7	    3.0	    6.1	     2.3	virginica
```

Birden fazla şartı bir arada kullanarak çoklu seçimler de yaptırabiliriz. Örneğin, Sepal_Length değeri 6,5'ten fazla, Pedal_Length değeri 4,5'ten az olan satırları seçelim. Aşağıdaki ifadede koşulları parantez içinde belirtmezseniz hata mesajı alırsınız.

```python
>>> iris[(iris.sepal_length > 6.5) & (iris.pedal_length < 4.5)]

       sepal_length	sepal_width	pedal_length	pedal_width	species
65	     6.7	     3.1	    4.4	    1.4	versicolor
75	     6.6	     3.0	    4.4	    1.4	versicolor
```

Bir sütun verilerine koşul uygulayarak bir başka sütundan veri çekmek de mümkündür. Örneğin, sepal_length değeri 7,5'tan büyük olan satırların pedal_length değerlerini görelim.

```python
>>> iris.pedal_length[iris.sepal_length > 7.5]

105    6.6
117    6.7
118    6.9
122    6.7
131    6.4
135    6.1
Name: pedal_length, dtype: float64
```

Buraya kadar anlattıklarımız dışında Pandas modülünde kullanılan farklı metodlar da vardır. Örneğin bir veri çerçevesinde hiç sıfır içermeyen sütunları görmek için **.all()**, sıfırlardan farklı değerler içeren sütunları görmek için **.any()**, NaN değeri içeren sütunları görmek için **isnull()**, içermeyenleri görmek için **.notnull()** metodları mevcuttur.

Son olarak Pandas veri çerçevelerinde gerçekleştirilebilecek yeniden şekillendirme ve manipülasyon işlemlerine göz atalım. Örneklerimiz kullanmak üzere aşağıdaki df veri çerçevesini oluşturalım.

```python
>>> import pandas as pd
>>> import numpy as np

>>> degisken = np.repeat(["A", "B", "C", "D"], [3,3,3,3], axis = 0)
>>> deger = np.random.random(12)
>>> df_dict = {"degisken": degisken, "deger":deger}
>>> df = pd.DataFrame(df_dict)
>>> df = df[["degisken","deger"]]
>>> df

	degisken	deger
0	A	0.878331
1	A	0.821828
2	A	0.476435
3	B	0.462610
4	B	0.812102
5	B	0.806930
6	C	0.954010
7	C	0.728809
8	C	0.228238
9	D	0.185912
10	D	0.981141
11	D	0.523202
```

Şimdi bu veri çerçevesini öyle bir değiştirelim ki A B C ve D değeri bir sütun haline gelsin. Bunun için kullanabileceğimiz Pandas metodlarından birisi **.pivot()** metodudur.

```python
>>> df2 = df.pivot(columns="degisken", values="deger")
>>> df2

degisken	A	       B	       C	       D
0	     0.878331	       NaN	       NaN	       NaN
1	     0.821828	       NaN	       NaN	       NaN
2	     0.476435	       NaN	       NaN	       NaN
3	     NaN	       0.462610	NaN	       NaN
4	     NaN	       0.812102	NaN	       NaN
5	     NaN	       0.806930	NaN	       NaN
6	     NaN	       NaN	       0.954010	NaN
7	     NaN	       NaN	       0.728809	NaN
8	     NaN	       NaN	       0.228238	NaN
9	     NaN	       NaN	       NaN	       0.185912
10	     NaN	       NaN	       NaN	       0.981141
11	     NaN	       NaN	       NaN	       0.523202
```

sütunları tekrar satır şeklinde yazmak için **.melt()** metodunu kullanabilirsiniz.

```python
>>> merge1_dict = {"Isimler" : ["Ali", "Baran", "Mehmet"],
                "Matematik" : [97, 85, 76 ]}
>>> merge1 = pd.DataFrame(merge1_dict)
>>> merge1

	Isimler	Matematik
0	Ali	           97
1	Baran	           85
2	Mehmet	           76

>>> merge2_dict = {"Isimler" : ["Ali", "Baran", "Umut"],
                "Türkçe" : [75, 94, 96 ]}
>>> merge2 = pd.DataFrame(merge2_dict)
>>> merge2

I      simler	       Türkçe
0	Ali	       75
1	Baran	       94
2	Umut	       96
```

Veri çerçevelerinin isimleri sırasıyla merge1 ve merge2 olsun. İki veri çerçevesini birleştirirken kullanabileceğimiz yöntemler "left", "right", "inner", "outer" yöntemleridir. Aşağıdaki örneklerde bu yöntemleri kullanırken önce merge1 ve sonra merge2 yazdığımıza dikkat edin. Bu özellikle "left" ve "right" yöntemleri için önemlidir.

İlk yani "left" yönteminde, önce yazılan çerçevesi esas alınır. Argüman olarak birleştirilecek iki ver çerçevesinin isimleri, birleştirmek yöntemi (how) ve veri çerçeveleri birleştirirken hangi sütunun dikkate alınacağı (on) belirtilir.

```python
>>> df1 = pd.merge(merge1, merge2, how="left", on="Isimler")
>>> df1


       Isimler	Matematik	Türkçe
0	Ali	              97	75.0
1	Baran	              85	94.0
2	Mehmet	              76	NaN

>>> df2 = pd.merge(merge1, merge2, how="right", on="Isimler")
>>> df2

       Isimler	Matematik	Türkçe
0	Ali	              97.0	75
1	Baran	              85.0	94
2	Umut	              NaN	96
```

Left ve right yöntemlerinin çalışma mantığı benzerdir. Diğer yandan, how="inner" seçildiğinde birleştirilecek sütunun sadece her iki veri çerçeesinde de yer alan satırları yani kesişimleri dikkate alınır.

```python
>>> df3 = pd.merge(merge1, merge2, how="inner", on="Isimler")
>>> df3


       Isimler	Matematik	Türkçe
0	Ali	              97	75.0
1	Baran	              85	94.0


>>> df4 = pd.merge(merge1, merge2, how="outer", on="Isimler")
>>> df4

       Isimler	Matematik	Türkçe
0	Ali	              97.0	75
1	Baran	              85.0	94
2	Mehmet	              76	NaN
3	Umut	              NaN	96
```
