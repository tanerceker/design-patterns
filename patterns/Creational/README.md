<br/>

# Yaratımsal Tasarım Kalıpları — Creational Design Patterns

Yaratımsal tasarım kalıpları nesne oluşturma sürecine odaklanır. Nesne oluşturma sürecini soyutlarlar ve sistemi nesnelerin nasıl oluşturulduğu, oluşturulduğu ve temsil edildiğinden bağımsız hale getirmeye yardımcı olurlar. Bu kalıplar, nesneleri doğrudan new operatörünü kullanarak oluşturmak yerine, oluşturma mantığını gizleyerek nesneleri oluşturmanın bir yolunu sağlar. Bu, belirli bir kullanım durumu için hangi nesnelerin oluşturulması gerektiğine karar verirken daha fazla esneklik sağlar. Bazı popüler yaratımsal tasarım kalıpları arasında;
Singleton, Abstract Factory, Builder, Factory Method ve Prototype yer alır.

<br/>

<p align="center">
  <img 
  width="85%" 
  title="Creational Design Patterns"
  src="../../images/creational-design-patterns.svg" />
</p>

<br/>

---

<br/>

<br/>

## Yaratımsal Tasarım Kalıpları Nedir?

Nesne yönelimli programlamada (OOP) yaratımsal tasarım kalıpları, nesne yaratma mekanizmalarıyla ilgilenir ve nesneleri duruma uygun bir şekilde yaratmaya çalışır. Nesne yaratmanın temel biçimi tasarım sorunlarına yol açabilir veya tasarıma karmaşıklık katabilir. Yaratımsal tasarım kalıpları, bu nesne yaratma sürecini bir şekilde kontrol ederek bu sorunu çözer.

**İşte beş tür yaratımsal tasarım kalıbı:**

<br/>

### **Singleton**

Bu kalıp, bir sınıfın örneklenmesini kısıtlar ve java sanal makinesinde sınıfın yalnızca bir örneğinin (only one instance) bulunmasını sağlar. Nesneye global bir erişim noktası sağlar. Bu, sistem genelinde eylemleri koordine etmek için tam olarak bir nesneye ihtiyaç duyulduğunda kullanışlıdır.

<br/>

### **Factory Method**

Bu kalıp, örnekleme mantığını (instantiation logic) alt sınıflara (child classes) devretmek için bir yol sağlar. Factory Method kalıbı, nesne oluşturma durumunu Factory Method uygulayan alt sınıflara (subclasses) devreder.

<br/>

### **Abstract Factory**

Bu kalıp, somut sınıflarını (concrete classes) belirtmeden ilgili veya bağımlı nesne aileleri oluşturmak için bir arayüz (interface) sağlar. Somut sınıflarını (Concrete classes) belirtmeden ortak bir temaya sahip bir grup fabrikayı (factories) kapsüller (encapsulate).

<br/>

### **Builder**

Bu kalıp, basit nesneler ve adım adım bir yaklaşım kullanarak karmaşık bir nesne oluşturur. Bu tür bir tasarım kalıbı, bir nesne oluşturmanın en iyi yollarından birini sağladığı için yaratımsal kalıp altında yer alır. Karmaşık bir nesnenin inşası ve temsili için net bir ayrım ve benzersiz bir katman sağlar.

<br/>

### **Prototype**

Bu kalıp, oluşturulacak nesnelerin türü, yeni nesneler üretmek için klonlanan prototip bir örnek tarafından belirlendiğinde kullanılır. Bu kalıp, mevcut nesnenin bir klonunu oluşturmayı söyleyen bir prototip arayüzünün uygulanmasını içerir.

<br/>

Tüm bu durumlarda, sistem daha esnek, uyarlanabilir ve yeniden kullanılabilirdir çünkü uygulamanın sınıflarına bağlı değildir, ancak gerekli arayüzü karşılayan herhangi bir sınıfla çalışabilir. Yaratımsal kalıpların tümü, bu sorumlulukları kapsülleyerek sistem modülerliğini geliştirmenin bir yolunu sağlar.

<br/>

---

<br/>

## Yaratımsal Tasarım Kalıplarına Neden İhtiyacımız Var?

Nesne yaratma sürecini soyutladıkları ve bir sistemi nesnelerinin nasıl yaratıldığı, birleştirildiği ve temsil edildiğinden bağımsız hale getirmeye yardımcı oldukları için yaratımsal tasarım kalıplarına ihtiyaç duyulur. Daha basit bir ifadeyle, sistemin hangi sınıfları kullandığına dair bilgiyi kapsüllemek için bir yol sağlarlar.

Yaratımsal tasarım kalıplarını kullanmak istememiz için çeşitli nedenler vardır:

<br/>

### Esneklik ve Yeniden Kullanılabilirlik — Flexibility and Reusability

Yaratımsal kalıplar, nesne yaratımının ne, kim ve ne zaman olacağı konusunda sistemi daha esnek hale getirir. Sistemlerin, çok az değişiklikle veya hiç değişiklik yapmadan yeni parçalar ekleyebileceğiniz değiştirilebilir parçalardan oluşmasına izin verirler. Bu, sistemi yükseltmeyi veya yeni işlevler sağlamak için değiştirmeyi kolaylaştırır.

<br/>

### Soyutlama ve Ayrıştırma — **Abstraction and Decoupling**

Yaratımsal kalıplar, sistemin hangi sınıfları kullandığı ve bu sınıfların nesnelerinin nasıl oluşturulduğu ve bir araya getirildiği hakkındaki bilgileri kapsüller. Bir istemci ile örneklediği somut sınıfları birbirinden ayırmak için bir yol sağlarlar. Ayrıştırma faydalıdır çünkü değişiklikler yapıldığında bozulma olasılığı daha düşük olan daha esnek bir sisteme yol açar.

<br/>

### Nesne Oluşturma Süreci Üzerinde Kontrol

Bazı yaratımsal tasarım kalıpları, nesne yaratma süreci üzerinde daha hassas kontrol sağlayarak, basit kurucularla elde edilemeyen nesne yaratma varyasyonlarını veya özel durumları ele almak için adımlar atmanıza olanak tanır.

<br/>

### Karmaşıklığı Ele Alma

Nesne oluşturma, çok sayıda yapılandırma veya diğer nesnelerin bileşimini içerdiğinde genellikle karmaşık hale gelebilir. Builder veya Factory Method gibi yaratımsal kalıplar, oluşturma sürecini düzenleyerek ve basitleştirerek bu karmaşıklığın yönetilmesine yardımcı olabilir.

<br/>

Genel olarak, yaratımsal tasarım kalıpları, sağlam ve esnek yazılım sistemleri oluşturmak için gerekli olan nesnelerin nasıl oluşturulduğunu yönetmek ve kontrol etmek için kodun yapılandırılmasına yardımcı olur.

<br/>
