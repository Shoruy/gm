# CLAUDE.md - AI Assistant Development Guide

**Project:** GM Bot Modified - Twitter/X Automation Browser Extension
**Version:** 10.5
**Last Updated:** 2026-01-22

---

## 🎯 Project Overview

### What is This Project?

GM Bot Modified is a browser extension for Chrome that automates interactions on Twitter/X (formerly Twitter). It provides automated scrolling, replies, likes, follows, and retweets based on user-configured settings.

**Key Technologies:**
- Chrome Extension Manifest V3
- JavaScript (pre-built/minified files)
- Chrome Storage API
- Content Scripts + Background Service Worker
- Ant Design (UI framework)

### Project Structure

```
/home/user/gm/
├── manifest.json              # Chrome extension configuration
├── plan.md                    # Central project plan with checkboxes
├── decision-log.md            # Architectural decision log
├── CLAUDE.md                  # This file - AI development guide
├── session-guide.md           # Practical examples for parallel sessions
│
├── Content Scripts:
│   ├── agent.4501d6d3.js     # Twitter DOM interaction agent
│   ├── antd-popups.9ba8c9e3.js # Popup UI components
│   └── xui.03f02ae4.js        # Extended UI features
│
├── UI Pages:
│   ├── popup.html / popup.100f6462.js      # Extension popup
│   ├── options.html / options.95eda3f3.js  # Settings page
│   └── pro.html / pro.c11eec1e.js          # Pro features page
│
├── Background:
│   └── index.js               # Service worker (153KB)
│
└── Assets:
    ├── icon*.plasmo.*.png     # Extension icons (16-128px)
    ├── computed_hashes.json   # Build verification
    └── verified_contents.json # Content verification
```

---

## 🚀 The "God Mode" Development System

The God Mode system is a methodology for working with multiple Claude Code terminal sessions in parallel to maximize development efficiency while avoiding chaos and context conflicts.

### Core Principles

1. **Architecture Understanding Over Raw Parallelism**
   - More terminals ≠ faster development
   - Understanding task dependencies is critical
   - Plan first, parallelize second

2. **Fresh Context for Each Phase**
   - Avoid context bloat with 100% fresh starts
   - Use relay race pattern to prevent auto-compaction issues
   - Each session focuses on a specific, well-defined scope

3. **Central Coordination**
   - `plan.md` is your command center
   - `decision-log.md` preserves architectural knowledge
   - Control session maintains oversight

---

## 📋 Three Parallel Work Modes

### Mode 1: True Parallel (Истинная параллельность)

**When to Use:** Completely independent tasks with zero dependencies

**Characteristics:**
- Tasks don't touch the same files
- No shared state or data structures
- Often non-technical or research tasks
- Can run simultaneously without coordination

**Example Scenario:**
```
Session 1: Research competitor extensions
Session 2: Write marketing copy for Chrome Web Store
Session 3: Design new icon variations
Session 4: Research Twitter API rate limits
```

**Setup:**
1. Open 3-4 separate terminal windows with Claude Code
2. Each session gets a distinct, independent task
3. No need to synchronize or coordinate
4. Can complete in any order

**Best Practices:**
- Ensure tasks truly have zero overlap
- Document findings in separate files
- Merge results manually at the end

---

### Mode 2: Phased Parallel (Поэтапная параллельность)

**When to Use:** After foundation is laid, for independent feature modules

**Characteristics:**
- Shared foundation (database schema, APIs, core utilities)
- Each module is self-contained
- Minimal interaction between modules
- Can develop in parallel after foundation phase

**Example Scenario:**
```
Foundation Phase (Sequential - Single Session):
  ✅ Create data schema
  ✅ Build message passing system
  ✅ Set up storage utilities
  ✅ Define module interfaces

Parallel Phase (4 Sessions):
  Session 1: Build admin dashboard UI
  Session 2: Implement user profile features
  Session 3: Create automation rules engine
  Session 4: Develop analytics tracking
```

**Setup:**

