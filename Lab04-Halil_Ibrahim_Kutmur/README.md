# YZM0206 — LAB04: Algılayıcılar ve Basit Yapay Sinir Ağları

> Wine veri seti üzerinde MLP tabanlı sınıflandırma deneyleri: veri standardizasyonu, aktivasyon fonksiyonları ve learning rate analizleri.

**Öğrenci:** Halil Ibrahim Kutmur  
**Tarih:** 16 Nisan 2026

---

## 📁 Repo Yapısı

```
├── LAB04_Wine_ANN_Analizi.ipynb   # Ana notebook
├── image/                          # Grafik ve confusion matrix görselleri
├── results/
│   ├── metrics_summary.csv         # Özet metrikler
│   └── metrics_details.json        # Detaylı çıktılar
└── README.md
```

---

## 📊 Veri Seti

[`sklearn.datasets.load_wine()`](https://scikit-learn.org/stable/modules/generated/sklearn.datasets.load_wine.html) kullanılmıştır.

| Özellik | Değer |
|---|---|
| Örnek sayısı | 178 |
| Özellik sayısı | 13 |
| Sınıf sayısı | 3 |
| Eğitim / Test | %80 / %20 (stratified) |

---

## 🧠 Model Mimarisi

Tüm deneylerde ortak temel yapı:

- **Model:** `MLPClassifier`
- **Gizli katman:** `(16,)`
- **Çözücü:** SGD (`momentum=0.9`)
- **Maksimum epoch:** 400
- **`random_state=42`**

İleri yayılım:

$$\hat{y} = \text{softmax}(W_2 \, \phi(W_1 x + b_1) + b_2)$$

---

## 🧪 Deneyler ve Sonuçlar

### 1. Ham Veri ile Eğitim (ReLU, LR=0.001)

Model, özellikler arası ölçek farklılıklarından ciddi biçimde etkilenmiş; neredeyse tüm örnekleri `class_1` olarak tahmin etmiştir.

| Accuracy | F1-macro | Final Loss |
|---|---|---|
| 0.3889 | 0.1867 | 1.0854 |

---

### 2. Standardize Veri ile Eğitim (ReLU, LR=0.001)

`StandardScaler` uygulaması sonrası öğrenme stabilitesi ve doğruluk dramatik biçimde iyileşmiştir.

| | Ham Veri | Standardize |
|---|---|---|
| Accuracy | 0.3889 | **0.9167** |
| F1-macro | 0.1867 | **0.9202** |
| Final Loss | 1.0854 | **0.1253** |

---

### 3. Aktivasyon Fonksiyonu Karşılaştırması (LR=0.001)

Test metrikleri eşit çıkmış, ancak ReLU final loss açısından belirgin şekilde daha iyi performans göstermiştir.

| | Sigmoid | ReLU |
|---|---|---|
| Accuracy | 0.9167 | 0.9167 |
| F1-macro | 0.9202 | 0.9202 |
| Final Loss | 0.6837 | **0.1253** |

---

### 4. Learning Rate Analizi (Standardize, ReLU)

| | LR=1.0 | LR=0.001 | LR=1e-7 |
|---|---|---|---|
| Accuracy | **0.9444** | 0.9167 | 0.5833 |
| F1-macro | **0.9457** | 0.9202 | 0.5805 |
| Final Loss | 0.000063 | 0.1253 | 0.9394 |

- **LR=1.0** → En iyi accuracy/F1, loss sıfıra yakın
- **LR=0.001** → Dengeli ve taşınabilir başlangıç değeri
- **LR=1e-7** → Öğrenme neredeyse gerçekleşmemiş

---

## 📌 Temel Çıkarımlar

- **Veri standardizasyonu** özellik ölçek farklılıklarını gidererek optimizasyonu doğrudan etkiler; uygulanmadan anlamlı sonuç almak güçtür.
- **ReLU**, sigmoid'e kıyasla daha düşük final loss ile daha etkin optimizasyon sağlar.
- **Learning rate** çok küçük seçilirse model yeterince öğrenemez; çok büyük seçilirse kararsızlık riski doğar (bu deneyde LR=1.0 stabil kalmıştır).
- En yüksek performans: **LR=1.0, standardize veri, ReLU** → Accuracy: 0.9444, F1: 0.9457

---

## ⚙️ Kurulum ve Çalıştırma

```bash
# Gerekli kütüphaneler
pip install scikit-learn numpy matplotlib

# Notebook'u aç
jupyter notebook LAB04_Wine_ANN_Analizi.ipynb
```
