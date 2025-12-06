# 📘 Kurumsal Evrak Takip ve E-Fatura Yönetim Sistemi

## 🎯 Projenin Amacı

Bu proje, kurumsal firmaların evrak yönetimi ve e-fatura süreçlerini dijitalleştirmek için geliştirilmiş kapsamlı bir web uygulamasıdır. Geleneksel kağıt tabanlı evrak takip süreçlerinin yarattığı verimsizlikleri, kaybolan belgeleri ve onay süreçlerindeki gecikmeleri ortadan kaldırmayı hedefler.

Firma için bu proje kritik önem taşıyordu çünkü:
- Aylık binlerce faturanın manuel olarak takip edilmesi gerekiyordu
- Onay süreçlerindeki gecikmeler ödeme planlarını olumsuz etkiliyordu
- Farklı departmanlar arası evrak akışında kopukluklar yaşanıyordu
- Yasal gereklilikler nedeniyle faturaların dijital olarak saklanması zorunluydu

Operasyona sağladığı ana katkılar:
- Evrak onay süreçlerini %70 hızlandırarak ödeme döngüsünü optimize etti
- Merkezi dijital arşivleme ile fiziksel depolama maliyetlerini %60 azalttı
- Rol bazlı erişim kontrolü ile veri güvenliğini artırdı
- Gerçek zamanlı bildirimler ile süreç takibini kolaylaştırdı

## 🧩 Kullanılan Teknolojiler

- ASP.NET Core 8.0
- Entity Framework Core
- SQL Server
- SignalR (Gerçek zamanlı bildirimler)
- Bootstrap 5
- jQuery
- DataTables
- DinkToPdf (PDF oluşturma)
- MailKit (E-posta gönderimi)
- EPPlus (Excel dışa aktarım)
- iText7 (PDF işlemleri)

## 👨‍💻 Rolüm ve Katkılarım

### Analiz Sürecinde Yaptıklarım
- Mevcut evrak takip süreçlerini analiz ederek verimsizlikleri tespit ettim
- Departmanlar arası bilgi akışını haritaladım
- Kullanıcı gereksinimlerini belirlemek için stakeholder görüşmeleri yaptım
- Rakip çözümleri analiz ederek fark yaratacak özellikleri belirledim

### Mimari Tasarımı Nasıl Kurguladığım
- Katmanlı mimari (UI, Business, Data, Integration) tasarladım
- Modüler yapı oluşturarak gelecekteki genişletmelere açık sistem kurdum
- Dependency Injection prensiplerini uygulayarak test edilebilirliği artırdım
- Repository Pattern kullanarak veri erişim katmanını soyutladım

### Geliştirdiğim Modüller
- E-Fatura yükleme ve işleme modülü
- Çok seviyeli onay süreci yönetimi
- Rol bazlı yetkilendirme sistemi
- Gerçek zamanlı bildirim altyapısı
- Raporlama ve analiz modülü
- Dosya yönetim sistemi

### Verimlilik/Performans Katkılarım
- Veritabanı sorgularını optimize ederek sayfa yükleme sürelerini %50 azalttım
- Lazy Loading teknikleri ile bellek kullanımını optimize ettim
- Önbellekleme mekanizmaları ile sık kullanılan verilere erişimi hızlandırdım
- Asenkron programlama ile uygulama yanıt süresini iyileştirdim

### Hataları Azaltmak İçin Yazdığım Mekanizmalar
- Kapsamlı validasyon katmanı oluşturdum
- Hata yönetimi ve loglama sistemi geliştirdim
- Transaction yönetimi ile veri tutarlılığını sağladım
- Birim testler yazarak kod kalitesini artırdım

### Projenin Sorumluluğunda Üstlendiğim Bölümler
- Sistem mimarisinin tamamı
- Veritabanı tasarımı ve optimizasyonu
- E-Fatura entegrasyonu
- Güvenlik altyapısı
- Performans optimizasyonları

## 🏗️ Mimari Yapı

Sistem, dört katmanlı bir mimari üzerine kurulmuştur:

