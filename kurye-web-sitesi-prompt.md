# Kurye Şahıs Şirketi – Kurumsal Web Sitesi (Claude Code Prompt)

> **Kullanım:** "FİRMA BİLGİLERİ" ve "UYGULAMALAR" bölümlerini doldur, sonra dosyanın tamamını Claude Code'a ver.
> Firma unvanı ve adres **vergi levhandaki ile birebir aynı** olmalı. Google ve D&B, sitedeki bilgileri başvurundaki bilgilerle karşılaştırır.

---

## FİRMA BİLGİLERİ (doldur)

- Resmi firma unvanı (Sedat Çağlar - Kurye Faliyetleri): `[ÖRN: AHMET YILMAZ - KURYE HİZMETLERİ]`
- Kısa marka adı (Sedat Çağlar): `[ÖRN: Yılmaz Kurye]`
- Yetkili adı soyadı: `[Sedat Çağlar]`
- Vergi dairesi: `[Harput]`
- Vergi numarası: `[2180203297]`
- Açık adres (Sürsürü Mah. Karahanlı Sok. No:9 İç Kapı No:4 Merkez/Elazığ): `[MAHALLE, SOKAK, NO, İLÇE / İL, POSTA KODU]`
- Telefon: `[+90 541 262 82 38]`
- E-posta (sedatcglr34@gmail.com): `[info@alanadim.com]`
- Alan adı: `[sedatcaglar.online]`
- Hizmet bölgesi: `[ÖRN: TÜRKİYE]`
- Kuruluş yılı: `[2025]`

## UYGULAMALAR (doldur – henüz yayında değilse "Yakında" yaz)

Uygulama 1:
- Adı: `[UYGULAMALARIM]`
- Kısa açıklama (Mobil Uygulamalarım 

Günlük ihtiyaçlarınızı kolaylaştırmak için geliştirdiğim mobil uygulamaları keşfedin. Kullanıcı dostu arayüzleri, pratik özellikleri ve güvenilir çalışma yapılarıyla her uygulama, farklı ihtiyaçlara hızlı ve kolay çözümler sunmak için tasarlanmıştır.

Yeni uygulamalar ve güncellemeler eklendikçe bu bölüm üzerinden tüm projelerimi inceleyebilirsiniz.
): `[AÇIKLAMA]`

(Birden fazla uygulama varsa aynı bloğu çoğalt.)

---

## PROMPT (Claude Code'a bunu ver)

Benim için sade, profesyonel, tamamen statik (saf HTML + CSS, framework yok, build adımı yok) bir kurumsal web sitesi oluştur. Site Vercel'e deploy edilecek ve kendi alan adıma bağlanacak. Sitenin amacı; Google Play Console kuruluş (organization) hesabı, Android geliştirici doğrulaması ve D-U-N-S başvurusunda "firma web sitesi" olarak kullanılmak ve geliştirdiğim mobil uygulamaları tanıtmak.

Firma ve uygulama bilgileri yukarıdaki bölümlerde. Bu bilgileri sitenin her yerinde **birebir aynı** yaz; değiştirme, kısaltma veya uydurma bilgi ekleme.

### Google ve D&B incelemesi için temel kurallar

- Firma unvanı, adres, telefon ve e-posta her sayfanın footer'ında ve "Hakkımızda" sayfasında açıkça görünsün.
- Site gerçek ve tamamlanmış görünmeli: "lorem ipsum", "yapım aşamasında", boş sayfa, kırık link olmasın.
- Abartılı veya doğrulanamayan iddialar (büyük filo, müşteri sayıları, sahte yorumlar, ödüller) yazma.
- Her uygulamanın kendine ait, herkese açık, giriş gerektirmeyen, HTML (PDF değil) gizlilik politikası sayfası olsun. Google Play bu URL'yi ister.
- Google Play'in istediği "hesap ve veri silme" sayfası olsun.

### Genel gereksinimler

