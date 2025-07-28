# Vibe Coding Guidelines for Claude Code

I've been developing with AI assistants since GPT-4, and now extensively with Claude Code. These guidelines represent hard-won insights from real-world projects. I'm sharing them to help others build more robust software with AI assistance.

## Essential Setup Instructions

Before starting any project, establish these ground rules with Claude:

- **No Mock Data:** Tell Claude to avoid mocks/stubs unless absolutely necessary for external dependencies
- **File Path Headers:** Request `# filepath: path/to/file.py` comments at the top of every file for easy navigation
- **Modern Stack Only:** During active development, skip legacy compatibility concerns - you can add them later if needed

- **Minimize assumptions:** Dont assume things and check them if they are important, you already have accses to code.   

## Core Steps

### 1. Context Loading: The Foundation Phase

Before writing any code, thoroughly brief Claude on your project:

- Share all documentation, project descriptions, goals, and desired outcomes (even non-technical ones)
- Request Claude to explain **why** this project exists and what problems it solves
- Focus on understanding the core philosophy and requirements
- Explicitly prevent code generation at this stage - you're still thinking

### 2. Create a Vague Architecture

Architecture should be intentionally fuzzy at first:
- Avoid getting too specific early
- Let the design solidify naturally through next steps
- Focus on high-level concepts and important edge cases

### 3. Ask for the Why, Not the How

- Before architecture, ask Claude to explain the problem domain
- "What are the core challenges this solves?"
- "What are the failure modes we should anticipate?"

### 4. Ask It to Designate Core Modules and Give You Folder Structure

- Uncoupled core modules enable isolated testing
- We want to test modules individually, then integrate  
- This feels like moving slower but actually feels like a development

### 5. Pick One Core Module as Starting Point

- Choose tool-like modules first
- We are building the peripherals before integrators
- For this designated module ask for all files and contents in full code
- If there are more than 5 files or if files are too big something is wrong

### 6. Dependency Mapping interface.md

- After picking a module: "What external libraries will this need?"
- "What are the interfaces to other modules?"
- And ask it to save them into interface.md for future reference
- This interface.mds should be updated after step 8
- Helps prevent integration surprises in the future

### 7. Ask It to Design a List of Smoke Tests (Not Code Yet)

- At least 5 smoke test files
- Each file containing ~10 subtests
- Detail what each tests and why
- If something lacks detail, ask to expand or divide

### 8. Ask It to Create the First Smoke Test and Run It

- Smoke tests = development-focused code
- Verbose logging for AI self-debugging
- Run one test at a time
- Fix errors before moving to next
- Check previous tests don't break
- 3+ breaks = refactor signal
- **Manual Verification:** Always run tests yourself and review terminal output - Claude may miss subtle errors or warnings

### 9. Create Next Module in Isolation and Follow Steps 5-8

- Maintain the same rigorous process
- Keep modules independent

### 10. The Refactor Checkpoint

- Every 3 modules, ask: "Is architecture solid, are we missing something important?"
- Prevents technical debt accumulation

### 11. Ask It to Write Integration Smoke Tests

- Test how modules work together
- Identify interface issues early

### 12. Ask for Edge Cases

- "What edge cases did we miss in our smoke tests?"
- "Generate adversarial test cases"
- Claude excels at finding weird scenarios

### 13. Turn Smoke Tests and Implementations into Documentation

- Tests become living documentation
- Implementation details captured

### 14. In the End Create the Main Integration Module

- Now that peripherals are solid
- Integration becomes straightforward

### 15. Configuration Strategy

- "Design a configuration system for all modules"
- Environment variables, config files, secrets management

### 16. Ask It to Use All Smoke Tests to Create Pytest Files in Root

- For CI/CD pipeline
- Comprehensive test coverage

### 17. Performance & Security Audit

- "Review the codebase for performance bottlenecks"
- "Identify potential security vulnerabilities"
- Do this before finalizing

### 18. Ask It to Update README File

- Complete documentation
- Setup instructions
- Architecture overview

## Pro Tips

- **When tests break repeatedly (3+ times):** Ask Claude "Is this a design smell? Should we split this module?"
- **Use magic phrases:** "Think step by step" for complex debugging
- **Request patterns:** Ask for "defensive programming" patterns in critical modules
- **Module selection:** Start with utilities/tools, move to business logic, finish with integration
- **Test philosophy:** Smoke tests should be verbose and educational, not just pass/fail

## Key Principles

1. **Vibe First, Code Later** - Understand the philosophy before implementation
2. **Isolation Testing** - Build solid foundations through modular testing
3. **Smoke Tests as Documentation** - Tests that teach and verify
4. **Iterative Verification** - Test-fix-verify cycle prevents cascade failures
5. **Gradual Integration** - Peripherals → Core → Integration