---
name: website
description: >-
  Eski ve demode kurumsal/medikal web sitelerini (orn. livamedical.com) sifirdan
  inceleyip bagli oldugu resmi uretici/distributör sitelerinden (ConvaTec, ANKA Saglik vb.)
  HD urun gorsellerini ve teknik sartnameleri cekme, C#/.NET ile urun fotograflarinin
  beyaz arka planlarini %100 seffaf (transparent PNG) yapip 3B sahnede sergileme,
  imlecle 3B dondurme ve optik buyutec (loupe) studyosu kurma, 2K 3B cift temali
  (Sage & Cobalt) kurumsal amblem logo uretme, Google Stitch MCP + Godly.design
  etkilesim kaliplariyla birlestirme ve GitHub Pages / Vercel uzerinden canliya alma is akisi.
---

# Website — Kurumsal & Medikal Web Yenileme, 3B Ürün Stüdyosu ve Canlı Yayın Rehberi (`website`)

## Overview

`website`, eski veya demode kalmış bir web sitesini (ör. **`http://www.livamedical.com/`**) uçtan uca analiz ederek; bağlı olduğu global ve yerel üretici/partner sitelerinden (**ConvaTec Türkiye**, **ANKA Sağlık / Ankalaps**, **Euroresearch / Bio-Gen**) yüksek çözünürlüklü ürün görsellerini ve klinik verileri çekmek, tüm ürün fotoğraflarını **%100 şeffaf arka planlı 3B objelere** dönüştürmek, **2K 3B çift temalı (`Sage` & `Cobalt`) amblem logo** üretmek, **🔄 3B İmleçle Döndürme** ve **🔍 Optik Büyüteç (Loupe)** stüdyosu kurmak ve **GitHub Pages / Vercel** üzerinden canlıya almak için oluşturulmuş kapsamlı iş akışı ve deneyim kütüphanesidir.

