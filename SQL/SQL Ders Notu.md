# MySQL Giriş Ders Notu

### SQL Nedir?

SQL (Structered Query Language) Veritabanı işlemleri için kullanılan bir alt dil olarak bilinmektedir. Verilerin belirli kriterlere göre sunulması işlemine sorgu denir. Sorgu işlemi ise SQL ile yapılabilmektedir. SQL Veritabanı sistemi bir programlama dili olarak bilinse de, aslında bir veritabanı yönetim sistemidir. Bilgisayarda dağınık olarak yer alan verilerin düzenlenerek depolanması için SQL veritabanı sistemi geliştirilmiştir.

### SQL Veritabanı Kullanımının Avantajları

- SQL Veritabanı bilgileri rahatlıkla kategorize edebilmektedir. Kategorik olarak depolanan bilgiler sayesinde dağınıklık ortadan kalkar. Ayrıca bir veriye ulaşmak çok daha kolay ve hızlı olacağından dolayı zamandan tasarruf sağlar.

- SQL sistemi sayesinde tekrar eden verilerden kurtulunmuş olacaktır.

- Bilgisayar hafızasında dağınık halde bulunan bilgilerin klasöre dönüştürülebilmesine yardımcı olur. Bu sayede boş yer işgalinin önüne geçilmiş olur.

- Bütün veritabanı işlemlerinde SQL sistemine ihtiyaç duyulmaktadır. SQL veritabanının temel amacı, hem verilerin hem de veri kümelerinin modellenmesini sağlamaktır.

### SQL Veritabanı Kullanılarak Yapılabilecek İşlemler

- Yeni veriler çekmek

- Var olan verileri kaydetmek

- Verilerin tamamını güncellemek

- Verilerin sorgulanmasını ve aramasını yapmak

- Silinen verilerin kayıtlarını yeniden oluşturulmasını sağlamak

- Güvenlik ayarları yapmak

- Yeni tablolar oluşturmak

### SQL ile Sorgulama Yapan Yazılımlar

- Oracle SQL: Veritabanı yazılım sistemleri arasında en güçlü olan yazılımdır. Bütün büyük firmalar ve uygulamalarda kullanılabilmektedir.

- Microsoft SQL Server (MSSQL): Sunucu tabanlıdır ve Microsoft tarafından geliştirilmiştir. SQL sistemi kullanarak işlemler yapılmaktadır.

- MySQL: Hem ücretsiz hem de açık kaynaklı olan bir SQL sistemidir. Bu sistemin geliştiricisi Oracle'dır.

- Access: Bu sistem de Microsoft tarafından geliştirilmiştir. Diğer sistemlere göre daha küçük olan uygulamalar için geliştirilmiştir.


## MySQL Kurulumu

