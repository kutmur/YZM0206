# YZM0206 - Lab03 Raporu

## Ogrenci Bilgileri
- Ad Soyad: Halil Ibrahim Kutmur
- Ogrenci Numarasi: 24458667010
- Ders: YZM0206
- Konu: Logistic Regression ve Linear Regression Performans Karsilastirmasi

## 1. Amac
Bu laboratuvarin amaci, ayni ikili siniflandirma problemi uzerinde Logistic Regression ve Linear Regression modellerini egitip performanslarini karsilastirmaktir.

Calismada asagidaki sorulara odaklanilmistir:
- Siniflandirma problemi icin hangi model daha uygundur?
- Linear Regression neden siniflandirma icin sinirlara sahiptir?
- Logistic Regression neden daha tutarli sonuclar verir?

## 2. Veri Seti
- Dosya: `data/Social_Network_Ads.csv`
- Toplam ornek: 400
- Hedef degisken: `Purchased` (0/1)

Kullanilan ozellikler:
- `Age`
- `EstimatedSalary`

Modellemede bilgi tasimadigi icin cikarilan sutunlar:
- `User ID`
- `Gender`

## 3. Veri On Isleme
Notebook icerisinde su adimlar uygulanmistir:
- Veri yukleme ve genel inceleme
- Eksik deger kontrolu
- Ozellik-hedef ayrimi (`X`, `y`)
- Egitim/test bolmesi (`%75 / %25`, `random_state=57`)
- `StandardScaler` ile ozellik olcekleme

## 4. Modeller

### A) Logistic Regression
- `scikit-learn` ile model egitimi
- Test setinde sinif tahmini ve olasilik tahmini
- Accuracy, Precision, Recall, F1-Score ve confusion matrix analizi

Sonuclar:
- Accuracy: `0.8600`
- Precision: `0.8788`
- Recall: `0.7436`
- F1-Score: `0.8056`

### B) Linear Regression (siniflandirmaya zorlanmis)
- Regresyon ciktilari uretildi
- `0.5` threshold ile ciktilar 0/1 sinifina cevrildi
- Ayni metriklerle degerlendirme yapildi

Sonuclar:
- Accuracy: `0.8300`
- Precision: `0.8929`
- Recall: `0.6410`
- F1-Score: `0.7463`

Ek gozlem:
- Linear Regression ham ciktilarinda `100` test tahmininin `19` adedi `[0, 1]` araligi disinda kalmistir.

## 5. Karsilastirma Ozeti
Genel performansta Logistic Regression daha basarili olmustur:
- Accuracy farki: `+0.0300`
- Recall farki: `+0.1026`
- F1-Score farki: `+0.0593`

Precision metriğinde Linear Regression az farkla yuksek gorunse de, siniflandirma acisindan kritik metriklerde (ozellikle recall ve F1) Logistic Regression daha gucludur.

## 6. Sonuc
Bu calisma, siniflandirma problemlerinde model seciminin kritik oldugunu gostermektedir.

- Logistic Regression, sigmoid fonksiyonu ve uygun kayip fonksiyonu (cross-entropy) nedeniyle siniflandirma icin dogrudan uygundur.
- Linear Regression, surekli deger tahmini icin tasarlandigindan siniflandirma icin teorik ve pratik olarak sinirli kalir.

Sonuc olarak bu veri setinde ve problem tipinde Logistic Regression daha dogru ve daha tutarli performans vermistir.

## 7. Dosya Bilgisi
- Notebook: `main.ipynb`
- Latex rapor: `rapor.tex`
- Bu ozet rapor: `README.md`
- Veri: `data/Social_Network_Ads.csv`
- Gorseller: `images/`