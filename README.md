# 🔣 JSON → Types

![vanilla JS](https://img.shields.io/badge/vanilla-JS-f7df1e?logo=javascript&logoColor=black)
![4 outputs](https://img.shields.io/badge/output-TS%20%C2%B7%20Py%20%C2%B7%20Zod%20%C2%B7%20Go-4dd0e1)
![license](https://img.shields.io/badge/license-MIT-4dd0e1)

**Paste JSON once. Get a TypeScript interface, a Python `TypedDict`, a Zod schema and a Go struct — nested objects, arrays, unions and nullables all inferred. No upload, no `npm install`.**

> Part of [The Antigle](https://github.com/mukund-buddy) 🔥 — AI-assisted build, hand-tested.
> Every output below was compiled or run against the sample before this README existed.

**Live demo:** _coming soon_ · [Repository](https://github.com/mukund-buddy/json-to-types)

---

## 🎯 Why This Exists

Hand-writing types from a JSON response is the most mechanical, error-prone part of
starting an API integration — and every tool I found either wanted my JSON on *their*
server, or only did TypeScript.

This one runs `JSON.parse` → one shared inference tree → four renderers, entirely in
your tab. Your API payloads (which often contain customer data) never leave the browser.

## ✨ Features

- **TypeScript** — interfaces, quoted keys when the JSON has `user-name`, `T | null`, optional `?`
- **Python** — `typing.TypedDict`, functional syntax when keys aren't identifiers, `NotRequired` only when a class mixes required + optional
- **Zod v3** — nested consts emitted child-first so the schema actually runs, `.nullable()` / `.optional()`
- **Go** — structs with `json:"…"` tags, pointers for nullable, proper `ID`/`URL` acronyms
- **Real inference** — arrays of objects get *merged* (missing keys become optional, conflicting types become unions), mixed arrays become unions
- **Root shapes** — object, array (`type Rows = RowsItem[]`, never self-referential) and bare primitives all work

## 🚀 Quick Start

```bash
git clone https://github.com/mukund-buddy/json-to-types
start index.html
```

Paste JSON (or hit **Load sample**) → click through the four tabs → **Copy output**.

## 🧱 How It Works

```
index.html   →  input pane + tabbed output
style.css    →  "blueprint" theme (engineering navy + cyan grid)
app.js       →  infer() builds ONE type tree; 4 renderers read it
```

The interesting code is `infer()` + `mergeAll()` + `collect()` — about 150 lines.
If you're learning, read those first; the renderers are just printers.

## ✅ Verified

- Python output passes `python -m py_compile` for object, array-root and mixed samples
- TS/Zod/Go outputs checked against hand-written equivalents
- Known-edge cases tested: empty object → `Record<string, never>` / `Dict[str, Any]`,
  integers vs floats, `null` in arrays, duplicate derived type names

## 🗺️ Roadmap

- [x] Four renderers (v1)
- [ ] JSON Schema (draft-07) output
- [ ] Rust (`serde`) output
- [ ] Import from a live URL (CORS permitting)
- [ ] Optional `snake_case` / `camelCase` field renaming

## 🧑‍💻 Honest Note

AI-assisted, human-tested. The inference rules were tuned by feeding it messy real-world
JSON (union-heavy arrays, `user-name` keys, `bio: null`) until every tab produced
something paste-ready. Not a compiler — always skim the output before shipping.

## 🏷️ Suggested GitHub Topics

`json` `typescript` `python` `zod` `go` `code-generator` `typeddict` `developer-tools` `vanilla-js` `the-antigle`

Add them under **Settings → General → Topics**.

---

Part of **[The Antigle](https://github.com/mukund-buddy)** — browser tools and web products, built with AI and finished by hand.

## 📄 License

MIT
