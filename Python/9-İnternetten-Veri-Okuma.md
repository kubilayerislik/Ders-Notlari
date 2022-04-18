# İnternetten Veri Okuma

Şimdiye kadar gördüğümüz örneklerde bilgisayarımızda yer alan veri dosyalarını okuduk. Ancak zaman zaman bir internet sayfasında yer alan verileri indirip kullanmamız gerekebilir. İnternetten veri okurken çoğu zaman iligili siteye girip veri dosyalarının linkini kullanarak dosyayı bilgisayarımıza indiririz. Örneğin, bazı finansal verileri günlük olarak indirip analiz ettiğinizi düşünün . Her gün, ilgili internet sitesine gidip dosyaları manuel olarak indirmek sonra Python kodunu çalıştırıp verileri okumak gereksiz zaman kaybına yol açacaktır. Bunun yerine verileri doğrudan Python'dan okuyabiliriz. Bu sayede, sizin yaptığınız çalışmayı daha sonra bir başkasının kontrol etmesi ve aynı çalışmayı tekrarlaması da olasıdır.

Akademik veya profesyonel iş hayatında, yaptığımız çalışmaların tekrar edilebilir olması son derece önemlidir. Bu konuya ülkenizde yeterince önem verilmiyor maalesef. Ancak, çalışmalarınzı, bir başkasının, sizin yazdığınız kodlarla, çalışmanızı, siz olmasanız bile baştan sonra tekrar edebilecek ve aynı ya da benzer sonuçlara ulaşacak şekilde tasarlamanızı öneririm.

İnternette veri bilimi, finans, yapay öğrenme gibi farklı konularda kullanabileceğiniz çok fazla veri setleri mevcuttur. Örneğin, https://archive.ics.uci.edu/ml/index.php adresinde yapay öğrenme çalışmalarında kullanabileceğiniz çok sayıda veri seti bulunmakta. Ya da https://www.quandl.com veya https://finance.yahoo.com gibi sayfalardan finansal verileri temin etmek mümkündür.

## İnternetten Veri Dosyası Okuma

Python'da internetten veri okumak için kullanılabilecek farklı modüller ve fonksiyonlar vardır. Önce, urllib.request modülüne ve bu modüldeki urlretrieve fonksiyonlarına göz atalım. Bu fonksiyon bir internet linkindeki dosyayı bilgisayarımıza aktarmak için kullanılır. Örnek olarak yukarıda verdiğimiz çok sayıda yapay öğrenme veri setinin yer aldığı UCI sitesindeki iris veri setini okuyalım.

```python
>>> from urllib.request import urlretrieve
>>> import pandas as pd

>>> link = "https://archive.ics.uci.edu/ml/machine-learning-databases/iris/iris.data"

>>> urlretrieve(link, "iris.csv") #linkte yer alan dosyayı iris.csv olarak kaydeder.
>>> iris = pd.read_csv("iris.csv", sep=",") #sep argümanı, csv dosyasında sütunların hangi işaretle ayrıldıklarını belirtir.

>>> iris.head()
```

Yukarıdaki yöntemde, ilgili dosyayı önce bilgisaiyarımıza indirmek gerekti. Pandas modülünü kullanarak veri dosyasını indirmeden de veri okuyabiliriz.

```python
>>> import pandas as pd

>>> link = "https://archive.ics.uci.edu/ml/machine-learning-databases/iris/iris.data"

>>> iris = pd.read_csv(link, sep=",")

>>> iris.head()
```

## HTML Verilerini Okuma

Gördüğünüz gibi ikinci yöntemde iki yerine bir satırda istediğimiz işlemi gerçekleştirmiştik. Aynı şekilde, Pandas **.read_excel()** fonksiyonunu kullanarak internette yer alan bir dosyayı, sanki bilgisayarımızdaymış gibi linkini belirterek okuyabiliriz. Bunun için dosya linkini (url) yazmanız yeterlidir.

