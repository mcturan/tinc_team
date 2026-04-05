# FEATURES — Özellik Takip Listesi

Bu liste tüm uygulamalardaki özellikleri kapsar.
Durum: ✅ Tamamlandı | 🔄 Devam Ediyor | ⏳ Beklemede | ❌ İptal

---

## QRVEE

### Temel Altyapı
| Özellik | Durum | Faz |
|---------|-------|-----|
| Monorepo yapısı (Next.js + Expo) | ✅ | - |
| Firebase Auth (Google + Apple OAuth) | ✅ | - |
| Firestore rules + indexes | ✅ | - |
| Cloud Functions v2 | ✅ | - |
| Admin onay sistemi | ✅ | - |
| Callsign doğrulama | ✅ | - |
| Cloudinary belge yükleme | ✅ | - |

### Temel Özellikler
| Özellik | Durum | Faz |
|---------|-------|-----|
| Feed sayfası (aktif sesyonlar) | ✅ | - |
| Harita (Mapbox, pulse animasyonları) | ✅ | - |
| Go QRV / Broadcast sayfası | ✅ | - |
| Following sistemi | ✅ | - |
| Bildirimler (FCM push) | ✅ | - |
| QSO Logbook (ADIF 3.1.0 export) | ✅ | - |
| Logbook istatistikler (7g/30g/90g) | ✅ | - |
| Organizasyon sistemi | ✅ | - |
| i18n (17 dil, RTL Arabic) | ✅ | - |
| Stripe PRO abonelik | ✅ | - |
| GDPR | ✅ | - |
| CI/CD pipeline | ✅ | - |

### AI ve Akıllı Özellikler
| Özellik | Durum | Faz |
|---------|-------|-----|
| AI Companions RF ♂ + ANT ♀ (Claude Haiku) | ✅ | - |
| NOAA Live Space Weather | ✅ | - |
| LLM QSO Parser (doğal dil → QSO) | ✅ | - |
| AI Propagation Oracle | ✅ | - |
| Voice TTS (Expo Speech) | ✅ | - |
| DX Cluster (DXWatch API) | ✅ | - |
| AgentService (8 senaryo) | ✅ | - |
| Friends Finder (callsign scanner) | ✅ | - |

### Dashboard + UI Engine
| Özellik | Durum | Faz |
|---------|-------|-----|
| Modular Dashboard + Tile Marketplace | ✅ | - |
| UIEngine (WidgetRegistry, SubscriptionPool) | ✅ | - |
| Lifecycle state machine (MOUNT/ACTIVE/HIDDEN/ERROR) | ✅ | - |
| WidgetErrorBoundary | ✅ | - |
| Tile: WorldClock, SolarFluxHistory, DXCluster, Grayline | ✅ | - |
| Tile: AI Companions, Smart Shack Webhooks | ✅ | - |
| UIEngine → gerçek dashboard entegrasyonu | ⏳ | FAZ 3 |

### Oyun Sistemi
| Özellik | Durum | Faz |
|---------|-------|-----|
| Flow Engine + WorkItem sistemi | ✅ | - |
| FlowWidget (timeline + list mode) | ✅ | - |
| Flow Motion (Framer Motion) | ✅ | - |
| Global Pulse (dashboard awareness) | ✅ | - |
| Mascot Engine (5 state machine) | ✅ | - |
| Game Launcher + Registry | ✅ | - |
| RF Signal Tune (hook game) | ✅ | - |
| RF Propagation (intelligence game) | ✅ | - |
| RF World (20x20 world game) | ✅ | - |
| XP sistemi (curved thresholds) | ✅ | - |
| Level sistemi (L1-L10+) | ✅ | - |
| Badge sistemi | ✅ | - |
| Quest sistemi (daily/weekly) | ✅ | - |
| Ghost sistemi (best run kayıt) | ✅ | - |
| Challenge modu | ✅ | - |
| Leaderboard | ✅ | - |
| User Profile (avatar, level, XP) | ✅ | - |

### Offline + PWA
| Özellik | Durum | Faz |
|---------|-------|-----|
| OfflineQueue (IndexedDB) | ✅ | - |
| Offline password (SecureStore) | ✅ | - |
| PWA resilience banner | ✅ | - |
| Offline sync conflict resolution | ✅ | - |

---

## TINC (Event Bus + Core)

| Özellik | Durum | Faz |
|---------|-------|-----|
| Event System V2.3 (immutable events) | ✅ | - |
| events_qrvee / events_pnot / events_minwin | ✅ | - |
| event_processing (per-consumer state) | ✅ | - |
| Router CF (onDocumentCreated) | ✅ | - |
| Retry CF (5 dakika scheduler) | ✅ | - |
| Firestore atomic transaction locking | ✅ | - |
| Dead-letter pattern | ✅ | - |
| Firestore security rules hardening | ✅ | - |
| MASTER_SPEC, DATA_MODEL, CALCULATION_RULES | ✅ | - |
| FLOW_UI_BRIDGE, AGENT_PROTOCOL | ✅ | - |
| KANUN-DENETCI.sh | 🔄 | FAZ 1 |
| GitHub Actions CI/CD | 🔄 | FAZ 1 |

---

## PNOT

| Özellik | Durum | Faz |
|---------|-------|-----|
| handlePnot (QRVEE'de hosted) | ✅ | - |
| session.started → pnot_notes | ✅ | - |
| qso.logged → pnot_notes | ✅ | - |
| Standalone PNOT Cloud Functions | ⏳ | FAZ 4 |
| PNOT bağımsız Firebase projesi | ⏳ | FAZ 4 |

---

## OPS

| Özellik | Durum | Faz |
|---------|-------|-----|
| LEDGER_RULES, CALCULATION_RULES spec | ✅ | - |
| FIN uygulaması | ⏳ | FAZ 5 |
| REMIT uygulaması | ⏳ | FAZ 5 |
| TRADE uygulaması | ⏳ | FAZ 6 |
| DOCS uygulaması | ⏳ | FAZ 6 |

---

## FIRINNA-POS

| Özellik | Durum | Faz |
|---------|-------|-----|
| HTML tabanlı POS | ✅ | - |
| TINC event entegrasyonu | ⏳ | FAZ 6 |

---

## MINWIN

| Özellik | Durum | Faz |
|---------|-------|-----|
| MINWIN_VISION.md | ✅ | - |
| Firestore schema tasarımı | ⏳ | FAZ 7 |
| Reverse auction engine | ⏳ | FAZ 7 |

---

## MARKETING + LANDING

| Özellik | Durum | Faz |
|---------|-------|-----|
| <1 saniye WOW etkisi landing page | ⏳ | FAZ 8 |
| Maskot entegrasyonu (landing) | ⏳ | FAZ 8 |
| SEO optimizasyonu | ⏳ | FAZ 8 |
