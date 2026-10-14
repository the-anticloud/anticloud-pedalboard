# Ethics — PEDALBOARD

**Project:** PEDALBOARD  
**Category:** AUDIO_CONSUMER  
**Upstream:** https://github.com/spotify/pedalboard  
**Pinned commit:** `1fe30ebe36659dced28f739c34511ff9c5a64c9d`  
**Assurance:** 16/16 checks passing  
**Ledger head:** `2ad4f8c8a78395eaf72c25907e468a07056c6a823d419072ddaf597fe7514ee1`  
**Date:** October 2026

## Position

PEDALBOARD is packaged for offline deployment with a verifiable audit trail. The
ethical questions this raises are answered by making the system's behaviour
checkable rather than by policy statements.

## The four commitments

1. **No hidden egress.** The deployment has no external API dependency; this is
   testable by running it with the network disconnected.
2. **Attributable output.** Every artifact is recorded in a hash chain, so what
   the system produced can be reconstructed.
3. **Operator control.** The institution owns the hardware and the keys.
4. **Refusal to overclaim.** Where a certification is not held, the project says
   so rather than implying it.

## Dual use

This project is packaged for civilian and public-sector deployment. Where an
upstream has dual-use characteristics, the licence gate and the reference-only
marking in `BENCH.json` record that.