Şimdiye kadar hep url'den bahsettik. Hepimiz url'nin internet adresi için kullanıldığını biliyoruz. Peki be anlama geliyor url? URL kelimesi **Uniform Resource Locator** kelimlerinin ilk harflerinden oluşuyor. İnternette yer alan her bir dosyanın, fotoğrafın, sayfanın yeri standart formattaki url adresi sayesinde belirlenir. URL adresi dendiğinde aklımıza en çok internet sayfaları gelir. Ancak, FTP (Dosya Transfer Protokolü) veya Veri Tabanı Erişimleri için de url adresleri kullanılabilir. Bir web sayfasını düşünelim: http://www.kubilayerislik.com/index.html. Bu url adresi üç ana parçadan oluşur. Protocol (http), hostname ya da host adı (www.kubilayerislik.com), ve son olarak sayfa ya da dosya adı (index.html). HTTP "bir kaynaktan dağıtılan ve ortak kullanıma açık olan bilgi sistemleri protokolüdür."

İnternette her türlü veri paylaşımı http yapısı ile gerçekleştirilebilir. Örneğin, Google Chrome, Safari, Internet Expolerer gibi bir program kullnarak herhangi bir internet sayfasıne girdiğimizde, bu sasyfadan veri çekmek istiyoruz. Diğer bir deyişle bu siteye bir veri talebi veya http talebinde bulunuyoruz. Python kullanarak bir siteden veri indirdiğimizde de aynı şekilde http talebinde bulunuyoruz. Bu talebi, yukarıda da gördüğümüz **urlretrieve()** fonksiyonu il gerçekleştiriliz.

Peki bir sayfadan beri talebinde bulunduğumuzda çektiğimiz veri tam olarak ne verisidir? Yukarıda gördüğümüz gibi bir csv veya excel dosyası olabilir. Ancak birçok internet sayfası HTML adı verilen bir dille yazılmış olan dökümanlardır. HTML web sayfaları ve uygulamaları oluşturmak için kullanılan standart metin işaretleme dilidir. CSS ve JavaScript dilleri ile birlikte web sayfaları oluşturmak için kullanılır. HTML parçaları, bir internet sayfasının yapıtaşlarını (başlıklar, paragraflar, cümleler, bölümler vb.) oluşturur. İşte, bir sayfadan veri talebinde bulunduğumuzda bu html parçalarına ilişkin verileri çekmiş oluruz.

Burada, HTML verilerinin yapısından bahsetmemiz gerekiyor. Veri türlerini sınıflandırmanın bir yolu yapılandırılmış veri ve yapılandırılmamış veri şeklinde ayırmaktır. Yapılandırılmış veriler, tanımlanmış bir modele sahip olan ya da belirli bir biçiçmde organize edilmiş olan verilerdir. Örneğin, SQL verileri ya da excel dosyaları yapılandırılmış türde verilerdir. Belirli bir veri modeli biçimi vb. olmayan veri türleri ise yapılandırılmamış verilerdir. Örneğin, Twitter veya Facebook gibi sosyal medya sayfalarında kullanıcıların yazdıkları yapılandırılmamış verilerdir.

HTML verileri hem yapılandırılmış hem de yapılandırılmamış veriler olarak düşünülebilir. Bir html dosyası çeşitli metinlerden oluşur. Ancak, bu metinler çeşitli etiketlerle (tag) birbirinden ayrılır. Örneğin, bir yazının başık olduğunu belirtmek için <head> Başlık </head> şeklinde iki başlık etiketinin içinde yazmak gerekir. Benzer şekilde, paragraf için <p></p>, başka bir web sayfasına link vermek için <a></a>, fotoğraf için <img></img> gibi çeşitli etiketler kullanılır.

Şimdi bir internet sayfasında html verisi çekmek için gerekli kodları adım adım görelim.
Önce, urllib modülünden, gerekli fonksiyonları aktarıyoruz ve veri çekmek isteiğimiz sayfayı tanımlıyoruz.

```python
>>> from urllib.request import urlopen, Request
>>> sayfa = "https://data.nasdaq.com/"
```

Sonraki adımda web sayfasına **Request()** ile beri talebi gönderiyoruz ve gelen yanıtı **urlopen()** fonksiyonu ile kaydediyoruz. Bu kaydettiğimiz urllib modülünde tanımlanmış olan bir cevap nesnesi. Bu nesneyi okumak için de **.read()** metodunu kullanıyoruz. Böylece veri çektiğimiz sayfanın html kodunu, metin olarak çekmiş oluyoruz.

