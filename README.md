# Nöbet Planlayıcı

Aylık nöbet listesi hazırlayan, **kurulum gerektirmeyen** tek dosyalık uygulama.
`nobet-planlayici.html` dosyasına çift tıklayın — tarayıcıda açılır, çalışır. Sunucu,
kurulum, eklenti ya da internet bağlantısı gerekmez; iş yeri bilgisayarında yasak
olan hiçbir şeye ihtiyaç duymaz.

Çıktı olarak **gerçek bir `.xlsx`** dosyası üretir (Excel'de "biçim uyuşmuyor"
uyarısı vermez) ve doğrudan **yazdırma / PDF** desteği vardır.

---

## Nöbet düzeni

| Gün türü | Nöbetler | Günlük |
|---|---|---|
| Hafta içi (iş günü) | `01:30–08:30` + `17:30–01:30` | 15 saat |
| Hafta sonu, resmî ve dinî bayram | `08:30–20:30` + `20:30–08:30` | 24 saat |
| Yarım gün (arife) | `13:00–20:30` + `20:30–08:30` | 19,5 saat |

**Her vardiyada birden çok nöbet yeri vardır** (varsayılan **4 görevli**). Görevli
sayısı 1–12 arası ayarlanabilir ve nöbet yerlerine ad verilebilir (*Ana Kapı,
Kule, Devriye, Telsiz* gibi) — bu adlar çizelgenin ve Excel'in kolon başlıkları
olur. Aynı kişi bir vardiyada iki yeri tutamaz.

4 görevliyle bir ay tipik olarak **62 vardiya × 4 = 248 nöbet, ~2.220 saat**
eder. Kişi başı yükün makul kalması için personel sayısının görevli sayısının en
az iki katı olması gerekir; altında kalırsanız uygulama uyarır.

Hafta içi **08:30–17:30** mesai saatlerinde nöbet yoktur. `01:30–08:30` nöbeti
yalnızca **önceki gün normal bir iş günüyse** açılır — çünkü o günün
`17:30–01:30` nöbeti gecenin ilk yarısını zaten kapatmıştır. Böylece ay boyunca
**hiç boşluk ve hiç çakışma kalmaz**; açıkta kalan tek zaman dilimi hafta içi
mesai saatleridir.

**Gece nöbeti:** `20:00–06:00` arasında geçen süre. Vardiya başına:

| Vardiya | Süre | Gece |
|---|---|---|
| `01:30–08:30` | 7,0 sa | 4,5 sa |
| `08:30–20:30` | 12,0 sa | 0,5 sa |
| `13:00–20:30` | 7,5 sa | 0,5 sa |
| `17:30–01:30` | 8,0 sa | 5,5 sa |
| `20:30–08:30` | 12,0 sa | 9,5 sa |

---

## Kullanım

1. **Dönem ve başlık** — ay ve yılı seçin; günler o aya göre kurulur (artık yıl
   dahil). Birim adı başlığa girer:
   *"Deniz Hizmetleri Daire Başkanlığı Ağustos 2026 Ayı Nöbet Listesi"*.
2. **Personel** — tek tek ekleyin ya da **Listeden Yapıştır** ile bir seferde
   aktarın (satır başındaki `1.` / `2)` numaraları otomatik ayıklanır). Kişi
   sayısı serbesttir, sonradan eklenip çıkarılabilir.
3. **Tatiller** — seçilen yılın resmî ve dinî bayramları otomatik yüklenir.
   Eklemek, silmek, adını ve türünü değiştirmek serbesttir.
4. **Planı Oluştur** — dağıtım hesaplanır (birkaç saniye sürebilir).
5. **Excel (.xlsx)** ya da **Yazdır / PDF** ile çıktı alın.

Tüm veriler tarayıcıda saklanır; sekmeyi kapatıp açtığınızda kaldığınız yerden
devam eder. **Yedek Al / Yedek Yükle** ile listeyi dosya olarak taşıyabilir ya da
bir başkasına verebilirsiniz.

### Dengeli dağıtım

Her personele **hem toplam nöbet saati hem gece nöbeti saati** olabildiğince eşit
düşecek şekilde dağıtım yapılır. Ay sonundaki *Kişi Bazlı Toplamlar* tablosunda
kişi başına nöbet sayısı, toplam saat, gece saati, hafta sonu/tatil saati ve
ortalamadan sapma görünür — **her değişiklikte anında güncellenir**.

Vardiya süreleri tam saat katları olmadığı için (7 / 8 / 12 saat) kusursuz
eşitlik matematiksel olarak her zaman mümkün değildir; uygulama ulaşılabilir en
düz dağıtımı arar. 4 görevli ve 24 kişilik bir kadroda tipik sonuç, kişi başı
~92 saatlik bir ayda **2–4 saatlik** bir aralıktır. Kalan farkı **Devir**
alanlarıyla bir sonraki aya taşıyabilirsiniz.

Dağıtım hesabı personel ve görevli sayısına göre **1,5–5 saniye** sürer; bu
sırada "hesaplanıyor" bilgisi görünür.