- **Canlı Önizleme Adresi:** [https://redmaster-sys.github.io/liva-medical/](https://redmaster-sys.github.io/liva-medical/)
- **GitHub Deposu:** [https://github.com/redmaster-sys/liva-medical](https://github.com/redmaster-sys/liva-medical)

---

## 1. Hangi Sistemlerden ve Referanslardan Nasıl Faydalandık?

1. **Mevcut Site ve Resmi Partner / Üretici Siteleri Derin Analizi:**
   - `http://www.livamedical.com/` adresindeki tüm ürün grupları, alt sayfalar, iletişim bilgileri (Adana / Seyhan Merkez Ofis) ve iş ortakları tarandı.
   - Sitenin bağlı olduğu resmi üretici ve distribütör sitelerine (**`https://www.convatec.com/tr-tr/`**, **`http://www.ankasaglik.com.tr`**) gidilerek eski sitedeki düşük kaliteli görseller yerine **49 adet yüksek çözünürlüklü (HD / 1800px) resmi ürün fotoğrafı** ve eksiksiz teknik şartname verileri çekildi.
2. **Görsel Referans Mimarisi (`Cleargrin` & `Rumah Sakit Anaverse` Çift Tema Sistemi):**
   - Eski sitenin demode renkleri ve yazı tipleri tamamen terk edilerek iki modern klinik referans görseli birebir modellendi:
     - **Tema 1 — `🌿 Görsel 1 (Sage)` (`Cleargrin` Referansı):** Botanik Adaçayı ve Derin Orman Yeşili (`#234234` ana renk, `#55846C` vurgu, `#EEF5F0` pastel yüzey, `#FAFDFB` arka plan).
     - **Tema 2 — `💙 Görsel 2 (Cobalt)` (`Anaverse` Referansı):** Medikal Kobalt Mavisi ve Buz Mavisi (`#183BF0` ana renk, `#3B82F6` vurgu, `#EDF2FF` pastel yüzey, `#F7FAFF` arka plan).
   - Üst menüdeki tema değiştirici (`Sage` / `Cobalt`) tıklandığında yalnızca arka planlar değil, **sol üstteki 2K 3B Liva Medical amblem logosu**, **Whatsapp İletişim alanı ve ikonu**, **tarayıcı sekme ikonu (Favicon)** ve **tema rengi** anında senkronize olarak dönüşür.
3. **Google Stitch MCP & Godly.design Etkileşim Kalıpları:**
   - Google Stitch API (`https://stitch.googleapis.com/mcp`) için özel başlık (`X-Goog-Api-Key`) enjekte eden yerel vekil sunucu (`C:/Users/TaylanMERT/.gemini/config/stitch-mcp-proxy.mjs`) yapılandırıldı.
   - `https://godly.design/` referanslı mikro etkileşimler (**`⌘K` Hızlı Ürün & Partner Arama Spotlight Modalı**, canlı önizleme kartları, buzlu cam *frosted glass* randevu kartı ve üst üste binen 4'lü istatistik barı) entegre edildi.

---

## 2. Adım Adım Neler Yaptık? (Uçtan Uca Tasarım, 3B Görsel İşleme ve Yayın Süreci)

### Adım 1: Tek Satır Modern Tipografi ve Üst Bar (`Plus Jakarta Sans` & `Outfit`)
- Üst navigasyon barında (`header.site-header`) menü elemanlarının (*Ana Sayfa, Hizmetlerimiz, Hakkımızda, Ürün Kataloğu, Partnerler, İletişim*) hiçbir ekran boyutunda iki satıra kırılmaması için `Plus Jakarta Sans` (`font-weight: 600–800`), `white-space: nowrap`, `flex-shrink: 0` ve kapsül (`pill`) aktif sekme mimarisi kuruldu.

### Adım 2: Benzersiz 2K 3B Liva Medical Amblem Logosu (Sage & Cobalt Çift Versiyon)
- Sitenin sol üst köşesi ve alt bilgisi (footer) için Liva Medical ile özdeşleşecek **2048x2048 (2K) 3B Heykelsi Kurumsal Amblem Logo** üretildi:
  - Fırçalanmış şampanya-gümüş metalik şeritlerle çevrili **kaligrafik `L` harfi**, **botanik şifa yaprağı** ve merkezde **negatif alanlı medikal artı (`+`)** sembolü.
- C# (`System.Drawing`) tabanlı özel algoritma ile:
  1. Köşelerden projektör/taşkın doldurma (*flood-fill*) uygulanarak arka plan **%100 şeffaf (`alpha = 0`)** yapıldı (`assets/images/transparent/liva-signature-logo-2k.png`).
  2. Renk bütünlüğünün bozulmaması için yeşil/adaçayı tonlarını gümüş/beyaz yansımalara dokunmadan **Kraliyet Kobalt Mavisine (`#183BF0` / `#3B82F6`)** dönüştüren `LogoColorGrader` ile **Cobalt 2K Logo** (`assets/images/transparent/liva-signature-logo-cobalt-2k.png`) üretildi.

### Adım 3: 49 Ürün Görselinin Beyaz Arka Planlarının C# ile %100 Şeffaflaştırılması ve 3B Sahne
- Ürün kartlarında ve stüdyoda beyaz kutu görüntüsünü tamamen kaldırmak için iki aşamalı C# görüntü işleme motoru (`BgRemoverPro` + `ShadowCleaner`) yazıldı:
  1. **Dış Arka Plan Temizliği:** Köşelerden başlayan BFS *flood-fill* ve kenar yumuşatma (*feathering*) ile tüm beyaz/gri stüdyo arka planları silindi.
  2. **İç Boşluk (Delik) Temizliği:** ANKA cerrahi aplikatörlerin parmak halkalarının içindeki ve Huber port iğnesi hortum kıvrımlarının arasındaki kapalı beyaz adacıklar tespit edilip şeffaflaştırıldı.
- Ürün kartlarında (`.product-stage`) beyaz zemin kaldırılarak `perspective: 950px`, `transform: translateZ(26px)` ve çift katmanlı derinlik gölgesi (`drop-shadow`) ile ürünlerin havada **3B obje gibi** süzülmesi sağlandı.

### Adım 4: İnteraktif 🔄 3B İmleçle Döndürme ve 🔍 Optik Büyüteç (Loupe) Stüdyosu
- Her ürün kartının sağ üst köşesine iki etkileşim modu eklendi:
  1. **`🔄 3B` Modu (Varsayılan):** İmleç ürünün üzerinde gezdirildikçe ürün gerçek zamanlı X/Y eksenlerinde 3B eğim (`rotateX` / `rotateY`) alır ve dinamik stüdyo ışığı (`stage-glare`) imleci takip eder.
  2. **`🔍 Büyüteç` Modu:** Tıklandığında dairesel **Optik Mercek (2.6x Zoom Loupe)** devreye girer; cerrahi aplikatörlerin kilit mekanizmaları, Hydrofiber® lif dokusu ve adaptör detayları yakından incelenebilir.
- Ürün kartına veya `3B & Büyüteç Stüdyosu →` butonuna tıklandığında açılan tam ekran modalda (`#productModal`) `-25°` ile `+25°` arası 3B açı sürgüsü, çoklu HD açı galerisi, teknik tablo ve resmi üretici bağlantısı yer alır.

### Adım 5: Tema Uyumlu `Whatsapp İletişim` Alanı ve Doğrudan Yönlendirme
- `Hızlı Randevu & Talep` kartının ve `Kurumsal Teklif & Bilgi Formu`'nun altındaki boşluğa, parlak yeşil yerine **sitenin kendi tema renkleriyle (`var(--surface-pastel)`, `var(--border-med)`, `var(--primary-800)`)** bütünleşik **`Whatsapp İletişim`** butonu eklendi.
- Kullanıcının referans görseline sadık kalınarak yuvarlatılmış kare (`squircle`) içinde **çizgisel konuşma balonu halkası + ahize** vektör ikonu kullanıldı ve üstteki durum noktası kaldırıldı.
- Buton üzerinde telefon numarası gösterilmez (yalnızca **`Whatsapp İletişim`** yazar); tıklandığında [`openLivaWhatsApp`](file:///c:/Users/TaylanMERT/Downloads/web%20tasar%C4%B1m/app.js#L1225-L1261) fonksiyonu formda girilen bilgileri de ekleyerek doğrudan **`https://wa.me/905417656520`** (`0541 765 65 20`) adresine yönlendirir.

### Adım 6: GitHub + GitHub Pages & Vercel ile Canlı Önizleme Yayını
- Proje dizininde [vercel.json](file:///c:/Users/TaylanMERT/Downloads/web%20tasar%C4%B1m/vercel.json) oluşturuldu, `git init -b main` ile yerel depo başlatıldı ve 139 dosyanın tamamı `https://github.com/redmaster-sys/liva-medical.git` deposuna `push` edildi.
- GitHub Pages (`main` dalı) aktifleştirilerek şifre/mail doğrulaması beklemeden **[https://redmaster-sys.github.io/liva-medical/](https://redmaster-sys.github.io/liva-medical/)** adresi üzerinden canlı yayına alındı.

---

## 3. Neleri Düzelttik ve Hangi Kritik Sorunları Çözdük? (Troubleshooting Log)

| # | Karşılaşılan Sorun / Hata | Kök Neden | Uygulanan Kesin Çözüm |
| :- | :--- | :--- | :--- |
| **1** | **Google Stitch MCP `401 Unauthorized` Hatası** | Stitch MCP sunucusu standart `Authorization` başlığı yerine `X-Goog-Api-Key` başlığı bekliyordu. | `C:/Users/TaylanMERT/.gemini/config/stitch-mcp-proxy.mjs` yazılarak JSON-RPC isteklerine otomatik `X-Goog-Api-Key` başlığı eklendi. |
| **2** | **İlk Tasarımın Eski Siteye Benzemesi** | İlk iterasyonda koyu lacivert/camgöbeği kurumsal renkler kullanılmıştı. | Kullanıcının paylaştığı `Cleargrin` (Sage) ve `Anaverse` (Cobalt) referans görselleri birebir modellenerek 6'lı pastel hizmet şeridi, buzlu cam randevu kartı ve çift tema sistemi kuruldu. |
| **3** | **Chrome'un Komut Satırından Açılıp Hemen Kapanması** | `Start-Process chrome.exe` komutu, geçici PowerShell oturumu kapandığında Windows Job Object tarafından sonlandırılıyordu. | Arka planda kalıcı Node.js sunucusu (`IsDaemon: true`, port `8088`) başlatıldı ve Chrome `Invoke-CimMethod -ClassName Win32_Process -MethodName Create` ile bağımsız süreç olarak açıldı. |
| **4** | **Üst Menüde `Ana Sayfa` Yazısının Alt Satıra Düşmesi** | Daralan esnek kutularda (`flex`) boşluklu kelimeler iki satıra kırılıyordu. | `Plus Jakarta Sans` yazı tipi, `white-space: nowrap`, `flex-shrink: 0` ve optimize edilmiş iç boşluklarla tüm menünün tek satırda kalması garanti altına alındı. |
| **5** | **Ürün Görsellerinde Beyaz Kutu ve İç Halka Beyazlıkları** | Standart JPG görsellerde beyaz arka plan ve cerrahi aletlerin parmak halkaları içinde beyaz alanlar kalıyordu. | C# `BgRemoverPro` (kenar flood-fill) + `ShadowCleaner` (kapalı iç beyaz adacık ve gri gölge temizliği) ile 49 görselin tamamı pürüzsüz şeffaf PNG'ye dönüştürüldü. |
| **6** | **WhatsApp Alanının Aşırı Yeşil Olması ve Cobalt Geçişinde Renk Uyumsuzluğu** | Sabit `#25D366` WhatsApp yeşili ve tek renkli yeşil logo, Cobalt mavi temaya geçildiğinde sırıtıyordu. | WhatsApp alanı sitenin tema değişkenlerine (`var(--surface-pastel)`, `var(--primary-800)`) bağlandı, numara gizlenip `Whatsapp İletişim` yazıldı ve Cobalt teması için özel 2K 3B Mavi Logo (`liva-signature-logo-cobalt-2k.png`) üretildi. |
| **7** | **Vercel'de `"Project liva-medical already exists"` ve Mail Kodu Sorunu** | İlk tıklamada proje kaydı oluştuğu için ikinci tıklamada isim çakışması yaşandı. | GitHub deposu üzerinden doğrudan **GitHub Pages (`main` branch)** devreye alınarak 25 saniye içinde `https://redmaster-sys.github.io/liva-medical/` canlıya açıldı. |

---

## 4. Neleri Takip Ettik? (İzleme ve Doğrulama Kontrol Listesi)

Yeni bir ürün, görsel veya tasarım güncellemesi yapılırken aşağıdaki 6 adım sırasıyla kontrol edilir:

1. **Şeffaf PNG Kontrolü:** Eklenen her yeni ürün görseli `assets/images/transparent/` klasörüne şeffaf PNG olarak kaydedilmeli, arkasında beyaz dikdörtgen kutu bulunmamalıdır.
2. **Çift Tema (`Sage` & `Cobalt`) Renk Bütünlüğü:** Eklenen her bileşen sabit renk kodları yerine `var(--primary-800)`, `var(--accent-500)`, `var(--surface-pastel)`, `var(--border-med)` değişkenlerini kullanmalı; tema değiştirildiğinde logo ve ikonlar otomatik uyum sağlamalıdır.
3. **Tek Satır Üst Bar Kuralı:** Üst menüdeki (`nav.main-nav`) hiçbir bağlantı veya buton alt satıra düşmemelidir (`white-space: nowrap`).
4. **Kırık Görsel / Dosya Yolu Denetimi (`0 Missing Assets`):** `index.html` ve `app.js` içindeki tüm `assets/images/...` yolları diskteki dosyalarla birebir eşleşmelidir (büyük/küçük harf duyarlılığı dahil).
5. **WhatsApp Gizlilik ve Yönlendirme Kuralı:** İletişim butonlarında telefon numarası açık metin olarak yazılmamalı, yalnızca **`Whatsapp İletişim`** görünmeli ve tıklandığında [`openLivaWhatsApp`](file:///c:/Users/TaylanMERT/Downloads/web%20tasar%C4%B1m/app.js#L1225-L1261) üzerinden hedef numaraya yönlendirmelidir.
6. **Canlı Önizleme Senkronizasyonu:** Yapılan her değişiklikten sonra `git add . && git commit -m "..." && git push origin main` çalıştırılarak `https://redmaster-sys.github.io/liva-medical/` canlı adresi güncellenir.

---

## Utility Commands (Hızlı Güncelleme & Canlıya Gönderme Komutları)

Projede yaptığınız herhangi bir değişikliği yerel sunucuda test etmek veya doğrudan canlı linke (`github.io` / `vercel`) göndermek için şu komutları kullanabilirsiniz:

```powershell
# 1. Tüm görsel yollarını doğrula (Eksik dosya olup olmadığını kontrol et)
$root = "c:\Users\TaylanMERT\Downloads\web tasarım"
$all = (Get-Content "$root\index.html" -Raw) + "`n" + (Get-Content "$root\app.js" -Raw)
[regex]::Matches($all, 'assets/images/[a-zA-Z0-9_\-\./]+') | ForEach-Object { $_.Value } | Select-Object -Unique | Where-Object { -not (Test-Path (Join-Path $root ($_ -replace '/','\'))) }

# 2. Değişiklikleri GitHub'a ve Canlı Linke (https://redmaster-sys.github.io/liva-medical/) gönder
Set-Location "c:\Users\TaylanMERT\Downloads\web tasarım"
git add index.html styles.css app.js vercel.json assets/
git commit -m "feat: site guncellemesi"
git push origin main
```
