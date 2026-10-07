# Brief Kuralları ve Link Envanteri

## 1. Marka tarafının standart brief maddeleri

Yeni bir iş geldiğinde brief bunları içerir; içermiyorsa varsayılan olarak bunlar geçerlidir.

- Editoryal bilgilendirme içeriği, advertorial değil
- Uzunluk: 600-1.400 kelime, konunun gerektirdiği kadar (bilerek kısaltılmaz, dolgu ile uzatılmaz)
- Ana başlıkta Turkcell geçmeyecek
- Turkcell metin içinde 3-6 kez geçebilir (kısa yazıda 3-4), ağırlığı H2 seviyesinde olacak
- Giriş paragrafında Turkcell geçmeyecek
- Fiyat, tarife adı, kampanya ve kesin rakam verilmeyecek
- Rakip operatör isimleriyle karşılaştırma yapılmayacak, genel olarak operatörlerden bahsedilebilir
- Ön ödemeli hatlar için "faturasız hat" ifadesi kullanılacak, "hazır kart" denmeyecek
- Reklam dili ve anahtar kelime doldurma kullanılmayacak; yazı sonunda tek cümlelik, yumuşak bir CTA paragrafı bulunacak
- Turkcell bölümünde operatörlerle kıyas cümlesi ("tüm operatörlerde aynı") kurulmayacak; mevzuat kuralları "mevzuat gereği" diye verilecek
- Genellikle 2-3 link verilir, anchor metinleri brief'te belirtilir
- İçerik marka onayından geçer

## 2. Onaylı anchor ve hedef URL envanteri

Bu eşleşmeler daha önce onaylanmış ve kullanılmıştır. Kullanmadan önce yine de HTTP durum kodunu doğrula; Turkcell tarafında URL yapısı zaman zaman değişiyor.

| Anchor | Hedef URL | Konu uyumu |
|---|---|---|
| numara taşıma | https://www.turkcell.com.tr/turkcellli-olmak/paket-secimi | Numara taşıma, operatör değişikliği, başvuru süreci |
| faturalı hat | https://www.turkcell.com.tr/paket-ve-tarifeler/faturali-hat | Hat tipi, abonelik yapısı, faturalı/faturasız ayrımı |
| eSIM | https://www.turkcell.com.tr/esim | eSIM, SIM tipi değişikliği, dijital profil |
| hız testi | https://www.turkcell.com.tr/hiz-testi | İnternet hızı ölçümü, ping, jitter, bağlantı teşhisi |
| ev interneti | https://www.turkcell.com.tr/ev-interneti | Ev interneti, altyapı, fiber/VDSL kapsamı |

Doğrulama:

```bash
for u in "<url1>" "<url2>"; do
  echo "$(curl -s -o /dev/null -w '%{http_code}' -A 'Mozilla/5.0' --compressed -L "$u")  $u"
done
```

Bilinen 404'ler (kullanma): `/superonline`, `/superonline/fiber-internet`, `/altyapi-sorgulama`, `/ping-testi`.

Envanterde karşılığı olmayan bir anchor istenirse, hedef sayfayı doğrula ve kullanıldıktan sonra bu tabloya ekle.

## 3. Yayın sitesi notları

Yazının iskeleti ve kuralları site fark etmeksizin aynı. Siteye göre değişen tek şey konu seçiminin derinliği:

- **webtekno, teknoseyir, maxicep:** geniş tüketici kitlesi. Teknik terim ilk geçtiğinde kısa parantez içi karşılık verilebilir.
- **technopat, teknotalk, chip:** teknik okur. Terim açıklamasına daha az ihtiyaç var, ölçüm ve mekanizma detayı daha fazla tolere ediliyor.

Her iki grupta da yazının bilgi yoğunluğu aynı kalır; değişen açıklama miktarıdır.

## 4. Dosya adlandırma

```
YYYYAAGG - Turkcell - Telco - Backlink Blog (site.com) - Başlık.docx
```

Örnek:

```
20260831 - Turkcell - Telco - Backlink Blog (teknotalk.com) - Numara Taşıma Başvurusu Neden Reddedilir_ En Sık Karşılaşılan Nedenler.docx
```

Başlıktaki `?` ve `:` karakterleri `_` ile değiştirilir; Türkçe karakterler korunur.

## 5. Kullanılmış başlıklar

Aynı konunun iki farklı sitede tekrarlanması yayıncı tarafında sorun oluşturmuyor ancak açı farklılaşmalı. Şu ana kadar üretilenler:

| Başlık | Site | Ana anchor |
|---|---|---|
| Numara Taşıma Nedir? Taahhüt, Paket ve Faturada Neler Değişiyor? | webtekno.com | numara taşıma |
| eSIM'e Geçerken Numaranızı Nasıl Taşırsınız? | technopat.net | eSIM |
| Numara Taşıma Başvurusu Neden Reddedilir? En Sık Karşılaşılan Nedenler | teknotalk.com | numara taşıma |
| Evde İnternet Hızı Neden Gün İçinde Değişir? Wi-Fi Sorunlarını Teşhis Etme | teknoseyir.com | hız testi |
| Fiber, VDSL ve Mobil İnternet Aynı Hızda mı Ölçülür? Bağlantı Tipine Göre Test Farkları | maxicep.com | hız testi |

Yeni yazı üretildiğinde bu tabloya eklenir.
