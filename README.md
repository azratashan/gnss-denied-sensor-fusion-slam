# GNSS-Denied Localization with Multi-Sensor Fusion and SLAM

**Ders:** Robot Tasarımı ve Uygulamaları (2026–2027)  
**Grup ID:** G14 | **Konu No:** 14 | **Proje Alanı:** Localization, SLAM & Sensor Fusion  

## Grup Üyeleri

| Ad Soyad | Öğrenci No | Sorumluluk Alanı | CV |
| :--- | :--- | :--- | :--- |
| Üye 1 | ... | Simülasyon Ortamı & Sensör Modelleri | [CV](cvs/Uye1_CV.pdf) |
| Üye 2 | ... | EKF / UKF State Estimation | [CV](cvs/Uye2_CV.pdf) |
| Üye 3 | ... | SLAM & Loop Closure | [CV](cvs/Uye3_CV.pdf) |
| Üye 4 | ... | Hata & Belirsizlik Analizi | [CV](cvs/Uye4_CV.pdf) |
| Üye 5 | ... | Sistem Entegrasyonu & Raporlama | [CV](cvs/Uye5_CV.pdf) |

---

## 1. Amaç, Problem Tanımı ve Kapsam

GNSS sinyalinin bulunmadığı, birbirine benzeyen koridorlara sahip endüstriyel bir yapıda uzun süre gezinen bir mobil robotun; teker odometrisi, IMU ve çevresel sensörleri (LiDAR/kamera) birleştirerek bütünleşik durum kestirimi (state estimation) ve haritalama (SLAM) yapması hedeflenmektedir.

Bu proje kapsamında aşağıdaki problemler deneysel ve kuramsal olarak incelenecektir:
- Tek sensöre dayalı konum kestiriminde zamanla biriken sürüklenme (**drift**),
- Tekrarlanan koridorlarda yanlış veri eşleştirme (**false data association**) riski,
- Kısmi sensör kaybı veya ölçüm koşullarının kötüleşmesi durumunda sistemin davranışı,
- Döngü kapatma (**loop closure**) ile global poz düzeltmesi ve belirsizlik (kovaryans) tahmini ile gerçek konum hatası arasındaki ilişki.

## 2. İş Paketleri

- **İP-1:** Endüstriyel koridor simülasyon ortamının ve gürültülü sensör modellerinin kurulması
- **İP-2:** Çoklu sensör füzyonu (Filtering vs. Smoothing) ve SLAM sisteminin entegrasyonu
- **İP-3:** Sensör kaybı, tekrarlanan koridor ve loop closure deney senaryolarının oluşturulması
- **İP-4:** Ground-truth verisiyle karşılaştırmalı performans ve başarısızlık analizi
- **İP-5:** Teorik araştırma raporu ve nihai dokümantasyon

## 3. Yöntemler ve Algoritmalar

- **Durum Kestirimi ve Optimizasyon:** Bayesian Filtering, Extended Kalman Filter (EKF), Unscented Kalman Filter (UKF), Particle Filter, Factor Graph Optimization
- **Odometri ve Haritalama:** Wheel Odometry, IMU, LiDAR / Visual Odometry, Loop Closure
- **Analiz ve Değerlendirme:** Filtering vs. Smoothing karşılaştırması, gürültü modeli varsayımları, Observability analizi, ATE/RPE hata metrikleri ve kovaryans tutarlılığı

## 4. Klasör Yapısı

```text
gnss-denied-slam/
├── README.md        # Proje tanıtımı, kurulum ve ilerleme kaydı
├── cvs/             # Grup üyelerinin CV dosyaları
├── src/             # Kaynak kodlar (localization, sensor_faults, evaluation)
├── simulation/      # Sanal ortam, robot modelleri, config ve launch dosyaları
├── experiments/     # Karşılaştırmalı deney çıktıları ve grafikler
└── docs/            # Teorik rapor, mimari diyagramlar ve sunumlar
