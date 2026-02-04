---
trigger: always_on
---

# GEMINI.md - Antigravity Kit (Персонализированный)

> Правила для AI в этом workspace. Адаптировано под стек Даниила.

---

## 🎯 ПЕРСОНАЛЬНЫЕ НАСТРОЙКИ (ПРИОРИТЕТ P0)

**Владелец:** Даниил (Junior Frontend Engineer)
**Язык общения:** Русский
**Комментарии в коде:** На русском!

**Стек:**
- React + TypeScript
- Next.js (по запросу)
- Tailwind CSS + shadcn/ui
- Zustand (Redux если проект требует)
- Firebase
- Framer Motion / GSAP

**Дизайн:**
- Glassmorphism + Neumorphism + Minimal
- Тёмная тема по умолчанию
- Вдохновение: Vercel, Linear, Raycast
- 🚫 Purple Ban — фиолетовый запрещён!
- 🚫 Шаблонные дизайны запрещены

---

## CRITICAL: AGENT & SKILL PROTOCOL

> **MANDATORY:** Read agent file + skills BEFORE coding.

- Agent activated → Check `skills:` → Read SKILL.md → Apply
- Priority: P0 (GEMINI.md) > P1 (Agent) > P2 (SKILL.md)
- Never skip "Read → Understand → Apply"

---

## 📥 REQUEST CLASSIFIER (STEP 1)

**Before ANY action, classify the request:**

| Request Type     | Trigger Keywords                           | Active Tiers                   | Result                      |
| ---------------- | ------------------------------------------ | ------------------------------ | --------------------------- |
| **QUESTION**     | "what is", "how does", "explain"           | TIER 0 only                    | Text Response               |
| **SURVEY/INTEL** | "analyze", "list files", "overview"        | TIER 0 + Explorer              | Session Intel (No File)     |
| **SIMPLE CODE**  | "fix", "add", "change" (single file)       | TIER 0 + TIER 1 (lite)         | Inline Edit                 |
| **COMPLEX CODE** | "build", "create", "implement", "refactor" | TIER 0 + TIER 1 (full) + Agent | **{task-slug}.md Required** |
| **DESIGN/UI**    | "design", "UI", "page", "dashboard"        | TIER 0 + TIER 1 + Agent        | **{task-slug}.md Required** |
| **SLASH CMD**    | /create, /orchestrate, /debug              | Command-specific flow          | Variable                    |

---

## 🤖 INTELLIGENT AGENT ROUTING (STEP 2 - AUTO)

**ALWAYS ACTIVE: Before responding to ANY request, automatically analyze and select the best agent(s).**

> 🔴 **MANDATORY:** You MUST follow the protocol defined in `@[skills/intelligent-routing]`.

### Auto-Selection Protocol

1. Analyze request → Select Agent → Apply rules
2. Announce: `🤖 Applying @[agent-name]...`
3. If user mentions `@agent` → use it

> 🔴 Writing code without agent = PROTOCOL VIOLATION

---

## TIER 0: UNIVERSAL RULES (Always Active)

### 🌐 Language Handling

Когда пользователь пишет НЕ на английском:

1. **Внутренне переводи** для лучшего понимания
2. **Отвечай на языке пользователя** — Даниилу на русском!
3. **Комментарии в коде:** НА РУССКОМ (по правилам Даниила)
4. **Переменные/функции:** на английском (camelCase)

### 🧹 Clean Code (Global Mandatory)

**ALL code MUST follow `@[skills/clean-code]` rules. No exceptions.**

- **Code**: Concise, direct, no over-engineering. Self-documenting.
- **Testing**: Mandatory. Pyramid (Unit > Int > E2E) + AAA Pattern.
- **Performance**: Measure first. Adhere to 2025 standards (Core Web Vitals).
- **Infra/Safety**: 5-Phase Deployment. Verify secrets security.

### 📁 File Dependency Awareness

**Before modifying ANY file:**

1. Check `CODEBASE.md` → File Dependencies
2. Identify dependent files
3. Update ALL affected files together

### 🗺️ System Map Read

> 🔴 **MANDATORY:** Read `ARCHITECTURE.md` at session start to understand Agents, Skills, and Scripts.

**Path Awareness:**

- Agents: `.agent/` (Project)
- Skills: `.agent/skills/` (Project)
- Runtime Scripts: `.agent/skills/<skill>/scripts/`

### 🧠 Read → Understand → Apply

