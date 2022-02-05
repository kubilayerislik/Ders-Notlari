# Modüller ve Nesne Yönelimli Programlama

Pyhton da yazdığınız kodlar uzadıkça programları parçalara ayırmak isteyebilir veya bu yazdığınız kodu birden fazla projenizde kullanmak istiyor olabilirsiniz. Bunun için Python'da modül kavramı geliştirilmiştir. Python'da modüller çok önemli yer tutmaktadır. Modüller sayesinde yazdığımız fonksiyonları yeniden yazmaya ya da bir programdan diğerine kopyalamaya gerek kalmadan tekrar tekrar kullanabiliriz.

Bir modülü kullanabilmek için önce "import" kelimesini kullanarak modülü program içine aktarmamız gerekmektedir. Örneğinm birçok matematiksel fonksiyonu barındıran math modülünü kullanacağımzı düşünelim. Bunun için önce __"import math"__ yazmamız gerekmektedir. Bu şekilde math modülündeki fonksiyonlar programın içinde kullanılabilir hale gelir.

Örneğin, math modülü içinde yer alan faktöriyel fonksiyonunu kullanacağımızı düşünelim.
```python
>>> import math
>>> math.factorial(4)
24
```

Yukarıda görüldüğü gibi bir modül içinde tanımlanmış olan bir fonksiyonu kullanmak için önce modülün isminden  sonra nokta getirerek istenen fonksiyon adı yazılmalıdır. Python'un günümüzde bu kadar popüler olmasının bir sebebi de geliştirilmiş olan çok çeşitli sayıda kullanışlı modüllerin varlığıdır. Bu modüller paket olarak isimlendirilir. Paketler sayesinde, istediğpimiz bir programı en baştan yazmak yerine daha önce geliştirilmiş hazır programları kullanabiliriz.

Paketleri anaconda üzerinden kurabilir silebilir veya her projeniz için ayrı bir çalışma alanı oluşturabilirsiniz. Eğer yazdığınız program kendi bilgisayarınızda çalışmayacak ve uzak bir sunucuda çalışacak ise bu tarz projeler için yeni bir çalışma alanı oluşturmak çok daha iyi olacaktır.

Anaconda da çalışma alanları environments sekmesinde bulunmaktadır. Anaconda Navigator uygulamasını açtığınızda sol tarafta environments sekmesini görseldeki gibi görebilirsiniz.