**Phase 1 - Foundation (Sequential):**
1. Single Claude session
2. Build core architecture
3. Define all module interfaces
4. Document in `plan.md` and `decision-log.md`
5. Commit and push foundation

**Phase 2 - Parallel Development:**
1. Open multiple Claude sessions
2. Each session reads `plan.md` and `decision-log.md`
3. Each session claims a specific module
4. Work in parallel on different features
5. Each session updates `plan.md` when completing tasks

**Phase 3 - Integration:**
1. Switch to sequential or relay race mode
2. Integrate modules one by one
3. Test interactions between modules
4. Fix conflicts and issues

**Best Practices:**
- Define clear module boundaries in foundation phase
- Use interfaces/contracts between modules
- Each module should have its own files
- Update `plan.md` to mark claimed modules
- Commit frequently with module-specific messages

---

### Mode 3: The Relay Race (Эстафета)

**When to Use:** Sequential tasks where context must be passed forward, or when context is getting bloated

**Characteristics:**
- Task B depends on Task A completion
- Fresh context for each phase prevents auto-compaction
- Clear handoff between phases
- Each session picks up where the last left off

**Example Scenario:**
```
Session 1: Design and implement database schema
  → Handoff: Schema complete, ready for API layer

Session 2: Build REST API endpoints using the schema
  → Handoff: API complete, endpoints documented

Session 3: Create frontend components consuming API
  → Handoff: UI complete, ready for integration testing

Session 4: Integration testing and bug fixes
  → Handoff: All tests passing, ready for deployment
```

**Setup:**

**Session 1 Start:**
1. Read `plan.md` to understand overall project
2. Read `decision-log.md` for architectural context
3. Work on Phase 1 tasks
4. Update `plan.md` with completions
5. Document any decisions in `decision-log.md`
6. Commit with message: "Phase 1: [description]"
7. Update `plan.md` with handoff notes

**Session 1 → Session 2 Handoff:**
1. Close Session 1 terminal
2. Open fresh Session 2 terminal
3. Read `plan.md` (especially handoff notes)
4. Read `decision-log.md` (especially new decisions)
5. Read git log to see what was completed
6. Start Phase 2 work with 100% fresh context

**Repeat for Each Phase**

**Best Practices:**
- Each session should have clear entry and exit criteria
- Update `plan.md` checklist at end of session
- Document any architectural changes in `decision-log.md`
- Commit before closing a session
- Next session starts by reading both markdown files
- Each phase should be 1-3 hours of focused work

---

## 🎛️ The Control Session (Sterile Session)

### What is the Control Session?

A dedicated Claude Code terminal that focuses ONLY on:
- Reading and understanding `plan.md`
- Reviewing code written by other sessions
- Checking architectural consistency
- Acting as a "project manager" or "tech lead"

### When to Use

- When running 2+ parallel development sessions
- During complex refactoring or integration phases
- When you need a "sanity check" on code quality
- To prevent architectural drift

### Setup

1. Open a separate Claude Code terminal
2. Title it "CONTROL SESSION - DO NOT CODE"
3. Never ask this session to write production code
4. Focus on review, analysis, and guidance

### Example Prompts for Control Session

```
"Review the changes in module-a.js and module-b.js.
Do they follow the architecture defined in decision-log.md?"

"Check if the new authentication code is consistent with
our security decisions in DECISION-005."

"Read plan.md and tell me which tasks are blocked and why."

"Analyze the git diff and identify any potential conflicts
between Session 1 and Session 2 changes."
```

### Best Practices

- Don't let control session write code (unless critical fix)
- Use it for code reviews between parallel sessions
- Keep it focused on plan.md and decision-log.md
- Use it to resolve conflicts between sessions
- Ask it strategic questions about architecture

---

## 📖 Development Workflows

### Starting a New Feature (True Parallel)

```bash
# Terminal 1
claude code
> "I need to research competing Twitter automation tools.
   Create a comparison document with features, pricing, and UX."

# Terminal 2
claude code
> "Write marketing copy for our Chrome Web Store listing.
   Focus on benefits: time-saving, engagement boost, easy setup."

# Terminal 3
claude code
> "Find 10 Twitter influencers in the productivity space
   who might be interested in reviewing our extension."
```

