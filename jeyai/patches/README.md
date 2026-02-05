# JeyAI Patches for OpenClaw

This directory contains monkey-patches for OpenClaw upstream code.

## ⚠️ Patches Are Last Resort

Before adding a patch:
1. Can you EXTEND in `/jeyai/integrations/` or `/jeyai/overrides/`?
2. Can you submit a PR to upstream OpenClaw?
3. Is there a configuration option you missed?

Only create a patch if ALL above are impossible.

## Patch Format

Each patch file must include:
1. **What** it patches (file:line)
2. **Why** it's needed (upstream limitation)
3. **Removal plan** (when upstream fixes / alternative approach)

## Active Patches

| Patch File | Target | Reason | Removal Plan |
|------------|--------|--------|--------------|
| (none yet) | | | |

## Adding a Patch

1. Create ADR in `/home/efmua/Jeyai/docs/adr/`
2. Add patch file here with clear documentation
3. Update this table
4. Create GitHub issue for removal tracking

## References

- Fork Strategy: `/home/efmua/Jeyai/docs/fork-tracking/OPENCLAW_MERGE_STRATEGY.md`
