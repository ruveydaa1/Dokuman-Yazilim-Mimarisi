# Katmanlı Mimari Nedir ?

Katmanlı mimari (Layered Architecture), bir yazılım uygulamasının farklı sorumluluklara sahip bölümlere (katmanlara) ayrılarak geliştirilmesini sağlayan bir mimari yaklaşımdır. Her katman belirli bir görevi üstlenir ve uygulamanın diğer bölümleriyle belirli kurallar çerçevesinde iletişim kurar.

Bu yaklaşımın temel amacı, uygulamadaki farklı sorumlulukları birbirinden ayırarak kodun daha düzenli, anlaşılır ve sürdürülebilir olmasını sağlamaktır. Böylece bir bölümde yapılan değişikliğin uygulamanın diğer bölümlerini mümkün olduğunca az etkilemesi hedeflenir.

Katmanlı mimaride uygulamanın tamamı tek bir yapı içerisinde geliştirilmek yerine, işlevlerine göre farklı katmanlara ayrılır. Örneğin bir web uygulamasında kullanıcıdan gelen istekleri karşılayan katman, iş kurallarını yöneten katman ve veritabanı ile iletişim kuran katman birbirinden ayrılabilir.

Basit bir katmanlı mimari aşağıdaki şekilde düşünülebilir:

```
Sunum / Presentation
          ↓
İş Mantığı / Business
          ↓
Veri Erişim / Data Access
          ↓
Veritabanı / Database
```

Her katmanın kendine ait bir sorumluluğu bulunur. Kullanıcı arayüzü veya API üzerinden gelen bir istek, ilgili katmanlardan geçerek gerekli işlemlerin gerçekleştirilmesini sağlar.

### Katmanların Birbirinden Ayrılması

Katmanlı mimarinin temel özelliklerinden biri **sorumlulukların ayrılmasıdır (Separation of Concerns)**.

Örneğin bir kullanıcı giriş işlemi ele alındığında:

* Sunum katmanı kullanıcıdan gelen giriş isteğini karşılar.
* İş mantığı katmanı kullanıcı bilgilerinin doğruluğunu kontrol eder.
* Veri erişim katmanı kullanıcı bilgilerini veritabanından alır.
* Veritabanı katmanı bilgilerin fiziksel olarak saklanmasını sağlar.

Bu görevlerin tek bir yerde toplanması yerine farklı katmanlara ayrılması, uygulamanın daha kolay anlaşılmasını ve yönetilmesini sağlar.

### Katmanlar Arasındaki İletişim

Katmanlar genellikle belirli bir sıra içerisinde birbirleriyle iletişim kurar. Üst seviyedeki bir katman, kendisinden daha alt seviyedeki katmanın sunduğu işlemleri kullanabilir.

Örneğin:

```
Controller
    ↓
Business / Service
    ↓
Data Access
    ↓
Database
```

Bu yapı sayesinde kullanıcı isteğinin uygulama içerisinde hangi aşamalardan geçtiği daha kolay takip edilebilir.

Ancak katmanlı mimarinin uygulanış şekli her projede aynı olmak zorunda değildir. Projenin büyüklüğüne, ihtiyaçlarına ve kullanılan teknolojilere göre katmanların sayısı ve isimleri değişebilir.

### Ne Zaman Tercih Edilir?

Katmanlı mimari özellikle birden fazla sorumluluğun bulunduğu orta ve büyük ölçekli uygulamalarda tercih edilebilir. Küçük uygulamalarda ise çok fazla katman oluşturmak gereksiz karmaşıklığa neden olabilir.

Bu nedenle mimari yapı belirlenirken yalnızca belirli bir mimariyi kullanmak yerine, projenin ihtiyaçları ve büyüklüğü dikkate alınmalıdır.