### Building a New Module (Phased Parallel)

```bash
# Phase 1: Foundation (Terminal 1)
claude code
> "Read plan.md. We're starting the Analytics Module foundation.
   Create the data schema, event tracking interface, and
   storage utilities. Update plan.md when done."

# [Wait for completion, commit, close]

# Phase 2: Parallel Development (Terminal 1, 2, 3)

# Terminal 1
claude code
> "Read plan.md and decision-log.md. I'm working on the
   Analytics Dashboard UI. Building the React components
   for displaying charts and metrics."

# Terminal 2
claude code
> "Read plan.md and decision-log.md. I'm implementing the
   Analytics Data Collection in content scripts. Tracking
   user actions and sending to background service."

# Terminal 3
claude code
> "Read plan.md and decision-log.md. I'm creating the
   Analytics Export feature. Allow users to download
   their data as CSV/JSON."
```

### Integration Phase (Relay Race)

```bash
# Session 1: Integrate Dashboard UI
claude code
> "Read plan.md. All analytics modules are complete.
   I need to integrate the Dashboard UI with the data
   collection system. Test that real data flows correctly."
# Update plan.md, commit, note any issues, close

# Session 2: Fix Integration Issues
claude code
> "Read plan.md and decision-log.md. Check the handoff notes.
   Fix the data sync issues identified in Session 1.
   Ensure Dashboard updates in real-time."
# Update plan.md, commit, close

# Session 3: End-to-End Testing
claude code
> "Read plan.md. Integration is complete. Run full E2E tests
   on the Analytics feature. Verify export, dashboard, and
   data collection all work together."
```

### Code Review with Control Session

```bash
# Development Session
claude code
> "Implement the auto-reply feature based on keyword matching."
# [Makes changes to reply-engine.js]

# Control Session (separate terminal)
claude code
> "Read decision-log.md DECISION-003 about our text matching
   strategy. Now review the changes in reply-engine.js.
   Does it follow our decision to use regex with rate limiting?"
# [Provides feedback]

# Back to Development Session
> "The control session identified an issue with rate limiting.
   Fix the implementation to match DECISION-003."
```

---

## 📝 File Conventions and Standards

### plan.md Maintenance

**Every Session Should:**
- ✅ Read `plan.md` before starting work
- ✅ Update checkboxes when completing tasks
- ✅ Add new tasks if discovered during work
- ✅ Note blockers in the "Notes & Blockers" section
- ✅ Update "Active Sessions Tracking" with current work
- ✅ Fill out "Session Handoff Checklist" when done
- ✅ Commit `plan.md` with each significant update

**Example Updates:**
```markdown
# Before starting work
### Session 2: UI Development
**Status:** Active
**Current Task:** Building settings page UI components
**Last Action:** Started at 14:30, reading requirements

# After completing work
### Session 2: UI Development
**Status:** Idle
**Current Task:** Completed settings page UI
**Last Action:** Committed at 16:45, ready for integration

## Phase 2: Parallel Development
- [x] Settings page layout ✅ Completed by Session 2
- [ ] Analytics dashboard
- [ ] User profile editor
```

---

### decision-log.md Guidelines

**When to Add a Decision:**
- Architecture changes affecting multiple modules
- Technology/library choices
- API design decisions
- Performance vs. readability trade-offs
- Security-related choices
- Deviation from original plan

**When NOT to Add:**
- Minor bug fixes
- Styling tweaks
- Variable naming changes
- Single-function refactors

**Decision Naming Convention:**
- Use DECISION-XXX numbering (001, 002, etc.)
- Make titles descriptive: "DECISION-005 - Rate Limiting Strategy"
- Always include date and session name
- Link related decisions