![Şekil 1](https://i.vgy.me/N333e3.png)

Environments menüsüne girdiğinizde bilgisayarınız üzerinde oluşturmuş olduğunuz çalışma alanlarını görebilirsiniz. Base(root) yazan environments sizin varsayılan olarak kullandığınız ve anaconda yüklenirken oluşturulmuş olan bir environmenttır. Bazı paketleri buraya yüklemek engellendiği için kendinize bir adet environment oluşturmanız sizin için yararlı olacaktır.

 ![Şekil 1](https://i.vgy.me/c1OkiE.png)

Yeni bir environment oluşturmak için aşağıda yer alan create kısmını kullanabilirsiniz. Create dedikten sonra karşınıza aşağıdaki gibi bir görsel çıkacaktır. Burada environmentınıza bir isim vermeniz gerekmektedir. Environmentınıza isim verdikten sonra create tuşuna basıp environmentınızı oluşturabilirsiniz.

![Şekil 1](https://i.vgy.me/RBh0Cc.png)

Create bastıktan sonra anaconda sizin için çalışma alanızı oluşturmaktadır. Daha sonrasında aşağıdaki paketler otomatik olarak anaconda tarafından environmentınıza yüklenmiş olacaktır. Yeni bir paket yüklemek için yukarıda yer alan dropdown menüsünden  __Installed__ yerine __All__ seçmeniz gerekmektedir. Bu sayede anaconda da bulunan bütün paketleri hızlı bir şekilde environmentınıza yükleyebilirsiniz.

![Şekil 1](https://i.vgy.me/tQWqZe.png)

Derslerimizde kullanacağımız numpy, matplotlib, scikit-learn, math gibi paketlerin kurulumunu bu alandan yapabilirsiniz. Anaconda içerisinde 9000 ine yakın paket bulunmaktadır.

![Şekil 1](https://i.vgy.me/vrRXpF.png)

Buradan kullanmak istediğiniz paketleri seçip daha sonrasında aşağıda çıkan __Apply__ tuşuna basarak paketleri environmentınıza yükleyebilirsiniz. Acondada bulunmayan paketlerin yüklenmesi işlemi ise biraz daha karmaşık bir yapıdadır. Bunun için bilgisayarınızın yada anacondanın konsolunu kullanmanız gerekmektedir.

![Şekil 1](https://i.vgy.me/d6fLYp.png)

Yüklemek istediğiniz paket başka paketlerin kurulmasını gerekiyorsa karşınızda aşağıdaki gibi bir görsel çıkacaktır. Buna da __Apply__ diyerek yükleme işlemini tamamlayabilirsiniz.

![Şekil 1](https://i.vgy.me/njtggf.png)

Kullanmak istediğiniz paket anacodanın içinde bulunmuyorsa anaconda komut istemcisini kullanmanız gerekmektedir. __Anaconda Prompt__ uygulamasını windows için sağ tıklayıp yönetici olarak aç demeniz gerekmektedir. Diğer türlü paket yükleme işleminde hata ile karşılabilirsiniz.

![Şekil 1](https://i.vgy.me/8nYbK5.png)

Aconda Prompt u yönetici olarak açtığınızda aşağıdaki gibi bir ekranla karşılaşmanız gerekmektedir. Burada kırmızı çerçeveli yazının bire bir aynı olması gerekmektedir. Eğer farklı bir yazı varsa yönetici olarak başlatmadığınız anlamına gelmektedir. Prompt'u açtıktan sonra öncelikle ilk yapılması gereken şey hangi environment üzerinde çalışma yapacağınız belirtmeniz gerekmektedir. Bunun içinde __conda activate (environment adı)__ şeklinde olmalıdır. Daha sonra enter tuşuna bastığınızda aşağıdaki gibi parantez içinde environmentınızın adının gözükmesi gerekmelidir.

![Şekil 1](https://i.vgy.me/geOYKI.png)

Anaconda içinde bulunmayan python paketlerine https://pypi.org/ üzerinden eşirmeniz mümkündür. Burada 350000'e yakın paket bulunmaktadır. Daha sonra saearch kısmına kullanmak istediğiniz paketi yazarak aratmanız gerekmektedir.

![Şekil 1](https://i.vgy.me/eubvT7.png)

Paketi arattıktan sonra karşınıza arattığınız kelime ile ilgili paketler çıkacaktır. Buradan doğru paketi seçmeniz çok önemlidir.

![Şekil 1](https://i.vgy.me/PROBDD.png)

Doğru paketi seçtikten sonra karşınıza paketin sayfası çıacaktır. Burada paketin altında paketi environmentınıza nasıl indireceğinizi gösteren kod bulunmaktadır.

![Şekil 1](https://i.vgy.me/nuGlq4.png)

Daha sonrasında burada yazan kodu aktive etmiş olduğunuz environmentınızın kod kısmına yazabilirsiniz ve sonrasında enter tuşuna bastığınızda paketi yükleme işlemi gerçekleşecektir.

![Şekil 1](https://i.vgy.me/YigZJ7.png)

Yükleme işlemi başarılı bir şekilde gerçekleştiğinde __success__ mesajını alacaksınız.

![Şekil 1](https://i.vgy.me/qLh0SB.png)

Anaconda içinde bulunmayan paketleri de bu şekilde çalışma alanınıza yükleyebilirsiniz. VS Code üzerinde environmentınızı değiştirmek için sağ yukarıdaki alanı kullanabilirsiniz.

![Şekil 1](https://i.vgy.me/Rgg2jX.png)

Bir paketin içindeki kullanılabilir fonksiyonları görmek için önce paketi help(paket_adı) komutunu kullanabilirsiniz.

```python
>>> import numpy
>>> help(numpy)
```

İçeri aktardığınız modüllere yeni bir isim verip programda bu isimle kullanmak mümkündür. Paket ismi uzun olan paketlerde sıklıkla kullanılan bir yöntemdir. Bu şekilde fonksiyonun önüne paket ismi yazmaya gerek kalmadan kısaltmasını kullanmak mümkündür.

```python
>>> import math as mt
>>> mt.log10(100)
2.0
```

Aslında bir modül, Python kodlarından ve tanımlarından oluşan .py uzantılı bir dosyadan başka bir şey değildir. Siz de sık kullandığınız fonksiyonları .py uzantılı bir dosyada kaydederek daha sonra farklı programlarda bu modülü içeri aktarıp içindeki fonksiyonları kullanabilirsiniz. Örneğin aşağıda gibi çok basit bir modül oluşturabilirsiniz.

```python
>>> def kare_al(x):
        return x ** 2

>>> def kup_al(x):
        return x ** 3

>>> def kok_al(x):
        return x ** 0.5

>>> def us_al(x, y):
        return x ** y
```

Yukarıda görmüş olduğunuz kodu usalma.py adlı bir dosya oluşturarak dosyanın içerisine yazıyoruz. Daha sonrasında asıl çalışma dosyamıza geçerek __import usalma__ kodunu yazarak modülümüzü kullanılabilir bir hale getiriyoruz.

```python
>>> import usalma
>>> usalma.kare_al(5)
25.0
```
