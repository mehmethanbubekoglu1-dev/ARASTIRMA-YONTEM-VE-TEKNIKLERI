# ARATIRMA-YONTEM-VE-TEKNIKLERI
EduAI-Analyzer Use Case Diagram Bu diyagramda sistemi kullanan kişi Araştırmacı olarak gösterilmiştir. Araştırmacı, kullanılacak ikincil veri setini (CSV) sisteme yükler ve analizi başlatır. Analiz bittikten sonra istatistiksel özetleri görüntüleyebilir, korelasyon grafiklerini oluşturabilir veya sonuç raporunu CSV veya JSON dosyası olarak dışa aktarabilir.Sistem, dışarıdan API yerine indirilmiş veri setleri ile çalışır. Analizi başlatma işlemi; verinin okunması, eksik verilerin temizlenmesi, değişkenlerin ayrıştırılması ve Spearman korelasyonunun hesaplanması gibi alt işlemleri kapsar (<<include>>). Tablo/grafik oluşturma ve CSV dışa aktarma işlemleri ise analiz tamamlandıktan sonra gerçekleştirilir.

Etkinlik diyagramı, veri analiz sürecinin hangi sırayla ilerlediğini gösterir. Süreç, veri setinin analize dâhil edilmesiyle başlar. Sistem dosyayı okur, dosya bulunamazsa veya bozuksa hata kaydı oluşturulur.
Dosya uygunsa Pandas kullanılarak ayrıştırma ve veri temizleme adımlarına geçilir. Ardından 'Yapay Zekâ Kullanım Sıklığı' ve 'Haftalık Çalışma Süresi' değişkenleri sayısal sıra kodlarına çevrilip eşleştirilerek Spearman sıra korelasyonu hesaplanır. Hesaplama sonucunda veriler bir Pandas tablosuna aktarılır, Matplotlib ile dağılım ve ortalama grafikleri oluşturulur ve sonuçlar karşılaştırmalı olarak sunulur.

Veri sınıfları
Dataset: Analiz edilecek açık erişimli veri setinin yolunu ve içeriğini (DataFrame) tutar.
StudentRecord: Veri setindeki her bir satırı (anket yanıtını) temsil eder. Haftalık çalışma süresi aralığını (saat/hafta) ve yapay zekâ kullanım sıklığını tutar.
AnalysisResult: Hesaplamalar sonucunda elde edilen Spearman katsayısını (ρ), p-değerini ve grup ortalamalarını barındırır.

Veri işleme sınıfları
DataLoader: CSV veya JSON dosyasını okuyarak içeriğini Dataset nesnesine aktarır.
DataCleaner: Eksik veya hatalı girişleri filtreler, kategorileri sayısal sıra kodlarına çevirir ve StudentRecord nesnelerini oluşturur.Analiz ve raporlama sınıfları
CorrelationAnalyzer: Temizlenmiş StudentRecord verilerini alarak Spearman sıra korelasyonunu hesaplar ve AnalysisResult nesnesini üretir.
ReportGenerator: AnalysisResult verilerini kullanarak Pandas tablosu, Matplotlib grafiği ve CSV/JSON çıktısı hazırlar. 4.2. Sınıflar Arasındaki İlişkiler bir Dataset nesnesi birden fazla StudentRecord içerebilir. DataLoader CSV veya JSON dosyasını okuyarak Dataset nesnesini oluşturur; DataCleaner bu verileri ayrıştırarak StudentRecord nesnelerine dönüştürür. CorrelationAnalyzer, bu kayıtları kullanarak Spearman sıra korelasyonunu hesaplar ve bir AnalysisResult nesnesi üretir. Son olarak ReportGenerator, bu sonuç nesnesini tablo, grafik ve CSV/JSON çıktılarına dönüştürür. Böylece okuma, temizleme, analiz ve görselleştirme işlemleri ayrı sınıflara dağıtılmış olur.

## Ekip katkıları
| Ekip üyesi | Görev / Katkı |
|---|---|
| Mehmethan Bubekoğlu (361526034) | Veri hazırlama (CSV/JSON), hesaplama, grafikler, yorum, README ve GitHub yüklemesi 
