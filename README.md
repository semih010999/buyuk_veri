# 🎯 CS2 Aimbot Anomali Tespiti (Makine Öğrenmesi ile Hileli Oyuncu Analizi)

Bu proje, **Counter-Strike 2** (CS2) oyununda hile yapan oyuncuları, özellikle *aimbot* türü hileleri tespit etmek amacıyla makine öğrenmesi ve derin öğrenme teknikleri kullanılarak geliştirilmiştir.

## 📌 Proje Özeti

Oyun içindeki oyuncu davranışları (crosshair hareketleri, ateş etme zamanlaması vb.) analiz edilerek, bu davranışların insan doğasına uygun olup olmadığı değerlendirilmiş ve hileli davranışları tespit etmek için bir model oluşturulmuştur.

> Bu analizde kullanılan veriler, CSGO'dan alınmış olsa da CS2'nin temel dinamikleriyle benzerlik gösterdiğinden geçerli kabul edilmiştir.

## 🎯 Amaçlar

- Oyuncuların **crosshair** hareketlerini analiz ederek aimbot kullananları tespit etmek.
- **Random Forest**, **LSTM**, ve **XGBoost** algoritmalarıyla anomali tespiti yapmak.
- En başarılı modelin sonuçlarını görselleştirerek bir tahmin arayüzü oluşturmak.

## 📁 Kullanılan Veri Seti

- [CSGO Cheating Dataset (Kaggle)](https://www.kaggle.com/datasets/emstatsl/csgo-cheating-dataset)
- 10.000 temiz oyuncu ve 2.000 hileli oyuncuya ait veriler içeriyor.
- Her oyuncu için 192 zaman adımı boyunca 5 temel özellik:
  - `AttackerDeltaYaw`, `AttackerDeltaPitch`
  - `CrosshairToVictimYaw`, `CrosshairToVictimPitch`
  - `Firing`

## 🧹 Veri Ön İşleme

- Veri dengesizliği göz önünde bulundurularak **class weights** yöntemi kullanılmıştır.
- SMOTE denemeleri sonuç vermediği için vazgeçilmiştir.

## 🧠 Kullanılan Modeller

### 1. Random Forest
- Hiperparametre seçimi: `RandomizedSearchCV`
- `class_weight='balanced'` ile sınıf dengesizliği giderildi.

### 2. LSTM
- Zaman serisi formatında yeniden şekillendirilmiş veri.
- Çift yönlü (Bidirectional) LSTM katmanları ile geçmiş ve gelecek bilgiler kullanıldı.
- Sigmoid aktivasyon ile ikili sınıflandırma.

### 3. XGBoost
- `binary:logistic` hedefiyle ROC AUC metrikli sınıflandırma.

## 📊 Analiz ve Sonuçlar

- **Hileli oyuncuların** hedefe çok hızlı kilitlendiği ve aynı noktaya tekrar tekrar ateş ettiği gözlemlendi.
- **Temiz oyuncular** daha yavaş ve doğal davranış sergilemekte, ateş etme kararları daha değişken.

## 🖥️ Arayüz

Tahmin sistemi, kullanıcının verdiği hareket verileri üzerinden **Random Forest modeli** ile %'lik olasılıkla hileci olup olmadığını tahmin eder.

## 🛠️ Öneriler

### Oyun Geliştiricileri İçin:
- Gerçek zamanlı anomali tespiti
- Eşik değerli karar sistemleri

### Anti-Hile Sistemleri İçin:
- Modellerin sürekli güncellenmesi
- Oyuncu seviyelerine göre ayrı modeller

### Topluluk İçin:
- Topluluk destekli hile bildirim sistemi

## 🚀 Katkılar

- Hile ve normal oyuncuların davranışları görselleştirildi.
- Zaman serisi verisi üzerinden davranış temelli analiz sistemi geliştirildi.
- Farklı modeller karşılaştırılarak en uygun yöntem belirlendi.

## 🔭 Gelecek Çalışmalar

- **Transfer learning** ile diğer FPS oyunlarına genelleştirme
- CNN veya Transformer gibi yeni mimarilerin denenmesi
- Gerçek zamanlı testler
- Göz takibi, klavye/fare verisi gibi çoklu veri kaynaklarının entegre edilmesi

## 📚 Kaynaklar

- https://www.kaggle.com/datasets/emstatsl/csgo-cheating-dataset
- https://bo3.gg/tr/articles/best-cs2-cheats
- https://www.faceit.com/en/anti-cheat
