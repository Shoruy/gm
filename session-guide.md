# Session Guide - Practical Examples

**Purpose:** Real-world examples of using the three parallel work modes effectively

---

## Table of Contents
1. [True Parallel Examples](#true-parallel-examples)
2. [Phased Parallel Examples](#phased-parallel-examples)
3. [Relay Race Examples](#relay-race-examples)
4. [Hybrid Approach Examples](#hybrid-approach-examples)
5. [Troubleshooting Common Issues](#troubleshooting-common-issues)

---

## True Parallel Examples

### Example 1: Research and Content Creation

**Scenario:** Need to research competitors, write documentation, and design marketing materials.

**Setup:**
- 4 independent terminal sessions
- No file conflicts possible
- Can complete in any order

**Session 1: Competitor Research**
```
Prompt:
"Research 5 competing Twitter automation tools. For each one, document:
- Main features
- Pricing
- User reviews summary
- Unique selling points
- Weaknesses

Create a file called competitor-analysis.md with your findings."

Expected Output:
- competitor-analysis.md created
- No dependencies on other sessions
```

**Session 2: User Documentation**
```
Prompt:
"Write a user guide for our Twitter automation extension. Include:
- Installation steps
- Initial setup
- How to configure auto-replies
- How to set up filters
- Troubleshooting common issues

Create user-guide.md"

Expected Output:
- user-guide.md created
- Can work independently from Session 1
```

**Session 3: Marketing Copy**
```
Prompt:
"Write compelling marketing copy for our Chrome Web Store listing:
- Catchy tagline (under 10 words)
- Description (under 132 characters)
- Detailed description (highlighting benefits, not features)
- 3 key value propositions
- Call to action

Save to marketing-copy.md"

Expected Output:
- marketing-copy.md created
- No code dependencies
```

**Session 4: Icon Design Research**
```
Prompt:
"Research icon design trends for Chrome extensions in 2026.
Find 10 examples of well-designed extension icons.
Analyze what makes them effective.
Suggest 3 design directions for our Twitter bot icon.

Create icon-design-research.md"

Expected Output:
- icon-design-research.md created
- Independent design research
```

**Coordination:**
- No need to update plan.md during work
- Each session creates its own deliverable
- Review all outputs at the end
- No merge conflicts possible

**When to Use True Parallel:**
- ✅ Research tasks
- ✅ Documentation writing
- ✅ Content creation
- ✅ Marketing materials
- ✅ Data gathering
- ✅ Non-code analysis

---

### Example 2: Feature Specification + Legal + Design

**Scenario:** Starting a new project phase, need multiple non-technical deliverables.

**Session 1: Technical Specification**
```
"Create a technical specification for our new 'Smart Reply' feature.
Include:
- Feature overview
- User stories
- Technical requirements
- API endpoints needed
- Data structures
- Success metrics

Save to specs/smart-reply-spec.md"
```

**Session 2: Privacy Policy Review**
```
"Review our current privacy policy. Update it to reflect:
- Data collection for auto-reply feature
- Storage of user preferences
- Twitter API data usage
- GDPR compliance notes
- User data deletion process

Update docs/privacy-policy.md"
```

**Session 3: UI Mockup Descriptions**
```
"Describe detailed UI mockups for the Smart Reply settings page.
Include:
- Layout description
- Each UI element and its purpose
- User flow through the settings
- Error states
- Success confirmations

Create mockups/smart-reply-ui.md"
```

---

## Phased Parallel Examples

### Example 3: Building Analytics Module

**Phase 1: Foundation (Sequential - Single Session)**

**Session 1: Architecture Setup**
```
Prompt:
"Read plan.md. We're building an Analytics module for tracking
user engagement metrics in our Twitter bot.

FOUNDATION TASKS:
1. Design the data schema for analytics events
2. Create the storage structure
3. Define the event tracking interface
4. Build utility functions for data aggregation
5. Document the API in decision-log.md as DECISION-010

Create:
- src/analytics/schema.js
- src/analytics/storage-utils.js
- src/analytics/events-interface.js
- src/analytics/aggregation-utils.js

Update plan.md when complete."

Expected Output:
✅ Foundation files created
✅ Interfaces defined
✅ DECISION-010 added to decision-log.md
✅ plan.md updated with foundation complete
```

**Commit and Close Session 1**
```bash
git add .
git commit -m "[Analytics Foundation] Core architecture complete

- Created data schema for analytics events
- Built storage utilities
- Defined event tracking interface
- Added aggregation functions

Updates plan.md: ✅ Analytics Foundation"
git push
```

---

**Phase 2: Parallel Development (Multiple Sessions)**

**Session 2A: Data Collection**
```
Prompt:
"Read plan.md and decision-log.md (especially DECISION-010).

I'm implementing data collection for the Analytics module.

TASKS:
- Create content script that tracks user actions
- Emit events when tweets are liked, replied to, followed
- Use the events-interface.js from foundation
- Store events using storage-utils.js
- Add rate limiting to prevent spam

Create src/analytics/collectors/content-collector.js

Mark 'Data Collection' as in-progress in plan.md"

Expected Output:
- content-collector.js created
- Uses foundation interfaces
- plan.md updated
```

**Session 2B: Dashboard UI (Parallel to 2A)**
```
Prompt:
"Read plan.md and decision-log.md (especially DECISION-010).

I'm building the Analytics Dashboard UI.

TASKS:
- Create React component for analytics dashboard
- Display metrics: total actions, actions per day, success rate
- Use Ant Design charts for visualizations
- Fetch data using storage-utils.js
- Add date range selector

Create src/analytics/ui/AnalyticsDashboard.jsx

Mark 'Dashboard UI' as in-progress in plan.md"

Expected Output:
- AnalyticsDashboard.jsx created
- Uses foundation storage utilities
- plan.md updated
```

**Session 2C: Export Feature (Parallel to 2A and 2B)**
```
Prompt:
"Read plan.md and decision-log.md (especially DECISION-010).

I'm creating the Analytics Export feature.

TASKS:
- Create export utility for analytics data
- Support CSV and JSON formats
- Use aggregation-utils.js for data formatting
- Add UI button in dashboard to trigger export
- Include date range filtering

Create src/analytics/export/exporter.js

Mark 'Export Feature' as in-progress in plan.md"

Expected Output:
- exporter.js created
- Uses foundation aggregation utilities
- plan.md updated
```

**All parallel sessions work independently, then commit**

---

**Phase 3: Integration (Sequential or Relay Race)**

**Session 3: Integration**
```
Prompt:
"Read plan.md and decision-log.md.

All Analytics module components are complete. I need to integrate them:

TASKS:
1. Connect content-collector to dashboard (real-time updates)
2. Add export button to dashboard UI
3. Test data flow: collection → storage → dashboard → export
4. Fix any integration bugs
5. Add error handling for edge cases
6. Update plan.md with integration status

Test scenarios:
- Like a tweet, verify it appears in dashboard
- Export data as CSV, verify format
- Test with no data collected yet"

Expected Output:
- All modules working together
- Integration bugs fixed
- plan.md updated
```

---

### Example 4: Refactoring Legacy Code

**Scenario:** Have messy legacy code, want to refactor into clean modules.

**Phase 1: Analysis**
```
Session 1:
"Analyze the existing popup.100f6462.js file.
Identify:
- Main functions and their purposes
- Dependencies and imports
- Data flow
- Potential module boundaries
- Code smells and issues

Create analysis/popup-analysis.md with findings.
Suggest a refactoring plan with 3-4 independent modules."
```

**Phase 2: Parallel Refactoring (Based on Analysis)**

```
Session 2A: UI Components Module
"Extract all UI rendering logic from popup.100f6462.js
into a new clean module: src/popup/ui-components.js"

Session 2B: State Management Module
"Extract state management logic into: src/popup/state-manager.js"

Session 2C: API Communication Module
"Extract API calls into: src/popup/api-client.js"
```

**Phase 3: Integration**
```
Session 3:
"Integrate the new modules to replace popup.100f6462.js
Test that all functionality still works"
```

---

## Relay Race Examples

### Example 5: Feature Implementation Pipeline

**Scenario:** Building a complex "Schedule Tweets" feature end-to-end.

**Session 1: Data Layer**
```
Prompt:
"We're building a Schedule Tweets feature. This is Phase 1: Data Layer.

TASKS:
1. Design schema for scheduled tweets (timestamp, content, conditions)
2. Create CRUD functions for scheduled tweets
3. Build persistence layer using Chrome storage
4. Add validation for schedule data

Create src/scheduler/data-layer.js

HANDOFF NOTES FOR NEXT SESSION:
- Data schema is in data-layer.js lines 1-20
- All CRUD functions use async/await
- Validation rules: max 50 scheduled tweets, min 1 min future time

Update plan.md and commit when done."

End of Session 1:
- Commit: "[Schedule Feature - Phase 1] Data layer complete"
- Update plan.md with handoff notes
- Close terminal
```

**Session 2: Background Job Runner**
```
Prompt:
"Read plan.md handoff notes from Session 1.
This is Phase 2: Background Job Runner.

TASKS:
1. Read the data layer implementation
2. Create a background service that checks scheduled tweets every minute
3. Execute tweets when their time comes
4. Mark completed tweets
5. Handle errors (network issues, rate limits)

Create src/scheduler/job-runner.js

HANDOFF NOTES FOR NEXT SESSION:
- Job runner uses Chrome alarms API
- Checks every 60 seconds
- Error handling: retry 3 times with exponential backoff
- Completed tweets are marked but not deleted (for history)

Update plan.md and commit when done."

End of Session 2:
- Commit: "[Schedule Feature - Phase 2] Background job runner complete"
- Update plan.md with handoff notes
- Close terminal
```

**Session 3: User Interface**
```
Prompt:
"Read plan.md handoff notes from Sessions 1-2.
This is Phase 3: User Interface.

TASKS:
1. Create UI for adding scheduled tweets
2. Show list of scheduled tweets (pending, completed, failed)
3. Allow editing/deleting scheduled tweets
4. Add form validation using data-layer validation rules
5. Show next execution time countdown

Create src/scheduler/ui/SchedulerPage.jsx

HANDOFF NOTES FOR NEXT SESSION:
- UI complete and styled with Ant Design
- Uses data-layer.js for all data operations
- Real-time updates when scheduled tweet executes
- Ready for integration testing

Update plan.md and commit when done."

End of Session 3:
- Commit: "[Schedule Feature - Phase 3] User interface complete"
- Update plan.md with handoff notes
- Close terminal
```

**Session 4: Integration & Testing**
```
Prompt:
"Read plan.md handoff notes from Sessions 1-3.
This is Phase 4: Integration & Testing.

TASKS:
1. Integrate UI with background job runner
2. Test end-to-end flow:
   - Add scheduled tweet via UI
   - Verify it appears in list
   - Wait for execution time (or mock time)
   - Verify tweet is posted
   - Verify UI updates
3. Test error scenarios
4. Add loading states and error messages
5. Performance test with 50 scheduled tweets

Mark Schedule Tweets feature as COMPLETE in plan.md."

End of Session 4:
- Commit: "[Schedule Feature - Phase 4] Integration complete, feature ready"
- Update plan.md: ✅ Schedule Tweets feature complete
```

**Why Relay Race Here:**
- Each phase builds on the previous
- Clear dependencies between phases
- Fresh context for each complex phase
- Prevents context bloat from spreading across all 4 phases

---

### Example 6: Bug Fix → Refactor → Feature Pipeline

**Scenario:** Found bugs that need fixing, which reveals need for refactoring, which enables new feature.

**Session 1: Bug Diagnosis & Fix**
```
"Users report that auto-reply sometimes fails silently.

TASKS:
1. Reproduce the bug
2. Add logging to understand failure points
3. Fix the immediate bug
4. Add tests to prevent regression

FINDINGS & HANDOFF:
- Bug was in error handling of reply-engine.js
- Fixed by adding try/catch and retry logic
- Noticed: reply-engine.js is doing too much (300+ lines)
- Recommendation: Refactor into smaller modules in next session

Update plan.md and decision-log.md with findings."
```

**Session 2: Refactoring Based on Findings**
```
"Read Session 1 findings in decision-log.md.

TASKS:
1. Split reply-engine.js into:
   - reply-matcher.js (keyword matching logic)
   - reply-sender.js (API calls)
   - reply-queue.js (queue management)
2. Maintain existing functionality
3. Improve error handling
4. Add unit tests for each module

HANDOFF:
- Refactoring complete, all tests pass
- reply-engine.js now has clean module boundaries
- Ready to add advanced features like conditional replies

Update plan.md: ✅ Refactor reply engine"
```

**Session 3: New Feature Using Refactored Code**
```
"Read Session 2 handoff notes.

NEW FEATURE: Conditional Replies
- Allow users to set conditions: only reply if tweet has >100 likes,
  or only reply to verified users

TASKS:
1. Add conditions schema to data layer
2. Extend reply-matcher.js to check conditions
3. Add UI for setting conditions
4. Test with various conditions

This is now easy because of the refactoring in Session 2!"
```

**Why Relay Race:**
- Bug fix revealed architectural issue
- Refactor needed before feature possible
- Each session has clear goal
- Fresh perspective at each stage

---

## Hybrid Approach Examples

### Example 7: Large Feature with Mixed Dependencies

**Scenario:** Building "AI-Powered Reply Suggestions" feature - has both parallel and sequential parts.

**Phase 1: Foundation (Sequential)**
```
Session 1: Core Architecture
- API client for AI service
- Response caching system
- Rate limiting
- Data schema
```

**Phase 2: True Parallel (Independent Research)**
```
Session 2A: Research AI APIs (GPT-4, Claude, local models)
Session 2B: Research prompt engineering best practices
Session 2C: Analyze competitor implementations
Session 2D: Draft user documentation
```

**Phase 3: Phased Parallel (Development)**
```
Session 3A: Backend integration with chosen AI API
Session 3B: UI for suggestion display
Session 3C: Settings for customizing suggestions
```

**Phase 4: Relay Race (Integration)**
```
Session 4: Integrate all parts
Session 5: Performance optimization
Session 6: Bug fixes and polish
```

---

### Example 8: Sprint Planning and Execution

**Scenario:** 1-week sprint with multiple features.

**Monday - Planning (True Parallel)**
```
Session A: Write technical specs for Feature 1
Session B: Write technical specs for Feature 2
Session C: Research technical feasibility of Feature 3
Session D: Design user flows for all features
```

**Tuesday-Wednesday - Foundation (Sequential)**
```
Session 1: Build shared utilities needed by all features
Session 2: Update data schema for all features
```

**Thursday - Development (Phased Parallel)**
```
Session 1: Implement Feature 1
Session 2: Implement Feature 2
Session 3: Implement Feature 3 (if feasible)
```

**Friday - Integration (Relay Race)**
```
Session 1: Integrate Feature 1, test
Session 2: Integrate Feature 2, test
Session 3: Integrate Feature 3, test
Session 4: End-to-end testing, bug fixes
```

---

## Troubleshooting Common Issues

### Issue 1: Parallel Sessions Both Modified Same File

**Problem:**
```
Session A and Session B both edited reply-engine.js
Git merge conflict when Session B tries to commit
```

**Solution:**
1. Use Control Session to review both changes
2. Determine which approach is better, or merge both
3. Have one session (or a third session) do the merge
4. Document decision in decision-log.md
5. Update plan.md to prevent future conflicts

**Prevention:**
- Before starting parallel sessions, clearly mark in plan.md which files each session owns
- If overlap is unavoidable, use Relay Race instead

---

### Issue 2: Foundation Wasn't Complete

**Problem:**
```
Started parallel sessions but foundation was missing key utilities
Sessions keep asking "where is the auth utility?"
```

**Solution:**
1. Pause parallel sessions
2. Use one session to add missing foundation piece
3. Commit foundation update
4. Resume parallel sessions

**Prevention:**
- Spend more time on foundation phase
- List all shared utilities needed before parallelizing
- Include "API Boundary Definition" in foundation tasks

---

### Issue 3: Context Too Large in Long Session

**Problem:**
```
Single session has been working for 3 hours
Responses getting slow, auto-compaction happening
Context feels "muddy"
```

**Solution: Switch to Relay Race**
1. Update plan.md with current status
2. Document any decisions in decision-log.md
3. Commit all work
4. Close session
5. Open fresh session
6. Prompt: "Read plan.md and decision-log.md. Continue from where Session X left off."

**Prevention:**
- Plan to switch sessions every 1-2 hours of focused work
- Use Relay Race for multi-hour tasks
- Keep sessions focused on specific goals

---

### Issue 4: Lost Track of What's Done

**Problem:**
```
Have 4 terminals open, not sure which tasks are complete
plan.md not updated, commits don't reference it
```

**Solution:**
1. Pause all sessions
2. Use Control Session to review git log and code
3. Update plan.md with actual current state
4. Have each session check in with their status
5. Reorganize work based on reality

**Prevention:**
- Update plan.md FREQUENTLY (every 30 min)
- Each commit must reference plan.md updates
- Use Control Session to monitor progress
- Review plan.md at start of each hour

---

### Issue 5: Parallel Work Without Clear Boundaries

**Problem:**
```
Started 3 parallel sessions but didn't define module boundaries
Sessions keep running into each other's work
Confusion about who's doing what
```

**Solution:**
1. STOP all parallel sessions
2. Use one session to define clear boundaries
3. Update plan.md with explicit file ownership
4. Document interfaces in decision-log.md
5. Restart parallel sessions with clear scope

**Example plan.md update:**
```markdown
## Parallel Phase - File Ownership

### Session A: Authentication Module
**Files:** src/auth/*.js
**Exports:** AuthManager class, login(), logout()
**Dependencies:** None

### Session B: API Client Module
**Files:** src/api/*.js
**Exports:** APIClient class, get(), post()
**Dependencies:** AuthManager from Session A (use interface)

### Session C: UI Components
**Files:** src/ui/*.jsx
**Dependencies:** APIClient from Session B (use interface)
```

**Prevention:**
- Always define boundaries BEFORE starting parallel work
- Use interface definitions
- Mark file ownership in plan.md

---

## Templates for Common Scenarios

### Template 1: Starting Parallel Development

**Before Starting:**
```markdown
# In plan.md

## Parallel Development Phase

**Start Date:** [DATE]
**Foundation Status:** ✅ Complete
**Estimated Duration:** [X] sessions

### Module Boundaries

#### Module A: [Name]
- **Owned by:** Session A
- **Files:** [list]
- **Exports:** [list]
- **Dependencies:** [list]
- **Completion Criteria:** [define]

#### Module B: [Name]
- **Owned by:** Session B
- **Files:** [list]
- **Exports:** [list]
- **Dependencies:** [list]
- **Completion Criteria:** [define]

### Integration Plan
- After all modules complete
- Session [X] will handle integration
- Integration criteria: [define]
```

### Template 2: Session Handoff (Relay Race)

**End of Session Prompt:**
```
"Update plan.md with the following handoff notes:

SESSION [X] COMPLETE - [Date] [Time]

Completed Tasks:
- [Task 1]
- [Task 2]

Files Modified:
- [File 1]: [what changed]
- [File 2]: [what changed]

Key Decisions:
- [Decision 1]
- [Decision 2]

Blockers/Issues:
- [Any problems encountered]

Next Session Should:
- [Specific next steps]
- [What to focus on]
- [Files to work with]

Important Notes:
- [Any gotchas or context needed]"
```

**Start of Next Session Prompt:**
```
"I'm starting Session [X+1] to continue the work from Session [X].

Please:
1. Read plan.md handoff notes from Session [X]
2. Read any relevant decisions in decision-log.md
3. Review git log -1 to see what was last committed
4. Summarize what was done and what I need to do next
5. Check for any blockers or issues noted

Then I'll proceed with the work."
```

---

## Advanced Techniques

### Technique 1: The "Watcher" Session

**Purpose:** Monitor multiple parallel sessions in real-time

**Setup:**
```
Dedicated terminal running watch commands:

watch -n 10 'git status'
watch -n 30 'git log --oneline -5'
watch -n 60 'cat plan.md | grep "Status: Active"'
```

**Use Case:**
- When running 4+ parallel sessions
- Need to detect conflicts early
- Want to see progress across sessions

---

### Technique 2: Time-Boxed Relay Race

**Purpose:** Force fresh context every N minutes

**Example:**
```
Session 1: 0:00-1:00 - Implement feature foundation
Session 2: 1:00-2:00 - Continue feature, add tests
Session 3: 2:00-3:00 - Polish and documentation
```

**Benefits:**
- Never hit context limits
- Fresh perspective each hour
- Forces good documentation

---

### Technique 3: Paired Sessions (A/B Testing Approaches)

**Purpose:** Try two different approaches to same problem

**Example:**
```
Problem: How to implement rate limiting?

Session A: Token bucket algorithm
Session B: Sliding window algorithm

After both complete:
Control Session: Compare both approaches
Decision: Choose best one or hybrid
Document: Add to decision-log.md
```

---

## Checklist: Am I Using God Mode Effectively?

### ✅ Planning
- [ ] I've read plan.md before starting work
- [ ] I understand which parallel mode applies (True/Phased/Relay)
- [ ] Module boundaries are clearly defined (if Phased Parallel)
- [ ] I've claimed my work area in plan.md
- [ ] Foundation is complete (if Phased Parallel)

### ✅ During Work
- [ ] I update plan.md every 30-60 minutes
- [ ] I document architectural decisions in decision-log.md
- [ ] I commit frequently with descriptive messages
- [ ] I reference plan.md in commit messages
- [ ] I avoid editing files owned by other sessions

### ✅ Session Handoff (Relay Race)
- [ ] I've completed my session's goals
- [ ] I've updated plan.md with handoff notes
- [ ] I've documented any decisions in decision-log.md
- [ ] I've committed all changes
- [ ] I've noted what next session should do
- [ ] I've closed the terminal for fresh context

### ✅ Coordination
- [ ] I use Control Session for code reviews
- [ ] I check for conflicts before parallel work
- [ ] I communicate through plan.md, not mental notes
- [ ] I read decision-log.md before making architectural changes

---

## Quick Decision Tree

```
Need to do multiple tasks?
│
├─ Are they completely independent?
│  │
│  └─ YES → Use TRUE PARALLEL
│     Open 3-4 terminals, work independently
│
├─ Do they share a foundation but are otherwise independent?
│  │
│  └─ YES → Use PHASED PARALLEL
│     Build foundation first (sequential)
│     Then parallelize feature development
│     Then integrate (sequential or relay)
│
└─ Are they sequential dependencies?
   │
   └─ YES → Use RELAY RACE
      Session 1 → commit → Session 2 → commit → Session 3
      Fresh context for each phase
```

---

**Remember: The right parallelization strategy depends on task dependencies, not just quantity of work.**

**Think dependencies. Plan with plan.md. Execute with focus. Review with control session.**

Happy parallel developing! 🚀
