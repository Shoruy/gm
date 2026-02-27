# CLAUDE.md - GM Bot Modified

**Project:** GM Bot Modified - Twitter/X Chrome Extension (Manifest V3)
**Updated:** 2026-01-22

---

## 🎯 Project Overview

Chrome extension automating Twitter/X interactions: scrolling, replies, likes, follows, retweets.

**Stack:** Chrome Extension MV3 · JavaScript · Chrome Storage API · Ant Design

**Files:**
- `agent.4501d6d3.js` — Twitter DOM agent (content script)
- `index.js` — Background service worker
- `popup.html / popup.100f6462.js` — Extension popup
- `options.html / options.95eda3f3.js` — Settings page
- `pro.html / pro.c11eec1e.js` — Pro features
- `antd-popups.9ba8c9e3.js` — UI components
- `manifest.json` — Extension config

> All JS files are pre-built/minified. Do NOT reverse engineer. Add new features as separate modules.

---

## 📋 God Mode System

Three coordination files — read them at the start of EVERY session:

| File | Purpose | Update When |
|------|---------|------------|
| `plan.md` | Tasks + progress | After every task |
| `decision-log.md` | Architectural decisions | When making arch choices |
| `CLAUDE.md` | This file — project context | Major changes only |

---

## 🔄 Three Work Modes

**1. True Parallel** — Fully independent tasks (research, docs, design). Open separate sessions, no coordination needed.

**2. Phased Parallel** — Build foundation first (sequential), then parallelize independent modules, then integrate.

**3. Relay Race** — Sequential phases with context handoff. Use when context bloats or tasks depend on each other.
```
Session 1 → commit + update plan.md → Session 2 → commit → Session 3
```

**Control Session** — One read-only session that only reviews plan.md and code. Never writes production code.

---

## ⚙️ Session Rules

**START:** Read plan.md → Read decision-log.md → Show status → Ask what to do

**DURING:** Update plan.md every 30 min · Commit frequently · Log decisions

**END:** Mark tasks [x] · Update plan.md with handoff notes · Commit everything

---

## 💻 Code Standards

```javascript
// ES6+ only. No var. Descriptive names.
async function doSomething(input) {
  console.info('ℹ️ [Module] Started');
  try {
    const result = await process(input);
    console.info('✅ [Module] Done', { result });
    return result;
  } catch (error) {
    console.error('❌ [Module] Failed', { error });
    throw error;
  }
}
```

- ✅ JSDoc for public functions
- ✅ INFO / WARN / ERROR logs everywhere
- ✅ try/catch for all async
- ✅ Validate inputs
- ❌ No separate README files — comments only
- ❌ No hard-coded values

**Git commits:**
```
[Module] Short description
- Change 1
- Change 2
Updates plan.md: ✅ Task name
```

---

## 🚦 Anti-Patterns to Avoid

- Parallel sessions editing the same file
- Starting work without reading plan.md
- Skipping decision-log.md for arch changes
- Context hoarding — use Relay Race instead
- Committing without updating plan.md

---

## ✅ You're Doing It Right When

- plan.md is always current
- Sessions never conflict
- Every arch decision is in decision-log.md
- Fresh context via Relay Race
- Commits reference plan.md updates

---

**Think in phases · Plan with plan.md · Document with decision-log.md · Execute with focus 🚀**
