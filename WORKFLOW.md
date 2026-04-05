# WORKFLOW — İş Akışı Protokolü

---

## STANDART DÖNGÜ

```
Müteahhit (karar/brief)
    ↓
Claude (spec yazar, komut dosyası üretir)
    → /home/turan/İndirilenler/FAZ-XX-KOMUT.md
    ↓
Claude Code (dosyayı okur, uygular)
    → Codex'e kod yazar
    → Gemini'ye tasarım atar
    → Denetçi çalıştırır
    → Push eder
    → /home/turan/İndirilenler/FAZ-XX-RAPOR.md yazar
    ↓
Müteahhit (raporu Claude'a verir)
    ↓
Claude (denetler, onaylar veya düzeltir)
    ↓
Sonraki faz
```

---

## KOMUT DOSYASI FORMATI

Claude Code'a verilen her komut dosyası şu formatı izler:

```markdown
# FAZ-XX — [Faz Adı]

## PRECHECK
Şu dosyaların var olduğunu doğrula:
- [ ] MASTER_SPEC.md
- [ ] EVENT_CONTRACTS.md
- [ ] ...
Eksik varsa DUR ve rapor et.

## GÖREVLER
### GÖREV 1 — [Açıklama]
[Komutlar]

### GÖREV 2 — [Açıklama]
[Komutlar]

## AUDIT
Şunları kontrol et:
- TypeScript: sıfır hata
- Uncommitted dosya yok
- DECISION_LOG güncellendi

## RAPOR
/home/turan/İndirilenler/FAZ-XX-RAPOR.md dosyasını yaz:
- Ne yapıldı
- Ne kaldı
- Hata/uyarı var mı
- Sonraki adım ne
```

---

## TASARIM WORKFLOW'U

```
Müteahhit (UI brief verir)
    ↓
Stitch (stitch.withgoogle.com)
    → UI üretir (prompt veya görsel)
    → React/Figma export
    ↓
Gemini CLI
    → DesignSpec.md yazar → DESIGN_SPECS/ klasörüne
    ↓
Claude (TINC spec uyum denetimi)
    → PASS: FINAL onayı verir
    → FAIL: Gemini'ye geri döner
    ↓
Codex (FINAL DesignSpec'e göre implement eder)
    ↓
Gemini Pro (doğrulama: spec'e uyuyor mu?)
```

---

## FAZ PLANI

| Faz | Konu | Durum |
|-----|------|-------|
| FAZ 1 | Workspace kurulum + Denetçi sistemi | DEVAM EDİYOR |
| FAZ 2 | TINC repo temizliği + ROLES.md | BEKLEMEDE |
| FAZ 3 | QRVEE iç yapı denetimi + UIEngine entegrasyonu | BEKLEMEDE |
| FAZ 4 | PNOT Standalone Cloud Functions | BEKLEMEDE |
| FAZ 5 | OPS Core — FIN uygulaması | BEKLEMEDE |
| FAZ 6 | FIRINNA-POS TINC entegrasyonu | BEKLEMEDE |
| FAZ 7 | MINWIN MVP | BEKLEMEDE |
| FAZ 8 | Landing page + Marketing | BEKLEMEDE |
