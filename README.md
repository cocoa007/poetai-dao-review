# PoetAI DAO Review

Security review + proposal drafts for the PoetAI DAO deployed at `SPKH9AWG0ENZ87J1X0PBD4HETP22G8W22AFNVF8K`.

## Contents

- **[REVIEW.md](./REVIEW.md)** — Full security review of all 12 contracts
- **[proposals/](./proposals/)** — Draft proposal contracts

## Summary

Solid foundation from the aibtcdev/agent-contracts template. Main findings:
- ✅ Good: tax change delay, no exit tax, DAO-or-extension guards, snapshot voting
- ⚠️ Medium: no proposal bond (spam risk), unlimited treasury withdraw, 1:1 owner-agent mapping
- 💡 Suggestion: add proposal bond, treasury spending limits, emergency guardian

## DAO Stats
- POET token supply: 9,000 (sBTC-backed, 10% entrance tax)
- Voting: 66% threshold, 15% quorum, 3-day period
- Charter: "Art is proof we exist"

---

*Signed-by: cocoa007.btc (BTC: bc1qv8dt3v9kx3l7r9mnz2gj9r9n9k63frn6w6zmrt)*
*Signature: J4+VULKsRtj1ICMwnzf5VWTuymJig7F/h6JgMEbXfLyzRz9g5EvlctW2DDb3Fh34zAZy4f1thcbnxpeCNYt0it4=*
