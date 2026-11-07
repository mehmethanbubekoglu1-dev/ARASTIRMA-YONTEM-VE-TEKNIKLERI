# ARATIRMA-YONTEM-VE-TEKNIKLERI
EduAI-Analyzer Use Case Diagram Bu diyagramda sistemi kullanan kişi Araştırmacı olarak gösterilmiştir. Araştırmacı,
kullanılacak ikincil veri setini sisteme yükler ve analizi başlatır. Analiz bittikten sonra
istatistiksel özetleri görüntüleyebilir, korelasyon grafiklerini oluşturabilir veya sonuç
raporunu CSV dosyası olarak dışa aktarabilir.
Sistem, dışarıdan API yerine indirilmiş veri setleri ile çalışır. Analizi başlatma işlemi; verinin
okunması, eksik verilerin temizlenmesi, değişkenlerin ayrıştırılması ve korelasyonun
hesaplanması gibi alt işlemleri kapsar (include). Tablo/grafik oluşturma ve CSV dışa
aktarma işlemleri ise analiz tamamlandıktan sonra gerçekleştirilir.

EduAI-Analyzer Class Diagram Sınıfların Görevleri
Veri sınıfları
Dataset: Analiz edilecek açık erişimli veri setinin yolunu ve içeriğini tutar.
StudentRecord: Veri setindeki her bir satırı (öğrenciyi) temsil eder. Yapay zeka kullanım
süresi ve ders çalışma saati bilgilerini tutar.
AnalysisResult: Yapılan hesaplamalar sonucunda elde edilen korelasyon katsayısı ve
istatistiksel özet verilerini barındırır.
Veri işleme sınıfları
DataLoader: CSV veya Excel dosyasını okuyarak içeriğini Dataset nesnesine aktarır.
DataCleaner: Veri setindeki eksik veya hatalı girişleri filtreleyerek StudentRecord
nesnelerini oluşturur.
Analiz ve raporlama sınıfları
CorrelationAnalyzer: Temizlenmiş StudentRecord verilerini alarak istatistiksel ilişkiyi
hesaplar ve AnalysisResult nesnesini üretir.
ReportGenerator: AnalysisResult verilerini kullanarak Pandas tablosu, Matplotlib grafiği ve
CSV çıktısı hazırlar.
Sınıflar Arasındaki İlişkiler
Bir Dataset nesnesi birden fazla StudentRecord içerebilir. DataLoader dosyayı okuyarak
veriyi sisteme dâhil eder ve DataCleaner bu verileri ayrıştırarak StudentRecord nesnelerine
dönüştürür. CorrelationAnalyzer, bu kayıtları kullanarak matematiksel hesaplamaları yapar
ve bir AnalysisResult nesnesi üretir. Son olarak ReportGenerator, bu sonuc nesnesini tablo
ve grafiklere dönüştürür. Böylece okuma, temizleme, analiz ve görselleştirme işlemleri ayrı
sınıflara dağıtılmış olur.

EduAI-Analyzer Activity Diagram 
Etkinlik diyagramı, veri analiz sürecinin hangi sırayla ilerlediğini gösterir. Süreç, veri setinin
analize dâhil edilmesiyle başlar. Sistem dosyayı okur, dosya bulunamazsa veya bozuksa hata
kaydı oluşturulur.
Dosya uygunsa Pandas kullanılarak ayrıştırma ve veri temizleme adımlarına geçilir.
Ardından &#39;Yapay Zeka Kullanım Süresi&#39; ve &#39;Ders Çalışma Süresi&#39; verileri eşleştirilerek
matematiksel korelasyon hesaplanır. Hesaplama sonucunda veriler bir Pandas tablosuna
aktarılır, Matplotlib ile dağılım grafikleri oluşturulur ve sonuçlar karşılaştırmalı olarak
sunulur.
