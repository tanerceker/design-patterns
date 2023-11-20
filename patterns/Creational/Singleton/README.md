<br/>

# Singleton Kalıbı (Pattern)

Singleton kalıbı, bir sınıfın yalnızca bir örneğe (only one instance) sahip olmasını sağlarken bu örneğe global bir erişim noktası sağlayan bir yaratımsal tasarım kalıbıdır (creational design pattern).

<br/>

![singleton-diagram.svg](images/singleton-diagram.svg)

<br/>

| Diyagram                                                            |
| ------------------------------------------------------------------- |
| **(-)** İşareti o üyenin **private** olduğu anlamına gelir.         |
| **(+)** İşareti o üyenin **public** olduğu anlamına gelir.          |
| **(Altı Çizili Üyeler)** O üyenin **static** olduğu anlamına gelir. |

<br/>

Birden fazla örneğe (instance) sahip olmanın tutarsız veriler veya senkronizasyon sorunları gibi sorunlara yol açabileceği senaryolarda yaygın olarak kullanılır.

---

<br/>

## Singleton Kalıbının Uygulanması (**Implementation**)

Nesne yönelimli programlamada bir Singleton kalıbını uygulamak tipik olarak aşağıdaki adımları içerir:

1. Singleton sınıfında private bir static öznitelik (attribute) bildirin.

2. Singleton nesnesi için global bir erişim noktası olarak public bir static yöntem (genellikle getInstance() olarak adlandırılır) oluşturun. Bu fonksiyon singleton nesnesinin "tembel başlatılmasını" uygular, yani yalnızca ihtiyaç duyulduğunda yeni bir örnek oluşturur.

3. Diğer nesnelerin singleton sınıfıyla new operatörünü kullanmasını önlemek için singleton sınıfının yapıcısını (constructor) private yapın.

4. Sınıfın static yönteminde, singleton örneğinin var olup olmadığını kontrol edin. Varsa, onu döndürün. Eğer yoksa, yeni bir tane oluşturun ve geri döndürün.

<br/>

Typescript'te Singleton kalıbı aşağıdaki gibi uygulanabilir:
<br/>

```tsx
class Singleton {
  // Adım 1: Private bir static örnek bildirin
  private static instance: Singleton;

  // Adım 3: Yapıcıyı (Constructor) private yapın
  private constructor() {}

  // Adım 2: Bir public static getInstance yöntemi oluşturun
  public static getInstance(): Singleton {
    // Adım 4: Singleton örneğinin var olup olmadığını kontrol edin.
    // Varsa, onu döndürün. Eğer yoksa, yeni bir tane oluşturun ve geri döndürün.
    if (!Singleton.instance) {
      Singleton.instance = new Singleton();
    }
    return Singleton.instance;
  }

  public someMethod(): void {
    console.log("Hello, I am a singleton!");
  }
}

// Kullanım
const instance1 = Singleton.getInstance();
const instance2 = Singleton.getInstance();

instance1.someMethod(); // 'Hello, I am a singleton!'
instance2.someMethod(); // 'Hello, I am a singleton!'

console.log(instance1 === instance2); // true
```

<br/>

Yukarıdaki kodda:

- Singleton sınıfı, örnek özniteliğinde (instance attribute) saklanan tek oluşturulmuş örneğe (instance) static bir referans tutar.

- getInstance() yöntemi, singleton örneği (instance) için global erişim noktasıdır. Henüz başlatılmamışsa Singleton örneğini başlatır ve oluşturulan örneğin referansını döndürür.

- Singleton yapıcısı (constructor), new operatörü aracılığıyla başka örneklerin (instances) oluşturulmasını önlemek için private yapılır.

- someMethod(), singleton örneği (instance) üzerinde erişilebilecek bir yöntem örneğidir.

Koddaki son satır (console.log(instance1 === instance2)) Singleton kalıbını doğrular: instance1 ve instance2'nin aynı nesneye atıfta bulunup bulunmadığını kontrol eder, ki bulunurlar, dolayısıyla konsola true değerini kaydeder. Bu, gerçekten de Singleton'ın yalnızca tek bir örneği (only single instance) olduğunu doğrular.

<br/>

---

<br/>

## Singleton Kalıbı Gerçek Dünya Örneği

