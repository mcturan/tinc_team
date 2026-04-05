# FIREBASE — Mevcut Durum ve Gereksinimler

---

## MEVCUT KONFIGÜRASYON
| Parametre | Değer |
|-----------|-------|
| Proje ID | qrvee-project |
| Region | us-central1 |
| Plan | Blaze (kullanım bazlı) |
| Hesap | mcturan@gmail.com |

---

## MEVCUT KOLEKSİYONLAR (QRVEE)
| Koleksiyon | Amaç | Durum |
|-----------|------|-------|
| users/{uid} | Profil, ayarlar | Aktif |
| sessions/{id} | Aktif yayınlar | Aktif |
| follows/{id} | Takip ilişkileri | Aktif |
| notifications/{id} | Bildirimler | Aktif |
| organizations/{id} | Dernekler | Aktif |
| fcmTokens/{uid} | Push notification | Aktif |
| logbook/{qsoId} | QSO günlükleri | Aktif |
| events_qrvee/{id} | TINC event bus (immutable) | Aktif |
| events_pnot/{id} | PNOT events (immutable) | Aktif |
| events_minwin/{id} | MINWIN events (immutable) | Aktif |
| event_processing/{id} | Event işleme durumu | Aktif |

---

## MEVCUT CLOUD FUNCTIONS
| Fonksiyon | Trigger | Durum |
|-----------|---------|-------|
| onQrveeEventCreated | onDocumentCreated(events_qrvee) | Canlı |
| onPnotEventCreated | onDocumentCreated(events_pnot) | Canlı |
| onMinwinEventCreated | onDocumentCreated(events_minwin) | Canlı |
| retryFailedProcessing | onSchedule (5 dk) | Canlı |
| onSessionCreated | Firestore trigger | Canlı |
| cleanExpiredSessions | onSchedule | Canlı |
| sendOrgBroadcast | Callable | Canlı |
| approveUser / rejectUser | Callable | Canlı |
| checkCallsign | Callable | Canlı |
| getUploadSignature | Callable | Canlı |
| deleteVerificationDoc | Callable | Canlı |
| parseQSOText (AI) | Callable | Canlı |
| getPropagationData | Callable | Canlı |
| generateCompanionAdvice | Callable | Canlı |
| fetchDxCluster | Callable | Canlı |
| triggerBackup | Callable | Canlı |

---

## EKSİK / YAPILMASI GEREKENLER

**YÜKSEK ÖNCELİK:**
- [ ] PNOT standalone Firebase projesi — handlePnot şu an qrvee'de hosted
- [ ] PNOT kendi Cloud Functions'ı — bağımsız deploy

**ORTA ÖNCELİK:**
- [ ] OPS Firebase projesi kurulumu (FIN, REMIT, TRADE, DOCS)
- [ ] FIRINNA-POS → events_firinna koleksiyonu entegrasyonu
- [ ] Firestore backup otomasyonu (weekly scheduled)

**DÜŞÜK ÖNCELİK:**
- [ ] MINWIN Firebase koleksiyon tasarımı

---

## GÜVENLİK KURALLARI
- Firestore security rules: events_* koleksiyonları immutable (allow update: false)
- event_processing: sadece Cloud Functions (admin SDK) yazabilir
- Kullanıcı kendi events'ini okuyabilir
- Admin RBAC: superadmin (GODMIN), admin, regular

---

## ENV DEĞİŞKENLERİ GEREKSİNİMLERİ
| Değişken | Konum | Amaç |
|----------|-------|------|
| Firebase config | apps/web/.env.local | Web app |
| Mapbox token | apps/web/.env.local | Harita |
| VAPID key | apps/web/.env.local | Push notification |
| STRIPE_SECRET_KEY | firebase/functions/.env | Stripe ödeme |
| STRIPE_PRO_PRICE_ID | firebase/functions/.env | PRO abonelik |
| STRIPE_WEBHOOK_SECRET | firebase/functions/.env | Webhook doğrulama |
| CLAUDE_API_KEY | firebase/functions/.env | AI özellikleri |
| Cloudinary config | firebase/functions/.env | Belge yükleme |
| APP_URL | firebase/functions/.env | Redirect URL |

**NOT:** Hiçbir .env dosyası commit edilmez.
