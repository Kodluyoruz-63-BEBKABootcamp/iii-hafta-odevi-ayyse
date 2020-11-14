# .Net kodu nedir ve nasıl derlenir? 

 .NET Framework çatısı farklı dillerin aynı ortamda çalışmasını sağlar. Yani bir projenin bir bölümü VB.NET diğer bölümü C# ile kodlanmış olabilir. .NET Framework barındırdığı ortak dil çalışma zamanı (Common Language Runtime) sayesinde, .NET in deslektediği diler ile yazılmış kodları makine diline çevirerek. Yazılımlarda çoklu dil kullanmaya olanak sağlar. 
 
 Çalışma Zamanı derleyicisi kodları derlerken çeşitli bileşenler kullanır. Bu bileşenler CLR (Common Language Runtime)'e bağlıdır. Bu bileşenlerden bazıları şunlardır:

- **MSIL(Microsoft Intermediate Language) to native compiler:** MSIL kodu makine diline çevirir. 
- **Code Menager:** Kodu uygulayarak kontrol eder. 
- **Garbage Collector:** Objelerin yaşam sürelerini otomatik olarak denetler. 
- **.NET Framework Class Libary Support:** Kodda yer alan classları .NET Framework ile birleşirir. 

Bu saydıklarımız en önemlileridir. Şimdi gelelim çoklu dil kullanımının nasıl gerçekleştiğine. Her kod öncelikle kendine ait derleyicisinde derlenir. Mesela Visual J# ile yazılmış kod önce Visual J# derleyicisinde derlenir. Kendi derleyicisinde derlenen kod MSIL (Microsoft Intermediate Language) ye göre yeniden derlenir. Elde ettiğimiz MSIL kodu kendi başına çalıştırılabilir bir kod değildir. MSIL birtakım özel taşınabilir assembly koddan oluşur. Program çalıştırıldığında MSIL olarak derlenmiş kodu çalıştırılabilir bir kod haline CLR getirir. Bu işlem tüm .NET dilleri için aynı şekilde uygulandığı için .NET dilleri arasında performans farkı yok denecek kadar azdır. Bu yok sayılabilecek farkta dillerin kendi derleyicilerinin performans farklarından doğabilir 

**Derleme Süreci =>** 
C# Kodu -> C# Derleyicisi -> MSIL Derleyicisi -> (Taşınabilir Assembly kod) MSIL Kod 
 
**Çalıştırma Süreci =>** 
MSIL Kod -> CLR(Common Language Runtime) -> Makine Dili 


# Roslyn compiler ne işe yarar? 

Roslyn bize Compiler-as-a-Service(CaaS) sunmaktadır. Derleyici kaynak kodları input olarak alır ve output olarak .net assemly üretirdi. Roslyn’in amacı derleyicinin iç kısmında neler olduğunu geliştiriciye sunmaktır. 

 

# Restful servisler nasıl çalışır? Alternatifleri nelerdir ve nasıl çalışırlar? 

Web servis geliştirmek için günümüzde iki farklı metod kullanılıyor. Bunlardan biri Restful(Representation state transfer) diğeri ise SOAP(Simple Object Access Protocol). 

> Rest standartlarına uygun yazılan web servislerine *restful* servisler denir. 

### REST NEDİR? 

Rest client-server arasında hızlı ve kolay şekilde iletişim kurulmasını sağlayan bir servis yapısıdır. Rest servis yönelimli mimari üzerine oluşturulan yazılımlarda kullanılan bir veri transfer yöntemidir. HTTP üzerinde çalışır. Diğer alternatiflere göre daha basittir, minimum içerikle veri alıp gönderdiği için de daha hızlıdır. Client ve server arasında XML veya JSON verilerini taşıyarak uygulamaların haberleşmesini sağlar. 

### SOAP NEDİR? 

Servis ve istemci arasında taşınan verilerin yani mesajların yapılarını tanımlamaya yönelik bir standartı ifade eder. 

Rest servislerin SOAP’tan avantajlı olduğu en önemli olduğu nokta **JSON** kullanmasıdır. JSON, XML’e göre performans bakımından avantajlıdır. JSON hem daha az yer kaplayarak network’te hem de yapısının basitliğiyle encode/decode (CPU) işlemlerinde daha hızlıdır. 

 

