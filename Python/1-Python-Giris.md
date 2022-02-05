# Python'a Giriş

## Python Nedir?

Pyhon, 1989 yılında [Guido van Rossum](https://tr.wikipedia.org/wiki/Guido_van_Rossum) tarafından geliştirilen bir programlama dilidir. Guidı van Rossum, Python ismini ünlü komedi grubu [Monty Python](https://tr.wikipedia.org/wiki/Monty_Python)'dan esinlenerek bulmuştur. Python açık kaynak kodlu bir programlama dilidir ve ücretsizdir.

Python bugüne kadar iki farklı koldan ilerlemiştir: Python 2 ve Python 3. Python 2 2000 yılında yayınlanmış, Python 3 ise 2008 yılında yayınlanmıştır. Bu iki sürüm birbirinden çok farklı değildir ancak iki sürümden birinde yazılan bir program diğerinde çalışmamaktadır. 2020 yılından itibaren Python 2'nin geliştirilmesi sona ermiştir. Bundan dolayı derslerimizde Python'un 3. sürümü kullanılacaktır.

 ## Neden Python Diğer Programlama Dilleri Değil

Python son derece güçlü bir dil olduğu kadar aynı zamanda öğrenmesi de oldukça kolay bir programlama dilidir. Python açık kaynak kodlu bir programlama dili olmasından kaynaklı olarak gelişmiş bir kütüphaneye sahiptir. Python için geliştirilmiş *Numpy*, *pandas*, *matplotlib* gibi veri biliminde kullanılabilecek çok güçlü kütüphanelere sahiptir. Bundan dolayı Python web programlama, bilimsel programlama, veri bilimi, yapay zeka ve makine öğrenmesi, derin öğrenme gibi farklı alanlarda yaygın olarak kullanılmaktadır.

Youtube, Netflix, Instagram gibi siteler web geliştiröe için Python'da geliştirilmiş web geliştirme kütüphaneleri *Django*, *Flask* ya da *Pyramid* kullanmaktadır.

Python'da geliştirilmiş olan *Numpy*, *SciPy* kütüphaneleri, bilimsel programlar için çok hızlı programlamaya imkan sağlayan kütüphanelerdir.

Son yıllarda önemi ve kullanımı giderek artan yapay öprenme uygulamaları için de Python'da çok sayıda kütüphane geliştirilmiştir. *Tensorflow*, *Keras* ve *Scikit Learn* bunlardan en önemlileridir. Ayrıca Python'da *Pandas*, *Matplotlib* ve *Bokeh* kütüphaneleriyle de veri analizi ve görselleştirme de çok kolaydır.

Bu kadar işlevselliğin yanında Python, yazması, okuması ve öğrenmesi oldukça kolay olan bir programlama dilidir.

Python, C, C++ ve Java gibi dillere göre çok daha anlaşılır bir yazı stiline sahiptir. Aşağıda, iki sayının toplamını bulan programların C++, C ve Java dillerindeki örnekleri yer almaktadır.

**C++ Programlama Dili**
 ```c++
 using namespace std;
 int main()
 {
  int a, b, c;

  count << "İki tam sayıyı giriniz: \n";
  cin >> a >> b;

  c = a + b;
  count << "İki sayının toplamı = " << c << endl;

  return 0;
 }
 ```

 **C Programlama Dili**
 ```c
 # include<stdio.h>
 int
 main()
 {
   int a, b, c;

   printf("İki tam sayı giriniz: \n");
   scanf ("%d%d", & a, & b);

   c = a + b;

   printf("İki sayının toplamı = %d\n", c);

   return 0;
 }
 ```

 **Java Programlama Dili**
```Java
import java.util.Scanner

class AddNumbers
{
  public static void main(String args[] )
  {
    int x, y, z;
    System.out.println("İki tam sayıyı giriniz: ");
    Scanner in = new
    Scanner(System. in);
    x = in.nextInt();
    y = in.nextInt();
    z = x + y;
    System.out.println("İki sayının toplamı = " + z);
  }
}
```

**Python Programlama Dili**
```python
sayi1 = float(input("İlk sayıyı girin: "))
sayi2 = float(input("İkinci sayıyı giriniz"))
toplam = sayi1 + sayi2
print("İki sayının toplamı:" + str(toplam))
```

Görüldüğü gibi aynı işlevi gören Python program çok daha kısa, basit ve anlaşılırdır. Bunun en önemli nedeni, diğer dillerde kullanılan parantezler ya da begin/end ifadeleri yerine girintilerin kullanılmasıdır.

Python için yazım standartları ve rehberleri yayınlanmakta ve sürekli olarak geliştirilmektedir. Bu rehberler [PEP (Python Enhancement Proposals)](https://www.python.org/dev/peps) olarak bilinmektedir.
