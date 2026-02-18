# Sanitization Changelog

Changes made from private → public version for ClawHub release.

## Identifying Information Removed

| File | What was removed |
|------|-----------------|
| `heartbeat-check.sh` | Hardcoded `cd /Users/nealme/clawd` → uses `$OPENCLAW_WORKSPACE` env var |
| `generate-persona.ts` | Default agent name "Aria" removed — now requires user input |
| `generate-persona.sh` | Default agent name "Aria" removed — now requires user input |
| `onboard.ts` | Default agent name "Aria" removed — now requires user input |
| `generate-persona.ts` | Fixed duplicate `import { fileURLToPath }` statement |
| `package.json` | Removed repository/bugs/homepage URLs pointing to specific GitHub repos |

## Files NOT Included (user-specific)

The entire `PERSONA/` folder from the original was excluded:
- `core-aria.md` — Personal persona file
- `core-wifey.md` — Personal persona file
- `core-dwight.md` — Personal persona file
- `core-phoenix.md` — Personal persona file
- `core-donna.md` — Personal persona file
- `core-rich.md` / `core-rich-v2.md` — Personal persona files
- `core-challenger.md` — Personal persona file
- `core-faithful-scribe.md` / `core-covenant-scribe.md` — Personal persona files
- `core-jarvis.md` — Personal persona file
- `voice-utah-mormon.md` — User-specific voice profile
- `voice-balanced-lds-scholar.md` — User-specific voice profile
- `CONTENT_HUMANIZATION_RULES.md` — User-specific content rules
- `active-persona.md` — Runtime state
- `.current-mode` / `current-mode.txt` — Runtime state

## Breaking Changes from Original

1. **No default agent name** — `generate-persona.ts`, `generate-persona.sh`, and `onboard.ts` no longer default to "Aria". Users must provide their own name.
2. **No hardcoded workspace path** — `heartbeat-check.sh` requires `$OPENCLAW_WORKSPACE` or must be run from the workspace directory.
3. **No bundled personas** — The original included 12+ pre-built persona files. The public version generates personas fresh via onboarding.

## Security Audit

- ✅ `heartbeat-check.sh` — No hardcoded paths, uses env var
- ✅ `analyze-session.ts` — Uses `process.cwd()`, no path assumptions
- ✅ `weekly-report.ts` — Generic templates only, no personal data
- ✅ `mode-switcher.ts` — Clean, no identifying info
- ✅ `cli.ts` — Clean, no identifying info
- ✅ `init.ts` — Templates use placeholder text only
- ✅ `expand.ts` — Interactive, no defaults with personal info
- ✅ `onboard.ts` — Interactive, no defaults with personal info
- ✅ `generate-demo.ts` — Generic template, no personal info
- ✅ No secrets, credentials, or API keys in any file
- ✅ `.clawhubignore` properly excludes user-generated PERSONA/ files
