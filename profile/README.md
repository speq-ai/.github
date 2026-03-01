![enthropic](banner.svg)

A declarative format for AI-assisted development.

You write one `.enth` file before writing any code. An AI reads it as context and generates code within the architectural decisions you've already made — not around them.

```
VERSION 1.0

PROJECT myapp
  LANG   python
  STACK  fastapi, postgresql
  ARCH   layered

VOCABULARY
  AuthToken    # never: jwt, token, access_token
  UserId       # never: user_id, uid, uuid

ENTITY user, session, order

LAYERS
  API
    CALLS   SERVICE
    NEVER   direct_database_access
  SERVICE
    CALLS   REPOSITORY
    NEVER   http_response_construction

CONTRACTS
  session.authenticate  ALWAYS  bcrypt-password-verification
  order.*               REQUIRES authenticated-user
```

The AI reads this. `AuthToken` stays `AuthToken` in session two, session ten, and on a different machine. The layer boundaries hold. The contracts don't drift.

---

## Repositories

**[enthropic](https://github.com/Enthropic-spec/enthropic)** — The specification.  
EBNF grammar, construct reference, validation rules, examples across domains.

**[enthropic-tools](https://github.com/Enthropic-spec/enthropic-tools)** — The CLI toolkit.  
Single binary. No runtime dependencies. Validate, manage state, store secrets encrypted, chat with AI using your spec as context.

```bash
# install (requires Rust)
cargo install --git https://github.com/Enthropic-spec/enthropic-tools

enthropic setup         # configure your API key (Anthropic, OpenAI, OpenRouter)
enthropic new           # guided .enth creation wizard
enthropic validate      # validate spec, auto-create state + vault
enthropic build         # AI chat session with your spec pre-loaded as context
```

---

## Status

Specification v0.1.0 — early development.  
The format is working and usable. Breaking changes are possible before v1.0.