# Extension method nedir? Nasıl yazılır? 

Extension metodlar herhangi bir yeni nesne oluşturmadan, üzerinde işlem yapılan nesne üzerinden çağrılabilen "genişletilmiş" manasına gelen metodlardır. Bu metodları kullanarak hem extra iş yükünden kurtuluruz, hem de sürekli aynı kodları yazmak zorunda kalmayız. Extension metodlar statik metodlar ve statik classlardan oluşur. Fakat referans olarak oluşturduğunuz obje üzerinden çağrılırlar. Extension metodların aldığı ilk parametre, bu metodun hangi nesne üzerinde çalışacağını belirtir. Ve alacağı ilk parametrenin önüne "this" anahtar kelimesi getirilir. Böylece metodun bu nesne üzerinde işlem yapacağı belirtilmiş olur. Extension metodları kullanılan kaynak koda, using anahtar kelimesini kullanarak ekleyince bu metodlar kullanılabilir. 

 

# MVC'nin alternatifleri nelerdir 

- HMVC - Hierarchical Model-View-Controller. 

- MVVM - Model-View-ViewModel. 

- MVP - Model View Presenter. 

- MVA - Model View Adapter. 

- PAC - Presentation Abstraction Control. 

- RMR - Resource-Method-Representation. 

- ADR - Action-Domain-Responder. 

 

 

# Architectural pattern nedir? Neden ihtiyaç duyuyoruz? 

Mimari desenler, yazılım mühendisliğindeki mimari sorunlara çözümler öneren yazılım desenleridir. Bir mimari desen, yazılım sistemi için alt sistemlerden ve bunların sorumluluklarıyla iç ilişkilerinden meydana gelen temel ve yapısal bir organizasyon şemasını ifade eder 

Yazılım mimarisine ihtiyaç duymamızın en önemli sebeplerinden biri de sistemin karmaşıklığını yönetmek ve bütünlüğünü korumak için pratik bir yapı sunmasıdır. Bunun yanı sıra son derece iyi hazırlanmış bir mimarisi olmadan, yazılan sistem üzerine gelecek yeni yazılımları ve teknolojileri kabul etmez. 

 

# ViewData, ViewBag, TempData farkları nelerdir? Çalıştığımız proje üzerinde başka bir branch açarak bunları deneyiniz? 

Bu üç asp.net mvc nesnesinin belirgin özelliği küçük boyutlardaki verilerimizi Controller'dan View kısmına aktarmak için kullanırız. 

### ViewData:  

Teknik olarak veri Controller sınıfından View sayfalarına ViewDataDictionary (ViewData) sınıfı ile taşınmaktadır. ViewData nesnesine veri aktarabilir ve bu veriyi okuyabiliriz. 

> ViewData[“CurrentTime”] = DateTime.Now;

  

### ViewBag: 

 ViewBag ise ASP.NET MVC 3 te C# 4 ile gelen dynamic anahtar kelimesinin getirdiği bir yeniliktir. ViewData nın dinamik (run time binding) halidir. Söz dizimi de daha iyidir. 

 > ViewBag.CurrentTime = DateTime.Now;

  

### TempData:  

Bu nesne de diğer ikisinin yaptığı işi yapar.

> TempData[“CurrentTime”] = DateTime.Now;

*Bu üç nesne arasında küçük ve kritik farklar vardır.* 
- Örneğin ViewBag nesnesi dynamic tipinde bir nesne olduğundan bununla alakalı hatalar compile time da değil run time da yakalanır. Teknik anlamda ViewData nesnesinden farkı yoktur. Söz dizim olarak farklıdır. 

- En büyük ve önemli fark TempData ile diğer ikisi arasındadır. ViewData ve ViewBag nesnesi o anki HTTP istek içerisinde geçerlidir. Yaşam döngüsü bir sonraki isteğe kadardır. Ama TempData bir alt HTTP istek içinde geçerlidir. Yaşam döngüsü o anki ve bir sonraki HTTP istek içerinde geçerlidir. 

 
