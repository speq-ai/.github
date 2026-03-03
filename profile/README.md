<p align="center">
  <img src="banner.svg" alt="enthropic" width="840"/>
</p>

---

<p align="center">
  A structured format for architectural decisions — readable by humans, unambiguous for AI.
</p>

<br/>

You write one `.enth` file before writing any code. Every AI session reads it as context. The same spec on two machines, with two different models, produces architecturally identical output.

`.md` files help — but natural language is inherently ambiguous. A structured spec has a grammar, a parser, and a validator. The AI cannot misread it.

```
VERSION 1

PROJECT "my-api"
  LANG    python
  STACK   fastapi, postgresql, redis
  ARCH    layered

ENTITY user, session, order

LAYERS
  API     CALLS SERVICE
  SERVICE CALLS STORAGE
  STORAGE

CONTRACTS
  user.password  NEVER    plaintext
  admin.*        REQUIRES verified-auth
```

---

**[enthropic](https://github.com/Enthropic-spec/enthropic)** — the spec format. Grammar, validation rules, examples.

**[enthropic-tools](https://github.com/Enthropic-spec/enthropic-tools)** — the CLI companion.

```bash
npm install -g enthropic
```

<p align="center">
  <sub><img src="https://img.shields.io/badge/spec-v0.1.0-ffafff?style=flat&labelColor=0f0f1a" alt="spec v0.1.0"/>
  &nbsp;
  <img src="https://img.shields.io/badge/license-MIT-lightgrey.svg" alt="MIT"/></sub>
</p>
