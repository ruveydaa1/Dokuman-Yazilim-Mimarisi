# Katmanlar ve Sorumlulukları

Katmanlı mimaride uygulama, farklı sorumluluklara sahip katmanlara ayrılır. Her katmanın belirli bir görevi bulunur ve bu görevlerin birbirinden ayrılması, uygulamanın daha düzenli bir şekilde geliştirilmesine yardımcı olur.

Katmanların isimleri ve sayıları kullanılan mimariye göre değişebilir. En yaygın katmanlı yapılardan biri **Presentation, Business, Data Access ve Database** katmanlarından oluşur.

### Presentation Layer

Presentation Layer, uygulamanın kullanıcıya veya dış sistemlere açılan kısmıdır. Kullanıcıdan gelen istekleri karşılar ve işlemlerin sonucunu kullanıcıya iletir.

Web uygulamalarında bu katman genellikle:

* Kullanıcı arayüzlerini,
* API Controller'larını,
* HTTP istek ve cevaplarını

içerebilir.

Presentation Layer'ın temel görevi iş mantığını gerçekleştirmek değil, gelen isteği uygun katmana iletmek ve sonucu geri döndürmektir.

Örneğin bir kullanıcı giriş yapmak istediğinde, giriş isteği öncelikle Presentation Layer tarafından karşılanır.

***

### Business Layer

Business Layer, uygulamanın **iş kurallarının ve uygulamaya özgü işlemlerin** bulunduğu katmandır.

Örneğin:

* Kullanıcı bilgilerinin doğrulanması,
* Yetki kontrollerinin yapılması,
* Sipariş oluşturma kuralları,
* Ödeme işlemleri,
* Bir işlemin gerçekleştirilmesi için gerekli kontroller

gibi işlemler bu katmanda gerçekleştirilebilir.

Bu katman, uygulamanın "hangi koşulda ne yapması gerektiğini" belirler.

Örneğin bir kullanıcının yalnızca aktif bir hesabı varsa sisteme giriş yapabilmesi bir iş kuralı olarak Business Layer içerisinde uygulanabilir.

***

### Data Access Layer

Data Access Layer, uygulamanın veritabanı gibi veri kaynaklarıyla iletişim kurmasını sağlayan katmandır.

Bu katmanda:

* Veritabanından veri okuma,
* Veri ekleme,
* Veri güncelleme,
* Veri silme,
* Veritabanı sorgularının çalıştırılması

gibi işlemler gerçekleştirilebilir.

Data Access Layer'ın amacı, uygulamanın geri kalan bölümlerinin verilerin nasıl saklandığını veya veritabanına nasıl erişildiğini doğrudan bilmek zorunda kalmamasıdır.

Örneğin Business Layer bir kullanıcı bilgisine ihtiyaç duyduğunda, veritabanına doğrudan bağlanmak yerine Data Access Layer üzerinden bu bilgiye ulaşabilir.

***

### Database Layer

Database Layer, uygulamanın verilerinin kalıcı olarak saklandığı bölümdür.

Kullanıcılar, roller, ürünler, siparişler veya uygulamanın ihtiyaç duyduğu diğer bilgiler veritabanında saklanabilir.

Bu katmanda PostgreSQL, MySQL, SQL Server veya Oracle gibi farklı veritabanı sistemleri kullanılabilir.

Uygulamanın diğer katmanları veritabanının kendisiyle doğrudan çalışmak yerine, çoğunlukla Data Access Layer üzerinden iletişim kurar.

***

### Katmanların Birlikte Çalışması

Bir kullanıcının bir web uygulamasında işlem gerçekleştirdiği basit bir senaryo şu şekilde ilerleyebilir:

```
Kullanıcı
    ↓
Presentation Layer
    ↓
Business Layer
    ↓
Data Access Layer
    ↓
Database
```

Örneğin kullanıcı bir giriş formu gönderdiğinde:

1. **Presentation Layer** giriş isteğini alır.
2. **Business Layer** giriş bilgilerinin geçerli olup olmadığını kontrol eder.
3. **Data Access Layer** gerekli kullanıcı bilgilerini veritabanından alır.
4. **Database** kayıtlı verileri sağlar.
5. Sonuç tekrar üst katmanlara iletilerek kullanıcıya gönderilir.

Bu yapı sayesinde her katman kendi sorumluluğuna odaklanır ve uygulamadaki görevlerin birbirine karışması önlenir.

> **Not:** Gerçek projelerde bu yapı her zaman birebir aynı şekilde uygulanmaz. Service, Repository, Domain veya Infrastructure gibi ek katmanlar kullanılabilir. Bu nedenle "katmanlı mimari" tek bir sabit klasör yapısından ziyade, sorumlulukların ayrıştırılmasına dayanan genel bir yaklaşımdır.
