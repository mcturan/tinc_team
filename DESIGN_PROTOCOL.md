# DESIGN PROTOCOL — Tasarım Pipeline Kuralları

Claude mimari bu dosyaya atıfta bulunur ama tasarım kararlarına karışmaz.

---

## ARAÇLAR
- **Google Stitch** (stitch.withgoogle.com) — UI üretimi (Gemini 2.5 Pro / Gemini 3, ücretsiz 350/ay)
- **Gemini CLI** — DesignSpec.md yazımı
- **DESIGN.md** — Stitch'e verilen tasarım sistemi kuralları
- **DESIGN_SPECS/** — Tüm DesignSpec dosyalarının bulunduğu klasör (`/home/turan/workspace/qrvee/DESIGN_SPECS/`)

---

## STITCH KAPASİTELERİ
- Metin promptu → çok ekranlı UI prototipi
- Görsel/screenshot → UI dönüşümü
- URL → tasarım sistemi çıkarımı (renkler, tipografi, spacing)
- React export → doğrudan kullanılabilir component
- Figma export → tasarım kolaborasyonu
- DESIGN.md okuyarak kurallarla üretim
- MCP server → Claude Code ile doğrudan entegrasyon
- Ses komutu → canvas yönlendirme

---

## PIPELINE (LAW-016 ile enforce edilir)
1. **Brief** — Müteahhit UI hedefini Türkçe açıklar
2. **Stitch** — UI üretir, React export alınır
3. **Gemini CLI** — DesignSpec.md yazar, `DESIGN_SPECS/[component-name].md` kaydeder
4. **DesignSpec formatı** — Intent, layout, states, tokens, motion, constraints, anti-patterns
5. **Claude denetimi** — TINC MASTER_SPEC uyum kontrolü (sadece teknik, estetik değil)
6. **FINAL onayı** — Claude "FINAL" statusu verir
7. **Codex implementation** — Sadece FINAL DesignSpec'e göre kod yazar
8. **Gemini Pro doğrulama** — Çıktı DesignSpec'e uyuyor mu?

---

## YASAKLAR (LAW-017)
- Claude tasarım tercihi yapamaz
- Codex DesignSpec dışında component ekleyemez
- Gemini backend/veri modeli kararı veremez
- Stitch üretimi Claude onayı olmadan Codex'e verilemez