```python
>>> from urllib.request import urlopen, Request
>>> sayfa = "https://data.nasdaq.com/"

>>> veri_talebi = Request(sayfa)
>>> gelen_veri = urlopen(veri_talebi)

>>> veri = gelen_veri.read()
```

Son olarak gerçekletirdiğimzi balantıyı kapatmamız gerekiyor.

```python
>>> gelen_veri.close()
```

Veri değişkenini yazdırdğımızda aşağıdaki şekilde sayfanın html kodunu görebiliriz. Fazla yer kaplamaması için buraya çıktının sadece başlangıç kısmı alınmıştır.

```python
b'<!DOCTYPE html>\n<head profile="http://a9.com/-/spec/opensearch/1.1/">\n  <meta name="msvalidate.01" content="82C779DE57BA1BC37AEF2B7FC6D31D04"/>\n\n  <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"/>\n  <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1"/>\n\n  <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=yes"/>\n\n  <meta name="robots" content="index, follow"/>\n\n  <link rel="search" type="application/opensearchdescription+xml" title="Nasdaq Data Link" href="/opensearch.xml"/>\n\n  <link rel="apple-touch-icon-precomposed" href="/images/head/apple-touch-icon.png">\n  <link rel="icon" href="/images/head/apple-touch-icon.png">\n  <link rel="image_src" type="image/jpeg" href="/images/head/ndl-og.jpg">\n\n  <meta property="og:title" content="Nasdaq Data Link">\n  <meta property="og:url" content="https://data.nasdaq.com">\n  <meta property="og:description" content="The source for financial, economic, and alternative datasets, serving investment professionals.">\n  <meta property="og:image" content="https://data.nasdaq.com/images/head/ndl-og.png">\n  <meta property="og:type" content="website">\n\n  <meta name="msvalidate.01" content="9AA8D9E90DBCA4138E42EF9D32B42C01"/>\n  \n\n  <link href="https://data.nasdaq.com/" rel="canonical" />\n\n  \n  <link rel="shortcut icon" type="image/png" href="/assets/favicon-81d3898518937c4c03fc9d11c8044cac20f465279a99c198d25c69a21d4c34f6.png" />\n\n  <script>\n//<![CDATA[\nwindow.gon={};gon.cache={"User":{"current_user":
```

Yukarıdaki yaptığımız için aynısını daha basit bir biçimde, çok yaygın olarak kullanılan Requests paketi ile de gerçekleştirebiliriz. Requests paketini kullanarak önce **.get()** metodu ile ilgili sayfaya bağlanıp verileri çekiyoruz. Sonrasında, **text** metodunu kullanarak çekilen veriyi metne çeviriyoruz.

```python
>>> import requests
>>> sayfa = "https://data.nasdaq.com/"
>>> veri = requests.get(sayfa)
>>> sonuc = veri.text
>>> print(sonuc)

<!DOCTYPE html>
<head profile="http://a9.com/-/spec/opensearch/1.1/">
  <meta name="msvalidate.01" content="82C779DE57BA1BC37AEF2B7FC6D31D04"/>

  <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"/>
  <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1"/>

  <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=yes"/>

  <meta name="robots" content="index, follow"/>

  <link rel="search" type="application/opensearchdescription+xml" title="Nasdaq Data Link" href="/opensearch.xml"/>

  <link rel="apple-touch-icon-precomposed" href="/images/head/apple-touch-icon.png">
  <link rel="icon" href="/images/head/apple-touch-icon.png">
  <link rel="image_src" type="image/jpeg" href="/images/head/ndl-og.jpg">

  <meta property="og:title" content="Nasdaq Data Link">
  <meta property="og:url" content="https://data.nasdaq.com">
  <meta property="og:description" content="The source for financial, economic, and alternative datasets, serving investment professionals.">
  <meta property="og:image" content="https://data.nasdaq.com/images/head/ndl-og.png">
  <meta property="og:type" content="website">

  <meta name="msvalidate.01" content="9AA8D9E90DBCA4138E42EF9D32B42C01"/>
```

Yine sonucu yazdırdığımızda bu defa html kodunun daha düzgün bir şekilde yazdırıldığını görüyoruz. Buraya kadar bir web sayfasından httml verilerini çekmeyi gördük. Ancak yukarıda da gördüğümüz gibi şimdiye kadar yaptıklarımızla verileri sadece düz metin olarak, html etiketleri ile birlikte çekebiliyoruz. Bu format da veri analizi için çok uygun değil. Python kullanarak html verilerini yapılandırılmış bir şekilde çekebilmek için **BeautifulSoup** isimli bir modül geliştirilmiştir.

