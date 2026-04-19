# AI Multi-Agent System

Complete AI-driven multi-agent system for software development that separates **Product thinking** (WHAT/WHY) from **Engineering execution** (HOW) with strict quality control (VALIDATION).

## 🎯 System Overview

This system implements a state-driven v2 architecture with:

- **Product Owner Layer** - Isolated from engineering, defines WHAT & WHY
- **Engineering Multi-Agent System** - Implements HOW with strict governance
- **Human Approval Gates** - Critical checkpoints requiring human review
- **Skills Reuse System** - Reusable engineering modules
- **Rules Enforcement System** - Automatic violation detection

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    PRODUCT OWNER LAYER                      │
│  (Fully Isolated - No access to engineering system)        │
│                                                              │
│  • PRODUCT_VISION.md    ← What problem we solve             │
│  • ROADMAP.md          ← MVP → Production path              │
│  • MVP_SPEC.md         ← Scope & acceptance criteria        │
│  • BACKLOG.md          ← Prioritized features               │
└─────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────┐
│                    PLANNING LAYER                           │
│                                                              │
│  Planner Agent                                              │
│  • Converts BACKLOG → EXECUTION_PLAN.md                     │
│  • 🛑 STOPS for HUMAN APPROVAL                              │
└─────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────┐
│                    ORCHESTRATION LAYER                      │
│                                                              │
│  Orchestrator Agent                                         │
│  • Reads STATE.json (Single Source of Truth)                │
│  • Controls phase transitions                               │
│  • Enforces human approval gates                            │
│  • Coordinates all agents                                   │
└─────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────┐
│                    ENGINEERING LAYER                        │
│                                                              │
│  Architecture Agent     ← Designs system structure         │
│       ↓                                                     │
│  Backend Agent          ← Implements code (MUST use skills) │
│       ↕                                                     │
│  Reviewer Agent         ← Validates (max 3 cycles)          │
└─────────────────────────────────────────────────────────────┘
```

## 📁 Project Structure

```
.opencode/
├── agents/
│   ├── product-owner.md      # 👤 Isolated Product Owner
│   ├── planner.md            # 🧠 Backlog → Execution Plan
│   ├── orchestrator.md       # ⚙️ State Management
│   ├── architecture.md       # 🏗️ System Design
│   ├── backend.md            # ⚙️ Implementation
│   └── reviewer.md           # 🔍 Quality Control
├── product/
│   ├── PRODUCT_VISION.md
│   ├── ROADMAP.md
│   ├── MVP_SPEC.md
│   └── BACKLOG.md
└── project/
    ├── STATE.json            # 📊 Single Source of Truth
    ├── EXECUTION_PLAN.md     # 📋 Human Approval Gate
    ├── ARCHITECTURE.md
    ├── DECISIONS.md
    ├── RULES.md              # ⚖️ Enforcement System
    └── SKILLS_INDEX.md       # 🧩 Skills Registry
```

## 🧩 Agent Roles

### 1. Product Owner (Isolated)
**Responsibilities:**
- Defines product vision and roadmap
- Creates prioritized backlog
- Writes MVP specifications
- **Cannot** interact with engineering system

### 2. Planner
**Responsibilities:**
- Converts backlog to execution plan
- Decomposes features into technical tasks
- Defines acceptance criteria
- **Creates** EXECUTION_PLAN.md
- **Triggers** human approval gate

### 3. Orchestrator
**Responsibilities:**
- Manages STATE.json (single source of truth)
- Controls phase transitions
- Enforces human approval gates
- Coordinates agent workflow
- Tracks violations

### 4. Architecture Agent
**Responsibilities:**
- Designs system architecture
- Selects technology stack
- Defines API contracts
- Maps required skills
- Follows KISS principle

### 5. Backend Agent (Senior Engineer)
**Responsibilities:**
- Implements tasks from execution plan
- **MUST** use existing skills
- Writes tests (80%+ coverage)
- Handles reviewer feedback
- **Max 3 review cycles**

### 6. Reviewer Agent
**Responsibilities:**
- Validates code quality
- Enforces RULES.md
- Checks skill usage
- Approves or rejects work
- Escalates after 3 cycles

## 🔄 System Flow

```
1. Product Owner generates artifacts
   ↓
2. Planner creates EXECUTION_PLAN.md
   ↓
3. 🛑 HUMAN APPROVAL GATE 🛑
   ↓
4. Orchestrator reads STATE.json
   ↓
5. Architecture Agent designs system
   ↓
6. Backend Agent implements task
   ↓
7. Reviewer validates (loop max 3)
   ↓
8. All tasks complete → DONE
```

## ⚖️ Rules System

All agents must follow **RULES.md**:

1. **STATE.json is the only truth** - All state in one place
2. **No scope expansion beyond plan** - Strict adherence to EXECUTION_PLAN
3. **Skills MUST be reused** - Backend cannot create duplicate skills
4. **Architecture is immutable** - Changes require human approval
5. **Backend-review loop max 3 cycles** - Then escalate to human
6. **Product Owner is fully isolated** - No engineering interaction
7. **KISS principle** - No over-engineering

## 🧩 Skills System

The system includes reusable engineering skills:

- **Language-specific:** `golang-*`, `python-*`, `typescript-*`
- **Domain-specific:** `auth`, `database`, `api-design`, `testing`
- **Infrastructure:** `docker`, `k8s`, `ci-cd`

## 🚀 Quick Start

### 1. Clone the Repository

```bash
git clone https://github.com/alekparkhomenko/ai-multi-agent-system.git
cd ai-multi-agent-system
```

### 2. Copy to Your Project

```bash
# Copy agents
cp -r agents/ /path/to/your/project/.opencode/

# Create product & project directories
mkdir -p /path/to/your/project/.opencode/product
mkdir -p /path/to/your/project/.opencode/project
```

### 3. Initialize STATE.json

Copy `project/STATE.json` schema and customize for your project.

### 4. Start with Product Owner

Begin by creating product artifacts in `product/` folder.

## 📚 Documentation

- **[Agent Definitions](agents/)** - Full agent specifications
- **[Product Artifacts](product/)** - Example product documentation
- **[Project Management](project/)** - State, rules, and decisions

## 🎯 Use Cases

This system is ideal for:

- **AI-assisted software development** - Structured approach to AI coding agents
- **Team collaboration** - Clear separation of product and engineering
- **Quality assurance** - Built-in review and validation
- **Knowledge reuse** - Skills system prevents duplication
- **Governance** - Human oversight at critical points

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

**⭐ Star this repository if you find it useful!**
