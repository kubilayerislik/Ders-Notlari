# Temel İşlemler ve Veri Tipleri

## Temel Aritmetik İşlemler

Python da diğer tüm programlama dilleri gibi temelde bir hesap makinesidir. Python'da matematik işlemleri direkt olarak yapılabilmektedir.
```python
>>> 18 + 7
25
>>> 81 - 17
64
>>> 12 * 6
72
>>> 96 / 12
 8.0
```
Bir değeri her defasında tekrar tekrar kullanmak yerine bu değeri bir değişkene atayıp değişkeni kullanmak ve değiştirmek daha yararlı ve pratik olabilir.
```python
>>> a = 12
>>> a
12
>>> a ** 2
144
```
__"**"__ operatörü üs alma için kullanılmaktadır. En son geçerli (hesaplanmış) değeri göstermek ya da kullanmak içinm alt çizgi "_" kullanılır.
```python
>>> _
144
>>> _ / 24
6.0
```
Ekrana herhangi bir şeyi yazdırmak için __print()__ komutu kullanılır.
```python
>>> print("Python Öğreniyorum.")
Python Öğreniyorum
```
Python'da kullanılan başlıca matematiksel işlem ve karşılaştırma ifadeleri (operatörleri) aşağıdaki gibidir.

<div align="center">

| Operatör |    Açıklama   |
|:--------:|:-------------:|
|     +    |    Toplama    |
|     -    |    Çıkarma    |
|     /    |     Bölme     |
|     *    |     Çarpma    |
|     %    |    Mod alma   |
|    **    |    Üs alma    |
|    //    | Tamsayı bölme |

</div>

Python, yazılan bir matematiksel işlemi değerlendirirken matematiksel kurallara uygun olarak önce parantez içini, sonra üs alma işlemini ve daha sonra da sırasıyla bölme ve çarpma işlemleri ile toplama ve çıkarma işlemlerini dikkate alır.
```python
>>> 3 ** 2 * 4
36
>>> 3 ** (2*4)
6561
>>> 5 + 4 / 2
7.0
>>> (5+4) / 2
4.5
```
Python terminalinde ya da IPython, Jupyter ve Visual Studio Code (ipynb uzantılı dosyalarda) işlem yapıyorsanız, yazdığınız işlemin sonucu yukarıda olduğu gibi hemen alt satırda görünecektir. Ancak PyCharm veya Visual Studio Code (py uzantılı dosyalarda) gibi Python ortamlarında kod yazıyorsanız, programı çalıştırdığınızda yazdığınız matematiksel işlemin sonucu çıktılar arasında görünmez. Python, işlemi hesaplar ancak çıktıyı yazması gerektiğini bilemez. İşlemin sonucunu yazmasını __print()__ komutu ile söylemeniz gerekmektedir.
```python
12 * 5
Process finished with exit code 0
print(12*5)
60
Process finished with exit code 0
```
__//__ (Tamsayı bölme) operatörü python'a özgü bir işlem olup bir bölme işlemindeki kalanın tamsayı kısmını verir.
```python
>>> 5 / 2
2.5
>>> 10 // 3
3
>>> 23 // 3
7
```
Bütün programlama dillerinde kodların arasında açıklama yazabilmek için belirli kurallar vardır. Yazdığınız programları okuyanların daha kolay anlayabilmesi için kod satırları arasında açıklayıcı cümleler yazmak iyi bir uygulama şeklidir. Daha önce yazmış olduğunuz bir kodu incelerken "Acaba burada ne yapmak istemiştim? " diye düşünebilirsiniz veya ders esnasında yazdığınız bir kodu evde tekrar ederken bu kod ne işe yarıyordu diye düşünebilirsiniz. Yazılan bir açıklama cümlesinin kod parçası olmadığını Python'a anlatmanın yolu cümlenin önüne __#__ işareti getirmektir. Python bu işareti gördüğünde satırın geri kalan kısmı değerlendirmeye alınmaz.
```python
>>> print(5 ** 2) #Üs alma işlemi
25
>>> print(13 % 3) # Mod alma işlemi
1
# Aşağıdaki işlemde tamsayı bölme örneği veriliyor
>>> print(15 // 4)
3
```
Python'da açıklama cümlelerini birden fazla satıra yaymak da mümkündür. Açıklamanın başına ve sonuna üç tırnak işareti __"""__ getirerek açıklamaları birden fazla satırda yazabilirsiniz.
```python
""" Birden fazla satıra
yayılmış açıklama cümlesi örneği.
Lütfen bir sayı giriniz.
"""
x = input("Karesi alınacak sayıyı giriniz:")
print(float(x)**2)
```