1. **UI Katmanı**: Kullanıcı arayüzü, Bootstrap 5 ile responsive tasarım
2. **Business Katmanı**: İş kuralları, validasyonlar ve servis mantığı
3. **Data Katmanı**: Entity Framework Core ile veritabanı işlemleri
4. **Integration Katmanı**: E-Fatura entegrasyonu ve harici servis bağlantıları

E-Fatura entegrasyonu, XML formatındaki faturaları sisteme aktararak otomatik olarak işler. API çağrıları, RESTful prensiplerine uygun olarak tasarlanmıştır. Terminal/B2B/Evrak/Üretim modülleri, birbirinden bağımsız ancak entegre çalışacak şekilde geliştirilmiştir.

Önbellekleme sistemi, sık erişilen verileri (kullanıcı bilgileri, yetkiler, parametreler) bellekte tutarak veritabanı yükünü azaltır.

### 🔶 Mimari Diyagramı

```
[Web UI Layer]
       |
       v
[API Controllers] ---> [Validation] ---> [Business Logic Layer]
       |                               |
       v                               v
[Data Access Layer] ----------> [E-Fatura Integration Layer]
       |
       v
[SQL Server Database]
```

## 🔄 Veri Akışı

### Veri Okuma Akışı:
1. Kullanıcı sisteme kimlik doğrulaması ile giriş yapar
2. Rol bazlı yetkilendirme kontrol edilerek menü ve veri erişimi belirlenir
3. Kullanıcı, evrak listesini veya detaylarını görüntülemek için istek gönderir
4. API katmanı isteği alır ve validasyon kontrollerini yapar
5. Business katmanı iş kurallarını uygular
6. Data katmanı veritabanından ilgili verileri çeker
7. Veriler UI katmanına gönderilerek kullanıcıya sunulur

### Veri İşleme/Kaydetme Akışı:
1. Kullanıcı yeni evrak oluşturur veya mevcut evrakı düzenler
2. Form verileri API katmanına gönderilir
3. Validasyon katmanı veri doğruluğunu kontrol eder
4. Business katmanı iş kurallarını uygular (örn: onay süreci başlatma)
5. Değişiklikler veritabanına kaydedilir
6. İlgili kullanıcılara SignalR üzerinden gerçek zamanlı bildirim gönderilir
7. Gerekirse e-posta bildirimleri tetiklenir
8. İşlem sonucu kullanıcıya geri bildirilir

## 🖼️ Ekran Görselleri İçin Placeholder

Ekran görüntüleri ticari veri içerdiği için paylaşılmamaktadır.
Ancak aşağıdaki alanlara anonim örnek ekran şablonları eklenebilir:
- Evrak listesi ve filtreleme arayüzü
- Evrak detay ve onay ekranları
- Raporlama ve analiz panelleri
- Kullanıcı yönetimi ve yetkilendirme arayüzleri

## 🎥 Demo Video Placeholder

Demo video, ticari veriler kullanmadan hazırlanacaktır.

## 📊 Sonuçlar ve Kazanımlar

Bu proje ile elde edilen somut sonuçlar:

- **Süreç Hızlandırma**: Evrak onay süreçleri ortalama 5 günden 1.5 güne düşerek %70 hızlandı
- **Hata Azaltma**: Manuel veri girişi hataları %85 azaldı
- **Otomasyon**: Fatura işleme süreçleri %90 otomatikleşti
- **Maliyet Tasarrufu**: Fiziksel depolama ve kargo maliyetlerinde yıllık %60 tasarruf sağlandı
- **Verimlilik Artışı**: Çalışanların evrak yönetimine ayırdığı zaman haftalık 8 saatten 2 saate düştü
- **İş Sürekliliği**: Pandemi gibi uzaktan çalışma zorunluluklarında süreçler aksamadan devam etti

E-Fatura entegrasyonu sayesinde firma:
- Yasal fatura saklama yükümlülüklerini eksiksiz yerine getirdi
- Maliyet muhasebesi ve bütçe takibini gerçek zamanlı yapabildi
- Denetim süreçlerinde dijital arşiv sayesinde hızlı raporlama yapabildi
- Tedarikçi ilişkilerini dijital platforma taşıyarak şeffaflığı artırdı

Proje, kurumsal dijital dönüşüm stratejisinin önemli bir parçası haline geldi ve diğer departmanların da dijitalleşme sürecini hızlandırdı.
