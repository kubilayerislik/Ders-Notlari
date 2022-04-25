# Yapay Öğrenme

Yapay öğrenme, bilgisayar algoritmalarının verileri kullanarak karar verme yeteneğini kazanması (öğrenmesi) olarak tanımlanabilir ve model oluşturmada istatistik kuramını kullanır.

Yapay öğrenmenin amacı, verileri kullanarak karar verebilen algoritmalar oluşturmaktadır. Örneğin, kullandığınız e-posta programının, gelen bir e-postanın spam olup olmadığına karar vermesi, bir bankanın bilgisayar algoritmaları yardımı ile kredi başvurusunda bulunan müşteri kredi değerlerinin ölçülmesi, belirli bir ürünü salın alan müşterilerin, bir başka ürünü de alıp almayacaklarının tahmin edilmesi, bir fotoğrafın kedi mi köpek mi olduğunun bilgisayar tarafından tespit edilmesi yapay öğrenme örnekleridir. Yapay öğrenme problemleri genel olarak tahmin yürütme veya sınıflandırma yapmak için kullanılır. Bir e-postanın spam olup olmadığı, ya da bir kredi müşterisinin borcunu geri ödeyip ödemeyeceği sınıflandırma problemi örnekleridir. Buna karşın belirli girdileri kullanarak sayısal bir çıktı üretme regresyon problemidir. Belirli sayısal değerler arasındaki ilişkiyi kullanarak bir tahminde bulunmak isteyebilir. Örneğin, bir kişinin eğitim durumu, cinsiyeti, yaşı gibi değerleri kullanarak bu kişinin ortalama gelirini tahmin etmek istiyorsak bu bir regresyon problemidir.

Yapay öğrenmeyi genel olarak üç sınıfa ayırabiliriz: gözetimli öğrenme (supervised learning), gözetimsiz öğrenme (unsupervised learning) ve pekiştirmeli öğrenme (reinforcement learning). Gözetimli öğrenmede sınıflandırılmış bir veri seti kullanılarak yeni verilerin özellikleri bulunmaya çalışılır. E-Posta örneğine geri dönecek olursak bir algoritmaya önce spam olan ve olmayan epostalardan oluşan bir veri seti tanıtılarak algoritmanın belirli özelliklere göre bunları sınıflandırmayı öğrenmesi sağlanır. Algoritmanın öğrenme başarısı, daha sonra gördüğü yeni epostaların spam olup olmadığını belirleme başarısı ile ölçülür. Bir başka örnek de bir bankanın kredi müşterilerinin borölarını geri ödeyip ödemeyeceklerini tahmin etmesi olabilir. Banka, daha önce kredi kullandırdığı müştelerilerin verilerini kullarak bir tahmin modeli geliştirir. Bu model ile yeni müşterilerin borçlarını geri ödeyip ödemeyecekleri tahmin edilir. Bir başka örnek de hisse senedi fiyat verilerini kullanarak gelecekteki fiyatları tahmin etme işi olabilir.

Gözetimli öğrenmenin aksine, gözetimsiz öğrenmede sınıflandırılmış bir veri seti yoktur. Gözetimli öğrenmede çoğu zaman doğru bir cevap vardır ama gözetimsiz öğrenmede durum bu değildir. Bilgisayar algoritması yardımıyla veri setindeki öbekler, sınıflar, örüntüler veya varsa anomaliler tespit edilmeye çalışılır. Örneğin, internetteki haberleri tarayıp bunları konularnın yakınlıklarına göre sınıflandıracak bir program yazmak istedğinizi düşünün. Siz haberlere herhangi bir etiket yapmayacaksınız. Yazacağınız algoritma haber içeriğindeki kelimeleri kullanarak birbirine yakın olan haberleri bir arada gruplandırsın. İşte bu genel olarak gözetimsiz, özel olarak ise öbekleme problemidir.

## Gözetimli Öğrenme

Gözetimli öğrenme bir özelliği tahmin etmek için kullanılır. Tahmin edilmek istenen özellik bir kategori veya sayısal bir değer olabilir. Bunun için daha önceden gözlemlenmiş ve sonucu bilinen bir veri seti kullanılarak bilinen farklı özellikler ile hedef değer arasınnda bir ilişki bulunmaya çalışılır.

