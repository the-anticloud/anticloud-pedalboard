# Educators — PEDALBOARD

**Project:** PEDALBOARD  
**Category:** AUDIO_CONSUMER  
**Upstream:** https://github.com/spotify/pedalboard  
**Pinned commit:** `1fe30ebe36659dced28f739c34511ff9c5a64c9d`  
**Assurance:** 16/16 checks passing  
**Ledger head:** `2ad4f8c8a78395eaf72c25907e468a07056c6a823d419072ddaf597fe7514ee1`  
**Date:** October 2026

## Teaching with PEDALBOARD

The project is usable as a worked example of offline-first packaging with a
cryptographic audit chain. It ships with the assurance suite, the evidence
register and the ledger, so students can verify claims rather than take them on
faith.

## Suggested exercises

1. Run `python tools/run_bench.py --out BENCH.json` and read the 16 results.
2. Recompute the SHA3-256 of a row's evidence file and compare to the register.
3. Walk the AIOSS chain from genesis to head `2ad4f8c8a78395eaf72c25907e468a07056c6a823d419072ddaf597fe7514ee1` and confirm every link.
4. Break one artifact and observe the chain fail to verify.

## Licence for teaching

Apache 2.0 terms apply to academic and teaching use. See `24_ANTICOMMONS_LICENSE`.