1. Saf HTML5 + tek ortak CSS dosyası. JavaScript sadece gerekirse (mobil menü) ve minimum düzeyde.
2. Tamamen responsive (mobil öncelikli), harici kütüphane/CDN/görsel yok. İkonlar inline SVG.
3. Temiz, güven veren tasarım: tek vurgu rengi, bol boşluk, sistem font yığını.
4. Site dili Türkçe; her sayfanın İngilizcesi `/en/` klasöründe olsun. Header'da TR / EN geçiş linki.
5. Header menüsü: Ana Sayfa, Hakkımızda, Hizmetler, **Uygulamalarımız**, İletişim.
6. Footer: resmi unvan, adres, telefon (`tel:`), e-posta (`mailto:`), vergi dairesi ve no, © yıl + unvan, Gizlilik Politikası, KVKK ve Veri Silme linkleri.
7. Her sayfada: anlamlı `<title>`, `meta description`, `lang`, Open Graph etiketleri, canonical link, SVG favicon.
8. Ana sayfada schema.org `LocalBusiness` JSON-LD (unvan, adres, telefon, e-posta, url, hizmet bölgesi).
9. Uygulama sayfalarında schema.org `MobileApplication` JSON-LD (ad, işletim sistemi Android, kategori, geliştirici = firma unvanı).
10. `robots.txt`, `sitemap.xml` (tüm TR ve EN sayfalar dahil) ve özel `404.html`.
11. `vercel.json`: `cleanUrls: true`, `trailingSlash: false`, temel güvenlik header'ları (X-Content-Type-Options, Referrer-Policy, X-Frame-Options).

### Sayfalar

**1. Ana sayfa (`index.html`)**
- Hero: marka adı, slogan (ör. "Hızlı, güvenilir ve güvenli teslimat"), "İletişime Geç" ve "Uygulamalarımız" butonları.
- Kısa hakkımızda özeti, hizmet kartları (4-6 adet), "Neden biz" bölümü, 3 adımlık "Nasıl çalışır".
- "Uygulamalarımız" önizleme bölümü: uygulama kartları ve "Tümünü gör" linki.
- İletişim özeti.

**2. Hakkımızda (`hakkimizda.html`)**
- Firmanın faaliyet alanını, hizmet bölgesini ve mobil uygulama geliştirme çalışmalarını anlatan dürüst bir metin.
- "Firma Bilgileri" tablosu: Unvan, Yetkili, Vergi Dairesi, Vergi No, Adres, Telefon, E-posta, Web sitesi.

**3. Hizmetler (`hizmetler.html`)**
- Kurye hizmetlerinin detaylı açıklaması: paket/evrak teslimatı, aynı gün teslimat, platform kuryeliği, e-ticaret teslimatları, şehir içi acil gönderi.

**4. Uygulamalarımız (`uygulamalar.html`)** – YENİ SEKME
- Tüm uygulamaları kart olarak listele: SVG ikon (uygulama adının baş harfiyle basit bir ikon), ad, kısa açıklama, durum rozeti ("Yakında" / "Google Play'de"), "Detaylar" butonu.
- Uygulama yayındaysa "Google Play'den indir" butonu (resmi Google Play rozeti görseli kullanma; kendi tasarımın olan metinli bir buton yap).
- Her uygulama için ayrı klasör oluştur: `uygulamalar/[uygulama-slug]/`
  - `index.html`: uygulama detay sayfası (açıklama, özellikler, desteklenen platform, geliştirici bilgisi, destek e-postası, gizlilik politikası ve veri silme linkleri).
  - `gizlilik-politikasi.html`: o uygulamaya özel gizlilik politikası. İçerik: geliştirici (firma unvanı, adres, e-posta), uygulamanın topladığı veriler (yukarıda yazdığım liste), toplama amacı, izinler (konum vb.) ve neden kullanıldığı, üçüncü taraf hizmetler (kullanılıyorsa; bilmiyorsan "Firebase/Google Play Hizmetleri gibi servisler kullanılıyorsa…" diye genel bir bölüm ve düzenlemem için yorum satırı bırak), saklama süresi, güvenlik, kullanıcı hakları, veri silme, çocukların gizliliği, değişiklikler, yürürlük tarihi, iletişim.
  - İngilizceleri: `/en/apps/[uygulama-slug]/index.html` ve `/en/apps/[uygulama-slug]/privacy-policy.html`.
