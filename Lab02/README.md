# YZM0206 - Lab02 Raporu

## Ogrenci Bilgileri
- Ad Soyad: Halil Ibrahim Kutmur
- Ogrenci Numarasi: 24458667010
- Ders: YZM0206
- Konu: Basit ve Coklu Dogrusal Regresyon (CarSales veri seti)

## 1. Amac ve Hazirlik
Bu laboratuvarin amaci, Python kullanarak:
- Basit Dogrusal Regresyon
- Coklu Dogrusal Regresyon

uygulamak ve modelin gradyan inisi surecini CarSales veri seti uzerinde gozlemlemektir.

Hazirlik asamasinda veri seti yuklenmis, eksik deger analizi yapilmis, eksik degerler uygun istatistiklerle doldurulmus ve korelasyon analizi ile modelde kullanilacak degiskenler secilmistir.

Not: Veri dosyasi laboratuvarda `data/car.csv` olarak kullanilmistir.

## 2. Veri On Isleme Adimlari
Notebook icerisinde asagidaki adimlar uygulanmistir:
- Veri setinin ilk/son satirlarinin incelenmesi
- Veri tipi ve eksik deger kontrolu
- Sayisal degiskenler icin ortalama ile eksik deger doldurma
- Kategorik degiskenler icin mod ile eksik deger doldurma
- Korelasyon haritasi (heatmap) olusturma
- Kategorik degiskenleri sayisal hale getirme (one-hot encoding)

## 3. A) Basit Dogrusal Regresyon
Bu bolumde hedef degisken olan `Price_in_thousands` ile mutlak korelasyonu en yuksek tek bagimsiz degisken otomatik olarak secilmistir.

Uygulanan adimlar:
- Tek ozellikli model kurulumu
- Egitim/test bolmesi
- Ozellik standardizasyonu
- Elle yazilmis gradyan inisi algoritmasi ile egitim
- Farkli ogrenme katsayilarinin (learning rate) loss egileriyle karsilastirilmasi

Grafik Alani:
- Basit Regresyon - Learning Rate Etkisi (Loss vs Iterasyon)
- Basit Regresyon - Gercek Veri ve Tahmin Dogrusu

## 4. B) Coklu Dogrusal Regresyon
Bu bolumde hedef degiskenle mutlak korelasyonu en yuksek en az 2 bagimsiz degisken secilerek coklu regresyon modeli kurulmustur.

Uygulanan adimlar:
- En yuksek korelasyonlu 2 ozelligin secilmesi
- Coklu ozellikli model kurulumu
- Gradyan inisi ile egitim (farkli learning rate degerleri)
- Test seti uzerinde MAE, RMSE, R2 metriklerinin hesaplanmasi
- Gercek vs Tahmin dagilim grafigi

Grafik Alani:
- Coklu Regresyon - Learning Rate Etkisi (Loss vs Iterasyon)
- Coklu Regresyon - Gercek vs Tahmin Grafigi

## 5. Ogrenme Katsayisi ve Korelasyon Etkisi
- Cok kucuk ogrenme katsayisi: model yavas yakinlar, daha fazla iterasyon gerekir.
- Uygun ogrenme katsayisi: loss daha hizli ve dengeli azalir.
- Cok buyuk ogrenme katsayisi: dalgalanma veya sapma olusturabilir.

Korelasyon etkisi:
- Hedef degiskenle korelasyonu yuksek ozellikler modele daha anlamli bilgi tasir.
- Coklu regresyonda birden fazla guclu ozelligin birlikte kullanilmasi genellikle tek degiskenli modele gore daha iyi tahmin basarimi verir.

## 6. Sonuc
Bu laboratuvarda basit ve coklu dogrusal regresyon modelleri Python ile uygulanmis, gradyan inisinin farkli ogrenme katsayilarina verdigi tepkiler gozlemlenmistir.
Korelasyon analizinin ozellik seciminde kritik oldugu ve coklu regresyonun uygun degisken secimiyle daha guclu tahmin performansi sundugu gosterilmistir.

## 7. Dosya Bilgisi
- Notebook: `main.ipynb`
- Rapor: `README.md`
- Veri: `data/car.csv`
