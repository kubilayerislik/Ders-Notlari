# NumPy Paketi,

Liste veri yapısı Python'a özel ve son derece kullanışlı bir veri türüdür. Listeleri kullanarak verileri bir arada saklayabilir ve bunlar üzerinde değişiklikler yapabilir, yeni veriler ekleyebilir ya da mevcut verileri çıkarabilirsiniz. Liste veri yapısında, veriler üzerinde analizler yapmak, matematiksel ya da istatistiksel işlemler uygulamak mümkün olmamaktadır. Halbuki R ya da Matlab gibi diğer dillerde bu tip işlemler kolaylıkla yapılabilmektedir.

NumPy paketi listelerde matematiksel işlem yapabilmek için geliştirilmiştir. Paket ismi Numeric Python (Sayısal Python) kelimelerinin kısaltılmasından oluşmaktadır. NumPy paketinin temel veri yapısı listeler yerine NumPy dizileridir (NumPy Array). NumPy dizilerinin normal listelerden farkı, listeler farklı türdeki veriler içerebiliyorken, NumPy dizilerinin sadece tek türde veriler içerebilmesidir. Bir NumPy dizisine farklı veri türleri tanımlarsanız, bunların hepsi aynı veri tipine çevrilir. Örneğin, diziye sayısal veriler ve metinm verileri tanımlanırsa, metinler sayısal verilere çevrilemeyeceği için tüm sayılar metin veri tipine çevrilir.

```python
>>> import numpy as np

>>> numpy_dizi = np.array(["Adana", 1, "Adıyaman", 2, "Afyon", 3])
>>> print(numpy_dizi)

['Adana' '1' 'Adıyaman' '2' 'Afyon' '3']
```

Herhangi bir Python listesi __.array()__ metodu kullanılarak NumPy dizisine dönüştürülebilir.
```python
>>> olcum =  [23, 34, 54, 42, 34, 22, 10, 18, 22]
>>> olcum_np = np.array(olcum)
>>> olcum_np

array([23, 34, 54, 42, 34, 22, 10, 18, 22])
```

NumPy dizileri ile kolay bir şekilde işlem yapılabilir. Örneğin 2 sınava ait notlar iki farklı istede tutulsun ve bu listelerin ortalaması alınmak istendiğinde bu işlem NumPy dizileri ile kolayca gerçekleştirilebilir.
```python
>>> sinav1 = [100, 84, 76, 48, 36, 77, 90]
>>> sinav2 = [95, 78, 66, 57, 75, 89, 95]

>>> sinav1_np = np.array(sinav1)
>>> sinav2_np = np.array(sinav2)
>>> ortalama = (sinav1_np+sinav2_np) / 2
>>> ortalama

array([97.5, 81. , 71. , 52.5, 55.5, 83. , 92.5])
```

NumPy dizilerinde işlemler eleman bazında gerçekleştirilir. Yukarıdaki örnekte __sinav1_np__ ve __sinav2_np__ arasında toplama işlemi yapıldığında bunların aynı sıradaki elemanları toplanır. NumPy dizilerinde istenen şartları taşıyan elemanları seçtirmek mümkündür. Bunun için mantıksal operatörlerden faydalınılmaktadır. Diyelim ki yukarıdaki örnekte hesaplanan ortalamalar dizisinden, geçme notu olan 70'in altındaki ortalamalar incelenmek istenmektedir.

```python
>>> ortalama < 70

array([False, False, False,  True,  True, False, False])
```

İncelenen dizi ile aynı uzunlukta bir mantıksal dizi üretilmiştir. Bu dizinin elamanmları şartı sağlıyorsa __True__ şartı sağlamıyorsa __False__ olacaktır. Şimdi, __ortalama__ dizisindeki istenilenm şartı sağlayan elemanları seçmek için yukarıda yazılan mantısak ifade diziye uygulanmalıdır.

```python
>>> ortalama[ortalama < 70]

array([52.5, 55.5])
```

Bir NumPy modülünde sayı dizileri oluşturmak için __.arange()__, __.libspace()__ veya __.logspace()__ metodları kullanılabilir.

