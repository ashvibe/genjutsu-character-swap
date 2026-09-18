<img width="1102" height="643" alt="image" src="https://github.com/user-attachments/assets/88c5363d-eb76-4b4c-a74c-788959b708cb" /># Genjutsu Character Swap — GitHub Pages Paketi

Basit, tek sayfalık bir site: final videoyu gösterir, indirme butonu verir,
kullanılan promptu gösterir ve kopyalama/indirme butonları sunar. Build
adımı, npm kurulumu veya sunucu gerektirmez — sadece HTML (CSS ve JS sayfanın
içine gömülü).

## İçerik

```text
.
├── index.html                 Tek sayfa — video, prompt, Instagram butonu
├── .nojekyll                  GitHub Pages'in Jekyll işlemesini atlamasını sağlar
├── assets/
│   ├── final-video.mp4        Final video (bu depoya zaten yerleştirildi)
│   ├── poster.jpg             Video yüklenirken gösterilen kapak karesi
│   └── og-image.jpg           Sosyal medya paylaşım önizleme görseli
└── prompts/
    ├── prompt-tr.txt          Türkçe prompt (TXT olarak indirilebilir)
    └── prompt-en.txt          İngilizce prompt (TXT olarak indirilebilir)
```

Video zaten `assets/final-video.mp4` yolunda hazır. Boyutu **6,8 MB**dır (30
saniye, 960×720, H.264) — GitHub'ın tarayıcıdan tek dosya yükleme sınırı olan
25 MiB'nin ve normal repo dosya sınırı olan 100 MiB'nin çok altında.

## Önemli: dosyaları birlikte tut

`index.html` çalışmak için `assets/` ve `prompts/` klasörlerine ihtiyaç
duyar — video ve TXT indirme bağlantıları bu klasörlerdeki dosyalara işaret
eder. **Sadece `index.html` dosyasını tek başına açarsan "dosya bulunamadı"
hatası alırsın.** Bu paketi bir klasöre çıkarttığında hepsini olduğu gibi
bırak, hiçbirini taşıma veya silme.

<img width="883" height="897" alt="image" src="https://github.com/user-attachments/assets/783ced0c-f591-415d-bf0d-4e71f08dc0f2" />


## 1. Yerelde önizleme

Klasörün içinde basit bir yerel sunucu başlat (çift tıklayarak `file://`
üzerinden açmak yerine — bazı tarayıcılar bunu kısıtlayabilir):

```bash
# Python 3 yüklüyse, bu klasörün içindeyken:
python3 -m http.server 8000
# sonra tarayıcıda aç: http://localhost:8000
```

## 2. GitHub'a yükleme

1. GitHub'da yeni bir **Public repository** oluştur.
2. Bu paketin içindeki bütün dosya ve klasörleri (bu README dahil) reponun
   **ana dizinine** yükle — `index.html`, `.nojekyll`, `assets/` ve
   `prompts/` hepsi aynı seviyede olmalı.
3. **Commit changes** ile kaydet.

## 3. GitHub Pages'i etkinleştirme

1. Repo içinde **Settings → Pages** bölümüne gir.
2. **Build and deployment** altında kaynak olarak **Deploy from a branch**
   seç.
3. Branch olarak `main`, klasör olarak `/ (root)` seç.
4. **Save** düğmesine bas.

Site bağlantısı birkaç dakika içinde şu yapıda yayına girer:

```text
https://KULLANICI-ADIN.github.io/REPO-ADI/
```

## 4. Instagram bağlantısını güncelleme

`index.html` içinde iki yerde Instagram bağlantısı var (üstteki buton ve
alttaki footer linki). Şu an `https://instagram.com/ashvibe` olarak ayarlı.
Değiştirmek için dosyada `instagram.com/ashvibe` metnini ara ve kendi
adresinle değiştir — iki `href` de aynı satırda kolayca bulunur.

## 5. Videoyu değiştirmek istersen

Yeni bir video kullanmak istersen, dosyanı `assets/final-video.mp4` yoluna
aynı adla koy (üzerine yaz). Farklı bir dosya adı kullanırsan `index.html`
içindeki `<source src="assets/final-video.mp4" ...>` ve `poster="assets/poster.jpg"`
satırlarını da güncellemen gerekir.

## 6. Promptu düzenleme

Prompt üç yerde bulunur ve üçünün de **aynı metni** içermesi gerekir:

- `prompts/prompt-tr.txt` / `prompts/prompt-en.txt` (indirilebilir dosyalar)
- `index.html` içindeki `<pre id="promptTr">` ve `<pre id="promptEn">`
  blokları (sayfadaki görünüm ve "Kopyala" butonu buradan okur)

`@Image1`, `@Image2` ve `@Image3` etiketlerini olduğu gibi koru.

## Sorun giderme

- **"Dosya bulunamadı" hatası (video veya TXT indirme):** `index.html`
  dosyasını `assets/` ve `prompts/` klasörlerinden ayırmışsındır — hepsini
  aynı klasörde birlikte tut, ya da GitHub Pages üzerinden aç.
- **Video oynamıyor:** `assets/final-video.mp4` dosyasının var olduğunu ve
  adının tam olarak bu şekilde yazıldığını kontrol et (büyük/küçük harf
  duyarlıdır).
- **Kopyalama çalışmıyor:** Sayfa `https://` üzerinden (GitHub Pages) veya
  `http://localhost` üzerinden açılmalı; bazı tarayıcılar `file://`
  üzerinden panoya yazmayı kısıtlar. Buton yine de otomatik olarak eski
  yönteme (metni seçip kopyalama) geçer.

## Not

Bu çalışma bağımsız bir kullanıcı rehberidir; Higgsfield ile bağlantılı
veya sponsorlu değildir. Yalnızca paylaşma hakkına sahip olduğun video ve
görselleri kullan.
