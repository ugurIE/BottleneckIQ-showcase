# BottleneckIQ

<p align="center">
  <img src="bottleneckiq-logo-selected.svg" alt="BottleneckIQ logo" width="420">
</p>

<p align="center">
  <strong>OpenAI Build Week 2026 Katılımcısı</strong>
</p>

## Türkçe

**BottleneckIQ**, depo el terminali veya WMS çıktılarındaki operasyon zamanlarından günlük darboğaz adayını bulan, karar güvenini açıklayan bir endüstri mühendisliği karar destek prototipidir.

> Bu repo public ürün vitrinidir. Skorlama motoru ve uygulama kaynak kodu private tutulmaktadır.

### Nasıl çalışır?

1. Excel/CSV operasyon kayıtları yüklenir ve kolonlar eşleştirilir.
2. Operasyon akışı, deponun gerçek çalışma düzenine göre doğrulanır.
3. Motor global, inbound/outbound ve zaman dilimli sonuçları PDF rapora dönüştürür.

Motor, birden fazla bağımsız operasyon sinyalini birlikte skorlar; kanıtlar çelişirse güven seviyesi düşürülür.

Karar güveni (`High / Medium / Low`), yapısal kanıt ve rapor güvenilirliği ayrı gösterilir. Kanıt zayıfsa sistem kesin bir teşhis veya parasal değer sunmaz.

### Gereken veri

- Operasyon adı ve işlem tarih-saat bilgisi
- Başlangıç + bitiş varsa tercih edilir; tek zaman damgalı milestone kayıtları da desteklenir
- `Staff_ID`, `Unit_Count` ve `Line_Count` isteğe bağlıdır
- Operasyonlar arasında ortak `Order_ID` veya sensör kurulumu gerekmez

### Örnek PDF raporlar

Bu public örnekler yönetici çıktısını gösterir; metrik adları, ham skorlar,
ağırlıklar, eşikler ve hesaplama ayrıntıları paylaşılmaz.

| Örnek | Karar | Gösterdiği davranış |
|---|---|---|
| [High confidence - Picking](sample_high_confidence_picking.pdf) | High / Strong | Net kısıt, saatlik destek ve varsayım olarak etiketlenmiş finansal senaryo |
| [Low confidence - Dengeli akış](sample_low_confidence_balanced.pdf) | Low / Weak | Yeterli veri olsa da operasyonlar ayrışmıyor; kesin teşhis ve finansal değer yok |
| [Low confidence - Sınırlı veri](sample_low_confidence_limited_data.pdf) | Low / Weak | Örneklem küçük; sonuç yalnızca aday olarak gösteriliyor |

Raporlardaki veriler sentetiktir ve yalnızca ürün davranışını göstermek için hazırlanmıştır.

### Doğrulama

- **222 / 222** çakışmayan otomatik kontrol geçti
- 112 senaryoluk geniş depo matrisi ve 33 adversarial kontrol dahil
- Halka açık gerçek WMS logunda **767.723 seçili event** incelendi
- Bağımsız analitik çapraz kontrolle sıra korelasyonu: **1.000**

[Doğrulama kapsamı ve sınırlar](validation_summary.md)

Sentetik testler ve implementasyon uyumu saha doğruluk yüzdesi değildir. Müdahale öncesi/sonrası ölçümlü ilk depo pilotu planlanmaktadır.

**Teknoloji:** Python, Streamlit, pandas, NumPy, Matplotlib, Altair<br>
**İletişim:** freshhcan@gmail.com

---

## English

<p align="center">
  <strong>OpenAI Build Week 2026 Participant</strong>
</p>

**BottleneckIQ** is an Industrial Engineering decision-support prototype that identifies the daily warehouse bottleneck candidate from handheld-terminal or WMS operation timestamps and explains the confidence behind the decision.

> This is the public product showcase. The scoring engine and application source code remain private.

### How it works

1. Upload Excel/CSV operation records and map their columns.
2. Confirm the operational flow against the warehouse's actual working model.
3. The engine exports global, inbound/outbound, and time-sliced findings as a PDF report.

The engine scores multiple independent operational signals together; when the evidence conflicts, the confidence level is reduced.

Decision confidence (`High / Medium / Low`), structural evidence, and report reliability are shown separately. Weak evidence does not become a hard diagnosis or a monetary claim.

### Minimum data

- Operation name and transaction timestamp
- Start + end timestamps are preferred; milestone-only records are supported
- `Staff_ID`, `Unit_Count`, and `Line_Count` are optional
- No shared cross-operation `Order_ID` or sensor installation is required

### Sample PDF reports

These public samples demonstrate the executive output; metric names, raw scores,
weights, thresholds, and calculation details are withheld.

| Sample | Decision | Behavior demonstrated |
|---|---|---|
| [High confidence - Picking](sample_high_confidence_picking.pdf) | High / Strong | Clear constraint, time-sliced support, and explicitly labeled financial scenario |
| [Low confidence - Balanced flow](sample_low_confidence_balanced.pdf) | Low / Weak | Adequate volume but no clear separation; no firm diagnosis or financial value |
| [Low confidence - Limited data](sample_low_confidence_limited_data.pdf) | Low / Weak | Small sample; the result remains a candidate only |

The report data is synthetic and provided only to demonstrate product behavior.

### Validation

- **222 / 222** non-overlapping automated checks passed
- Includes a 112-scenario warehouse matrix and 33 adversarial checks
- **767,723 selected events** evaluated from a public real WMS log
- Independent analytical cross-check rank correlation: **1.000**

[Validation scope and limitations](validation_summary.md)

Synthetic tests and implementation agreement are not a field-accuracy percentage. The first measured warehouse pilot with before/after operational confirmation is planned.

**Stack:** Python, Streamlit, pandas, NumPy, Matplotlib, Altair<br>
**Contact:** freshhcan@gmail.com