**Example Entry:**
```markdown
### [DECISION-008] - Tweet Detection Algorithm
**Date:** 2026-01-22
**Session:** Content Scripts Development (Session 1)
**Status:** Accepted

#### Context
Need to detect tweets on Twitter/X timeline for automation actions.
Twitter's DOM structure changes frequently.

#### Decision
Use a combination of data attributes and ARIA labels with fallback
to class name patterns. Cache selectors for performance.

#### Rationale
- Data attributes are more stable than classes
- ARIA labels provide semantic meaning
- Caching reduces DOM query overhead
- Fallbacks ensure compatibility with UI updates

#### Alternatives Considered
1. **Class names only**: Too fragile, breaks with Twitter updates
2. **XPath selectors**: Slower performance, harder to maintain

#### Consequences
**Positive:**
- More robust against Twitter changes
- Better performance
- Easier to debug

**Negative/Trade-offs:**
- Slightly more complex code
- Need to update fallbacks periodically

**Impact on Other Modules:**
- automation-engine.js must use these selectors
- analytics.js can reuse the detection logic

#### Implementation Notes
Store selectors in selectors-config.js for easy updates.
Add unit tests for selector matching.

#### Related Decisions
- Builds on DECISION-003 about DOM interaction strategy
```

---

### Git Commit Messages

**Format:**
```
[Phase/Module] Brief description

Detailed description if needed.

- Change 1
- Change 2
- Change 3

Updates plan.md: [checkboxes completed]
```

**Examples:**
```
[Foundation] Set up data storage utilities

Implemented Chrome storage wrapper with async/await support.
Added error handling and data migration utilities.

- Created storage-utils.js with get/set/remove functions
- Added migration system for schema updates
- Implemented error logging for storage failures

Updates plan.md: ✅ Storage layer, ✅ Data migration utilities
```

```
[UI Module] Complete settings page layout

Built settings page using Ant Design components.
Integrated with storage system for persistence.

- Settings form with validation
- Save/reset functionality
- Import/export settings feature

Updates plan.md: ✅ Settings management UI
```

```
[Relay Race - Phase 3] Integration testing complete

Tested all modules working together. Fixed data sync issues.

- Resolved race condition in message passing
- Fixed storage key conflicts between modules
- Added integration tests

Updates plan.md: ✅ Integration tests, ✅ Bug fixes
Closes blocker noted in previous session.
```

---

## 🔧 Technical Guidelines

### Code Quality Standards

**JavaScript Style:**
- Use ES6+ features (async/await, destructuring, arrow functions)
- Prefer `const` over `let`, avoid `var`
- Use descriptive variable names
- Add JSDoc comments for complex functions
- Handle errors explicitly (try/catch)

**Chrome Extension Best Practices:**
- Use Manifest V3 features
- Minimize permissions requested
- Use message passing between contexts
- Store data efficiently (avoid large objects)
- Handle Twitter/X DOM changes gracefully

**Performance:**
- Debounce/throttle frequent operations
- Use event delegation for dynamic content
- Cache DOM queries
- Lazy load when possible
- Monitor memory usage

**Security:**
- Validate all user input
- Sanitize before DOM insertion (XSS prevention)
- Use Content Security Policy
- Don't store sensitive data in plain text
- Follow principle of least privilege

---

### Working with Existing Codebase

**Current State:**
- Pre-built, minified JavaScript files
- No source code or build system visible
- Working production code

**Development Strategy:**
See DECISION-001 in decision-log.md:

1. **Don't Reverse Engineer:** Work with existing builds
2. **Incremental Enhancement:** Add new features as separate modules
3. **Modern Standards:** New code uses ES6+, proper structure
4. **Clear Interfaces:** Define APIs between old and new code
5. **Future Refactor:** Plan for eventual full modernization

**Adding New Features:**
```javascript
// Create new module as separate file
// new-feature.js

// Use modern JavaScript
export class NewFeature {
  constructor(options) {
    this.options = options;
  }

  async initialize() {
    // Modern async/await
    const data = await chrome.storage.local.get('settings');
    this.applySettings(data.settings);
  }

  // Clear, documented functions
  applySettings(settings) {
    // ...
  }
}

// Create adapter to integrate with legacy code
// legacy-adapter.js
import { NewFeature } from './new-feature.js';

window.legacyBridge = {
  newFeature: new NewFeature({
    // Bridge to existing code
    onAction: window.existingLegacyCallback
  })
};
```

