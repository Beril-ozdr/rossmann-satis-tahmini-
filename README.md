
# Rossmann Mağaza Satış Tahmini ve Güvenlik Stoku Önerisi

Rossmann mağazalarının günlük satışlarını SQL ve zaman serisi yöntemleriyle tahmin eden, promosyon ve tatil etkisini istatistiksel olarak ölçen ve tahmin aralığından güvenlik stoku miktarı öneren bir veri analizi projesi.

## Amaç

Mağazalarda **stok tükenmesi** (kaçan satış) ve **fire** (fazla stok maliyeti) sorunlarını azaltmak. Bunun için:

1. Günlük satışları basit yöntemlere göre daha doğru tahmin etmek,
2. Promosyon ve tatil günlerinin satışa etkisini istatistiksel olarak ölçmek,
3. Tahmin aralığına dayanarak her mağaza için güvenlik stoku miktarı önermek.

## Veri Seti

[Kaggle - Rossmann Store Sales](https://www.kaggle.com/c/rossmann-store-sales)

| Dosya | İçerik |
|---|---|
| `train.csv` | Mağazaların günlük satışları (2013-01-01 / 2015-07-31) |
| `store.csv` | Mağaza bilgileri (tür, ürün çeşidi, rakip mesafesi, uzun dönem promosyon) |
| `test.csv` | Tahmin edilecek dönem (satış bilgisi yok) |

> Ham veri dosyaları bu depoda yer almaz. Kaggle bağlantısından indirilebilir.

## Proje Aşamaları

- [x] **Aşama 1: Veri temizleme** (`notebooks/01_veri_temizleme.ipynb`)
- [ ] Aşama 2: SQL ile keşifsel analiz
- [ ] Aşama 3: Görselleştirme
- [ ] Aşama 4: Basit referans tahminler
- [ ] Aşama 5: Zaman serisi tahmin modeli
- [ ] Aşama 6: Promosyon ve tatil etkisinin istatistiksel testi
- [ ] Aşama 7: Tahmin aralığı ve güvenlik stoku önerisi
- [ ] Aşama 8: Sonuç ve sunum

## Aşama 1: Veri Temizleme Özeti

Her temizlik kararı ve etkilediği satır sayısı `outputs/temizlik_ozeti.csv` dosyasında yer alır.

| Sorun | Etkilenen | Karar |
|---|---|---|
| Mağaza açık görünüyor ama satış 0 | 54 satır | Silindi |
| Mağaza kapalı günler | 172.817 satır | Modelleme tablosundan çıkarıldı |
| 2014 Temmuz-Aralık kaydı olmayan mağaza | 180 mağaza | Doldurulmadı, raporlandı |
| Aykırı satış değerleri | 1.113 satır | Silinmedi, işaretlendi |
| Rekabet mesafesi eksik | 3 mağaza | Medyanla dolduruldu |
| Rakip açılış tarihi hatalı veya boş | 355 mağaza | Uydurma tarih yazılmadı, işaretlendi |

Temizlik sonrası: **1.115 mağaza, 844.338 satır, eksik değer yok.**

## Klasör Yapısı

```
notebooks/   Her aşama için not defteri
outputs/     Özet tablolar ve grafikler
sql/         SQL sorguları (Aşama 2'de eklenecek)
```

## Hazırlayan

Beril Özdizdar - Manisa Celal Bayar Üniversitesi, Büyük Veri Analistliği