### Elle düzeltme

- Her hücre bir açılır listedir; kişiyi değiştirdiğinizde hücre **otomatik
  kilitlenir** (turuncu çerçeve) ve *Planı Oluştur*'a bastığınızda korunur.
- 🔒 / 🔓 düğmesiyle bir hücreyi elle kilitleyip açabilirsiniz.
- **İnce Ayar**, kilitli hücrelere dokunmadan geri kalanı yeniden dengeler —
  bayramda üst üste nöbet düşen birini elle taşıdıktan sonra kullanışlıdır.
- **Denetim** panosu çakışma, yetersiz dinlenme, izin ihlali, üst üste nöbet ve
  denge sapmalarını sürekli kontrol eder.

### Köprü günleri ve idari izinler

Bayram ile hafta sonu arasında sıkışan 1–2 iş günü otomatik saptanır ve tatil
listesinin altında tek tuşla eklenebilecek **öneri** olarak çıkar. (Örneğin
29 Ekim Perşembeye denk geldiğinde 30 Ekim Cuma.) Dilediğiniz günü elle de
ekleyebilirsiniz.

### Ayarlar

| Ayar | Ne yapar |
|---|---|
| Her nöbette görevli sayısı | Bir vardiyada kaç kişi nöbet tutacak (varsayılan 4) |
| Nöbet yeri adları | Kolon başlıkları — boş bırakılırsa “1. Nöbetçi, 2. Nöbetçi …” |
| Asgari dinlenme | İki nöbet arasında bırakılacak en az süre (varsayılan 12 saat) |
| Azami üst üste nöbet günü | Kesintisiz nöbet günü sınırı (0 = sınırsız) |
| Gece saati denge ağırlığı | Toplam saat dengesi ile gece saati dengesi arasındaki tercih |
| Devir Sa. / Devir Gece | Önceki aydan devreden fazla/eksik saat (eksi değer girilebilir) |
| İzin Günleri | Nöbet verilmeyecek günler — `3, 7, 12-15` |

Zorunlu hâllerde bile **çakışma** ve **izin günü** ihlal edilmez; sıkışıklıkta
önce kota, en son dinlenme süresi gevşetilir ve durum Denetim panosunda bildirilir.

---

## Çıktılar

Çizelgede **her vardiya kendi satırını** alır; tarih, gün ve gün durumu hücreleri
o günün vardiyaları boyunca dikey olarak birleştirilir. Nöbet yerleri kolonlarda
yer alır.

**Excel** üç sayfa üretir: *Nöbet Listesi* (başlık, gün tipine göre renkli
çizelge, birleştirilmiş tarih hücreleri, altta iki imza alanı) ve *Özet* (kişi
bazlı toplamlar, sayısal hücreler) ve *Vukuat ve İmza* (aşağıda). Başlık satırı donuk, her sayfada yinelenir,
sayfaya sığdırılmış olarak gelir; 4+ görevlide yatay sayfa düzenine geçer.

Excel'in *Vardiya* sütununda yalnızca **saat aralığı** yazar.

**Yazdır / PDF** ile bir ay tek A4 sayfaya, imza alanlarıyla birlikte sığar;
özet tablosu ayrı sayfaya geçer.

### Vukuat ve İmza Formu

**🖊 Vukuat / İmza Formu** düğmesi, nöbetin tutulduğunu belgeleyen ayrı bir A4
form basar. Her nöbetçi için bir satır: tarih, gün, vardiya saati, nöbet yeri ve
ad soyad hazır basılı gelir; **Vukuat / Açıklama** ve **İmza** hücreleri elle
doldurulmak üzere boş ve yüksek bırakılır. Bir şey olursa kutuya yazılır ve
imzalanır.

Okunur boyutta A4 sayfasına **yaklaşık 20 satır** sığar; günler arasında kalın
ayraç çizgisi vardır. 4 görevliyle bir ay 248 satır, ~13 sayfa eder. Aynı form
Excel'in üçüncü sayfası (*Vukuat ve İmza*) olarak da gelir — böylece isterseniz
Excel'den yazdırabilirsiniz.

İmza alanları **Şube Müdürü** ve **Daire Başkanı** olarak hazır gelir; unvan ve
adları doğrudan sayfada değiştirebilirsiniz — hem Excel'e hem çıktıya geçer.

---

## Dinî bayram tarihleri

Ramazan ve Kurban Bayramı tarihleri **2025–2034** için Diyanet takvimine göre
öngörülmüştür. Bu tarihler resmî ilanla bir gün kayabilir; **kontrol edip
düzeltmeniz önerilir** — tatil listesindeki her kayıt serbestçe değiştirilebilir.

## Teknik not

Tek `.html` dosyası: harici kütüphane, CDN, ağ isteği yok. `.xlsx` dosyası
tarayıcı içinde sıfırdan yazılır (ZIP + CRC32 + SpreadsheetML), bu yüzden Excel
dosyayı uyarı vermeden açar. Test edilen tarayıcılar: Chrome / Edge (Chromium).
