# sedatcaglar.online — Kurumsal Web Sitesi

**Sedat Çağlar - Kurye Faliyetleri** için saf HTML + CSS ile hazırlanmış statik kurumsal site. Framework yok, build adımı yok.

## 1. Yerelde açma

- **En kolay yol:** `index.html` dosyasına çift tıklayın. Site tarayıcıda açılır ve tüm linkler çalışır.
- **Yerel sunucu ile (önerilir):**
  ```bash
  npx serve .
  ```
  Ardından terminalde görünen adresi (ör. `http://localhost:3000`) açın.

> `404.html` sayfası kök dizine göre (`/assets/...`) link verir. Bu yüzden yalnızca sunucu üzerinde düzgün görünür.

## 2. GitHub'a yükleme ve Vercel'e deploy

1. GitHub'da yeni bir depo (repository) oluşturun ve bu klasörün içeriğini yükleyin:
   ```bash
   git init
   git add .
   git commit -m "İlk sürüm"
   git branch -M main
   git remote add origin https://github.com/KULLANICI_ADINIZ/sedatcaglar-site.git
   git push -u origin main
   ```
2. [vercel.com](https://vercel.com) adresinde GitHub hesabınızla giriş yapın → **Add New… → Project** → depoyu seçin.
3. Ayarlar:
   - **Framework Preset:** `Other`
   - **Build Command:** boş bırakın
   - **Output Directory:** boş bırakın (kök dizin)
4. **Deploy**'a basın. Bundan sonra GitHub'a gönderdiğiniz her değişiklik otomatik olarak yayına alınır.

`vercel.json` dosyası uzantısız adresleri (`/hakkimizda`) ve güvenlik başlıklarını ayarlar. `.vercelignore` dosyası ise şablon klasörlerinin ve bu README'nin yayına çıkmasını engeller.

## 3. Alan adını bağlama (sedatcaglar.online)

1. Vercel'de projeyi açın → **Settings → Domains** → `sedatcaglar.online` yazıp **Add**'e basın. `www.sedatcaglar.online` adresini de ekleyin ve ana alan adına yönlendirin.
2. Vercel size eklemeniz gereken DNS kayıtlarını gösterir. Bunlar genellikle şunlardır:
   - `A` kaydı → `@` → Vercel'in verdiği IP adresi
   - `CNAME` kaydı → `www` → Vercel'in verdiği adres
3. Alan adını satın aldığınız firmanın panelinde **DNS yönetimi** bölümüne girip bu kayıtları **Vercel panelinde gösterildiği gibi aynen** ekleyin.
4. Kayıtların yayılması birkaç dakika ile 48 saat arasında sürebilir. Vercel'de alan adının yanında yeşil onay işareti göründüğünde SSL (https) otomatik olarak etkinleşir.

## 4. Google Search Console'da alan adını doğrulama

Play Console, geliştirici hesabındaki web sitesinin size ait olduğunu doğrulamak isteyebilir. Aynı Google hesabıyla Search Console'da alan adını doğrulamak bu süreci kolaylaştırır. Ayrıca sitenin Google'da indekslenmesini sağlar.

1. [search.google.com/search-console](https://search.google.com/search-console) adresine **Play Console'da kullandığınız Google hesabıyla** giriş yapın.
2. **Mülk ekle → Alan adı (Domain)** seçeneğini seçin ve `sedatcaglar.online` yazın.
3. Google size `google-site-verification=...` ile başlayan bir **TXT kaydı** verir.
4. Domain firmanızın DNS panelinde yeni bir `TXT` kaydı ekleyin: Ad/Host `@`, Değer: Google'ın verdiği metin.
5. Birkaç dakika bekleyip Search Console'da **Doğrula**'ya basın.
6. Doğrulandıktan sonra **Site haritaları** bölümüne `sitemap.xml` ekleyin.

## 5. Yeni uygulama ekleme

Örnekte uygulamanın adı "Not Defterim", slug'ı ise `not-defterim` olsun.

1. **Klasörleri kopyalayın:**
   - `uygulamalar/_sablon/` → `uygulamalar/not-defterim/` (`KART-ORNEGI.html` dosyasını yeni klasöre kopyalamayın)
   - `en/apps/_template/` → `en/apps/not-defterim/`
2. **Yer tutucuları değiştirin.** Yeni klasörlerdeki 4 HTML dosyasında (VS Code: Ctrl+Shift+H) şunları değiştirin:
   `{{APP_NAME}}`, `{{APP_SLUG}}`, `{{APP_LETTER}}`, `{{APP_SHORT_TR}}`, `{{APP_SHORT_EN}}`, `{{APP_CATEGORY}}`, `{{PLAY_URL}}`, `{{EFFECTIVE_DATE_TR}}`, `{{EFFECTIVE_DATE_EN}}`
3. **İçeriği düzenleyin.** Dosyalardaki `<!-- ... -->` yorumlarının gösterdiği yerleri doldurun: özellikler, **toplanan veriler**, **izinler**, **üçüncü taraf hizmetler**. Bu bölümler Google Play'deki "Veri güvenliği" formuyla birebir uyumlu olmalıdır.
4. **Şablon notunu ve noindex etiketini silin.** 4 dosyanın her birinde en üstteki şablon açıklama yorumunu ve `<meta name="robots" content="noindex, nofollow">` satırını kaldırın.
5. **Kartı ekleyin.** `uygulamalar/_sablon/KART-ORNEGI.html` içindeki TR kartı `uygulamalar.html` ve `index.html` dosyalarına, EN kartı ise `en/apps.html` ve `en/index.html` dosyalarına yapıştırın. İlk uygulamayı eklerken "Yeni uygulamalar / Yakında" kartını silebilirsiniz.
6. **Veri silme sayfalarını güncelleyin.** `veri-silme.html` ve `en/data-deletion.html` sayfalarındaki "Kapsanan uygulamalar" listesine uygulamanın adını ekleyin.
7. **Site haritasını güncelleyin.** `sitemap.xml` dosyasının sonundaki yorumda bulunan 4 örnek URL'yi kopyalayıp düzenleyin.

## 6. Play Console'a girilecek URL'ler

| Alan | URL |
|---|---|
| Web sitesi | `https://sedatcaglar.online` |
| Genel gizlilik politikası | `https://sedatcaglar.online/gizlilik-politikasi` |
| Hesap ve veri silme URL'si | `https://sedatcaglar.online/veri-silme` |
| Uygulama gizlilik politikası (her uygulama için) | `https://sedatcaglar.online/uygulamalar/UYGULAMA-SLUG/gizlilik-politikasi` |
| İngilizce gizlilik politikası (isteğe bağlı) | `https://sedatcaglar.online/en/apps/UYGULAMA-SLUG/privacy-policy` |
| İngilizce veri silme (isteğe bağlı) | `https://sedatcaglar.online/en/data-deletion` |

## 7. Firma bilgilerini değiştirme

Firma bilgileri (unvan, adres, telefon, e-posta, vergi dairesi/no) **tüm HTML dosyalarında** header, footer, tablolar ve JSON-LD içinde tekrar eder. Değiştirmek için:

1. VS Code'da klasörü açın → **Ctrl+Shift+H** (tüm dosyalarda bul ve değiştir).
2. Eski değeri tam olarak yazın (ör. `Sedat Çağlar - Kurye Faliyetleri`), yeni değeri girin ve **Tümünü Değiştir**'e basın.

Bilgilerin bulunduğu dosyalar:
- Tüm `.html` dosyaları (footer, header ve iletişim/hakkımızda tabloları)
- `index.html` ve `en/index.html` → `LocalBusiness` JSON-LD (telefon burada `+905412628238` biçimindedir)
- `404.html` → alt bilgi satırı
- `robots.txt` ve `sitemap.xml` → alan adı (yalnızca alan adı değişirse)

Diğer düzenlenebilir alanlar:
- **Çalışma saatleri:** `iletisim.html` ve `en/contact.html` (ilgili `<!-- ÇALIŞMA SAATLERİ -->` yorumunu arayın)
- **Vurgu rengi:** `assets/style.css` → `--accent` ve `--accent-hover`
- **Telif yılı:** footer'lardaki `© 2026`
