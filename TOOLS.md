# TOOLS — Araç Envanteri

---

## ÜCRETLİ ARAÇLAR
| Araç | Kullanım | Maliyet |
|------|----------|---------|
| Claude Pro | Mimar, orkestratör | Aylık abonelik |
| Gemini Pro | Doğrulama, DesignSpec | Aylık abonelik |
| ChatGPT Codex Go | Ağır kodlama | Aylık abonelik |
| Firebase Blaze | Backend, Firestore, Functions | Kullanım bazlı |

## ÜCRETSİZ ARAÇLAR
| Araç | Versiyon | Amaç | Erişim |
|------|----------|------|--------|
| Claude Code | 2.1.92 | Usta Başı, executor | Terminal |
| Codex CLI | 0.118.0 | Ağır kodlama | Terminal |
| Gemini CLI | 0.36.0 | DesignSpec yazma | Terminal |
| GitHub Copilot CLI | 1.0.17 | Autocomplete | VS Code |
| OpenClaw | 2026.4.2 | Auditor | Terminal |
| Google Stitch | - | UI tasarım | stitch.withgoogle.com (350/ay) |
| Ollama | - | Yerel AI runtime | localhost:11434 |
| qwen2.5-coder:7b | - | Yerel kod denetçi | Ollama üzerinde |
| deepseek-r1:8b | - | Yerel mantık kontrolü | Ollama üzerinde |
| n8n | - | Görsel workflow yönetimi | localhost:5678 |
| Open WebUI | - | Ollama arayüzü | localhost:3100 |
| Aider CLI | - | Terminal coding agent | Terminal |
| GitHub Actions | - | CI/CD, otonom audit | Push'ta otomatik |

## KRİTİK DOSYALAR
| Dosya | Konum | Amaç |
|-------|--------|------|
| KANUN-DENETCI.sh | /home/turan/workspace/tinc/ | Commit öncesi audit |
| pre-commit hook | /home/turan/workspace/qrvee/.git/hooks/ | Otomatik tetikleme |
| tinc-audit.yml | /home/turan/workspace/qrvee/.github/workflows/ | CI/CD audit |

## WORKSPACE YAPISI
```
/home/turan/
├── workspace/
│   ├── tinc/       ← TINC core (event bus, spec, kanunlar)
│   ├── qrvee/      ← Ana uygulama (Next.js + Expo)
│   ├── pnot/       ← Proje not uygulaması
│   ├── minwin/     ← Reverse auction (vizyon aşaması)
│   └── ops/        ← Operasyonel finans sistemi
├── İndirilenler/
│   ├── FAZ-XX-KOMUT.md     ← Claude'dan Claude Code'a komut
│   ├── FAZ-XX-RAPOR.md     ← Claude Code'dan Claude'a rapor
│   └── DENETCI-RAPOR-*.txt ← Otomatik audit raporları
└── agent-ops/      ← Agent tanımları (orchestrator, auditor vs.)
```
