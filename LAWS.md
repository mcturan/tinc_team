# LAWS — Kanunlar (İhlal Edilemez)

Bu kanunlar yoruma kapalıdır. İstisna yoktur. Değişiklik için Müteahhit onayı gerekir.

---

## TEMEL KANUNLAR

**LAW-001 — Çift Giriş Muhasebesi**  
Her finansal işlemde DR + CR toplamı sıfır olmalıdır. OPS sistemi için zorunlu.

**LAW-002 — Task Pipeline**  
Tüm görevler TASK.md → EXECUTION → RESULT.md pipeline'ından geçer. Adım atlanamaz.

**LAW-003 — Karar Kaydı**  
Tüm kararlar, değişiklikler ve özellikler DECISION_LOG.md'ye commit edilmeden tamamlanmış sayılmaz.

**LAW-004 — Deterministik Sistem**  
Aynı input her zaman aynı output'u üretmeli. Rastgele veya yoruma bağlı davranış kabul edilmez.

**LAW-005 — Event-Only İletişim**  
Uygulamalar birbirine doğrudan API çağrısı yapamaz. Tüm iletişim TINC event bus (Firestore) üzerinden geçer.

**LAW-006 — İmmutable Events**  
`events_*` koleksiyonlarına yazılan event belgeler asla güncellenmez, silinemez. Firestore rules bunu enforce eder.

**LAW-007 — Server Time Otoritesi**  
Tüm iş mantığı hesaplamalarında `serverTime` tek zaman otoritesidir. `clientTime` sadece kayıt amaçlıdır.

**LAW-008 — Offline-First**  
İstemci çevrimdışıyken event'leri OfflineQueue'ya yazar. Bağlantı gelince sırayla flush eder.

**LAW-009 — Audit Zorunluluğu**  
Her task sonucu audit edilir. Audit edilmemiş task tamamlanmış sayılmaz.

**LAW-010 — Spec-First Execution**  
Spec dosyaları (MASTER_SPEC, DATA_MODEL, EVENT_CONTRACTS, CALCULATION_RULES, VALIDATION_RULES, LEDGER_RULES, TRANSACTION_MAPPING, ENFORCEMENT) eksikse hiçbir task execute edilemez.

**LAW-011 — TypeScript Sıfır Hata**  
Her commit öncesi TypeScript build sıfır hata üretmelidir. Hatalı build push edilemez.

**LAW-012 — Commit Format**  
Commit mesajları `TASK-XXX:`, `FAZ-XX:`, `feat:`, `fix:`, `docs:`, `chore:`, `SYNC:` ile başlamalıdır.

**LAW-013 — Local State Geçicidir**  
Local state kalıcı sistem olarak kullanılamaz. Firestore tek kalıcı kaynak olmalıdır.

**LAW-014 — Cross-App Etkileri Sadece Cloud**  
Başka uygulamaları etkileyen tüm işlemler (XP, PNOT notu, bildirim) sadece Cloud Function'da çalışır. İstemci bu mantığı tekrar edemez.

**LAW-015 — Zorlamayan UX**  
Kullanıcıya zorlayıcı UX uygulanamaz. Hiçbir popup, modal veya bildirim kullanıcı aksiyonu olmadan tetiklenemez.

**LAW-016 — DesignSpec FINAL**  
DRAFT statüsündeki DesignSpec ile Codex çalışamaz. Sadece Claude onaylı FINAL DesignSpec implement edilir.

**LAW-017 — Tasarım Ayrımı**  
UI/UX tasarım kararları sadece Gemini + Stitch'e aittir. Claude mimari bu konulara karışmaz.

**LAW-018 — Push Öncesi Denetçi**  
`KANUN-DENETCI.sh` her commit öncesi çalışır. BAŞARISIZ sonuçta push yapılamaz.

**LAW-019 — DECISION_LOG Append-Only**  
DECISION_LOG.md'den satır silinemez, değiştirilemez. Sadece alt tarafa ekleme yapılır.

**LAW-020 — Rol Sınırları**  
Hiçbir agent kendi rol tanımı dışında karar veremez. Sınır aşımı tespit edilirse iş durdurulur ve Müteahhit'e bildirilir.

**LAW-021 — Kanun Değişikliği**  
Bu dosyadaki kanunlar sadece Müteahhit onayıyla değiştirilebilir. Agent önerisi sunabilir, uygulayamaz.
