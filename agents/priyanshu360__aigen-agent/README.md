
# Aigen Agent — LLM Skill Definitions

Agent repository for [Aigen](https://github.com/priyanshu360/aigen), the build-time TypeScript function generator.

This repo defines the LLM agent's personality, rules, and skills used to generate utility functions at build time. It's a separate Git repo so prompts can be versioned and iterated independently of the build tool.

## Structure

```
aigen-agent/
├── agent.yaml         ← agent metadata, model, skill list
├── SOUL.md            ← agent personality and core principles
├── RULES.md           ← generation constraints and style rules
├── skills/
│   ├── utility-function-generation/   ← generates TypeScript from call-site context
│   ├── type-inference/                ← infers argument/return types
│   └── compile-error-repair/          ← fixes functions that fail tsc
└── workflows/
    └── generate-function.yaml        ← orchestrates the generation flow
```

## Usage

Point your Vite/esbuild plugin's `agentDir` option to this repo:

```ts
aigenPlugin({ agentDir: "../aigen-agent" })
```

## Relation to Aigen

| Repo | Purpose |
|---|---|
| `aigen` (build tool) | Scanner, pipeline, plugins, runtime |
| `aigen-agent` (this repo) | LLM prompts, skills, rules |