Örneğin elimizde bir spam ve normal sınıflandırılmış 1000 adet eposta olsun. Bu epostalarda spam olarak tanımlanmış olanların içerdiği ortak kelimeleri bularak bu kelimeleri içeren epostaları spam olarak işaretleyelim. Örneğin "bedava", "fırsat", "ücretsiz", "miras" kelimelerini içeren epostalar spam olsun. Burada daha önce spam olduğu ve olmadığı bilinen epostaların ortak özelliklerini kullanarak yeni epostaları "spam" ve "spam değil" olarak sınıflandırdık.

Özetleyecek olursak gözetimli öğrenme, bağımsız değişkenleri kullanarak bağımlı bir değişkeni tahmin etme işidir. Yukarıdaki örneklerde bir epostanın türü bağımlı değişken, bunları tahmin etmek için kullanılacak diğer tüm değişkenler ise bağımsız değişkenlerdir.

### Yapay Sinir Ağları

Makine öğrenmesi modern toplumda web aramalarından, sosyal ağlarda içerik filtrelemelerine, e-ticaret web sitelerinde size önerilen ürünler gibi aklınıza gelebilecek birçok alanda makine öğrenmesi kullanılmaktadır. Makine öğrenmesi, mevcut verilerden bir model veya algoritma oluşturarak yeni verilerin tahmin edilmesi işlemidir. Yapay sinir ağları, makine öğrenmesinin eğitim kısmında kullanılan yöntemlerden bir tanesidir. Yapay sinir ağları, insan beyninin özelliklerinden olan öğrenme yol ile yeni bilgiler üretebilme gibi kabiliyetini herhangi bir yardım olmaksızın otomatik olarak ortaya çıkartmak niyetiyle geliştirilen bilgisayar sistemleridir (Öztemel, 2012).
Yapay sinir ağları bazı ayırt edici özellikleri sayesinde tahmin etme işlemlerinde kullanılan diğer yöntemlere göre daha değerlidir. Bu özelliklerden birincisi, geleneksel model tabanlı yöntemlerin aksine yapay sinir ağları varsayıma değil, veriye dayalı kendinden uyarlamalı bir yöntemdir. Yapay sinir ağları örneklerden öğrenirler ve tanımlaması zor olsa da veriler arasındaki ince fonksiyonel ilişkileri yakalarlar. Bu anlamda yapay sinir ağları çok değişkenli doğrusal olmayan istatistiksel yöntemlerden biri olarak ele alınabilir (Cheng & Titterington, 1994; Hornik, Stinchcombe, & White, 1989).

Yapay sinir ağlarının ikinci özelliği veride bulunan eksik gözlemleri doğru bir şekilde tamamlayabilmesidir. Aynı zamanda bu sayede geçmiş gözlemlerden yararlanarak gelecek tahmini yapılmasını mümkün kılar. Yapay sinir ağlarının üçüncü özelliği geleneksel istatistiksel yöntemlerden daha genel ve esnek işlevsel biçimlere sahip olmasıdır. Geleneksel istatistiksel tahmin modellerinde, girdiler ile çıktılar arasında temel bir ilişki olduğu varsayılır. Gerçek hayattaki problemlerin karmaşıklığında çoğunlukla bu varsayımlar sağlanamaz. Bundan dolayı yapay sinir ağları tahmin işlemleri için iyi bir alternatif olabilir.

Yapay sinir ağları doğrusal değildir. Tahmin işlemlerinde uzun zamandır doğrusal istatistik yöntemleri kullanılmıştır. Doğrusal yöntemlerin anlaşılması, analiz edilmesi ve yorumlanması kolaydır. Ancak gerçek hayattaki problemler çoğunlukla doğrusal değildir. Birçok doğrusal olmayan tahmin modelleri vardır. Ancak doğrusal olmayan bir modelin belirli bir veri setine uygulanması oldukça zordur. Çünkü çok fazla sayıda olası doğrusal olmayan model vardır ve önceden belirlenmemiş doğrusal olmayan model verideki önemli özellikleri yakalamada yeterince başarılı olamayabilir. Veri odaklı olan yapay sinir ağları girdi ve çıktı değişkenleri arasındaki ilişkiler sayesinde önceden bilgi sahibi olmadan doğrusal olmayan modelleme yapabilir.

