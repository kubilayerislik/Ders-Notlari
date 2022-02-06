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
