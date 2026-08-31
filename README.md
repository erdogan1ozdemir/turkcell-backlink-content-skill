# turkcell-backlink-content

Turkcell Telco tarafı için harici yayın sitelerinde (webtekno, technopat, teknotalk, teknoseyir, maxicep gibi) yayımlanacak backlink blog yazılarını, marka onayından geçmiş editoryal ev üslubuyla üreten Claude Code skill'i.

## Ne yapar

Başlık, yayın sitesi ve anchor/URL bilgisi verildiğinde 1.200-1.400 kelimelik editoryal bir yazı üretir ve teslime hazır .docx olarak kaydeder. Yazı iskeleti, ton, link yerleşimi ve marka kullanımı onaylı örneklerden çıkarılmıştır.

## Kurulum

```bash
git clone https://github.com/erdogan1ozdemir/turkcell-backlink-content-skill.git ~/.claude/skills/turkcell-backlink-content
```

Gereksinim: Python 3 ve `python-docx`.

```bash
pip3 install python-docx
```

## İçerik

```
SKILL.md                                  akış, kurallar, iskelet, üretim adımları
references/uslup.md                       ton, cümle kalıpları, yasak-tercih sözlüğü, sık hatalar
references/kurallar-ve-linkler.md         brief kuralları, onaylı anchor/URL envanteri, dosya adlandırma
scripts/build_docx.py                     JSON -> .docx üretici
scripts/qa_check.py                       teslim öncesi kural kontrolü
assets/ornek-yazi-numara-tasima-red.json  onaylı bir yazının tam JSON hali
```

## Kullanım

```bash
python3 scripts/build_docx.py article.json "Çıktı.docx"
python3 scripts/qa_check.py "Çıktı.docx"
```

`qa_check.py` kelime sayısı, marka kullanımı, giriş/H1 marka yasağı, rakip operatör adı, reklam kalıbı, fiyat ifadesi, em dash, çift boşluk, link ve anchor tutarlılığını denetler. Advertorial, tekrar ve doğruluk testleri okuma gerektirdiği için scriptin dışındadır.
