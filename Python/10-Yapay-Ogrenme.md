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

#### Örnek Çalışma (Banka Müşteri Kaybı)

Bu ders için seçtiğim İş problemimiz, bir bankanın müşterilerinin detaylarının bulunduğu bir veri setimizin olduğu bir sınıflandırma problemidir ve hedef değişken, müşterinin bankadan ayrılıp ayrılmadığını (hesabını kapattığını) yansıtan ikili bir değişkendir.

Çalışmada Kaggle'da bulunan "Churn Modelling Dataset" kullanılmıştır. https://www.kaggle.com/datasets/aakash50897/churn-modellingcsv

**Yapay Sinir Ağı İçin Gerekli Kitaplıkları İçe Aktarma**

Yapay sinir ağlarının kullanılabilmesi için gerekli kütüphaneler aşağıda belirtildiği gibi çalışmaya dahil edilir.

```python
>>> import numpy as np
>>> import pandas as pd 
>>> import tensorflow
>>> import keras
>>> import matplotlib.pyplot as plt
>>> import seaborn as sns
>>> sns.set()
```

**Verisetinin Tanımlanması ve İncelenmesi**

```python
churn_data = pd.read_csv('Churn_Modelling.csv',index_col='RowNumber')
churn_data.head()
```
```python
churn_data.info()
```
```python
churn_data.describe()
```
**Verisetindeki Kullanılmayan Değişkenlerin Çıkartılması**

Verisetinde bulunan "CustomerId" ve "Surname" değişkenleri dataframeden çıkartılmıştır.

```python
churn_data.drop(['CustomerId','Surname'],axis=1,inplace=True)
churn_data.head()
```

**Metin Olarak Tutulan Değişkenler İçin Kukla Değişken Oluşturulması**

```python
Geography_dummies = pd.get_dummies(prefix='Geo',data=churn_data,columns=['Geography'])
Geography_dummies.head()
```
```python
Gender_dummies = Geography_dummies.replace(to_replace={'Gender': {'Female': 1,'Male':0}})
Gender_dummies.head()
```
```python
churn_data_encoded = Gender_dummies
```

**Bağımlı Değişken Sınıfının İncelenmesi**
```python
sns.countplot(y=churn_data_encoded.Exited ,data=churn_data_encoded)
plt.xlabel("Hedef Sınıf Frekans Dağılımı")
plt.ylabel("Hedef Sınıf")
plt.show()
```

**Değişkenlerin Dağılımlarının İncelenmesi**

```python
churn_data_encoded.hist(figsize=(15,12),bins = 15)
plt.title("Features Distribution")
plt.show()
```

**Değişkenler Arasındaki İlişkilerin İncelenmesi**
```python
plt.figure(figsize=(15,15))
p=sns.heatmap(churn_data_encoded.corr(), annot=True,cmap='RdYlGn',center=0) 
```

**Bağımlı Değişken ve Bağımsız Değişkenlerin Oluşturulması**

```python
X = churn_data_encoded.drop(['Exited'],axis=1)
y = churn_data_encoded.Exited
```

**Eğitim ve Test Verisetlerinin Oluşturulması**

```python
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size = 0.33, random_state = 0)
```

**Bağımsız Değişkenlerin Standartlaştırılması**

```python
from sklearn.preprocessing import StandardScaler
sc = StandardScaler()
X_train = sc.fit_transform(X_train)
X_test = sc.transform(X_test)
```

**Yapay Sinir Ağ Modelinin Oluşturulması**

```python
from keras.models import Sequential
from keras.layers import Dense
classifier = Sequential()
classifier.add(Dense(units = 6, kernel_initializer = 'uniform', activation = 'relu', input_dim = 12))
classifier.add(Dense(units = 6, kernel_initializer = 'uniform', activation = 'relu'))
classifier.add(Dense(units = 1, kernel_initializer = 'uniform', activation = 'sigmoid'))
classifier.compile(optimizer = 'adam', loss = 'binary_crossentropy', metrics = ['accuracy'])
classifier.fit(X_train, y_train, batch_size = 10, epochs = 100,verbose = 0)
score, acc = classifier.evaluate(X_train, y_train, batch_size=10)
print('Train score:', score)
print('Train accuracy:', acc)
```

**Oluşturulan Yapay Sinir Ağı Modelinin Test Verisetine Uygulanması**

```python
y_pred = classifier.predict(X_test)
y_pred = (y_pred > 0.5)
score, acc = classifier.evaluate(X_test, y_test, batch_size=10)
print('Test score:', score)
print('Test accuracy:', acc)
```

**Sınıflandırma Tablosunun Oluşturulması**

```python
from sklearn.metrics import confusion_matrix
cm = confusion_matrix(y_test, y_pred)
p = sns.heatmap(pd.DataFrame(cm), annot=True, cmap="YlGnBu" ,fmt='g')
plt.title('Confusion matrix', y=1.1)
plt.ylabel('Gerçek Değer')
plt.xlabel('Tahmin Değeri')
```

**Sınıflandırma Raporunun Oluşturulması**
```python
from sklearn.metrics import classification_report
print(classification_report(y_test,y_pred))
```

Yorumlama ve daha fazla bilgi için: https://tez.yok.gov.tr/UlusalTezMerkezi/TezGoster?key=_F5QEpayDXGqGZlp9XiFtGcL8B3K2dw0qIWxwvgmfiu7awSo0Z2au8XOX2T86lwO