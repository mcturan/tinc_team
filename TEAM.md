# TEAM — Ekip Üyeleri ve Roller

---

## MÜTEAHHİT
**Kim:** Muhammed Cevad Turan (mcturan@gmail.com)  
**Rol:** Proje sahibi. Tüm kararları verir ve onaylar.  
**Yetki:** Sınırsız. Tek veto hakkı sahibi.  
**Kısıt:** Yok.

---

## MİMAR + ORKESTRATÖR
**Kim:** Claude Pro (Anthropic, claude-sonnet-4-6)  
**Erişim:** claude.ai — her oturumda bu repo okunur  
**Rol:**
- Sistem spec'lerini yazar
- Mimari kararlar verir
- Komut dosyası üretir → `/home/turan/İndirilenler/FAZ-XX-KOMUT.md`
- Her faz bitiminde audit yapar
- Codex ve Gemini'ye iş atar
- Tasarım kararlarına KARIŞMAZ

**Token Politikası:** Token hassastır. Rutin işler Codex/Gemini/Ollama'ya devredilir. Claude sadece mimari, spec ve denetim için kullanılır.

**Oturum Başlangıç Protokolü:** Her yeni oturumda Claude şunları okur:
1. `github.com/mcturan/tinc_team` — ekip ve kanunlar
2. `github.com/mcturan/tinc` — mevcut spec ve DECISION_LOG
3. Kullanıcıdan son faz raporu alır

---

## USTA BAŞI
**Kim:** Claude Code (Anthropic, @anthropic-ai/claude-code v2.1.92+)  
**Kurulum:** `/home/turan/` — yeni PC  
**Rol:**
- Komut dosyasını (`FAZ-XX-KOMUT.md`) okur ve uygular
- Kodu yazar, test eder, commit eder, push eder
- Her faz bitiminde `FAZ-XX-RAPOR.md` yazar → `/home/turan/İndirilenler/`
- `KANUN-DENETCI.sh` çalıştırır her commit öncesi
- DECISION_LOG'u günceller
- agent-ops/ klasöründeki tanımları takip eder

**Kısıt:** Spec dışı karar veremez. Mimari değişiklik öneremez. Değişiklik gerekiyorsa Claude'a sorar.

---

## AĞIR KODLAMA
**Kim:** Codex CLI (@openai/codex v0.118.0) + Codex Go (ücretli)  
**Rol:**
- Büyük kod blokları yazar
- Refactor, migration işlemleri
- Sadece FINAL DesignSpec ve TINC MASTER_SPEC'e göre çalışır
- Spec dışı field, fonksiyon, logic ekleyemez

**Kısıt:** LAW-010 — spec olmadan execution yapamaz. LAW-016 — DRAFT DesignSpec ile çalışamaz.

---

## İÇ MİMAR — TASARIM
**Kim:** Google Stitch (stitch.withgoogle.com) + Gemini CLI (@google/gemini-cli v0.36.0)  
**Rol:**
- **Stitch:** UI üretir. Metin veya görsel prompt → React/HTML export + Figma
  - Ücretsiz: 350 üretim/ay (Gemini 2.5 Pro / Gemini 3)
  - DESIGN.md dosyasına göre tasarlar
  - MCP server ile Claude Code'a doğrudan iletir
- **Gemini CLI:** DesignSpec.md yazar → `DESIGN_SPECS/` klasörüne kaydeder

**Tasarım Pipeline:**
```
Brief (Müteahhit) → Stitch (UI üretir) → React export
                  → Gemini CLI (DesignSpec.md yazar)
                  → Claude (TINC spec uyum denetimi)
                  → FINAL onayı
                  → Codex (implement eder)
```

**Kısıt:** Tasarım dışı hiçbir şeye karışmaz. Backend, veri modeli, event sistemi hakkında karar veremez.

---

## DOĞRULAYICI
**Kim:** Gemini Pro  
**Rol:**
- Codex çıktısının DesignSpec'e uyduğunu doğrular
- Spec compliance kontrol eder
- REJECT veya PASS verir
- Subjektif kalite, performans değerlendirmesi YAPMAZ

---

## YEREL DENETÇİ
**Kim:** Ollama + qwen2.5-coder:7b + deepseek-r1:8b  
**Kurulum:** `ollama pull qwen2.5-coder:7b`  
**Rol:**
- Token sıfır — sınırsız çalışır
- Commit öncesi kod kalite kontrolü
- KANUN-DENETCI.sh entegrasyonu ile çalışır
- Rutin audit, format kontrol

---

## AKIŞ YÖNETİCİSİ
**Kim:** n8n (self-hosted Docker)  
**Erişim:** `http://localhost:5678`  
**Rol:**
- Tüm TINC workflow'larını görsel olarak yönetir
- TINC Firestore event'lerini webhook ile dinler
- Faz raporlarını tetikler
- Özellik takip listesini yönetir
- Slack/Telegram/Discord bildirimleri gönderir

---

## OTONOM DENETÇİ
**Kim:** GitHub Actions + KANUN-DENETCI.sh  
**Tetikleyici:** Her `git push`  
**Dosya:** `/home/turan/workspace/qrvee/.github/workflows/tinc-audit.yml`  
**Rol:**
- TypeScript build kontrolü
- Commit mesaj format kontrolü
- Raporu `/home/turan/İndirilenler/DENETCI-RAPOR-*.txt` dosyasına yazar
- Token sıfır, tamamen otonom

---

## EKIP DIŞI ARAÇLAR (Referans)
| Araç | Amaç | Durum |
|------|------|-------|
| Open WebUI (localhost:3100) | Ollama için ChatGPT arayüzü | Kurulu |
| Aider CLI | Ollama destekli terminal agent | Kurulu |
| GitHub Copilot CLI | VS Code autocomplete | Kurulu |
| OpenClaw | Claude alternatif client | Kurulu |
| GitHub Actions | CI/CD | Aktif |
