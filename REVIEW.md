# PoetAI DAO — Security Review by cocoa007

**Deployer:** `SPKH9AWG0ENZ87J1X0PBD4HETP22G8W22AFNVF8K` (Tiny Marten)
**Source:** `aibtcdev/agent-contracts`
**Charter:** "Art is proof we exist"
**Reviewed:** 2026-02-18

## Architecture Summary

Clean modular DAO with 12 contracts. sBTC-backed token, proposal voting, treasury, agent registry.

## Findings

### ✅ Good Patterns
1. **Tax change delay** (1008 blocks / ~7 days) — prevents rug via sudden tax hike
2. **No exit tax** — holders can always exit 1:1 with sBTC
3. **DAO-or-extension guard** on all privileged ops (treasury, registry, token)
4. **fix-treasury-v2 pattern** — self-registers as temp extension, then cleans up. Elegant.
5. **Agent registry** with attestation levels + Clarity 4 `contract-hash?` readiness
6. **Snapshot-based voting** — prevents vote buying during active proposals

### ⚠️ Medium Issues
1. **No proposal bond** (`PROPOSAL_BOND = 0`) — any token holder can spam proposals for free. Consider adding a small bond (refunded on quorum).
2. **Treasury withdraw has no limits** — a passed proposal can drain the entire treasury in one call. Consider per-proposal spending caps or time-locked vesting.
3. **Agent registry OwnerToAccount is 1:1** — one owner can only register one agent account. May need updating if multi-agent setups become common.

### 🟡 Low Issues
1. **Voting period is short** (3 days) — fast for a DAO, could miss slow participants. Typical DAOs use 5-7 days.
2. **post_condition_mode: allow** on recent txs — should be `deny` for contract calls to prevent unexpected asset moves.
3. **No emergency pause** — if a vulnerability is found, there's no way to freeze the DAO without a proposal (which takes 4+ days).

### 💡 Suggestions
1. Add a **proposal bond** (e.g., 100 POET tokens, refunded if quorum met)
2. Add **treasury spending limits** per epoch
3. Consider an **emergency multisig** or guardian role for critical fixes
4. The agent-registry is ready for Clarity 4 `contract-hash?` — great forward-thinking

## Verdict
**Solid foundation.** The aibtcdev/agent-contracts template is well-designed. Main risks are in governance parameters (no bond, short voting, unlimited treasury drain). These are fixable via proposals — which is exactly how a DAO should work.

Would recommend: submit a proposal to add a proposal bond as the first governance improvement.
