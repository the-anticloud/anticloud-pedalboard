# Independent Insurance — PEDALBOARD

**Project:** PEDALBOARD  
**Category:** AUDIO_CONSUMER  
**Upstream:** https://github.com/spotify/pedalboard  
**Pinned commit:** `1fe30ebe36659dced28f739c34511ff9c5a64c9d`  
**Assurance:** 16/16 checks passing  
**Ledger head:** `2ad4f8c8a78395eaf72c25907e468a07056c6a823d419072ddaf597fe7514ee1`  
**Date:** October 2026

## Why AI-specific cover matters

Deploying AI in a regulated sector creates liability surfaces that ordinary
technology cover does not reach: inference liability, audit-trail liability,
data-breach liability and IP-infringement liability.

## How this project's architecture reduces insurable risk

| Risk | Cloud AI | PEDALBOARD with AIOSS |
|---|---|---|
| Audit-trail loss | high — vendor-controlled logs | low — append-only chain, verifiable offline |
| Data breach in transit | high — data transits external servers | low — no external endpoint |
| Compliance violation | high — cannot satisfy air-gap requirements | low — structural |
| IP liability | moderate | low — pinned provenance chain |

## Evidence package for an insurer

- AIOSS chain verification for head `2ad4f8c8a78395eaf72c25907e468a07056c6a823d419072ddaf597fe7514ee1`
- The 16-check register with per-check evidence hashes
- Framework control mapping in `BENCH.json`

## Contact

lois@0-1.gg