## Değişkenler

Tüm programlama dillerinin ortak bir özelliği de değişken kullanmalarıdır. Değişken, en basit tanımıyla bir değeri daha sonra da kullanabilmek için bu değere verilen isimdir. Örneğin, __e = 1.71828183__ yazarsanız, bundan sonra her defasında sayıyı uzun uzun yazmak yerine e yazmanız yeterli olacaktır. Program aslında e yazdığınızda neyi kast etmek istedğinizi anlayacaktır.

Bir değişken tanımlamak için kullanılacak değişken ismi ve sonrasında = yazıldıktan sonra değişkene atanacak değer yazılır. Bir değişkene basit bir değer atanabileceği gibi daha karmaşık veri yapıları da tanımlanabilir.
```python
>>> isim = "Kubilay Erişlik"
>>> pi = 3.14
>>> x = 18
```
Python'da bir değişkenin hangi tipte olduğunu açıkça belirtmeye gerek yoktur. Python, değişkenin aldığı değere bakarak hangi tipte olduğunu anlayabilir.

Python'da değişken isimlerini belirlerken uyulması gereken bazı kurallar mevcuttur. Bu kurallardan bazılarına uymamak hataya ve programın durmasına yol açabilir. Bazıları ise sadece iyi programlama alışkanlığı için önerilmektedir.

 * Değişkenler harf, sayı ya da alt çizgi içerebilir.
 * Bir deeğişken ismi harf veya alt çizgi ile başlayabilir ancak sayı ile başlayamaz.
 * Bir değişken boşluk içeremez.
 * Bir değişken nokta içeremez.
 * Python'da tanımlanmış olan anahtar kelime ve fonksiyon isimleri değişken ismi olarak kullanılamaz. Örneğin
 Python'da **def** komutu bir fonksiyon tanımlamak için kullanılır. Bundan dolayı bir değişkene **def** ismini vermeye çalıştığınızda aşağıdaki gibi bir hata alırsınız.
 ```python
 >>> def = 3
 SyntaxError: invalid syntax
 ```
 * Değişkenlerde türkçe karakter kullanılabilir ancak önerilen bir durum değildir. Kodu türkçe haricinde bir dilde çalışan bilgisayarda çalıştırdığınızda hata verir.

 Python'da diğer programlama dillerinde olmayan özelliklerden biri de aynı satır içinde birden fazla değişken tanımlanabilir.
 ```python
 >>> a, b = 3.14, 2.78
 >>> a
 3.14
 >>> b
 2.78
 ```
 Birden fazla değişken tanımlaması yapılırken normal parantez veya köşeli parantez kullanılabilir.
 ```python
 >>> [x, y, z] = [7, 8, 9]
 >>> x
 7
 >>> y
 8
 >>> z
 9
 ```
 Mümkün olduğunca kısa ama aynı zamanda anlaşılır değişken isimlerini tercih etmeniz önerilmektedir. Örneğin bir programda müşteri numarası için değişkene ihtiyaç duymanız halinde mn, m_n, gibi pratik ancak anlaşılması zor değişken isimleri yerine musteri_no gibi bir değişken ismi tercih edilmelidir.

 Değişkenleri isimlendirme konusunda genel kabul gören birkaç yöntem vardır. Bu şekilde kullanmak mecburi olmamakla birlikte yazdığınız kodların kendi içinde tutarlı olması ve anlaşılabilir olması açısından belirli bir isimlendirme şeklini kullanmayı alışkanlık edinmeniz tavsiye edilir.

 Öncelikle, değişken isimlerini küçük harflerle tanımlamak, şart olmamakla birlikte tavsiye edilen bir alışkanlıktır. Değişken ismi, birden fazla kelimeden oluşuyorsa kelimeleri alt çizgi ile ayırabilir ya da ilk kelime küçük harf sonraki her kelimenin ise sadece ilk harfi büyük olacak şekilde bitişik yazabilirsiniz: **musteri_no** veya **musteriNo** gibi.

 **NOT: Değişken isimlerinin büyük ve küçük harfe duyarlı olduğu unutulmamalıdır.**

 ## Temel Veri Tipleri

 Python'da temel olarak __int__ (integer:tamsayı), __float__ (gerçel sayı) ve __string__ (metin) veri tipleri bulunmaktadır. Bu üç veri tipinin dışında da bir değeri olmayan ve yer tutucu görevi gören __None__ (boş) ve sadece True, False (Doğru, Yanlış) değerlerini alabilen __bool__ veri tipleri bulunmaktadır. Ayrıca karmaşık sayıları belirtmek için __complex__veri tipi de mevcuttur. Daha ileride karşımıza çıkacak olan veri yapıları bu temel veriler kullanılarak oluşturulmaktadır.

 ### Sayısal Veri Tipi(Integer & Float)

