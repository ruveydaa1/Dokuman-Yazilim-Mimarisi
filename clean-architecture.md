# Clean Architecture

Clean Architecture, yazılım projelerinde kodun daha düzenli, sürdürülebilir, test edilebilir ve değişikliklere karşı daha dayanıklı olmasını amaçlayan bir mimari yaklaşımdır. Uygulamanın farklı sorumluluklarını birbirinden ayırarak, iş mantığının kullanılan teknoloji ve dış sistemlerden mümkün olduğunca bağımsız olmasını sağlar.

Bu yaklaşımda uygulama tek bir katman halinde geliştirilmek yerine, farklı sorumluluklara sahip bölümlere ayrılır. Böylece veritabanı, kullanıcı arayüzü veya kullanılan framework gibi dış etkenlerde yapılan değişikliklerin uygulamanın temel iş mantığını doğrudan etkilemesi önlenir.

### Temel Katmanlar

Clean Architecture genellikle aşağıdaki temel katmanlar üzerinden ele alınır:

#### Domain

Uygulamanın temel iş kurallarının ve iş modellerinin bulunduğu katmandır. Entity'ler ve uygulamanın temel kuralları burada yer alır.

Domain katmanı, veritabanı veya belirli bir framework gibi dış teknolojilere bağımlı olmamalıdır. Bu sayede uygulamanın temel iş mantığı farklı teknolojilerle kullanılabilir.

#### Application

Uygulamanın gerçekleştirdiği işlemlerin ve kullanım senaryolarının bulunduğu katmandır. Kullanıcı oluşturma, giriş yapma veya belirli bir işlemin gerçekleştirilmesi gibi uygulama davranışları burada tanımlanabilir.

Application katmanı, iş kurallarını kullanarak uygulamanın ne yapacağını belirler. Ancak işlemlerin nasıl gerçekleştirildiğine ilişkin altyapı detaylarından mümkün olduğunca bağımsız tutulur.

#### Infrastructure

Veritabanı, dış servisler, dosya sistemi, e-posta servisleri ve benzeri teknik işlemlerin bulunduğu katmandır.

Örneğin PostgreSQL bağlantısı, Entity Framework Core kullanımı veya bir dış API ile iletişim gibi işlemler Infrastructure katmanında gerçekleştirilebilir.

#### Presentation

Kullanıcı ile uygulama arasındaki iletişimi sağlayan katmandır. Web API projelerinde Controller'lar bu katmanda yer alabilir.

Presentation katmanı gelen HTTP isteklerini karşılar, gerekli işlemleri Application katmanına iletir ve sonucu kullanıcıya HTTP response olarak döndürür.

### Bağımlılık Kuralı

Clean Architecture'ın en önemli özelliklerinden biri **Dependency Rule (Bağımlılık Kuralı)** olarak adlandırılır.

Temel olarak bağımlılıkların dış katmanlardan iç katmanlara doğru olması amaçlanır. İç katmanlar dış katmanların detaylarını bilmemelidir.

Örneğin iş mantığının doğrudan belirli bir veritabanına veya web framework'üne bağımlı olması yerine, gerekli işlemler soyutlamalar üzerinden gerçekleştirilir.

Bu yaklaşım sayesinde kullanılan veritabanı, framework veya başka bir teknik bileşen değiştirildiğinde uygulamanın temel iş mantığının yeniden yazılması gerekmez.

### Clean Architecture'ın Avantajları

* **Sorumlulukların ayrılması:** Her katman belirli bir göreve odaklanır.
* **Test edilebilirlik:** İş mantığı dış sistemlerden bağımsız olduğu için daha kolay test edilebilir.
* **Bakım kolaylığı:** Kodun hangi bölümünün hangi sorumluluğa sahip olduğu daha kolay anlaşılır.
* **Esneklik:** Veritabanı veya framework gibi teknik bileşenler daha kolay değiştirilebilir.
* **Düşük bağımlılık:** Katmanlar arasındaki bağımlılıkların kontrol altında tutulması sağlanır.
* **Büyüyebilirlik:** Proje büyüdükçe kodun yönetilmesi daha kolay hale gelir.

### Ne Zaman Tercih Edilebilir?

Clean Architecture özellikle uzun süre geliştirilecek, birden fazla geliştiricinin çalıştığı ve zaman içerisinde büyümesi beklenen projelerde tercih edilebilir.

Küçük ve basit uygulamalarda ise bu mimarinin tüm katmanlarını oluşturmak gereksiz bir karmaşıklığa neden olabilir. Bu nedenle kullanılacak mimari, projenin büyüklüğü ve ihtiyaçlarına göre belirlenmelidir.