Öncelikle [burada belirtilen linkten](https://dev.MySQL.com/downloads/windows/installer/8.0.html) MySQL indirme sayfasına gidiniz. Burada karşınıza iki tane versiyon çıkacaktır. Bir tanesi düşük boyutlu bir tanesi ise yüksek boyutlu olandır. Burada yüksek boyutlu olan dosyanın yanındaki download butonundan dosyayı indiriyorsunuz.

![Image 1](https://i.imgur.com/jw92hvu.png "Yüksek Boyutlu Dosya")

Belirtilen yerden dosyayı indirmeniz uzun sürebilir ancak kurulum aşaması çok daha kısa sürecektir. Dosyayı bilgisayarınıza indirikten sonra açtığınızda karşınıza aşağıdaki gibi bir ekranın çıkması gerekmektedır.

![Image 2](https://i.imgur.com/MnlGyI7.png "Ana Kurulum Ekranı")

Burada "FULL" yazan versiyonu seçmeniz gerekmektedir. FULL versiyonunu seçtikten sonra "NEXT" ile devam edebilirsiniz.

![Image 3](https://i.imgur.com/EM1NjA2.png "Gerekli Programların Kontrolü")

Burada ekran karşınıza çıktığında "NEXT" ile devam edebilirsiniz. Bilgisiyarınıza Visual Studio yüklü ise bu ekran karşınıza çıkmayacaktır.

![Image 4](https://i.imgur.com/UivalTv.png "VS Hatası")

Next'e tıkladıktan sonra karşınıza bu şekilde bir hata çıkacaktır burada "YES" ifadesine tıklayarak devam ediniz.

![Image 4](https://i.imgur.com/pdDkHJq.png "Execute Ekranı")

Yes ifadesine tıkladıktan sonra karşınıza bu ekranın çıkması gerekmektedir. Bu ekranda "EXECUTE" butonuna tıklayarak yükleme işlemini başlatabilirsiniz.

![Image 4](https://i.imgur.com/XubZnqr.png "Complete")

Bütün yüklemeler tamamlandıktan sonra "NEXT" butonuna tıklayarak işleme devam edebilirsiniz. Daha sonra karşınıza aşağıdaki bir ekran çıkacaktır. Burada da "NEXT" ifadesine tıklayarak işleme devam edebilirsiniz.

![Image 4](https://i.imgur.com/KOmeDst.png "Configure")

Next ile bir sonraki ekrana geçtikten sonra karşınıza aşağıdaki gibi bir ekran çıkacaktır. Burada hiçbir ayarı değiştirmeden "NEXT" ile bir sonraki adıma geçiyoruz.

![Image 4](https://i.imgur.com/J9wZ613.png "Networking")

Bir sonraki adımda da herhangi bir değişiklik yapmadan "NEXT" ile bir sonraki adıma devam ediyoruz.

![Image 4](https://i.imgur.com/0xSGL85.png "Password")

Bu adımda MySQL SERVER için bir adet ROOT parolası belirlemeniz gerekmektedir. MySQL Root Password alanına istediğiniz bir şifreyi giriyorsunuz. Daha sonrasında Repeat Password kısmına da MySQL Root Password kısmına girmiş olduğunuz şifreyi tekrardan giriyorsunuz. Eğer iki şifre birbiri ile aynı ise aşağıdaki "NEXT" butonu aktif olacaktır ve bu butona tıklayarak bir sonraki adıma geçebilirsiniz.

![Image 4](https://i.imgur.com/1LAkZsK.png "Server Name")

Bu adımda da herhengi bir değişiklik yapmadan "NEXT" butonuna tıklayarak işleme devam ediyoruz.

![Image 4](https://i.imgur.com/TNSXnHQ.png "Apply Configure")

Karşımıza çıkan bu adımda "EXECUTE" butonuna tıklayarak belirtmiş olduğumuz ayarların SERVER'a yüklenmesini sağlıyoruz.

![Image 4](https://i.imgur.com/ZALfFuI.png "Apply Configure")

Server ayarlarının kurulumu tamamlanmış oldu şimdi "FINISH" butonuna tıklayarak bir sonraki adıma geçebilirsiniz.

![Image 4](https://i.imgur.com/oXbXWro.png "Product Configure")

Karşımıza çıkan bu ekranda da "NEXT" tuşuna basarak bir sonraki adıma ilerleyebilirsiniz.

![Image 4](https://i.imgur.com/uAMgnpu.png "Router Configure")

Router ayarlarının kurulumu tamamlanmış oldu şimdi "FINISH" butonuna tıklayarak bir sonraki adıma geçebilirsiniz.

![Image 4](https://i.imgur.com/48AFQcn.png "Product Configure")

Karşımıza çıkan bu ekranda da "NEXT" tuşuna basarak bir sonraki adıma ilerleyebilirsiniz.

![Image 4](https://i.imgur.com/45zzIqc.png "Server Check")

Bu adımda daha önceden belirlemiş olduğumuz ROOT şifresini girerek "CHECK" butonuna tıklıyoruz. Girdiğiniz bilgilerin doğru olması durumunda "NEXT" butonu aktif olacaktır. "NEXT" tuşuna tıklayarak bir sonraki adıma geçebilirsiniz.

![Image 4](https://i.imgur.com/jqmdD7R.png "Product Configure")

Karşımıza çıkan bu adımda "EXECUTE" butonuna tıklayarak belirtmiş olduğumuz ayarların SERVER'a yüklenmesini sağlıyoruz.

![Image 4](https://i.imgur.com/yearDIm.png "Product Configure")

Ürün ayarlarının kurulumu tamamlanmış oldu şimdi "FINISH" butonuna tıklayarak bir sonraki adıma geçebilirsiniz.

![Image 4](https://i.imgur.com/LcV6T0N.png "FINISH")

Karşımıza çıkan ekranda "NEXT" butonuna tıklayarak tüm adımları bitirebilirsiniz.

![Image 4](https://i.imgur.com/xhbOVGk.png "FINISH")

Karşımıza çıkan ekranda "FINISH" butonuna tıklayarak kurulumu bitirebilirsiniz. MySQL ve diğer kullanacağımız araçları başarı ile bilgisayarınıza yüklemiş oldunuz.

## Syntax Kullanımı

SQL dilinde kodları büyük küçük harf duyarsız şekilde yazabilirsiniz ancak bu genellikle tercih edilmeyen bir şeydir. Genel olarak SQL dilinde KOMUTLAR BÜYÜK HARFLER, tablo ve sütunlar küçük harfler ile kodlanırlar daha rahat anlaşılabilmesi için.

```SQL
Select * FROM Ogrenciler; # Tercih edilmeyen kullanım
SeLEcT * FROM oGreCilER; # Tercih edilmeyen kullanım

SELECT * FROM ogrenciler # Tercih edilen kullanım
"String değerler tek tırnak veya çift tırnak ile gösterilmelidir"
```
Herkesin kullanmış olduğu yazım kurallarını kullanırsanız hem daha rahat hem de başkaları tarafından daha kolay okunabilir bir kod yazmış olursunuz.

## Database Kodları

#### Database Oluşturma
```SQL
CREATE DATABASE test;
```
Bu kod sayesinde SQL Server'a test adlı bir database oluşturmuş oluyoruz. *__CREATE__* komutunu kullandıktan sonra database oluşturulmuş oluyor. *__CREATE__* komutu sistemi otomatik olarak refreshlemediği için **"SCHEMAS"** alanında oluşturmuş olduğunuz database gözükmeyecektir. **"SCHEMAS"** alanındaki **refresh** tuşuna basmanız gerekmektedir. Eğer Serverda ismi olan bir database oluşturmaya çalışırsanız aşağıdaki gibi bir hata alırsınız bundan dolayı böyle bir hata alıyorsanız mutlaka **"SCHEMAS"** kısmını kontrol ediniz.

![Image 4](https://i.imgur.com/ayFXz2R.png "Error Code: 1007")

#### Database Silme
```SQL
DROP DATABASE test;
```
Bu kod sayesinde SQL Server'da test adlı bir database'i silmiş oluyoruz. **DROP DATABASE** komutu database'i komple silmektedir buna içindeki **tablo ve verilerde dahildir**. Bundan dolayı normal şartlarda asla kullanılmaması gereken bir komuttur. Eğer Serverda ismi olmayan bir database'i silmeye çalışırsanız aşağıdaki gibi bir hata alırsınız bundan dolayı böyle bir hata alıyorsanız mutlaka **"SCHEMAS"** kısmını kontrol ediniz.

![Image 4](https://i.imgur.com/eYVtTF4.png "Error Code: 1008")

#### Database'i Aktif Hale Getirmek
```SQL
USE test;
```
Bu kod sayesinde belirttiğimiz database aktif hale gelir. Aktif hale gelmiş bir database **SCHEMAS** alanında kalın bir hale gelir. Bu sayede database'in içinde bulunan tablo ve verilere ulaşabiliriz.

![Image 4](https://i.imgur.com/CDYqw8Z.png "Error Code: 1008")

#### Tablo Oluşturmak
```SQL
CREATE TABLE test(
  test_sutun INT
);
```
Tablo oluşturmak database oluşturmanın birbirine benzer bir yapıdadır. Ancak tabloları oluştururken tablolarda bulunacak sütünları ve sütünların özelliklerini de belirtmek gerekmektedir.

#### Var Olan Bir Tabloyu Güncellemek
```SQL
ALTER TABLE test ADD yeni_sutun VARCHAR(255);
```
**ALTER TABLE** komutu ile var olan bir tabloyu güncelleyebilirsiniz. Tabloya yeni bir sütun ekleyebilir veya tablodan bir sütun çıkartabilirsiniz.

#### Tablo Silme
```SQL
DROP TABLE test;
```
Bu kod sayesinde database de bulunan test adlı bir tabloyu silmiş oluyoruz. **DROP TABLE** komutu tabloyu komple silmektedir buna içindeki **veriler de dahildir**. Bundan dolayı normal şartlarda asla kullanılmaması gereken bir komuttur.


# Öğrenci Sistemi
```SQL
CREATE DATABASE ogrenci_sistemi;

USE ogrenci_sistemi;

CREATE TABLE ogrenci_bilgileri(
  id INT NOT NULL AUTO_INCREMENT,
  ogrenci_adi VARCHAR(255) NOT NULL,
  ogrenci_numarasi INT NOT NULL,
  kayit_tarihi DATE,
  PRIMARY KEY (id)
);
```
Bu kod sayesinde **ogrenci_bilgileri** adlı bir tablo oluşturduk ve bu tablonun içinde **id** sütunu bulunmakta integer yapıda boş bir değer olamayan ve her yeni kayıtta otomatik olarak artan bir yapısı bulunmaktadır. Yeni bir öğrenci tanımladığınızda sistem id yi otomatik olarak verir siz bir değer girmezsiniz. **ogrenci_adi** adlı bir sütun bulunmakta ve bu karakter yapısında bir sütün ve maksimum 255 karakter girilebilmektedir ve yine bu sütun da boş bırakılamaz. **Ogrenci_numarasi** adlı bir sütun bulunmakta ve buraya öğrencinin numarasının girilmesi gerekmektedir ve boş bırakılamaz. **Kayit_tarihi** adlı bir sütun bulunmakta ve ogrencinin kayıt yaptırdığı tarih girilebilir ancak istenirse boş da bırakılabilir. **PRIMARY KEY** bir tablodaki benzersiz alanı göstermektedir. Hiçbir kayıtta aynı olamayacak alanlardır. Bir kaydın eşleniksiz karşılığıdır.

```SQL
CREATE TABLE dersler(
  id INT NOT NULL AUTO_INCREMENT,
  ders_adi VARCHAR(255) NOT NULL,
  ders_donemi VARCHAR(30) NOT NULL,
  ders_gunu VARCHAR(20),
  PRIMARY KEY (id)
);

CREATE TABLE kayitlar(
  id INT NOT NULL AUTO_INCREMENT,
  ogrenci_id INT NOT NULL,
  ders_id INT NOT NULL,
  vize INT,
  final INT,
  genel INT,
  harf_notu VARCHAR(5),
  PRIMARY KEY (id),
  FOREIGN KEY (ogrenci_id) REFERENCES ogrenci_bilgileri(id),
  FOREIGN KEY (ders_id) REFERENCES dersler(id)
);
```
Burada **dersler** ve **kayitlar** adlı iki tablo oluşturduk. Her tabloya bir adet **PRIMARY KEY** belirledik. **FOREIGN KEY** eğer tablodaki alan aslında başka bir tablo ile ilişkili ise bu ilişkinin belirtilmesi için kullanılmaktadır. Örneğin **FOREIGN KEY (ogrenci_id) REFERENCES ogrenci_bilgileri(id)** kodu **kayitlar** tablosunda bulunan **ogrenci_id** sutunundaki değerlerinin **ogrenci_bilgileri** tablosunda bulunan **id** alanı ile ilişkili olduğunu belirtmek için kullanılmaktadır.  

#### Veri Girişi (INSERT INTO)

```SQL
INSERT INTO ogrenci_bilgileri (ogrenci_adi,ogrenci_numarasi,kayit_tarihi)
VALUES ("Deniz",120101008,"2012.06.12");
```
**INSERT INTO** komutu ile veri girişi işlemi gerçekleştirilmektedir. Kod bloğunda gördüğünüz gibi önce insert into diyerek hangi tablodaki hangi alanlara veri girişinin yapılacağı belirtiliyor sonrasında da values ile değerler tabloya girilmiş oluyor. Tek bir insert into komutu ile birden çok değeri tabloya ekleyebilirsiniz.

```SQL
INSERT INTO ogrenci_bilgileri (ogrenci_adi,ogrenci_numarasi,kayit_tarihi)
VALUES ("Cemre",120101007,"2012.06.15"),("Gizem",120101003,"2012.06.22"),
("Safa",120101011,"2012.07.01"));
```

#### Sorgulama (SELECT * FROM)
```SQL
SELECT * FROM ogrenci_bilgileri;

SELECT * FROM ogrenci_bilgileri LIMIT 2;
```
**SELECT * FROM** Sorgusu bir tabloda bulunan bütün sütünlara ait bilgilere ulaşmanızı sağlamaktadır. SQL sorgulamasının en temel yapı taşı olarak gösterilmektedir. **LIMIT** komutu ise sorgu ilk kaç satırdaki veriyi istediğinizi belirtmektedir. Örnekte kullandığımız **LIMIT 2** sonucunda  karşımıza ilk iki öğrenci çıkmaktadır. Sorgudaki * bütün sütunları anlamına gelmektedir.  

#### İstenilen Sütunların Sorgulanması (SELECT "Sütün Adı" FROM)
```SQL
SELECT ogrenci_adi FROM ogrenci_bilgileri;

SELECT ogrenci_adi, ogrenci_numarasi FROM ogrenci_bilgileri;
```
İlk sorguda **ogrenci_adi** sütunundaki bütün veriler sorgulanmaktadır. İkinci sorguda ise **ogrenci_adi** ve **ogrenci_numarasi** sütunları birlikte sorgulanmaktadır.

#### Sorgudaki Sütun İsimlerine Label Ekleme (AS)
```SQL
SELECT ogrenci_adi AS "Öğrenci Adı" FROM ogrenci_bilgileri;

SELECT ogrenci_adi AS "Öğrenci Adı", ogrenci_numarasi AS "Öğrenci Numarası"
FROM ogrenci_bilgileri;
```
**AS** komutu sorgu sonucundaki sütünların daha okunabilir olması için label ataması yapmak için kullanılmaktadır. **AS** komutu sadece sorgu sonucundaki gösterimi değiştirmektedir, tablo isminde değişiklik **yapmaz**.

#### Sorguyu Sıralama (ORDER BY)
```SQL
SELECT ogrenci_adi AS "Öğrenci Adı" FROM ogrenci_bilgileri
ORDER BY ogrenci_adi;

SELECT ogrenci_adi AS "Öğrenci Adı", ogrenci_numarasi AS "Öğrenci Numarası"
FROM ogrenci_bilgileri ORDER BY ogrenci_numarasi DESC;
```
İstediğiniz bir sütuna göre sıralama yaparak sorgulama işlemi gerçekleştirmeniz mümkündür bunun için **ORDER BY Sütun Adı** komutu kullanılmaktadır. Ters çekilde sıralama yapmak isterseniz ise **Sütun Adından** sonra **DESC** komutunu kullanmanız gerekmektedir.

```SQL
INSERT INTO dersler (ders_adi,ders_donemi,ders_gunu)
VALUES ("İstatistik 1","2012 - 2013 Güz","Çarşamba 13:00"),
("Olasılık 1","2012 - 2013 Güz","Cuma 10:00");

INSERT INTO dersler (ders_adi,ders_donemi)
VALUES ("Regresyon Analizi 1", "2014 - 2015 Güz");

#Yukarıdaki ve Aşağıdaki Kodlar aynıdır.

INSERT INTO dersler (ders_adi,ders_donemi,ders_gunu)
VALUES ("Regresyon Analizi 1", "2014 - 2015 Güz",NULL);
```
**INSERT INTO** komutu ile veri girişi gerçekleştirirken sütün adları kadar veri girmeniz gerekmektedir. Eğer elinizde bir sütunu boş olan veri varsa bunu ayrı bir insert into komutu ile sisteme girmeniz gerekmektedir. Örneğin yukarıdaki örnekte **Regresyon Analizi 1** dersinin **ders_gunu**  bilgisi olmadığı için ayrı bir komut ile eklememiz gerekmektedir ya da boş bırakabilir alanlar için **NULL** değerini girebilirsiniz.

#### Tekrarsız Sorgulama (DISTINCT)

```SQL
INSERT INTO kayitlar (ogrenci_id,ders_id,harf_notu,vize)
VALUES (1,1,"CC",40),(2,1,"DD",35),(3,1,"AA",90),(1,2,"BB",70);

SELECT * FROM kayitlar;
SELECT ders_id FROM kayitlar;
SELECT DISTINCT ders_id FROM kayitlar;
```
**DISTINCT** komutu sütunda bulunan verilerdeki tekrarları sadece 1 kez alarak sorgulama sonucunda getirir.

#### Veri Güncelleme (UPDATE 'Tablo Adı' SET 'Sütun Adı' = 'Değer' WHERE 'Koşul')

```SQL
UPDATE kayitlar SET harf_notu = "CB" WHERE id = 1

SELECT * FROM kayitlar;
```
**UPDATE** sorgularında **WHERE** koşulu kullanmak oldukça önemlidir. Eğer **WHERE** ile koşul yazılmazsa sütundaki bütün değerler belirtilen değer ile değiştirilir. Bu da geri dönüşü olmayan oldukça büyük bir probleme yol açılmasına neden olmaktadır. Bundan dolayı **UPDATE** komutu dikkatli bir şekilde kullanılmalıdır.

#### Koşul Kullanımı (WHERE, LIKE, %, OR, AND, BETWEEN, IS NOT NULL, IS NULL)
```SQL
SELECT * FROM ogrenci_bilgileri WHERE kayit_tarihi > "2012.06.16";

SELECT * FROM ogrenci_bilgileri WHERE ogrenci_adi LIKE '%iz' OR ogrenci_id = 2;
SELECT * FROM kayitlar WHERE ogrenci_id = 1 AND harf_notu = "BB";

SELECT * FROM kayitlar WHERE vize BETWEEN 30 AND 60;
SELECT * FROM dersler WHERE ders_gunu IS NOT NULL;
SELECT * FROM dersler WHERE ders_gunu IS NULL;
```
**WHERE** koşulu tüm sorgulamalarda ve komutlarda kullanılabilmektedir. **%** işareti başlangıçta ve sonda kullanılabilmektedir. **%** işareti her ne olursa olsun anlamına gelirse anlamına gelmektedir.  
**OR** ve **AND** komutu pythondaki gibi çalışmaktadır.   
**BETWEEN** komutu iki değer arasındaki verileri sorgulamak için kullanılmaktadır.   
**IS NOT NULL** sütundaki boş olmayan verileri sorgulamak için, **IS NULL** ise sütundaki boş olan verileri sorgulamak için kullanılır.

#### Veri Silme (DELETE FROM "Tablo Adı" WHERE "Koşul")
```SQL
DELETE dersler WHERE ders_id = 3;
SELECT * FROM dersler;
```
**DELETE** komutunu koşulsuz kullanmak ya hataya neden olacaktır yada tablodaki tüm verilerin silinmesine neden olacaktır. Bundan dolayı **DELETE** komutunu kullanırken koşul belirtmeyi **unutmayın**.

#### Tablo Birleştirerek Sorgulama (Join, Left Join, Right Join, Inner Join)
```SQL
SELECT * FROM ogrenci_bilgileri JOIN kayitlar
ON ogrenci_bilgileri.id = kayitlar.ogrenci_id;

SELECT * FROM ogrenci_bilgileri LEFT JOIN kayitlar
ON ogrenci_bilgileri.id = kayitlar.ogrenci_id;

SELECT * FROM ogrenci_bilgileri RIGHT JOIN kayitlar
ON ogrenci_bilgileri.id = kayitlar.ogrenci_id;

SELECT * FROM kayitlar RIGHT JOIN ogrenci_bilgileri
ON ogrenci_bilgileri.id = kayitlar.ogrenci_id;

SELECT * FROM kayitlar INNER JOIN ogrenci_bilgileri
ON ogrenci_bilgileri.id = kayitlar.ogrenci_id;
```
**JOIN** komutu her iki tablodaki değerlerin tamamını almak için kullanılır. Yukarıdaki örnek ele alındığında ders kaydı bulunmayan öğrenciler ve kayit bulunan ama öğrenci olmayan tüm kayıtlar birleştirilerek sorgulanmış olur.                                                        
**LEFT JOIN** komutunda ise sol tarafta belirtilen tablodaki tüm kayıtlar alınır ancak sağ tarafta belirtilen kayıtlarda ise sadece eşleşme sağlanan kayıtları alır.   
**RIGHT JOIN** komutunda ise sağ tarafta belirtilen tablodaki tüm kayıtlar alınır ancak sol tarafta belirtilen kayıtlarda ise sadece eşleşme sağlanan kayıtları alır.  
**INNER JOIN** komutunda ise sadece eşleşen kayıtlar sorgulanmış olur.

#### Integer Alanlarda İşlemler (AVG, SUM, COUNT)
```SQL
SELECT AVG(vize) FROM kayitlar;

SELECT SUM(vize) FROM kayitlar;

SELECT COUNT(ogrenci_adi) FROM ogrenci_bilgileri;
```
**AVG** komutu integer bir sütunun ortalamasını alarak sorgu sonucunda tek bir sonuç geri döndürür.
**SUM** komutu integer bir sütundaki tüm değerleri toplar ve tek bir sonuç geri döndürür.   
**COUNT** komutu belirtilen sütunda kaç adet kayıt bulundurduğunu geri döndürür.

#### Verileri Gruplandırmak (Group By)
```SQL
Select count(ogrenci_id) FROM kayitlar;

SELECT ogrenci_id, count(ogrenci_id) FROM kayitlar GROUP BY ogrenci_id;

SELECT ogrenci_adi AS "Öğrenci Adı", count(ogrenci_id) AS "Ders Sayısı" FROM kayitlar
JOIN ogrenci_bilgileri
ON ogrenci_bilgileri.id = kayitlar.ogrenci_id  GROUP BY ogrenci_id;

SELECT ogrenci_adi AS "Öğrenci Adı", count(ogrenci_id) AS "Ders Sayısı" FROM kayitlar
RIGHT JOIN ogrenci_bilgileri
ON ogrenci_bilgileri.id = kayitlar.ogrenci_id  GROUP BY ogrenci_id;
```
**GROUP BY** komutu belirtilen sütuna göre grupları birleştirme işlemi gerçekleştirmektedir.

#### HAVING ve WHERE Komutları
```SQL
SELECT ogrenci_adi AS "Öğrenci Adı", count(ogrenci_id) AS "Ders Sayısı" FROM kayitlar
RIGHT JOIN ogrenci_bilgileri
ON ogrenci_bilgileri.id = kayitlar.ogrenci_id  GROUP BY ogrenci_id
HAVING count(ogrenci_id) = 1;

SELECT ogrenci_adi AS "Öğrenci Adı", count(ogrenci_id) AS "Ders Sayısı" FROM kayitlar
RIGHT JOIN ogrenci_bilgileri
ON ogrenci_bilgileri.id = kayitlar.ogrenci_id WHERE ogrenci_adi = "Cemre"
GROUP BY ogrenci_id HAVING count(ogrenci_id) = 1;
```
WHERE komutu Group By yapısından önce kullanılması gereken bir komuttur. Eğer Group By işleminden etkilenen bir koşul yazmak için **HAVING** komutu kullanılmalıdır. HAVING komutu WHERE komutu ile aynı işlemi gerçekleştirmektedir. GROUP BY komutundan etkilenmeyen koşullar için GROUP BY dan önce WHERE komutu kullanılabilir.  