__Integer:__ Tamsayı türündeki veridir. Python'da tamsayıları 10'luk sistem dışında ikilik, sekizlik veya 16'lık sistemde yazmak mümkündür. İkilik sistemde bir tamsayı yyazmak için sayının başına __0b__ (0 ve binary kelimesinin ilk harfi) getirilir. Benzer şekilde sekizli sayma düzeni için sayınmın başına __0o__, 16'lık sayma düzeninde bir sayı yazmak için sayının başına __0x__ karakterleri getirilir.

```python
# Onluk düzende 100 sayısı:
>>> 100
100
```

```python
# İkilik düzende 100 sayısnın onluk düzendeki karşılığı
>>> 0b100
4
```

```python
# Sekizlik düzende 100 sayısnın onluk düzendeki karşılığı
>>> 0o100
64
```

```python
# 16'lık düzende 100 sayısnın onluk düzendeki karşılığı
>>> 0x100
256
```

Bir gerçel sayıyı tam sayıya çevirmek için __int()__ fonksiyonu kullanılır. Bu fonksiyon, gerçel sayının ondalık bölümünü alır.

```python
>>> int(-3.999)
-3
>>> int(4.2)
4
>>> int(-2.78)
2
>>> int(7.99)
7
```

__int()__ fonksiyonu, metin oılarak girilmiş bir sayıyı da tamsayıya çevirebilir.
```python
>>> int("1807")
1807
```
Bir verinin türünü öğrenmek için __type()__ fonksiyonu kullanılır.
```python
>>> type(17)
int
```
Bir verinin kaç bit büyüklüğünde olduğunu görmek için __.bit_length()__ özelliği kullanılır. Bu özellik tamsayılar için de kullanılabilir.
```python
>>> (10).bit_length()
4
>>> (1000000000).bit_length()
30
```

__Float:__ Gerçel sayılar ya da ondalık sayılar float veri tipi olarak saklanır. Python ondalık kısmı olan her sayıyı __float__ olarak kabul eder.
```python
>>> 3.14
3.14
>>> type(2.7818)
float
```

Çok büyük sayıları yazmak için bilimsel notasyon da kullanılabilir. Örneğin 4*10^12 sayısı __4e12__ olarak yazılabilir.
```python
>>> 4e12
4000000000000.0
```

Tam sayılardaki __int()__ fonksiyonu gibi bir veriyi float veri tipine çevirmek için __float()__ fonksiyonu kullanılır.
```python
>>> float(11)
11.0
>>> float("10.87")
10.87
```

__None:__ Herhangi bir değeri olmayan boş nesneyi temsil eder. İlk harf mutlaka büyük yazılmalıdır. Python'da herhangi bir değer döndürmeyen fonksiyonlar None nesnesini verir. Python'da genelde bir fonksiyonun opsiyonel argümanlarının varsayılan değeri None olur. bu şekilde fonksiyon kullanıldığında, opsiyonel argümana bir değer atanıp atanmadığı program tarafından anlaşılır.

```python
>>> x = None
>>> x is None
True
```

__Bool:__ Sadece True(Doğru) veya False(Yanlış) değerlerinden birini alabilen mantıksal bir veri türüdür. Sayısal olarak 0 değeri False ve sıfır dışındaki tüm sayılar True kabul edilir.
```python
>>> bool(0)
False
>>> bool(3)
True
>>> bool(-4.12)
True
```
Bool verileri 0 ve 1 olarak kabul edildiğinden bunlarla yapılan matematiksel işlemlerde de 0 ve 1 değerlerini alırlar.
```python
>>> False + True
1
>>> True + True
2
>>> False + False
0
```

### Metin Veri Tipi(String)

