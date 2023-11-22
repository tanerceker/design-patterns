<br/>

# Yapısal Tasarım Kalıpları — Structural Design Patterns

Yapısal tasarım kalıpları, sınıfların ve nesnelerin bileşimi (composition) ile ilgilidir. Sınıfları ve nesneleri kullanarak büyük yapılar (large structures) oluşturmaya yardımcı olurken aynı zamanda yapıların ölçeklenebilir (scalable), verimli (efficient) ve sürdürülebilir (maintainable) olmasını sağlarlar.

Bu kalıplar, varlıklar (entities) arasındaki ilişkileri belirleyerek ve bunları uyumlu bir yapı oluşturacak şekilde düzenleyerek tasarımı basitleştirmeye odaklanır. Yapısal tasarım kalıpları, arayüzlerin (interfaces) veya uygulamaların (implementations) bileşimini (composition) sağlayarak yazılım tasarımını kolaylaştırır. Bazı yaygın yapısal tasarım kalıpları arasında; Adapter, Bridge, Composite, Decorator, Facade, Flyweight ve Proxy yer alır.

<br/>

<p align="center">
  <img 
  width="100%" 
  title="Structural Design Patterns"
  src="../../images/structural-design-patterns.svg" />
</p>

<br/>

---

<br/>

## Yapısal Tasarım Kalıpları Nedir?

Yapısal tasarım kalıpları, nesne bileşimi (composition) ve sınıfların ve nesnelerin yapısıyla (structure) ilgilenen bir tasarım kalıbı türüdür. Bir sistemin bir bölümünde değişiklik yapıldığında bunun diğer bölümlerde değişiklik gerektirmemesini sağlamaya yardımcı olurlar. Bu da sistemi daha esnek ve bakımı daha kolay hale getirir.

**İşte yedi tür yapısal tasarım kalıbı:**

<br/>

### Adapter

Uyumsuz arayüzlere sahip sınıfların birlikte çalışmasına izin verir. Kendisini bir nesnenin etrafına sarar ve bu nesneyle etkileşim kurmak için standart bir arayüz sunar.

<br/>

### Bridge

Bir soyutlamayı uygulamasından ayırır, böylece ikisi bağımsız olarak değişebilir. İleriye dönük uyumluluğu zorlayarak gevşek bağlantıyı teşvik eder.

<br/>

### Composite

Karmaşık sistemlerin kullanımını basitleştirmek için kullanılır. Aynı nesne türünün tek bir örneğiyle aynı şekilde ele alınabilecek bir grup nesneyi tanımlar.

<br/>

### Decorator

Mevcut bir nesneye, yapısını değiştirmeden yeni işlevler eklemek için kullanılır. Somut sınıfları (Concrete classes) sarmak için kullanılan bir dizi dekoratör sınıfı (decorator classes) içerdiğinden yapısal bir kalıptır.

<br/>

### Facade

Karmaşık bir alt sisteme basitleştirilmiş bir arayüz sağlar. İstemci kodunun çeşitli alt sistem arayüzleriyle etkileşime girmesini sağlamak yerine, tek bir birleşik arayüz sağlar.

<br/>

### Flyweight

İlgili nesnelerle mümkün olduğunca fazla veri paylaşarak bellek kullanımını en aza indirir. Basit bir tekrarlı gösterimin kabul edilemez miktarda bellek kullanacağı durumlarda nesneleri çok sayıda kullanmanın bir yoludur.

<br/>

### Proxy

Başka bir nesneye erişimi kontrol etmek için bir vekil veya yer tutucu sağlar. Bu kalıp, bir nesnenin erişimine bir tür kontrol dahil etmek istediğimizde kullanılır.

<br/>

Yapısal tasarım kalıpları, bu yapıları esnek ve verimli tutarken, daha büyük yapılar oluşturmak ve yeni işlevsellik sağlamak için farklı nesneleri ve sınıfları birbirine bağlamak için yönergeler sağlar. Sistem mimarisinin iyi yapılandırılmış, ölçeklenebilir ve yönetilebilir olduğundan emin olmak için gereklidirler.

<br/>