```python
>>> #1'den 10'a kadar sayılar. Argüman olarak 1 ve 11 yazıldığına dikkat edilmelidir.
>>> np.arange(1,11)

array([ 1,  2,  3,  4,  5,  6,  7,  8,  9, 10])

>>> #1'den 10'a kadar sayılar. 2'şer artarak
>>> np.arange(1,11,2)

array([1, 3, 5, 7, 9])

>>> #linspace (linear space): -2 ve 2 arasında 21 adet eşit aralıklı sayı
>>> np.linspace(-2, 2, 21)

array([-2. , -1.8, -1.6, -1.4, -1.2, -1. , -0.8, -0.6, -0.4, -0.2,  0., 0.2,  0.4,  0.6,  0.8,  1. ,  1.2,  1.4,  1.6,  1.8,  2. ])

>>> #logspace (logaritmic  space): dizideki sayıları 10'un üssü olarak yazar.
>>> np.logspace(0, 3, 4)

array([1., 10., 100., 1000.,])
```

### Çok Boyutlu NumPy Dizileri

Şimdiye kadar gördüğümüz liste, sözlük, NumPy dizileri gibi veri yapıları hepo bir boyutlu nesnelerdi. Ancak, birden fazla boyutlu olan veri yapıları da vardır. Örneğin aşağıdaki tablo satır ve sütunlardan yani iki boyuttan oluşmaktadır.