Singletonlar genellikle sistem genelindeki eylemlerin tek bir merkezi yerden koordine edilmesi gereken durumlarda kullanılır. Böyle bir kullanım durumuna örnek olarak bir günlük hizmeti (logging service) verilebilir.

Günlükleri bir dosyaya yazmak istediğiniz bir uygulama düşünün. Birden fazla örnek (instance) aynı günlük dosyasına yazmaya çalıştığında dosya izinleriyle ilgili sorunları önlemek için, günlüğün yalnızca tek bir örneğinin (only a single instance) oluşturulmasını sağlamak isteyebilirsiniz.

Typescript'te bir Logger singleton:

```tsx
class Logger {
  private static instance: Logger;

  private constructor() {}

  public static getInstance(): Logger {
    if (!Logger.instance) {
      Logger.instance = new Logger();
    }
    return Logger.instance;
  }

  public log(message: string): void {
    const timestamp = new Date();
    console.log(`[${timestamp.toLocaleString()}] - ${message}`);
  }
}

// Kullanım
const logger1 = Logger.getInstance();
logger1.log("First log message");

const logger2 = Logger.getInstance();
logger2.log("Second log message");
```

<br/>

---

<br/>

## Singleton Kalıbı Ne Zaman Kullanılır?

Singleton kalıbının uygun olabileceğini gösteren bazı göstergeler şunlardır:

<br/>

**1. Global Değişkenler (Global Variables):** Sisteminizin birçok farklı bölümü tarafından erişilebilmesi gereken bazı verileri tutmak için global bir değişken kullandığınızı fark ederseniz, Singleton bunu kapsüllemek için uygun bir yol olabilir.
<br/>

**2. Tekrarlanan Başlatma (Repeated Initialization):** Kodunuz aynı şeyin tekrarlanan, pahalı başlatılmasını içeriyorsa (bir dosyadan yapılandırma verilerini okumak, bir veritabanı bağlantısı kurmak gibi), bunu yalnızca bir kez yapmak ve ardından sonucu sisteminizin geri kalanına sağlamak için bir Singleton kullanmak iyi bir fikir olabilir.
<br/>

**3. Çoklu Erişim, Tek Kontrol (Multiple Access, Single Control):** Sisteminizin birkaç parçası veri önbelleği veya sistem genelinde yapılandırma gibi paylaşılan bir kaynağa erişiyor ve potansiyel olarak bu kaynağı değiştiriyorsa, bu kaynağa erişimi kapsüllemek için bir Singleton kalıbının yararlı olacağı bir kod kokusu olabilir.
<br/>

**4. Tekdüze Olmayan Erişim (Non-Uniform Access):** Sisteminiz, sistem genelinde tek tip olmayan veya tutarsız şekillerde erişilen bir varlık içeriyorsa, bu varlığı bir Singleton içine kapsüllemek, kullanımını daha öngörülebilir ve yönetilebilir hale getirebilir.
<br/>

**5. Tekrarlanan Örnekler (Duplicate Instances):** Sisteminizin bir nesnenin birden fazla örneğini oluşturduğunu ve bu örneklerin her birinin aynı olduğunu ve farklı durumları korumadıklarını gözlemlerseniz, Singleton kalıbını düşünmek isteyebilirsiniz. Yazdırma biriktiricisi veya aygıt sürücüsü nesnesi gibi tek bir kontrol noktasına sahip olması gereken bir kaynağı yönetiyorsanız bu durum söz konusu olabilir.
<br/>

**6. Aşırı Parametreler (Excessive Parameters):** Bir nesnenin örneğini sadece derinlemesine iç içe geçmiş bir bileşenin kullanımına sunmak için programınızın birkaç katmanından geçiriyorsanız, bunun nesnenin bir Singleton olabileceğine dair bir işaret olup olmadığını göz önünde bulundurun.

<br/>

Yine, Singleton'ın dezavantajları olduğunu ve mantıklı bir şekilde kullanılması gerektiğini unutmamak çok önemlidir. Kodun test edilmesini zorlaştırabilir ve bir sisteme gereksiz durumsallık ve bağlanma getirebilir. Singleton'a başvurmadan önce hedeflerinize ulaşmak için bağımlılık enjeksiyonu (dependency injection) veya bir hizmet konteyneri (service container) kullanmak gibi başka yollar olup olmadığını her zaman göz önünde bulundurun.

<br/>
