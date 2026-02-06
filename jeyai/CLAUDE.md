# CLAUDE.md — JeyAI OpenClaw Customizations

`/home/efmua/Jeyai/openclaw-fork/jeyai/` = ONLY allowed location for JeyAI code in fork.

## 🚨 NO UPSTREAM EDITS (CRITICAL)

NEVER modify outside this dir. Forbidden:
```
openclaw-fork/
├── src/           # ❌ FORBIDDEN
├── packages/      # ❌ FORBIDDEN
├── apps/          # ❌ FORBIDDEN
├── extensions/    # ❌ FORBIDDEN
├── skills/        # ❌ FORBIDDEN
├── docs/          # ❌ FORBIDDEN
├── scripts/       # ❌ FORBIDDEN
├── test/          # ❌ FORBIDDEN
├── ui/            # ❌ FORBIDDEN
├── vendor/        # ❌ FORBIDDEN
└── jeyai/         # ✅ JeyAI customizations
```

## Structure
```
jeyai/
├── integrations/     # Telegram, Supabase, Gateway adapters
├── overrides/        # Override upstream behavior (e.g. session.ts)
├── patches/          # Monkey-patches (last resort, document removal plan)
└── CLAUDE.md
```

## Extension Pattern

EXTEND upstream, NEVER MODIFY:
```typescript
// ✅ Import and extend
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
// ❌ FORBIDDEN: modifying ../src/session.ts directly
```

## Why
1. Upstream merges quarterly — src/ changes cause conflicts
2. CI fails on forbidden path changes
3. Code review: P0 rejection for upstream modifications

## References
- Fork Strategy: `/home/efmua/Jeyai/docs/fork-tracking/OPENCLAW_MERGE_STRATEGY.md`
- AD-SDD: `/home/efmua/Jeyai/docs/adr/ADR-001-methodology-adsdd.md`
- Main CLAUDE.md: `/home/efmua/Jeyai/CLAUDE.md`
