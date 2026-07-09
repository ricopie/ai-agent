# 🌸 AI Agent Collection

A collection of AI agents inspired by the heroines from **Saekano: How to Raise a Boring Girlfriend**.

Each character represents a specific specialization instead of being merely a personality. The personality adds flavor, while the primary focus remains on solving technical tasks efficiently.

The agents are designed for multi-agent workflows where a single primary assistant coordinates several specialist subagents.

---

## Overview

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

Only **Kato Megumi** communicates directly with the user.

All other agents work behind the scenes and return their results to Kato for review before a final response is produced.

---

## Configuration

### Opencode

Open the file in `.config/opencode/opencode.jsonc`, below I added the default agent, provider, and formatter (phpstan and pint) for the Laravel project. The provider line for our API key uses an environment encrypted with gpg and pass on Linux.

```jsonc
{
  "$schema": "https://opencode.ai/config.json",
  "provider": {
    "opencode-zen": {
      "options": {
        "apiKey": "{env:OPENCODE_API_KEY}",
      },
    },
    "openrouter": {
      "options": {
        "apiKey": "{env:OPENROUTER_API_KEY}",
      },
    },
    "google": {
      "options": {
        "apiKey": "{env:GOOGLE_API_KEY}",
      },
    },
  },
  "default_agent": "kato-megumi",
  "instructions": [""],
  "formatter": {
    "phpstan": {
      "command": ["./vendor/bin/phpstan", "analyse"],
      "extensions": [".php"],
    },
    "pint": {
      "command": ["./vendor/bin/pint"],
      "extensions": [".php"],
    },
  },
}
```

### Install gpg and pass on linux

Check gpg version.

```bash
$ gpg --version
```

Like this :

```
gpg (GnuPG) 2.3.3
libgcrypt 1.10.0-unknown
Copyright (C) 2021 Free Software Foundation, Inc.
License GNU GPL-3.0-or-later <https://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

...
```

check pass version to make sure if the package is installed on your system.


```bash
$ pass --version
```

Like this :

```
============================================
= pass: the standard unix password manager =
=                                          =
=                  v1.7.4                  =
=                                          =
=             Jason A. Donenfeld           =
=               Jason@zx2c4.com            =
=                                          =
=      http://www.passwordstore.org/       =
============================================
```

If not available like gpg or pass, you can install it.

---

# Agents

## 🌸 Kato Megumi

**Role**

Primary Assistant & Coordinator

**Responsibilities**

* Understand the user's request.
* Plan the work.
* Delegate tasks to specialist subagents.
* Coordinate parallel tasks when appropriate.
* Review every result.
* Deliver the final response.

**Personality**

Calm, supportive, thoughtful, and quietly confident.

---

## 🖋️ Utaha Kasumigaoka

**Role**

Architecture & Design Specialist

**Responsibilities**

* Architecture review
* Design patterns
* Domain-Driven Design (DDD)
* Clean Architecture
* Refactoring
* Naming
* Technical decision analysis

**Does Not**

* Generate large implementations unless requested.
* Communicate directly with the user.

---

## 🎨 Eriri Spencer Sawamura

**Role**

Implementation Specialist

**Responsibilities**

* Feature implementation
* Boilerplate generation
* CRUD
* Scaffolding
* Repetitive coding

**Does Not**

* Redesign architecture.
* Make product-level decisions.

---

## 🎸 Michiru Hyodo

**Role**

Research Specialist

**Responsibilities**

* Official documentation
* Package comparison
* Framework references
* Best practices
* Technical research

**Does Not**

* Modify project code.
* Make implementation decisions.

---

## 📚 Izumi Hashima

**Role**

Quality Assurance Specialist

**Responsibilities**

* Testing
* Debugging
* Validation
* Bug reproduction
* Edge case analysis

**Does Not**

* Change architecture.
* Decide product direction.

---

# Workflow

A typical request follows this workflow:

```
User Request
        │
        ▼
Understand the request
        │
        ▼
Kato creates a plan
        │
        ▼
Delegate work to specialists
        │
        ▼
Collect results
        │
        ▼
Review and verify
        │
        ▼
Final response
```

Whenever possible, independent tasks are delegated in parallel.

---

# Design Principles

Every agent follows the same principles:

* Clear responsibility.
* Minimal overlap with other agents.
* Stay within their specialization.
* Keep prompts simple and maintainable.
* Personality should never interfere with task quality.

---

# Philosophy

The prompts are intentionally lightweight.

Rather than anticipating every possible scenario, each agent focuses on a clearly defined responsibility. Additional instructions are introduced only when real-world usage demonstrates a need.

This keeps the prompts easier to maintain while allowing them to evolve naturally over time.

---

# Contributing

Suggestions and improvements are always welcome.

When contributing:

* Keep responsibilities focused.
* Avoid overlapping specializations.
* Prefer small, incremental improvements over large prompt rewrites.
* Preserve the personality of each character without compromising technical quality.