![vgy.me](https://i.vgy.me/z5rJS5.png)

Yukarıdaki tabloda görülenm mtcars veri seti iki boyutlu bir veri nesnesine örnek olarak verilebilir.

Bir veri nesnesinin kaç boyutlu olduğu o veri nesnesindeki herhangi bir veriye erişmek için kaç tane bilgiye ihtiyaç duyduğumuzla ilgilidir. Örneğin, bir listede herhangi bir veriye ulaşmak için sadece verinin listedeki sıra numarasını bilmek yeterlidir. Yukarıdaki tabloda ise herhangi bir veriye ulaşmak için o verinin satır ve sütun bilgisinin bilinmesi gerekmektedir.

NumPy dizileri aslında n boyutlu diziler olarak tanımlanmıştır. Bir NumPy dizisinin türünü __type()__ fonksiyonunu kullanarak görmek istediğimizde __numpy.ndarray__ olduğunu görürüz. Bu ifadedeki __ndarray__ ifadesi n dimensional yani n boyutlu dizi anlamına gelmektedir.

```python
>>> hisse = np.array([3.4, 3.6, 3.9, 4.2, 4.0, 3.8])
>>> type(hisse)

numpy.ndarray
```

NumPy paketini kullanarak 2 boyutlu bir veri nesnesi oluşturmak için listelerden oluşan bir listeyi kullanabiliriz.
```python
>>> hisse_fiyat = np.array([[3.57, 4.42, 5.25, 12.50, 29.30],
                            [3.43, 4.69, 5.00, 11.00, 32.12],
                            [3.15, 4.35, 4.95, 10.50, 29.00]])
```

Yukarıda yer alan iki boyutlu __hisse_fiyat__ dizini aynı zamanda her biri 5 veriden oluşan arka arkaya 3 dizi şeklinde de tarif edebiliriz.

---

### NumPy Dizileri ile İşlemler

Bir NumPy dizisinin boyutlarını görmek için __.shape()__ metodunu kullanabilirsiniz.

```python
>>> hisse_fiyat.shape

(3, 5)
```

Şimdi de üç boyutlu bir dizi oluşturalım.

```python
>>> dizi = np.array([[[1, 2, 3, 4, 5],
                      [6, 7, 8, 9, 10],
                      [11, 12, 13, 14, 15]],
                     [[1, 2, 3, 4, 5],
                      [6, 7, 8, 9, 10],
                      [11, 12, 13, 14, 15]]])

>>> dizi.shape

(2, 3, 5)
```

Üç boyutlu dizinin yüksekliğinin 2, satır sayısının 3 ve sütun sayısının 5 olduğu görülmektedir.

Bir dizinin transpozunu almak için __.T__ metodu kullanılır.
```python
>>> hisse_fiyat.T

array([[ 3.57,  3.43,  3.15],
       [ 4.42,  4.69,  4.35],
       [ 5.25,  5.  ,  4.95],
       [12.5 , 11.  , 10.5 ],
       [29.3 , 32.12, 29.  ]])
```

Bir NumPy dizisinin farklı eksenleri (yükseklik, satır, sütun) üzerindeki toplamları bulmak için __.sum()__ metodu kullanılır. Toplamı bulmak için istediğimiz eksen numarasını parantez içinde belirtilmelidir.
İki boyutlu dizilerde sütun 0, satır ise 1 indeksi ile gösterilir. Üç boyutlu dizilerde ise yükseklik 0, sütun 1, satır ise 2 ile gösterilir.

```python
>>> dizi.sum(0)  # Yükseklik Toplamları

array([[ 2,  4,  6,  8, 10],
       [12, 14, 16, 18, 20],
       [22, 24, 26, 28, 30]])

>>> dizi.sum(1)  # Sütun Toplamları

array([[18, 21, 24, 27, 30],
       [18, 21, 24, 27, 30]])

>>> dizi.sum(2) # Satır Toplamları

array([[15, 40, 65],
       [15, 40, 65]])
```

Aynı şekilde, herhangi bir eksen boyunca birikimli toplamları bulmak için __.cumsum()__ metodu kullanılır.

```python
>>> hisse_fiyat.cumsum(1)  # Satırların birikimli toplamları

array([[ 3.57,  7.99, 13.24, 25.74, 55.04],
       [ 3.43,  8.12, 13.12, 24.12, 56.24],
       [ 3.15,  7.5 , 12.45, 22.95, 51.95]])
```

NumPy dizilerinde kullanılabilen diğer metodlar aşağıdaki tabloda açıklanmıştır.

| Metod               | Açıklama                                                                                                                               |
|---------------------|----------------------------------------------------------------------------------------------------------------------------------------|
|      dizi.max()     | Verilen eksendeki maksimum değerler                                                                                                    |
| dizi.argmax()       | Verilen eksendeki maksimum değerlerin sıra numarası                                                                                    |
| dizi.min()          | Verilen eksendeki minimum değerler                                                                                                     |
| dizi.argmin()       | Verilen eksendeki minimum değerlerin sıra numarası                                                                                     |
| dizi.ptp()          | Verilen eksendeki maksimum ve minimum değerler arasındaki fark                                                                         |
| dizi.clip(min, max) | Dizide yer alan min ve max arasındaki değerleri aynen, min'den <br>düşük değerleri min, max'tan büyük değerleri ise max olarak iletir. |
| dizi.round(a)       | Dizide yer alan sayıları a ondalık basamağa kadar yuvarlar.                                                                            |
| dizi.trace()        | Dizideki köşeggnler toplamını hesaplar.                                                                                                |
| dizi.mean()         | Verilen eksen boyunca ortalama değerleri hesaplar.                                                                                     |
| dizi.var()          | Verilen eksen boyunca varyans değerlerini hesaplar.                                                                                    |
| dizi.std()          | Verilen eksen boyunca standart sapma değerlerini hesaplar.                                                                             |
| dizi.prod()         | Verilen eksendeki sayıların çarpımını hesaplar.                                                                                        |
| dizi.cumprod()      | Verilen eksendeki sayıların birikimli çarpımını hesaplar.                                                                              |
| dizi.sort()         | Verilen eksendeki verilerin sıralanmış halini iletir.                                                                                  |

Bir listenin herhangi bir sırasındaki veriye nasıl ulaşacağımızı daha önce görmüştük. Örneğin listenin 3. sıradaki elemanın ne olduğunu görmek için liste[2] yazmamız yeterlidir. __Python'da liste numaralarının sıfırdan başladığı unutulmamalıdır.__ NumPy dizilerinde de aynı metodu kullanabiliriz. Sadece, dizi kaç boyutlu ise o kadar sayıda bilgiye ihtiyacımız olacaktır. Örneğin yukarıda yer alan hisse_fiyat dizisinin 2.satır ve 4. sırasındaki veriye ulaşmak için __hisse_fiyat[1][3]__ yazmamız yeterlidir. Burada önce __hisse_fiyat[1]__ yazarak ikinci sıradaki satırı seçiyoruz. Sonda ra bu satırdaki 4. elemanı seçmek için sonuna [3] ekliyoruz. Bunu yapmanın daha kolay yolu ise ayrı ayrı köşeli parantezler kullanmak yerine satır ve sütun indeksini tek bir köşeli parantez içinde virgülle ayırarak göstermektir.

```python
>>> hisse_fiyat[1][3]
11.0

>>> hisse_fiyat[1, 3]
11.0
```

Peki tek bir veri yerine belirli bir satır ve sütunları seçmek için ne yazmamız gerekir? Örneğinm sadece birinci ve ikinci satırları seçmek istersem ne yazmalıyım.

```python
>>> hisse_fiyat[0:2, :]

array([[ 3.57,  4.42,  5.25, 12.5 , 29.3 ],
       [ 3.43,  4.69,  5.  , 11.  , 32.12]])
```

NumPy dizilerinde aritmetik işlemler yapmak mümkündür.
```python
>>> a = np.array([[3, 4, 7, 4],
                  [2, 9, 4, 2],
                  [1, 5, 8, 3]])

>>> b = np.array([[4, 2, 8, 9],
                  [6, 3, 6, 1],
                  [3, 2, 4, 2]])

>>> a + b
array([[ 7,  6, 15, 13],
       [ 8, 12, 10,  3],
       [ 4,  7, 12,  5]])

>>> a - b
array([[-1,  2, -1, -5],
       [-4,  6, -2,  1],
       [-2,  3,  4,  1]])
```
İki NumPy dizisi arasında matris çarpımı uygulamak için __np.matmul()__ metodu uygulanabilir.

```python
>>> hisse_fiyat[0:2, :]

array([[ 3.57,  4.42,  5.25, 12.5 , 29.3 ],
       [ 3.43,  4.69,  5.  , 11.  , 32.12]])
```

NumPy dizilerinde aritmetik işlemler yapmak mümkündür.
```python
>>> a = array([[3, 4, 7, 4],
               [2, 9, 4, 2],
               [1, 5, 8, 3]])

>>> b = b.T
        
>>> np.matmul(a, b)
array([[112,  76,  53],
       [ 76,  65,  44],
       [105,  72,  51]])
```
NumPy metodlarını uygulamanın bir başka yolu da isteediğimiz metodu __np.metod_ismi()__ şeklinde kullanmaktır. Örneğin, bir dizinin istediğimiz satır veya sütununun toplamını bulmak için __np.sum(dizi[:,1])__ metodunu uygulayabiliriz.

```python
>>> np.sum(a[:, 1]) # İkinci sütundaki sayıların toplamı
18

np.mean(a[:,2]) # Üçüncü sütundaki sayıların ortalaması
6.333333333333333

>>> dizi = np.array([[2.34, 3.76],
                     [4.23, 5.76],
                     [1.18, 9.32],
                     [7.43, 12.25],
                     [3.14, 2.78],
                     [11.45, 14.32],
                     [5.78, 4.43],
                     [8.87, 9.43]])

>>> np.std(dizi[:,0]) # Birinci sütun standart sapma
3.285786625756456
```

NumPy dizilerine döngü uygularken dikkatli olunması gerekir. Şimdi yukarıda gördüğümüz iki boyutlu __hisse_fiyat__ dizisini ele alalım. Önce bu diziye bir for döngüsü uyguladığımızda ne olduğuna bakalım.

```python
>>> hisse_fiyat = np.array([[3.57, 4.42, 5.25, 12.50, 29.30],
                            [3.43, 4.69, 5.00, 11.00, 32.12],
                            [3.15, 4.35, 4.95, 10.50, 29.00]])

>>> for i in hisse_fiyat:
      print(i)

[ 3.57  4.42  5.25 12.5  29.3 ]
[ 3.43  4.69  5.   11.   32.12]
[ 3.15  4.35  4.95 10.5  29.  ]

```
Döngüyü doğrudan doğruya NumPy dizisine uyguladığımızda dizi içindeki listeleri ya da diğer bir deyişle satırları görüyoruz. Ancak biz tek tek elemanlara erişmek istiyoruz diyelim. Bunun için yine NumPy paketindeki __.nditer()__ metodunu kullanmamız gerekmektedir.

```python
>>> for i in np.nditer(hisse_fiyat):
       print(i)

3.57
4.42
5.25
12.5
29.3
3.43
4.69
5.0
11.0
32.12
3.15
4.35
4.95
10.5
29.0
```

---
### Kullanışlı NumPy Metodları

Önceki bölümde ne çok kullanılan NumPy dizilerine örnekler vermiştik. Bu bölümde işlemlerinizde kullanabileceğiniz ve zaman kazandıracak ilave NumPy fonksiyon ve metod örnekleri yer almaktadır. __Burada aktarılanlar dışında çok fazla sayıda NumPy metodu bulunduğunu unutmayın.__ 

__np.amax():__ Bir NumPy dizisinde istenen eksendeki maksimum değerleri iletir.

```python
>>> x = np.random.uniform(low=1, high=50, size=16).reshape(4, 4) # Minimum 1 ve maksimum 50 değerini alabilecek uniform dağılıma sahip 16 adet sayı üretir ve bunları 4x4 formatına getirir.
>>> x


array([[24.21822172, 33.94938125, 40.75814109, 14.95639957],
       [19.46434823, 15.6271811 , 46.876862  , 29.69476613],
       [42.94929529, 37.06352804, 40.96284712, 34.02980614],
       [22.49084048, 26.21055894, 42.99748819, 21.28104311]])

>>> np.amax(x, axis=0) # Her sütundaki maksimum değer
array([42.94929529, 37.06352804, 46.876862  , 34.02980614])

>>> np.amax(x, axis=1) # Her satırdaki maksimum değer
array([40.75814109, 46.876862  , 42.94929529, 42.99748819])
```

__np.amin():__ Bir NumPy dizisinde istenen eksendeki minimum değerleri iletir..

__np.argsort():__ Bir dizinin elemanların, dizi küçükten büyüğe sıralandığında kaçıncı sırada olacağını belirtir.

```python
>>> x = np.array([4, 2, 1, 6, 9, 3, 15, 11, 10, 7])
>>> x.argsort()

array([2, 1, 5, 0, 3, 9, 4, 8, 7, 6], dtype=int64)
```

__np.concatenate():__ İki NumPy dizisini eksenlerden birleştirmek için kullanılır. Örneğin iki boyutlu (matris) iki diziyi birleştirirken, axis = 0 seçilirse satırları yani alt alta, axis = 1 seçilirse sütunlarını yani yan yana birleştirme işlemi gerçekleştirilir. 

```python
>>> x = np.arange(1, 7).reshape(3, 2)
>>> y = np.arange(7, 13).reshape(3, 2)

>>> x
array([[1, 2],
       [3, 4],
       [5, 6]])

>>> y
array([[ 7,  8],
       [ 9, 10],
       [11, 12]])

>>> np.concatenate([x,y], axis = 0)
array([[ 1,  2],
       [ 3,  4],
       [ 5,  6],
       [ 7,  8],
       [ 9, 10],
       [11, 12]])

>>> np.concatenate([x,y], axis = 1)
array([[ 1,  2,  7,  8],
       [ 3,  4,  9, 10],
       [ 5,  6, 11, 12]])
```

__np.intersect1d():__ İki veya daha fazla NumPy dizisindeki ortak elemanları seçer.
```python
>>> x = np.array([1, 3, 5, 7, 9, 11, 13, 15])
>>> y = np.array([3, 6, 9, 11, 13])

>>> np.intersect1d(x,y)
array([ 3,  9, 11, 13])
```

__np.setdiff1d():__ bir dizide olup ikinci dizide olmayan elemanları seçmek için kullanılır.
```python
>>> x = np.array([1, 3, 5, 7, 9, 11, 13, 15])
>>> y = np.array([3, 6, 9, 11, 13])

>>> np.setdiff1d(x,y)
array([ 1,  5,  7, 15])
```

__np.isin():__ Aranan elemanların bir lite veya dizide olup olmadığını gösterir.
```python
>>> x = [1, 3, 5, 7]
>>> dizi  = [3, 4, 5, 8, 9, 10]

>>> np.isin(x, dizi)
array([False,  True,  True, False])
```
---

__np.isnan():__ Bir dizideki verilerin NaN olup olmadığını görmek için kullanılır.

__np.ones():__ Birden meydana gelen istenen boyutta NumPy dizisi oluşturur.

__np.repeat():__ Tekrar eden elemanalrdan meydana gelen bir dizi oluışturur.

__np.reshape():__ Bir NumPy dizisinin boyutlarını yeniden belirlemek için kullanılır.

__np.unique():__ Bir dizideki tekil değerleri gösterir. 

__np.where():__ Bir NumPy dizisinde istenen şartları sağlayan elemanları seçer.
```python
>>> dizi = np.arange(0,101)
>>> np.where(dizi % 10 == 0)

(array([  0,  10,  20,  30,  40,  50,  60,  70,  80,  90, 100], dtype=int64),)
```

---

#### Alıştırmalar

1. 1'den 1000'e kadar sayıların olduğu bir NumPy dizisi oluşturun ve bu dizide 18 ile tam bölünen sayıları seçen sorguyu yazınız.
2. Bir NumPy dizisindeki en büyük 3 elemanı seçecek tek satırlık bir kod yazınız.
   