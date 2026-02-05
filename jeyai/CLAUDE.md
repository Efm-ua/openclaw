# CLAUDE.md - JeyAI OpenClaw Customizations

This directory (`/home/efmua/Jeyai/openclaw-fork/jeyai/`) is the **ONLY** place where JeyAI-specific code should be added to the OpenClaw fork.

## 🚨 CRITICAL: NO UPSTREAM EDITS POLICY

**NEVER modify files outside this directory in the openclaw-fork!**

```
openclaw-fork/
├── src/           # ❌ FORBIDDEN - upstream code
├── packages/      # ❌ FORBIDDEN - upstream packages
├── apps/          # ❌ FORBIDDEN - upstream apps
├── extensions/    # ❌ FORBIDDEN - upstream extensions
├── skills/        # ❌ FORBIDDEN - upstream skills
├── docs/          # ❌ FORBIDDEN - upstream documentation
├── scripts/       # ❌ FORBIDDEN - upstream scripts
├── test/          # ❌ FORBIDDEN - upstream tests
├── ui/            # ❌ FORBIDDEN - upstream UI
├── vendor/        # ❌ FORBIDDEN - upstream vendor
└── jeyai/         # ✅ THIS DIRECTORY - all JeyAI customizations go here
```

## Directory Structure

```
jeyai/
├── integrations/     # Adapters for JeyAI services
│   ├── telegram.ts   # Telegram Mini App integration
│   ├── supabase.ts   # Supabase auth/DB adapter
│   └── gateway.ts    # JeyAI Gateway client
├── overrides/        # Override upstream behavior
│   └── session.ts    # Extended session with tenant context
├── patches/          # Monkey-patches (last resort)
│   └── README.md     # Document each patch and removal plan
└── CLAUDE.md         # This file
```

## Extension Pattern

Always EXTEND upstream, never MODIFY:

```typescript
// ✅ CORRECT: Import and extend
import { Session } from '../src/session';

export class TenantSession extends Session {
  tenantId: string;

  constructor(tenantId: string, ...args: ConstructorParameters<typeof Session>) {
    super(...args);
    this.tenantId = tenantId;
  }
}
```

```typescript
// ❌ WRONG: Modifying upstream file directly
// File: ../src/session.ts (FORBIDDEN!)
```

## Why This Matters

1. **Upstream Merges** - We merge OpenClaw updates quarterly. Any changes in `src/` will cause conflicts.
2. **CI Enforcement** - CI fails if `git diff` shows changes in forbidden paths.
3. **Code Review** - P0 rejection for any upstream modifications.

## References

- Fork Strategy: `/home/efmua/Jeyai/docs/fork-tracking/OPENCLAW_MERGE_STRATEGY.md`
- AD-SDD v2.1: `/home/efmua/Jeyai/docs/adr/ADR-001-methodology-adsdd.md`
- Main CLAUDE.md: `/home/efmua/Jeyai/CLAUDE.md`
