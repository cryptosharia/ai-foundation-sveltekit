# Security Audit Report Template

```md
## Security Audit Report

### Scope

- <changed files/modules>

### Findings

- <none>
  or
- path: `path/to/file`
  risk: `<critical|high|medium|low> - <impact>`
  fix: `<what changed or required fix>`

### Residual Risk

- <none>
  or
- <deferred risk + rationale>

### Verification Gates

- `npm run check`: <pass/fail/not available>
- `npm run lint`: <pass/fail/not available>
- `npm test`: <pass/fail/not available>
```
