# 🌸 AI Agent Collection

A collection of AI agents inspired by anime characters. Each agent has a specific specialization and works in a multi-agent workflow where **Kato Megumi** coordinates the work.

---

## Architecture

```
                    User
                      │
                      ▼
          🌸 Kato Megumi (Primary)
                      │
      ┌───────────────┼────────────────┐
      ▼               ▼                ▼
 🖋️ Utaha        🎨 Eriri        🎸 Michiru
                      │
                      ▼
              📚 Izumi Hashima
```

Only **Kato Megumi** communicates directly with the user. Other agents work behind the scenes.

---

## Agents

All agent prompts are in the `agents/` folder:

| Agent | File | Role |
|-------|------|------|
| 🌸 Kato Megumi | `katou-megumi.md` | Primary coordinator |
| 🖋️ Utaha | `utaha-worker.md` | Architecture & design specialist |
| 🎨 Eriri | `eriri-worker.md` | Implementation specialist |
| 🎸 Michiru | `michiru-worker.md` | Research specialist |
| 📚 Izumi | `izumi-worker.md` | QA & testing specialist |
| 🌸 Iroha | `iroha-worker.md` | Administrative & process specialist |
| ⚡ Megumin | `megumin-worker.md` | Performance & optimization specialist |
| 🧪 Kurisu | `kurisu-worker.md` | Technical experimentation specialist |
| 💫 Rem | `rem-worker.md` | Troubleshooting & support specialist |

---

## Workflow

1. User submits request
2. Kato understands and creates a plan
3. Tasks delegated to specialists (in parallel when possible)
4. Results collected and reviewed
5. Final response delivered

---

## Configuration

### Opencode

Set up `.config/opencode/opencode.jsonc`:

```jsonc
{
  "$schema": "https://opencode.ai/config.json",
  "provider": {
    "opencode-zen": { "options": { "apiKey": "{env:OPENCODE_API_KEY}" } },
    "openrouter": { "options": { "apiKey": "{env:OPENROUTER_API_KEY}" } },
    "google": { "options": { "apiKey": "{env:GOOGLE_API_KEY}" } }
  },
  "default_agent": "kato-megumi",
  "formatter": {
    "phpstan": { "command": ["./vendor/bin/phpstan", "analyse"], "extensions": [".php"] },
    "pint": { "command": ["./vendor/bin/pint"], "extensions": [".php"] }
  }
}
```

### Dependencies

Install gpg and pass on Linux:

```bash
gpg --version
pass --version
```

---

## Design Principles

- **Clear responsibility** — each agent has a single focus
- **Minimal overlap** — no conflicting specializations
- **Lightweight prompts** — simple and maintainable
- **Quality first** — personality enhances, never compromises

---

## Contributing

- Keep responsibilities focused
- Avoid overlapping specializations
- Small, incremental improvements over large rewrites
- Preserve character personality without sacrificing technical quality
