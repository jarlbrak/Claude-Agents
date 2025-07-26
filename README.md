# Claude Agents Team

A specialized team of AI agents designed to handle different aspects of software development and project management. Each agent has specific expertise and tools tailored to their role.

> **Note**: This folder contains agent definitions for use with Claude Code. The orchestration logic is defined in `CLAUDE.md`. Each `.md` file (except this README and CLAUDE.md) defines a specialized agent with specific tools and responsibilities.

## Team Members

### Product Spec Manager
**Role**: Product strategy and requirements definition  
**Expertise**: Creating detailed product specifications, clarifying feature requirements, prioritizing development tasks, and ensuring team alignment with product goals.  
**When to use**: Need help defining new features, prioritizing development work, or creating comprehensive specifications.

### Software Architect
**Role**: System design and technical leadership  
**Expertise**: Architectural guidance, system design decisions, coding standards establishment, and breaking down product specifications into developer tasks. Follows KISS principles and functional programming paradigms.  
**When to use**: Designing new systems, establishing coding standards, or translating product requirements into technical tasks.

### Code Standards Enforcer
**Role**: Quality assurance and standards compliance  
**Expertise**: Ruthlessly enforcing coding standards, reviewing code changes for architectural compliance, and ensuring consistency across the codebase.  
**When to use**: After code implementation to ensure adherence to established standards and architectural patterns.

### Backend Systems Engineer
**Role**: Server-side development and infrastructure  
**Expertise**: Building bulletproof backend systems with comprehensive error handling, functional programming techniques, API development, and graceful failure patterns.  
**When to use**: Designing APIs, implementing server-side logic, database integrations, or any backend system requiring high reliability.

### Frontend UI Engineer
**Role**: User interface and user experience  
**Expertise**: Building accessible UI components, responsive design, API integration, and creating intuitive user experiences that work across all devices and assistive technologies.  
**When to use**: Creating user interfaces, implementing responsive designs, or integrating frontend with backend APIs.

### UI Documentation Tester
**Role**: Documentation validation and user experience testing  
**Expertise**: Ensuring user interfaces match their documentation and validating that documented workflows actually work as described.  
**When to use**: Before release to validate that UI matches documentation and users can successfully follow documented procedures.

### Release Manager
**Role**: Quality control and repository management  
**Expertise**: Pre-commit validation, stakeholder coordination, commit management, and ensuring nothing enters the repository without meeting quality standards.  
**When to use**: When ready to commit changes after development is complete - handles the entire release process.

### Technical Documentation Specialist
**Role**: Documentation creation and technical writing  
**Expertise**: Creating comprehensive technical documentation that bridges the gap between technical implementation and user understanding, serving multiple audiences.  
**When to use**: Creating API docs, user guides, architectural overviews, or any documentation that needs to be accessible to diverse audiences.

## Tool Usage Matrix

| Agent | Basic Tools | Analysis Tools | Development Tools | Testing Tools | Documentation Tools | Browser Tools | Specialized Tools |
|-------|-------------|----------------|-------------------|---------------|-------------------|---------------|------------------|
| **Product Spec Manager** | ✅ Glob, Grep, LS, Read | ❌ | ❌ | ❌ | ✅ TodoWrite | ❌ | ✅ chat, planner, consensus, challenge |
| **Software Architect** | ✅ Glob, Grep, LS, Read, Edit, Write | ✅ analyze, debug | ✅ Task, Bash, executeCode | ✅ testgen | ✅ docgen, TodoWrite | ❌ | ✅ chat, thinkdeep, planner, consensus, codereview, precommit, secaudit, refactor, tracer, challenge |
| **Code Standards Enforcer** | ✅ Glob, Grep, LS, Read | ❌ | ❌ | ❌ | ✅ TodoWrite | ❌ | ✅ codereview, precommit, secaudit, analyze, challenge |
| **Backend Systems Engineer** | ✅ Glob, Grep, LS, Read, Edit, Write | ✅ debug | ✅ Task, Bash, executeCode | ✅ testgen | ✅ TodoWrite | ❌ | ✅ codereview, precommit, secaudit, analyze, refactor, tracer, testgen, challenge |
| **Frontend UI Engineer** | ✅ Glob, Grep, LS, Read, Edit, Write | ✅ debug | ✅ Task, Bash, executeCode | ❌ | ✅ TodoWrite | ❌ | ✅ analyze, refactor, tracer, challenge |
| **UI Documentation Tester** | ✅ Glob, Grep, LS, Read, Write | ❌ | ✅ Bash | ❌ | ✅ TodoWrite | ❌ | ❌ |
| **Release Manager** | ✅ Glob, Grep, LS, Read | ❌ | ✅ Task, Bash | ❌ | ✅ TodoWrite | ❌ | ✅ precommit, secaudit, challenge |
| **Technical Documentation Specialist** | ✅ Glob, Grep, LS, Read, Edit, Write | ✅ analyze | ✅ Task, Bash | ❌ | ✅ docgen, TodoWrite | ❌ | ✅ chat |

### Tool Categories Explained

- **Basic Tools**: File system operations (Glob, Grep, LS, Read, Edit, Write, etc.)
- **Analysis Tools**: Deep thinking and analysis capabilities (analyze, thinkdeep, chat, debug)
- **Development Tools**: Code execution and system interaction (Task, Bash, executeCode)
- **Testing Tools**: Test generation and validation (testgen)
- **Documentation Tools**: Documentation creation and management (docgen, TodoWrite)
- **Browser Tools**: Web interface testing and interaction (Playwright tools)
- **Specialized Tools**: Role-specific advanced capabilities (planner, consensus, codereview, etc.)

## Setup Instructions

1. **Copy the agent files** to your project's `.claude/agents/` folder
2. **Use the orchestrator** by copying `CLAUDE.md` to your project root or `.claude/` folder
3. **Start your session** with: `Read CLAUDE.md and tell me what you do and what you need from me to start.`

See `CLAUDE.md` for complete orchestration workflows and operational guidelines.

## Team Orchestration & Workflow

**Important**: All agents now operate through an orchestrator and cannot directly invoke each other. Each agent has been configured with specific orchestration guidelines:

### Workflow Enforcement
- **No direct agent-to-agent communication**: All coordination goes through the orchestrator
- **Work artifact handoffs**: Agents pass complete deliverables through the orchestrator with clear approval status
- **Role boundary enforcement**: Each agent knows exactly when to request other team members through the orchestrator

### Key Orchestration Patterns
1. **Product Spec Manager** → Requests architect for feasibility, developers for implementation
2. **Software Architect** → Requests product specs for requirements, passes technical specs to developers  
3. **Backend/Frontend Engineers** → Request architect for guidance, standards enforcer for review, release manager for deployment
4. **Code Standards Enforcer** → Requests architect for design decisions, passes review reports back through orchestrator
5. **Release Manager** → Coordinates with all team members through orchestrator for quality gates
6. **Technical Documentation Specialist** → Requests implementation details from engineers, architectural context from architect
7. **UI Documentation Tester** → Reports issues back to appropriate agents through orchestrator

### Usage Guidelines

1. **Orchestrated Workflow**: All agents work through the orchestrator - no direct agent invocation allowed
2. **Quality Gates**: Multiple checkpoints ensure standards compliance at each phase
3. **Work Artifact Management**: Clear handoff protocols with complete deliverables and approval status
4. **Team Boundaries**: Each agent has explicit limits and knows when to escalate through orchestrator
5. **Context Preservation**: Orchestrator maintains project context and passes relevant artifacts between agents