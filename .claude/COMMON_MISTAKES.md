# Common Mistakes

**⚠️ CRITICAL - Read at session start**

---

## Top 5 Critical Mistakes

### 1. Hook blocks tool execution

**Symptom**: Claude Code tool calls fail or hang after a hook change.
**Check**: Does the hook `exit` non-zero on parse/non-critical errors, or make network calls in a blocking hook?
**Fix**: Always `exit 0` on non-critical errors, log to stderr with a `[HookName]` prefix, keep PreToolUse/stop hooks <200ms.

### 2. Hook bypasses runtime gating

**Symptom**: `ECC_HOOK_PROFILE` / `ECC_DISABLED_HOOKS` have no effect on a hook.
**Check**: Is the hook routed through `scripts/hooks/run-with-flags.js`?
**Fix**: Wire every hook through `run-with-flags.js` (export `run(rawInput)`).

### 3. ESM or TypeScript in scripts

**Symptom**: `SyntaxError: Cannot use import statement outside a module`.
**Check**: `import`/`export` in a `.js` file under `scripts/`.
**Fix**: CommonJS only (`require`/`module.exports`), plain `.js`; ESM only in `.mjs`.

### 4. Missing tests for new code

**Symptom**: CI fails or review rejects the change.
**Check**: New `scripts/lib/*` without `tests/lib/*`, new hook without `tests/hooks/*`.
**Fix**: Add the matching test and run `node tests/run-all.js`.

### 5. Serial-only suites run in the pool

**Symptom**: Flaky failures around `.opencode/dist` or time budgets with `ECC_TEST_JOBS`.
**Check**: Suite rebuilds/backs up `.opencode/dist` or asserts a time budget.
**Fix**: List it in `ECC_TEST_SERIAL` (see QUICK_START.md).

---

**Last Updated**: 2026-11-04