Yapay sinir ağaları, sinir hücrelerinin birbirine çeşitli şekillerdebağlanmasından oluşur. Hücrelerin bağlantı şekillerine, öğrenmekurallarına ve transfer fonksiyonlarına göre birçok yapay sinir ağı yapısıgeliştirilmiştir (Arıkan Kargı, 2015). Sınıflandırma ve tahminanalizlerinde genellikle çok katmanlı yapay sinir ağları kullanılmaktadır.Çok katmanlı yapay sinir ağlarında yapay sinir ağı modelinde girdi katmanı(input layer), gizli katmanlar (hidden layer) ve çıktı katmanı (outputlayer) yer almaktadır. Çok katmanlı algılayıcı ağından hazırlanan bilgilergirdi katmanından ağa sunulur ve gizli katmanlardan geçerek çıktıkatmanına ulaşır ve ağa sunulan girdilere karşılık ağın cevabı dış dünyayailetilir (Öztemel, 2012). Çok katmanlı ağlarda öğrenme aşamasında, gerçekdeğeri ile ağın ürettiği çıktı değeri arasındaki hatayı en aza indirmekiçin ağırlıklar sürekli olarak değiştirilir. Hata minimuma indiği andaöğrenme süreci gerçekleştirilmiş olur (Velo, López, & Maseda, 2014).

Yapay sinir ağlarının en büyük özelliği katmanların insanlar tarafından tasarlanmamasıdır. Girdi katmanından sisteme giriş yapan veriler incelenir ve veriler arasındaki önemli olan yönler güçlendirilir ve alakasız yönler bastırılır. Birbiri ile güçlü ilişkide olan veriler aynı sınıfa atanır ve bu şekilde sınıflandırma işlemi yapılır ve bu şekilde veriler yardımı ile öğrenme işlemi gerçekleştirilir.

Yapay sinir ağlarının gelecekte çok daha fazla başarıya ulaşacağı düşünülmektedir. Çünkü elle çok az hesaplama işlemi gerektirmektedir. Bu sayede veri miktarındaki artış analizin uygulanabilirliğini zorlaştırmamaktadır. Birçok sınıflandırma yönteminin yerine tercih edilmesindeki neden de tam olarak budur.

---

#### Örnek Çalışma (Online Ödemelerde Dolandırıcılık Tespiti)

Çalışmada Kaggle'da bulunan "Online Payments Fraud Detection Dataset" kullanılmıştır. https://www.kaggle.com/datasets/rupakroy/online-payments-fraud-detection-dataset?resource=download

**Değişkenler:**

1. Step: Zamanın bir göstergesidir. 1 Adım 1 Saate eşittir.
2. Type: Online işlemin tipi
3. Amount: İşlem tutarı
4. nameOrig: İşlemi başlatan müşteri
5. oldbalanceOrg: İşlemden önceki bakiye
6. newbalanceOrig: İşlemden sonraki bakiye
7. nameDest: İşlemin alıcısı
8. oldbalanceDest: Alıcının işlemden önceki ilk bakiyesi
9. newbalanceDest: İşlemden sonra alıcının yeni bakiyesi
10. isFraud: Dolandırıcılık işlemi

Yukarıdaki maddelerden de gördüğünüz gibi toplam 10 değişken bulunmaktadır.

Buradal, asıl amacımız, tüm bağımsız değişkenleri (ilk 9) dikkate alacak ve buna göre işlemin dolandırıcılık olup olmadığını tahmin edecek bir yapay sinir ağı oluşturmaktır (Dolandırıcılık burada bağımlı değişken).

**Yapay Sinir Ağı İçin Gerekli Kitaplıkları İçe Aktarma**

Yapay sinir ağlarının kullanılabilmesi için gerekli kütüphaneler aşağıda belirtildiği gibi çalışmaya dahil edilir.

```python
>>> import numpy as np
>>> import pandas as pd
>>> import tensorflow as tf
```

**Verisetinin Tanımlanması**

```python
>>> data = pd.read_csv("fraud_data.csv")
>>> data.head()
```

**Özellik Matrisinin Oluşturulması**

Bir makine öğrenme modeli oluştururken temel ilke, Özellik Matrisi olarak da adlandırılan X'i oluşturmaktır. Bu X temel olarak tüm bağımsız değişkenlerimizi içeririr.

```python
>>> X = data.iloc[:,0:-2].values
>>> X
```

Burada, veri kümesi içindeki istenen sütundan istenen değerleri getirmemizi sağlayan PANDAS veri çerçevesinin iloc yöntemi kullanılmıştır. Burada gördüüğünüz gibi 1. sütündan itibaren 9.sütuna kadar tüm veriler alınmıştır.

**Bağımlı Değişken Vektör(Y) Oluşturma**

Bağımsız değişken için öznitelik matrisimizi (X) oluşturduğumzu gibi, sadece bağımlı değişken değerlerimizi içeren bir bağımlı değişken vektörü (Y)'de oluşturmamız gerekmektedir.

```python
>>> Y = data.iloc[:,-2:-1].values
>>> Y
```
