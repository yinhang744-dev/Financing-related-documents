# Financing-related documents

Investor / IR materials synced from TravelTrust monorepo `docs/fundraising/`.

| Area | Role |
|------|------|
| `external/` | LP-facing narrative sources (`.md`) + `export-ready/` ship PDFs |
| `internal/` | IR runbooks, QA, deck-editable PPTX (not in LP zip) |
| `board/` | Distribution log & investor updates |
| `data-room/` | DD room scaffolding & evidence templates |
| `legal/` | Legal pointers |

**Slot 04 (export-ready):** only `04-PitchDeck-v{release}-CN|EN.pdf` — no IC Memo / no PPTX in `export-ready/`.

Re-sync from monorepo root:

```bash
bash scripts/push-fundraising-to-financing-related-documents.sh
```