String, bir veya daha fazla karakter dizesinden oluşan metin tipi veri yapısıdır. String veri tipi Python'da tırnak işareti ("") veya kesme işareti ('') arasıda yazılarak belirtilir. Metin veri tipi için iki işareti de kullanabilmenin faydası metnin içinde tırnak veya kesme işareti kullanımına izin vermesidir.
```python
>>> "Python, 'Guido van Rossum' tarafından geliştirilmiştir."
```
Yukarıdaki metni aşağıdaki şekillerde yazarsanız hata mesajı ile karşılaşırsınız.
```python
>>> "Python, "Guido van Rossum" tarafından geliştirilmiştir."
File "<ipython-input-7-fe5099aa0e11>", line 1
    "Python, "Guido van Rossum" tarafından geliştirilmiştir."
              ^
SyntaxError: invalid syntax
>>> 'Python, 'Guido van Rossum' tarafından geliştirilmiştir.',
File "<ipython-input-7-fe5099aa0e11>", line 1
    'Python, 'Guido van Rossum' tarafından geliştirilmiştir.',
              ^
SyntaxError: invalid syntax
```
Yan yana metinleri ayrı tırnak işaretleri içinde yazarsanız Python bunları da bir araya getirir.
```python
>>> "birinci " "ikinci " "üçüncü"
'birinci ikinci üçüncü'
```
Python'da, string veri tipi UTF-8 karakter setini desteklemektedir. Bunun anlamı Python'da string türü verilerde, Türkçe karakteri de kullanılabilir.

Bir metnin içindeki karakterler 0'dan başlayan sıra numaraları ile numaralandırılırlar. İlk karakterin sırası sıfır, ikinci sıradaki karakterin sırası bir ve üçüncü karakterin sırası iki olmak üzere devam eder. Bir metinde herhangi bir sıradaki karakteri çekmek için köşeli parantez, __[]__ içinde sıra numarası yazılır.

| P | y | t | h | o | n |   | p | r | o | g  | l  | a  | m  | l  | a  | m  | a  |
|---|---|---|---|---|---|---|---|---|---|----|----|----|----|----|----|----|----|
| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 | 16 | 17 |

```python
>>> il = "İstanbul"
>>> il[0]
"İ"
>>> il[1]
"s"
>>> il[2]
"t"
>>> il[3]
"a"
```
__Not: Python'da tüm sıra numaraları 0'dan başlar.__

Python'da tüm değişkenleri olduğu gibi metinleri de yazdırmanın yolu __print()__ fonksiyonunu kullanmaktadır. Birden fazla metni bir arada yazdırmak için print fonksiyonu içinde bir araya getirilmek istenen metinler arasında __+__ işareti konur.

```python
>>> print("Python " + "öğreniyorum" + "!")
Python öğreniyorum!
```
Bir veriyi metne çevirmenin yolu __str()__ fonksiyonunu kullanmaktır.
```python
>>> x = 12345
>>> type(x)
int
>>> y = str(x)
>>> y
"12345"
>>> type(y)
str
```

Python'da metinleri birden fazla satırda da yazmak mümkündür. Bunun iki yolu vardır. İlk yolu, daha önce açıklama yazımında gördüğünüz gibi metin başında ve sonunda üçer adet tırnak ya da kesme işareti kullanmaktır. Arada kalanm metrni farklı satırlara yazabilirsiniz.
```python
>>> """ Python'da metinler
... birden fazla satıra
... yazılabilir.
"""

" Python'da metinler\nbirden fazla satıra\nyazılabilir.\n"
```
Metin çıktısı tek satırda verilir ama çıktıdaki "\n" karakteri dikkatinizi çekmiştir. Bu karakter satır sonu karakteri olarak kullanılır. Program, metin içinde \n karakteri gördüğünde alt satıra geçer. Aynı şekilde, yukarıdaki gibi enter tuşuna basılarak alt satıra geçildiğinde de program buraya \n karakterini yerleştirir.

```python
>>> metin = "Bu metin \nbirden fazla \nsatırda yazılmıştır."
>>> metin
"Bu metin \nbirden fazla \nsatırda yazılmıştır."
>>> print(metin)
Bu metin
birden fazla
satırda yazılmıştır.
```
Benzer şekilde metin için sekme (tab) karakteri koymak için \t kullanılır.

```python
>>> metin = "Python \t ile \t programlama"
>>> print(metin)
Python 	 ile 	 programlama
```