- Yeni uygulama eklemeyi kolaylaştırmak için `uygulamalar/_sablon/` klasöründe kopyalanabilir bir şablon bırak.

**5. İletişim (`iletisim.html`)**
- Telefon, e-posta, adres, çalışma saatleri. Form KULLANMA; belirgin "E-posta Gönder" ve "Ara" butonları. Adres için sadece "Google Haritalar'da aç" linki.

**6. Genel Gizlilik Politikası (`gizlilik-politikasi.html`)**
- Web sitesi ve kurye hizmeti için genel gizlilik politikası (site çerez kullanmıyor). İngilizcesi `/en/privacy-policy.html`.

**7. KVKK Aydınlatma Metni (`kvkk.html`)**
- 6698 sayılı KVKK'ya uygun standart aydınlatma metni: veri sorumlusu, işlenen veriler, amaçlar, hukuki sebepler, aktarım, toplama yöntemi, KVKK md. 11 hakları, başvuru yöntemi.

**8. Hesap ve Veri Silme (`veri-silme.html`)**
- Tüm uygulamalar için ortak sayfa: kullanıcının e-posta ile nasıl talepte bulunacağı (hangi uygulama, hangi hesap bilgisi), silinecek ve yasal zorunlulukla saklanacak veriler, işlem süresi. Sayfada firma ve uygulama adları geçsin. İngilizcesi `/en/data-deletion.html`.

### Klasör yapısı

```
/
├── index.html
├── hakkimizda.html
├── hizmetler.html
├── uygulamalar.html
├── uygulamalar/
│   ├── _sablon/
│   └── [uygulama-slug]/
│       ├── index.html
│       └── gizlilik-politikasi.html
├── iletisim.html
├── gizlilik-politikasi.html
├── kvkk.html
├── veri-silme.html
├── 404.html
├── en/
│   ├── index.html, about.html, services.html, apps.html, contact.html
│   ├── privacy-policy.html, data-deletion.html
│   └── apps/[uygulama-slug]/index.html, privacy-policy.html
├── assets/style.css, favicon.svg
├── robots.txt
├── sitemap.xml
├── vercel.json
└── README.md
```

### README.md

Türkçe bir README yaz:
- Siteyi yerelde açma (tarayıcıda veya `npx serve`).
- GitHub'a yükleyip Vercel'e deploy etme (Framework Preset: "Other", build komutu yok).
- Vercel'de alan adı bağlama (panelde gösterilen DNS kayıtlarını domain firmasına girme).
- Google Search Console'da alan adını doğrulama (DNS TXT kaydı yöntemi) ve bunun Play Console için neden önemli olduğu.
- Yeni uygulama ekleme adımları (`_sablon` klasörünü kopyalama, uygulamalar sayfasına kart ekleme, sitemap'i güncelleme).
- Play Console'a girilecek URL'lerin listesi: web sitesi, her uygulamanın gizlilik politikası URL'si, veri silme URL'si.
- Firma bilgilerini sonradan hangi dosyalarda değiştireceğim.

### Kontrol listesi (bitirmeden önce kendin kontrol et)

- Firma unvanı, adres, telefon, e-posta tüm sayfalarda birebir aynı mı?
- Tüm iç linkler (TR ve EN) çalışıyor mu? Kırık link yok mu?
- Her uygulamanın gizlilik politikası sayfası giriş gerektirmeden açılıyor mu?
- Gizlilik, KVKK ve Veri Silme sayfaları footer'dan erişilebilir mi?
- Mobilde (375px) yatay kaydırma yok mu, konsolda hata yok mu?
- Sitede "lorem ipsum" veya doldurulmamış yer tutucu kaldı mı?

Bitirdiğinde oluşturduğun dosyaları, Play Console'a girmem gereken URL'leri ve Vercel'e deploy için yapmam gerekenleri kısaca özetle.
