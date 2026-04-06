# FEATURES — Özellik Takip Listesi
**Son Güncelleme:** FAZ-05 sonrası (2026-04-06)
Durum: ✅ Tamamlandı (GitHub'da kod var) | 🔄 Devam | ⏳ Beklemede | ❌ Kod yok (spec var) | ⚠️ Spec dışı

---

## QRVEE — TEMEL ALTYAPI
| Özellik | Durum | Not |
|---------|-------|-----|
| Monorepo (Next.js 14 + Expo) | ✅ | |
| Firebase Auth (Google + Apple) | ✅ | |
| Firestore rules + indexes | ✅ | |
| Cloud Functions v2 | ✅ | |
| Admin onay sistemi | ✅ | |
| Callsign doğrulama | ✅ | |
| Cloudinary belge yükleme | ✅ | |
| Feed sayfası | ✅ | |
| Harita (Mapbox) | ✅ | |
| Go QRV / Broadcast | ✅ | |
| Following sistemi | ✅ | |
| Bildirimler (FCM) | ✅ | |
| QSO Logbook (ADIF export) | ✅ | |
| Logbook istatistikler | ✅ | |
| Organizasyon sistemi | ✅ | |
| i18n (17 dil, RTL) | ✅ | |
| Stripe PRO abonelik | ✅ | |
| GDPR | ✅ | |
| CI/CD pipeline | ✅ | |

## QRVEE — AI VE AKILLI ÖZELLİKLER
| Özellik | Durum | Not |
|---------|-------|-----|
| AI Companions RF ♂ + ANT ♀ | ✅ | CharacterWidget.tsx |
| TamagotchiCompanion | ✅ | Yeni bileşen — spec'te yok |
| NOAA Live Space Weather | ✅ | |
| LLM QSO Parser (Claude Haiku) | ✅ | |
| AI Propagation Oracle | ✅ | |
| Voice TTS | ✅ | |
| DX Cluster | ✅ | |
| AgentService (8 senaryo) | ✅ | |
| Friends Finder | ✅ | |

## QRVEE — DASHBOARD + UI ENGINE
| Özellik | Durum | Not |
|---------|-------|-----|
| Dashboard tile marketplace | ✅ | 499 satır, monolitik ama yönetilebilir |
| UIEngine (WidgetRegistry) | ❌ | TINC ZIP'te spec var, kod yok — git'te hiç commit edilmemiş |
| SubscriptionPool | ❌ | Kod yok |
| LifecycleState machine | ❌ | Kod yok |
| WidgetErrorBoundary | ✅ | FAZ-04 implement — tile izolasyonu |
| useWidgetState hook | ❌ | Kod yok |
| Dashboard → UIEngine entegrasyonu | ❌ | FAZ 3 hedefi |

## QRVEE — OYUN SİSTEMİ
| Özellik | Durum | Not |
|---------|-------|-----|
| useGameStore (RF+ANT, XP/Level/Mood/Streak) | ✅ | Tam implement — 250+ satır, persist middleware |
| XP tablosu (8 olay tipi) | ✅ | useGameStore içinde |
| Level sistemi (MAX_LEVEL=50) | ✅ | useGameStore içinde |
| Streak sistemi (onairStreak + noteStreak) | ✅ | useGameStore içinde |
| 7-gün streak bonus (250 XP) | ✅ | useGameStore içinde |
| Mood state machine (5 durum) | ✅ | useGameStore içinde |
| Social events (konuşma baloncuğu) | ✅ | useGameStore.speak() |
| PNOT sync (syncPnot) | ✅ | useGameStore içinde |
| LeagueBadge + LeagueTile | ✅ | Ayrı component |
| Leaderboard sayfası | ✅ | leaderboard/page.tsx |
| Flow Engine + WorkItem | ❌ | Spec var (TINC ZIP), git'te hiç commit edilmemiş |
| FlowWidget (timeline/list) | ❌ | Spec var, kod yok |
| Flow Motion (Framer) | ❌ | Spec var, kod yok |
| Global Pulse | ❌ | Spec var, kod yok |
| Mascot Engine (5-state machine) | ❌ | TamagotchiCompanion farklı bir implementasyon |
| Game Launcher + Registry | ✅ | FAZ-05 implement — GameLauncher, GameRegistry |
| RF Signal Tune | ✅ | FAZ-05 implement — RfSignalTuneGame.tsx |
| RF Propagation | ⏳ | FAZ-06 — placeholder var |
| RF World | ⏳ | FAZ-06 — placeholder var |
| Badge sistemi | ❌ | Kod yok |
| Quest sistemi | ❌ | Kod yok |
| Ghost sistemi | ✅ | FAZ-05 implement — useGhostStore.ts |
| Challenge modu | ✅ | FAZ-05 implement — useChallengeStore.ts |
| useContestStore | ✅ | Contest sistemi — mock data |

## QRVEE — SPEC DIŞI (Müteahhit Kararı Gerekiyor)
| Özellik | Durum | Not |
|---------|-------|-----|
| Modem stack (AFSK Bell 202 + AX.25) | ⚠️ | Spec FAZ 9+, başlanmış — tam APRS encoder |
| CAT kontrol (Yaesu FT-897D) | ⚠️ | ESP32 bridge protokolü dahil |
| SDR Waterfall (Canvas 60fps) | ⚠️ | Mock FFT, Web Audio API altyapısı var |
| YLRL sayfası | ⚠️ | Young Ladies Radio League grant formu |
| Kiosk modu | ⚠️ | Tam screen shack dashboard, Wake Lock API |
| pnot-client.ts | ⚠️→❌ | LAW-005 ihlali — FAZ-03'te devre dışı bırakıldı |

## TINC — EVENT BUS
| Özellik | Durum | Not |
|---------|-------|-----|
| Event System V2.3 | ✅ | Production'da canlı |
| Router CF | ✅ | |
| Retry CF | ✅ | |
| Firestore rules hardening | ✅ | |
| MASTER_SPEC ve tüm spec dosyaları | ✅ | |
| KANUN-DENETCI.sh | ✅ | FAZ-01'de kuruldu |
| GitHub Actions CI/CD | ✅ | FAZ-01'de kuruldu |

## PNOT
| Özellik | Durum | Not |
|---------|-------|-----|
| handlePnot (qrvee'de hosted) | ✅ | 2 dosyada: handlers/pnot.ts + pnot.ts |
| session.started → pnot_notes | ✅ | |
| qso.logged → pnot_notes | ✅ | |
| Standalone PNOT Cloud Functions | ⏳ | FAZ 4 |

## OPS
| Özellik | Durum | Not |
|---------|-------|-----|
| LEDGER_RULES, CALCULATION_RULES spec | ✅ | |
| FIN, REMIT, TRADE, DOCS uygulamaları | ⏳ | FAZ 5+ |

## MARKETİNG
| Özellik | Durum | Not |
|---------|-------|-----|
| Landing page (<1sn wow) | ⏳ | FAZ 8 |
| İsim değişikliği (FOXR adayı) | ⏳ | FAZ 8 — Müteahhit onayı bekliyor |
| Platform maskotu (antropomorfik tilki) | ⏳ | FAZ 8 |