---

## 🎯 Common Scenarios and Solutions

### Scenario 1: Context is Getting Too Large

**Problem:** Claude session has too much context, responses slow down, auto-compaction kicks in.

**Solution: Relay Race Mode**
1. Update `plan.md` with current status
2. Document decisions in `decision-log.md`
3. Commit all changes
4. Close session
5. Open fresh session
6. New session reads markdown files for context
7. Continue with 100% fresh context

### Scenario 2: Multiple Features Need Development

**Problem:** 5 new features requested, all important.

**Solution: Phased Parallel**
1. Session 1: Define foundation (data models, APIs)
2. Commit foundation
3. Open 3-4 parallel sessions
4. Each claims a feature in `plan.md`
5. Develop features independently
6. Use Relay Race for integration phase

### Scenario 3: Parallel Sessions Making Conflicting Changes

**Problem:** Session 1 and Session 2 both modified same function.

**Solution: Control Session + Clear Boundaries**
1. Open control session
2. Review both changes
3. Identify conflict
4. Decide on resolution strategy
5. Have one session merge both approaches
6. Document decision in `decision-log.md`

**Prevention:**
- Define clear module boundaries before parallel work
- Update `plan.md` to claim files/modules
- Use feature branches if available
- Coordinate through `plan.md` notes

### Scenario 4: Blocked Task

**Problem:** Can't proceed because waiting on external factor.

**Solution: Switch Focus**
1. Mark task as blocked in `plan.md`
2. Document blocker with details
3. Move to different independent task
4. Use True Parallel mode to work on unrelated items
5. Return when blocker is resolved

### Scenario 5: Need to Test Complex Integration

**Problem:** Three modules need to work together, not sure if they integrate correctly.

**Solution: Dedicated Integration Session (Relay Race)**
1. Ensure all modules committed
2. Start fresh session focused on integration
3. Read `plan.md` and `decision-log.md`
4. Import all modules
5. Write integration tests
6. Document issues found
7. Hand off to fix sessions via Relay Race

---

## 🚦 Warning Signs and Anti-Patterns

### 🔴 Red Flags

**Architectural Red Flags:**
- Sessions making conflicting architectural decisions
- No clear module boundaries
- Parallel sessions editing same files
- No documentation of major changes
- `decision-log.md` not updated for weeks

**Process Red Flags:**
- `plan.md` not updated regularly
- Sessions not reading markdown files before starting
- No control session when running 3+ parallel sessions
- Commits without updating `plan.md`
- Integration left until the end

**Code Red Flags:**
- Duplicated logic across modules
- Hard-coded values that should be configurable
- No error handling
- Security vulnerabilities (XSS, injection)
- Memory leaks in content scripts

### ❌ Anti-Patterns to Avoid

**"Shotgun Surgery"**
- Making same change across many files
- Indicates poor abstraction
- Solution: Create shared utilities

**"God Object"**
- One module doing everything
- Hard to test and maintain
- Solution: Split into focused modules

**"Magic Numbers"**
- Hard-coded values scattered everywhere
- Solution: Configuration file

**"Cowboy Coding"**
- Parallel sessions without coordination
- No plan, no documentation
- Solution: Use `plan.md` religiously

**"Context Hoarding"**
- Never starting fresh sessions
- Trying to fit everything in one session
- Solution: Use Relay Race mode

---

## 📚 Quick Reference Commands

### Starting a Session

```bash
# Read the plan
cat plan.md

# Check recent decisions
tail -50 decision-log.md

# See what was last worked on
git log --oneline -10

# Check current state
git status
```

### During Development

