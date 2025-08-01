# Vibe Refactoring with Claude

Refactoring legacy code with AI requires a systematic approach. This guide shows how to leverage Claude for safe, comprehensive refactoring while maintaining functionality.

## Phase 1: Documentation (Know What You Have)

### 1. Creating Generic Documentation

First, you must ask Claude to document the codebase thoroughly:
- "Analyze this codebase and create comprehensive documentation"
- "What does each module do and why does it exist?"
- "Document the data flow and key algorithms"
- Save output as `generic_documentation.md`

### 2. Creating endpoints_interfaces.md

Ask Claude to inspect the codebase to create interfaces documentation:
- "List all public interfaces, APIs, and entry points"
- "Document input/output formats for each endpoint"
- "Map dependencies between interfaces"
- This becomes your contract that must not break

### 3. Document Edge Cases

- "What edge cases does this codebase handle?"
- "Find all error handling and special conditions"
- "What assumptions does the code make?"
- Save as `edge_cases.md` - these are your test targets

### 4. Create Smoke Tests with Old Code

If your code is working, make sure to create smoke tests:
- "Create comprehensive smoke tests for current functionality"
- Running smoke tests provides good baseline during refactoring
- These tests are your safety net - they must pass after refactoring
- Save as `legacy_smoke_tests/`

## Phase 2: Planning (Design the Future)

### 5. Create Refactoring Proposal

Ask Claude to create a refactoring plan:
- "Create a refactoring proposal for this codebase"
- **Critical:** "Do not give me code, let's detail the architecture"
- Focus on structure, patterns, and design decisions
- Discuss module boundaries and responsibilities

### 6. Iterate and Expand

- Inspect the proposal and expand parts you like
- Ask for more detail on critical sections
- Challenge assumptions and explore alternatives
- Save final version as `refactoring_proposal.md`

### 7. Validate Against Documentation

Ask: "Will this proposal cover everything we documented in edge_cases.md, endpoints_interfaces.md, and generic_documentation.md?"
- Ensure no functionality is lost
- Verify all interfaces remain compatible
- Check edge case handling is preserved

### 8. Improve Based on Validation

- Update the proposal based on gaps found
- Add missing functionality coverage
- Ensure backward compatibility where needed

### 9. Unbloat the Design

Claude will overengineer some parts, so:
- "Create an unbloated version with same coverage"
- "What can we simplify without losing functionality?"
- "Remove unnecessary abstractions"
- Keep it as simple as possible, but no simpler

### 10. Identify Core Modules and Structure

- "Identify the core modules in this refactored design"
- "Create the folder structure for the new architecture"
- "Which modules are foundational vs dependent?"
- This guides your implementation order

### 11. Design Key Abstractions

Ask: "What abstractions would immensely make this codebase cleaner and easier to interact with?"
- Use the answer to improve the proposal
- Focus on abstractions that reduce complexity
- Ensure abstractions have clear boundaries

## Phase 3: Implementation (Build It)

### 12. Implement All Core Files

- "Implement all core files according to the proposal"
- Start with foundational modules first
- Each file should include `# filepath: path/to/file.py`
- No mocks unless absolutely necessary

### 13. Create New Smoke Tests

Ask Claude to create smoke tests for the new architecture:
- At least 5 test files
- 10 subtests in each file
- Focus on critical paths and edge cases
- More verbose logging than production tests

### 14. Run and Fix Tests Gradually

- Run smoke tests one by one
- Fix failures before moving to next test
- If a test keeps breaking (3+ times), reconsider that module's design
- Document any design changes made during fixes

## Phase 4: Verification (Ensure Success)

### 15. Create new_endpoints_interfaces.md

Once all smoke tests pass:
- "Document the new interfaces and endpoints"
- Compare with original `endpoints_interfaces.md`
- Ensure all contracts are maintained
- Note any improvements or changes

### 16. Create how_edge_cases_are_handled.md

- "Document how each edge case from edge_cases.md is now handled"
- Map old edge case handling to new implementation
- Verify nothing was missed
- This proves completeness of refactoring

### 17. Migration Documentation

Use these documents for migrating other codebases that use the refactored module:
- Create migration guide from old to new interfaces
- Document breaking changes if any
- Provide code examples for common migrations
- Include compatibility shims if needed

## Pro Tips

- **Incremental Approach:** Refactor one module at a time when possible
- **Test Continuously:** Never go too far without running tests
- **Document Changes:** Keep a refactoring log of decisions made
- **Preserve Behavior:** Refactoring changes structure, not functionality
- **Review Generated Code:** Claude might introduce subtle bugs - always review

## Success Metrics

Your refactoring is successful when:
1. All legacy smoke tests pass with new code
2. New smoke tests provide better coverage
3. Code is cleaner and more maintainable
4. All edge cases are handled
5. Migration path is clear and documented