# Project Structure Standards

## Why Structure Matters More with AI

Humans navigate codebases through memory and intuition. AI navigates through structure. Good structure = AI superpowers. Bad structure = AI confusion.

## The Universal Structure

Every vibe coding project needs:

```
project-root/
├── README.md           # Project overview
├── GROUND_RULES.md     # AI instructions
├── architecture.md     # System design
├── requirements.md     # What we're building
├── devdocs/           # Development documentation
├── src/               # Source code
├── tests/             # Test files
└── .gitignore         # Standard ignores
```

This isn't arbitrary. Each file serves a purpose in AI collaboration.

## The Documentation Layer

### README.md
What humans read. Project overview, setup instructions, basic usage.

### GROUND_RULES.md
What AI reads first. Your project's constitution.

### architecture.md
Living document. Starts fuzzy, becomes specific. AI's blueprint.

### requirements.md
The "why" behind features. AI uses this for context.

### devdocs/
The thinking space:
```
devdocs/
├── decisions/       # Architectural decisions
├── concepts/        # Feature clarifications
├── interfaces/      # Module contracts
└── explorations/    # Experiments and spikes
```

## The Code Layer

### Modular by Design

```
src/
├── core/           # Business logic
├── services/       # External integrations
├── utils/          # Shared utilities
├── models/         # Data structures
└── api/           # Interface layer
```

Why: AI can work on modules independently.

### Test Proximity

Option 1: Separate test directory
```
tests/
├── test_core/
├── test_services/
├── test_utils/
└── test_api/
```

Option 2: Co-located tests
```
src/
├── core/
│   ├── auth.py
│   └── test_auth.py
```

Choose one. Be consistent. AI follows patterns.

## Language-Specific Structures

### Python Projects

```
project/
├── src/
│   └── myproject/      # Package name
│       ├── __init__.py
│       └── ...
├── tests/
├── requirements.txt    # Dependencies
├── setup.py           # Package setup
└── pyproject.toml     # Modern Python config
```

### JavaScript/TypeScript

```
project/
├── src/
│   ├── components/    # UI components
│   ├── services/      # Business logic
│   └── utils/         # Helpers
├── public/            # Static assets
├── package.json       # Dependencies
└── tsconfig.json      # TypeScript config
```

### Full-Stack Projects

```
project/
├── frontend/          # Client application
│   └── [framework structure]
├── backend/           # Server application
│   └── [framework structure]
├── shared/            # Common types/utils
└── docs/              # Unified documentation
```

## The Interface Pattern

Every module gets an interface file:

```
src/auth/
├── index.py          # Public interface
├── interface.md      # Contract documentation
├── implementation.py # Private implementation
└── tests.py         # Module tests
```

`interface.md` contains:
- What this module does
- What it needs (dependencies)
- What it provides (exports)
- How to use it

AI uses these for integration.

## The Evolution Pattern

### Stage 1: Exploration
```
project/
├── exploration.md     # What we're figuring out
├── spikes/           # Throwaway experiments
└── notes/            # Random thoughts
```

### Stage 2: Structure Emerges
```
project/
├── README.md
├── architecture.md
├── src/
│   └── prototype/
└── smoke_tests/
```

### Stage 3: Production Shape
```
project/
├── [Full structure as shown above]
└── ci/               # CI/CD configuration
```

Let structure grow with understanding.

## Anti-Patterns to Avoid

### The Kitchen Sink
```
src/
├── utils.py          # 5000 lines of random functions
├── helpers.py        # More random functions
└── common.py         # Even more random functions
```

AI can't navigate this. Neither can humans.

### The Deep Nest
```
src/app/modules/feature/subfeature/component/implementation/actual_code.py
```

AI loses context in deep hierarchies.

### The Flat Earth
```
src/
├── user_model.py
├── user_service.py
├── user_controller.py
├── product_model.py
├── product_service.py
└── [50 more files]
```

No organization = no AI understanding.

## Structure for AI Success

### 1. Consistent Naming
- `user_service.py` not `usersvc.py`
- `test_auth.py` not `auth_tests.py`
- Patterns AI can predict

### 2. Clear Boundaries
- One concept per directory
- One responsibility per file
- Explicit interfaces between modules

### 3. Documentation Proximity
- README in each major directory
- Interface docs with code
- Examples near implementations

## The `.ai` Directory Pattern

Some teams add:
```
.ai/
├── prompts/          # Reusable prompts
├── context/          # Files AI should always read
└── examples/         # Code examples for AI
```

This standardizes AI interaction across team.

## Migration Strategy

Starting with existing codebase?

1. Add documentation layer first
2. Create module interfaces
3. Gradually reorganize
4. Update as you work

Don't reorganize everything at once. Let structure emerge through use.

## The Golden Rule

Structure should make AI's job easier, not yours harder.

If you're fighting the structure, it's wrong. Good structure feels natural and makes AI more effective.

## Quick Start Script

```bash
#!/bin/bash
# init-vibe-project.sh

mkdir -p src tests devdocs/decisions devdocs/concepts
touch README.md GROUND_RULES.md architecture.md requirements.md
echo "# Project Name" > README.md
echo "# Ground Rules" > GROUND_RULES.md
echo "# Architecture" > architecture.md
echo "# Requirements" > requirements.md
echo "Project structure initialized for vibe coding!"
```

Start right, code happy.

Next: Part II - Understanding AI Collaboration →