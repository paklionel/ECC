# Quick Start

## Tests

```bash
node tests/run-all.js                                   # all tests
ECC_TEST_JOBS=4 node tests/run-all.js                   # parallel pool
ECC_TEST_ONLY=package-manager,hooks/hooks.test node tests/run-all.js
node tests/hooks/hooks.test.js                          # single file
```

## Lint

```bash
npx eslint .
npx markdownlint-cli '**/*.md' --ignore node_modules
```

## Token budget

```bash
cto measure        # tokens loaded at session start
cto audit --json   # structural checks (exits 1 on errors)
```