Before coding: What is GOAL? What PRINCIPLES? How DIFFERS from generic?

---

## TIER 1: CODE RULES (When Writing Code)

### 📱 Project Type Routing

| Project Type                           | Primary Agent         | Skills                        |
| -------------------------------------- | --------------------- | ----------------------------- |
| **MOBILE** (iOS, Android, RN, Flutter) | `mobile-developer`    | mobile-design                 |
| **WEB** (Next.js, React web)           | `frontend-specialist` | frontend-design, react-best-practices, tailwind-patterns |
| **BACKEND** (API, server, Node.js)     | `backend-specialist`  | api-patterns, nodejs-best-practices |

> 🔴 **Mobile + frontend-specialist = WRONG.** Mobile = mobile-developer ONLY.
> 🔴 **Даниил = WEB.** Используй `frontend-specialist` по умолчанию.

### 🛑 Socratic Gate

**Complex requests → STOP and ASK first:**
- New Feature → 3+ questions
- Bug Fix → Confirm + impact
- Vague → Purpose, Users, Scope
- Never assume. Wait for user confirmation.

### 🏁 Final Checklist Protocol

**Trigger:** Когда пользователь говорит "финальные проверки", "final checks", "проверь всё" и подобное.

| Task Stage       | Command                                            | Purpose                        |
| ---------------- | -------------------------------------------------- | ------------------------------ |
| **Manual Audit** | `python .agent/scripts/checklist.py .`             | Priority-based project audit   |
| **Pre-Deploy**   | `python .agent/scripts/checklist.py . --url <URL>` | Full Suite + Performance + E2E |

**Priority Execution Order:**

1. **Security** → 2. **Lint** → 3. **Schema** → 4. **Tests** → 5. **UX** → 6. **Seo** → 7. **Lighthouse/E2E**

**Rules:**

- **Completion:** A task is NOT finished until `checklist.py` returns success.
- **Reporting:** If it fails, fix the **Critical** blockers first (Security/Lint).

**Available Scripts (актуальные):**

| Script                     | Skill                 | When to Use         |
| -------------------------- | --------------------- | ------------------- |
| `lint_runner.py`           | lint-and-validate     | Every code change   |
| `ux_audit.py`              | frontend-design       | After UI change     |
| `accessibility_checker.py` | frontend-design       | After UI change     |
| `seo_checker.py`           | seo-fundamentals      | After page change   |
| `bundle_analyzer.py`       | performance-profiling | Before deploy       |
| `lighthouse_audit.py`      | performance-profiling | Before deploy       |

> 🔴 **Agents & Skills can invoke ANY script** via `python .agent/skills/<skill>/scripts/<script>.py`

### 🎭 Gemini Mode Mapping

| Mode     | Agent             | Behavior                                     |
| -------- | ----------------- | -------------------------------------------- |
| **plan** | `project-planner` | 4-phase methodology. NO CODE before Phase 4. |
| **ask**  | -                 | Focus on understanding. Ask questions.       |
| **edit** | `frontend-specialist` | Execute. Check `{task-slug}.md` first.   |

**Plan Mode (4-Phase):**

1. ANALYSIS → Research, questions
2. PLANNING → `{task-slug}.md`, task breakdown
3. SOLUTIONING → Architecture, design (NO CODE!)
4. IMPLEMENTATION → Code + tests

> 🔴 **Edit mode:** If multi-file or structural change → Offer to create `{task-slug}.md`. For single-file fixes → Proceed directly.

---

## TIER 2: DESIGN RULES

> Design rules in specialist agents. Read `.agent/agents/frontend-specialist.md` for web UI.

---

## 📁 QUICK REFERENCE

### Агенты (12 шт)

- **Frontend:** `frontend-specialist` (основной для Даниила)
- **Backend:** `backend-specialist`
- **Mobile:** `mobile-developer`
- **Debug:** `debugger`
- **Planning:** `project-planner`
- **Performance:** `performance-optimizer`
- **Docs:** `documentation-writer`
- **SEO:** `seo-specialist`
- **Explore:** `explorer-agent`, `code-archaeologist`
- **Product:** `product-manager`, `product-owner`

### Ключевые скиллы

- **Code:** `clean-code`, `react-best-practices`, `tailwind-patterns`
- **Design:** `frontend-design`, `mobile-design`, `web-design-guidelines`
- **Planning:** `brainstorming`, `plan-writing`, `architecture`
- **Docs:** `documentation-templates`, `seo-fundamentals`

---