Metin içinde tırnak işareti ve kesme işareti kullanmak için \" ve \' kullanılır. Yukarıda görüldüğü gibi "\" karakterinin özel bir kullanımı olduğundan dosya ve klasör adreslerini yazarken bu karakterin olduğu gibi kullanılması hata mesajı alınmasına yol açabilir.
```python
>>> dir = "C:\users\kubil\Desktop"
SyntaxError: (unicode error) 'unicodeescape' codec can't decode bytes in position 2-3: truncated \uXXXX escape (<ipython-input-4-a8b6e03f9f96>, line 1)
  File "<ipython-input-4-a8b6e03f9f96>", line 1
    dir = "C:\users\kubil\Desktop"
          ^
SyntaxError: (unicode error) 'unicodeescape' codec can't decode bytes in position 2-3: truncated \uXXXX escape
```
Bu hatanın önüne geçmek için yazılacak metnin önüne "r" harfi getirilebilir veya "\" karakter yerine "//" yazılarak, yazılan metnin olduğu gibi alınması sağlanır.

```python
>>> dir = r"C:\users\kubil\Desktop"
>>> print(dir)
C:\users\kubil\Desktop
>>> dir2 = "C://users//kubil//Desktop"
>>> print(dir2)
C://users//kubil//Desktop
```
Metinleri ya da metin veri tipindeki değişkenleri toplamak da mümkündür. İki veya daha fazla metni __"+"__ operatörü ile topladığımızda, bu metinler birleştirilir.
```python
>>> ad = "Guido "
>>> soyad = "van Rossum"
>>> adsoyad = ad + soyad
>>> print(adsoyad)
Guido van Rossum
```

Nasıl ki metinlerle toplama işlemi yapmak mümkünse, çarpma işlemi de mümkündür. Çarpma işlemi de bir metni yan yana istenen miktarda yazmak için kullanılır.
```python
>>> dil = "Python "
>>> dil3 = dil * 3
>>> print(dil3)
Python Python Python
```
Python'da metinlerle işlem yapmak ve metinleri değiştirebilmek için geliştirilmiş bir takım metodlar bulunmaktadır. Aşağıdaki örnekte görülen __.title()__ metodu, metindeki her kelimenin ilk harfini büyük diğerlerini küçük yapar.
```python
>>> isim = "ünal halit özden"
>>> isim.title()
"Ünal Halit Özden"
>>> isim = "kubilay erişlik"
>>> isim.title()
"Kubilay Erişlik"
```
Bir metnin sadece ilk harfini büyük, diğerlerini ise küçük yapmak için __.capitalize()__ mmetodu, benzer şekilde metnin tamamını büyük harf yapmak için __.upper()__, küçük harf yapmak için __.lower()__ metodu kullanılabilir.
```python
>>> isim = "ünal halit özden"
>>> isim.capitalize()
"Ünal halit özden"
>>> isim.upper()
"ÜNAL HALİT ÖZDEN"
>>> isim = "Ünal Halit ÖZDEN"
>>> isim.lower()
"ünal halit özden"
```
Bir metin boşluk içeriyor olabilir ve bu metni saklamadan ya da bir işlem yapmadan önce metindeki boşlukları kaldırmanız gerekebilir. Bunun için __.rstrip()__, __lstrip()__ ve __.strip()__ metodları kullanılır. Bu metodlardan ilk ikisi metnin sağındaki ve solundaki boşlukları kaldırır. Sonuncusu ise metindeki tüm boşlukları kaldırır.

Bir metni kelimelerine ayırmak için __.split()__ metodunu kullanabilirsiniz.
```python
>>> msj = "Python ile programlama öğreniyorum"
>>> msj.split()
["Python", "ile", "programlama", "öğreniyorum"]
```

Bir metnin herhangi bir bölümünü değiştirmek için __.replace()__ metodu kullanılabilir.
```python
>>> metin = "İstanbul Ankara Adana İstanbul Edirne Kars İstanbul"
>>> metin.replace("İstanbul", "İzmir")
"Izmir Ankara Adana İzmir Edirne Kars İzmir"
>>> metin.replace("İstanbul", "İzmir", 1)
"Izmir Ankara Edirne İstanbul Edirne Kars İstanbul"
```
Bir metinde belirli bir karakter dizisinin kaç kez yer aldığını bulmak için __.count()__ metodu kullanılır.
```python
>>> metin = "İstanbul Ankara Adana İstanbul Edirne Kars İstanbul"
>>> metin.count("İstanbul")
3
```
Bir metinde bir karakter ya da karakter dizisinin sırasını bulmak için __.find()__ metodu kullanılır. Bu metod, ilgili harfin metinde ilk kez görüldüğü sırayı verir. Metinde aranan harf bulunmazsa sonuç -1 olur.
```python
>>> kelime = "Programlama"
>>> kelime.find("r")
1
>>> kelime.find("ml")
6
>>> kelime.find("f")
-1
```
