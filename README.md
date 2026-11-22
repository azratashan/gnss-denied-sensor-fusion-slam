# GNSS-Denied Localization with Multi-Sensor Fusion and SLAM

![Course](https://img.shields.io/badge/Ders-Robot%20Tasar%C4%B1m%C4%B1%20ve%20Uygulamalar%C4%B1-blue)
![Group](https://img.shields.io/badge/Grup-G14-informational)
![Topic](https://img.shields.io/badge/Konu%20No-14-success)
![Domain](https://img.shields.io/badge/Alan-Localization%20%7C%20SLAM%20%7C%20Sensor%20Fusion-orange)
![Status](https://img.shields.io/badge/Durum-Kurulum%20Tamamland%C4%B1-yellow)

**Üniversite:** Bursa Uludağ Üniversitesi — Bilgisayar Mühendisliği  
**Dönem:** 2026–2027 | **Grup ID:** G14 | **Konu No:** 14  

---

## Grup Üyeleri

| Ad Soyad | Öğrenci No | Sorumluluk Alanı | CV |
| :--- | :--- | :--- | :--- |
| Üye 1 | ... | Simülasyon Ortamı, Sensör Modelleri & Entegrasyon | [CV](cv/Uye1_CV.pdf) |
| Üye 2 | ... | EKF / UKF State Estimation & Sensör Füzyonu | [CV](cv/Uye2_CV.pdf) |
| Üye 3 | ... | SLAM, Loop Closure & Haritalama | [CV](cv/Uye3_CV.pdf) |
| Üye 4 | ... | Hata/Belirsizlik Analizi, Deneyler & Raporlama | [CV](cv/Uye4_CV.pdf) |

---

## 1. Amaç, Problem Tanımı ve Kapsam

GNSS sinyalinin bulunmadığı, birbirine benzeyen koridorlara sahip endüstriyel bir yapıda uzun süre gezinen mobil robotlarda tek bir sensöre dayalı konum kestirimi zamanla bozulmaktadır. Bu projede; **teker odometrisi (wheel odometry)**, **ataletsel ölçüm birimi (IMU)** ve **çevresel sensörleri (LiDAR / kamera)** birleştiren bütünleşik bir durum kestirimi (*state estimation*) ve eşzamanlı konumlandırma-haritalama (*SLAM*) sistemi geliştirilecektir.

Proje kapsamında aşağıdaki temel problemler deneysel ve kuramsal olarak incelenecektir:
- **Sürüklenme (Drift):** Tek sensör veya salt odometri kullanımında zamanla biriken konum/yönelim hatası,
- **Yanlış Veri Eşleştirme (False Data Association):** Tekrarlanan endüstriyel koridorlarda algısal belirsizliklerin haritalamaya etkisi,
- **Kısmi Sensör Kaybı (Sensor Dropout):** Sensörlerden birinin geçici olarak devre dışı kalması veya gürültünün artması durumunda kalan kaynakların kestirime etkisi,
- **Global Poz Düzeltmesi ve Belirsizlik:** Döngü kapatma (*loop closure*) anındaki harita/yörünge düzeltmeleri ve tahmin edilen belirsizlik (kovaryans) ile gerçek konum hatası (*ground-truth*) arasındaki tutarlılık.

---

## 2. İş Paketleri

| İş Paketi | Kapsam |
| :--- | :--- |
| **İP-1** | Tekrarlanan koridorlara sahip sanal endüstriyel ortamın ve gürültülü sensör modellerinin kurulması |
| **İP-2** | Çoklu sensör füzyonu (Filtering vs. Smoothing) ve SLAM mimarisinin entegrasyonu |
| **İP-3** | Sensör kaybı, yüksek gürültü, tekrarlanan koridor ve loop closure deney senaryolarının kurgulanması |
| **İP-4** | Ground-truth referans verisiyle karşılaştırmalı performans, kovaryans tutarlılığı ve başarısızlık analizi |
| **İP-5** | Teorik araştırma raporu, mimari dokümantasyon ve nihai sunum |

---

## 3. Yöntemler, Algoritmalar ve Değerlendirme

- **Durum Kestirimi & Optimizasyon:** Bayesian Filtering, Extended Kalman Filter (EKF), Unscented Kalman Filter (UKF), Particle Filter, Factor Graph Optimization
- **Odometri & Haritalama:** Wheel Odometry, IMU, LiDAR / Visual Odometry, Loop Closure
- **Kuramsal & Deneysel Analiz:**
  - *Filtering* ve *Smoothing* yaklaşımlarının kuramsal ve deneysel karşılaştırması
  - Gürültü modeli (*noise model*) varsayımları ve *Observability* analizi
  - **Metrikler:** Absolute Trajectory Error (ATE), Relative Pose Error (RPE) ve kovaryans tutarlılığı (NEES)

---

## 4. Klasör Yapısı

```text
gnss-denied-sensor-fusion-slam/
├── README.md                 # Proje tanıtımı, kurulum, mimari ve ilerleme kaydı
├── cv/                       # Tüm grup üyelerinin PDF formatındaki CV dosyaları
├── src/                      # Kaynak kodlar
│   ├── localization/         # EKF/UKF, Particle Filter, Factor Graph ve SLAM düğümleri
│   ├── sensor_faults/        # Gürültü enjeksiyonu ve kısmi sensör kaybı senaryoları
│   └── evaluation/           # Ground-truth karşılaştırma, ATE/RPE ve belirsizlik analizleri
├── simulation/               # Sanal endüstriyel ortam ve robot yapılandırması
│   ├── worlds/               # Tekrarlanan koridorlar içeren endüstriyel haritalar
│   ├── models/               # Robot ve sensör (IMU, LiDAR, Odometri) tanımları (URDF/SDF)
│   ├── config/               # Filtre ve SLAM parametre dosyaları (.yaml)
│   └── launch/               # Sistemi başlatan launch dosyaları
├── experiments/              # Karşılaştırmalı deney çıktıları, grafikler ve başarısızlık kayıtları
└── docs/                     # Teorik araştırma raporu, sistem mimarisi şemaları ve sunumlar
```

---

## 5. Simülasyon Ortamı ve Çalıştırma

*(Geliştirme aşamasında güncellenecektir.)*

- **Gereksinimler:** Ubuntu Linux, ROS / ROS 2, Gazebo, RViz, Python / C++
- **Kurulum ve Çalıştırma:**
```bash
git clone [https://github.com/azratashan/gnss-denied-sensor-fusion-slam.git](https://github.com/azratashan/gnss-denied-sensor-fusion-slam.git)
cd gnss-denied-sensor-fusion-slam
# Bağımlılık kurulumu, build ve launch komutları geliştirme aşamasında eklenecektir.
```

---

## 6. Sistem Mimarisi, Deneyler ve Sonuçlar

*(Bu bölüm geliştirme sürecinde aşağıdaki çıktılarla doldurulacaktır:)*
- Sistem mimari diyagramı ve sensör veri akışı
- Tek sensör vs. çoklu sensör füzyonu yörünge karşılaştırmaları (*ground-truth* referanslı)
- Loop closure öncesi ve sonrası harita/poz düzeltme sonuçları
- Kısmi sensör kaybı ve yanlış veri eşleştirme başarısızlık analizleri

---

## 7. Sürekli İlerleme Kaydı

| Tarih | Ne Yapıldı? | Mevcut Durum | Sonraki Adım |
| :--- | :--- | :--- | :--- |
| 22.11.2026 | GitHub reposu oluşturuldu, klasör iskeleti ve `README.md` hazırlandı. | Başlangıç kurulumu tamamlandı. | Grup üyelerinin CV'leri `cv/` klasörüne eklenecek ve literatür taramasına başlanacak. |

---

## 8. Kaynaklar

- Thrun, S., Burgard, W., & Fox, D. *Probabilistic Robotics*. MIT Press.
- Barfoot, T. D. *State Estimation for Robotics*. Cambridge University Press.
- *(Proje boyunca faydalanılan makaleler ve kütüphane dokümanları eklenecektir.)*