```bash
# Update plan (use Claude to edit)
# "Update plan.md to mark task X as complete"

# Add architectural decision (use Claude to edit)
# "Add DECISION-009 to decision-log.md about [topic]"

# Commit progress
git add .
git commit -m "[Module] Brief description

- Change 1
- Change 2

Updates plan.md: ✅ Task completed"
```

### Ending a Session (Relay Race)

```bash
# Final commit
git add .
git commit -m "[Phase Complete] Summary

Handoff notes: [what next session should know]"

# Push if working on branch
git push -u origin <branch-name>

# Update plan.md with handoff notes (use Claude)
# "Update plan.md session tracking: Session 1 complete,
#  handoff to Session 2 for integration phase"
```

---

## 🎓 Learning Resources

### Understanding Chrome Extensions
- Chrome Extension Documentation: https://developer.chrome.com/docs/extensions/
- Manifest V3 Migration Guide
- Content Scripts Best Practices
- Message Passing Patterns

### JavaScript Modern Patterns
- Async/Await for asynchronous operations
- ES6 Modules for code organization
- Promises and error handling
- Event delegation and performance

### Parallel Development Strategies
- Module boundaries and interfaces
- Dependency management
- Integration testing strategies
- Merge conflict resolution

---

## 🔄 Continuous Improvement

### Regular Reviews

**Weekly:**
- Review `decision-log.md` for outdated decisions
- Update `plan.md` with new priorities
- Archive completed phases
- Identify technical debt

**Monthly:**
- Evaluate parallel development effectiveness
- Update this CLAUDE.md with new learnings
- Refine session strategies
- Document new patterns

### Feedback Loop

**After Each Major Feature:**
1. What worked well with parallel sessions?
2. What conflicts or issues arose?
3. How can we improve module boundaries?
4. What should be documented better?

**Update These Files:**
- Add learnings to CLAUDE.md
- Document new patterns in session-guide.md
- Refine decision template if needed
- Update plan.md structure if needed

---

## 📞 Getting Help

### When Claude Gets Stuck

**Context Overload:**
- Use Relay Race to start fresh session
- Provide focused, specific prompts
- Reference specific files and line numbers

**Architectural Questions:**
- Ask control session for review
- Reference decision-log.md decisions
- Break down into smaller questions

**Integration Issues:**
- Create minimal reproduction
- Test modules in isolation first
- Check decision-log.md for interface definitions

### Useful Prompts

**For Planning:**
```
"Read plan.md and suggest the next 3 tasks to focus on,
 considering dependencies and current blockers."
```

**For Architecture:**
```
"Review decision-log.md decisions 1-5. Based on these,
 what's the best way to implement [feature]?"
```

**For Code Review:**
```
"Review changes in [file]. Check against our architecture
 decisions in decision-log.md. Identify any violations."
```

**For Parallel Coordination:**
```
"Read plan.md active sessions. I want to work on [feature].
 Which session should I join, or should I start a new one?"
```

---

## 🎉 Success Metrics

You're doing it right when:

✅ `plan.md` is always up to date
✅ Major decisions are documented in `decision-log.md`
✅ Parallel sessions don't conflict
✅ Code reviews happen via control session
✅ Context stays fresh via Relay Race
✅ Modules have clear boundaries
✅ Integration is smooth
✅ Code quality is consistent
✅ Commits reference plan.md updates
✅ Sessions read markdown files before starting

---

## 📄 File Checklist for New Projects

When starting a new project with God Mode:

- [ ] Create `plan.md` with phase structure
- [ ] Create `decision-log.md` with template
- [ ] Create `CLAUDE.md` (this file)
- [ ] Create `session-guide.md` with examples
- [ ] Define module boundaries
- [ ] Set up git branch structure
- [ ] Create initial architecture decisions
- [ ] Plan foundation phase tasks
- [ ] Identify potential parallel work
- [ ] Set up control session process

---

**Remember:** The goal isn't to run as many parallel sessions as possible. The goal is to architect your work so that parallelization is natural, efficient, and conflict-free.

**Think in phases. Plan with plan.md. Document with decision-log.md. Execute with focus.**

Good luck, and happy building! 🚀