```python
>>> from bs4 import BeautifulSoup
>>> import requests

>>> sayfa = "https://finance.yahoo.com/"
>>> veri = requests.get(sayfa)
>>> sonuc = veri.text
>>> sonuc_duzgun = BeautifulSoup(sonuc, "html.parser")
>>> print(sonuc_duzgun.prettify())
```

Burada yaptıklarımızın öncekinden farkı, elde ettiğimiz metni, **BeautifulSoup()** fonksiyonunu kullanarak bir BeautifulSoup nesnesine çeviriyoruz. Sonrasında da kullandığımız **.prettify()** metodu, bu nesneyi düzgün, sorgulanabilir bir formata getiriyor. Bu, sadece çektiğimiz html verisini düzgün bir şekilde yazdırmaya yaramıyor. Aynı zamanda, çektiğimiz veriler arasında çeşitli sorgular yapmamıza da olanak sağlıyor.

BeautifulSoup modülünde tanımlanmış, html verilerini sorgulamaya yarayan çok sayıda metod vardır. Ancak bu metodlara örnekler verilmiştir. Tüm örnekleri incelemek isterseniz modülün https://www.crummy.com/software/BeautifulSoup/bs4/doc/ sayfasında yer alan dökümanlara göz atabilirsiniz.

```python
>>> print(sonuc_duzgun.title)

<title>Yahoo Finance - Stock Market Live, Quotes, Business &amp; Finance News</title>

>>> print(sonuc_duzgun.get_text())
Yahoo Finance - Stock Market Live, Quotes, Business & Finance NewsHomeMailNewsFinanceSportsEntertainmentSearchMobileMore...Yahoo FinanceSearchSkip to NavigationSkip to Main ContentSkip to Related ContentSign inMailSign in to view your mailFinance HomeWatchlistsMy PortfolioCryptocurrenciesYahoo Finance PlusScreenersMarketsNewsPersonal FinanceVideosYahoo UIndustriesTechContact UsWe are experiencing some temporary issues. The market data on this page are currently delayed. Please bear with us as we address this and restore your personalized lists.U.S. markets closedS&P 5004,392.59-54.00(-1.21%)Dow 3034,451.23-113.36(-0.33%)Nasdaq13,351.08-292.51(-2.14%)Russell 20002,004.98-20.12(-0.99%)Crude Oil106.54-0.41(-0.38%)Gold1,972.90+2.00(+0.10%)


print(sonuc_duzgun.p)
<p class="P(20px) M(0)"><span>We are experiencing some temporary issues. The market data on this page are currently delayed. Please bear with us as we address this and restore your personalized lists.</span></p>
```

### İnternetten Veri Okuma Örneği: Kripto Paralar

```python
from bs4 import BeautifulSoup
from selenium import webdriver
from datetime import datetime
import pandas as pd
import time


working_time = 0
starting_time = datetime.now()


while (datetime.now()-starting_time).seconds <= 240:
    data = []
    degisken = []
    gozlem = []
    degisken.append("Zaman")
    now = datetime.now()
    current_time = now.strftime("%H:%M:%S")
    gozlem.append(current_time)
    driver = webdriver.Chrome('./chromedriver')
    driver.get("https://finance.yahoo.com/cryptocurrencies/")

    sonuc = BeautifulSoup(driver.page_source, "html.parser")
    driver.close()
    table = sonuc.find("table", attrs={"class": "W(100%)"})
    table_body = table.find("tbody")
    rows = table_body.find_all("tr")
    for row in rows:
        cols = row.find_all("td")
        cols = [ele.text.strip() for ele in cols]
        data.append([ele for ele in cols if ele])

    for para in data:
        degisken.append(para[1])
        gozlem.append(para[2])

    dataframe = pd.DataFrame([gozlem], columns=degisken)

    df = pd.read_excel("kriptolar.xlsx")
    df2 = pd.concat([df, dataframe])
    df2.to_excel("kriptolar.xlsx", index=False)
    time.sleep(30)

```

