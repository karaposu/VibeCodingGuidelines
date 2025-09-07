# VIBE CODING A NEW PROJECT 

This document contains ready-to-use prompts establishing the complete DevDocs pattern in your project. These prompts incorporate all concepts between Chapter 6 and chapter 11


As we mentioned in 

## Complete DevDocs Setup for The New Project


### Phase 0: Data Dump

This phase is explained in detailed in chapter_11/the_data_dump.md 

Dumb all project relevant info to AI. This is essential. Avoid making decisions in a rush. fuzzy is just fine. 
In Phase 1 we will digest all these information into 3 documents. 

   If you have multiple sources create data_dump.txt file and copy paste all 
   Make sure talk about 4 things, even in a fuzzy way. 
      - project purpose in terms of what you want to accomplish (non technical)
      - any preference in tech stack
      - platforms (mobile, web, embedded)
      - priorities in terms of platform, feartures and goals 



### Phase 1: Foundation Documents

This phase is explained in detailed in chapter_6/01_devdocs_pattern.md and chapter_6/02_root_docs.md

```
Based on the provided project information, I need you to establish the DevDocs pattern foundation.

First, analyze the project requirements and create a clear understanding of what we're building.
Create the following foundation documents:

1. devdocs/project_description.md

   What are we building?
   What problem are we solving
   What are the various scopes of this project?
   Who are the targeted users?


2. devdocs/philosophy.md
   - what is the philosophy of this project? (dont go into technical details)

   
3. devdocs/known_requirements.md
   - Technical requirements
   - Business requirements 
   - User requirements 

Focus on clarity and mutual understanding before any implementation.
```

### Phase 2: Concept Extraction and Clarification

This phase is explained in detail in chapter_6/03_concept_docs.md 

```
Using the foundation documents you just created (project_description.md, philosophy.md, known_requirements.md), 
extract and document the key core concepts (only needed and core ones):

1. Create devdocs/concepts.md
   - List only essential technical concepts
   - Order by importance/dependency
   - Brief one-line description for each

2. For each concept, create detailed clarification in devdocs/concept_clarifications/
   Name files with ordering prefixes (01_[concept].md, 02_[concept].md, etc.)
   
   Each clarification must answer:
    - Clear short explanation what it is and why it matters
    - How this concept helps the overall project
    - How this concept limits the overall project
    - What kind of information this concept needs as input
    - What kind of process this concept should use
    - What kind of information this concept outputs or relays
    - Explain the good expected outcome of realizing this concept
    - Explain the bad unwanted outcome of realizing this concept


```

### Phase 3: Simplification for MVP

This phase is explained in detail in chapter_6/03_concept_docs.md 

```
I want you to create simplified_concepts.md using concepts.md and the goal is to trim the features but the core ones for each concept so we can still have these concepts but they are more about prototype. 

And make sure you follow these rules during simplification
        - do not oversimplify the concept to the point underlying architecture is oversimplified and does not support the original concept
        - if a concept has a support for multi subconcept, do not binarize it but diminish the number of supported subconcepts by priotizing the most important ones. 

And then for each concept in simplified_concepts.md create me a clarification markdown file
which includes answer to these questions:

 For each concept write
    - clear short explanation what it is and why it matters
    - How this concept helps the overall project
    - How this concept limits the overall project
    - What kind of information this concept needs as input
    - What kind of process this concept should use
    - What kind of information this concept outputs or relays
    - explain the good expected outcome of realizing this concept
    - explain the bad unwanted outcome of realizing this concept

Put 1_ 2_ 3_ like prefix of each file to order them and make sure priotize the core concepts when you are ordering them. and do this in devdocs/simplified_concept_clarifications/

Critical: The simplification should reduce features, not break architecture and be flexible for future scope expansion
```


### Phase 4: Identifying Modules


We want development to be done in modular way. This ensures project stays in debuggable/testable complexity. 
This step identifies all possible modules. 


"""
Review the simplified concepts and identify logical abstractions that can be organized into modules. Focus on creating a modular architecture that will facilitate cleaner, more maintainable development. Ensure the proposed modularity doesn't compromise performance or security requirements. Avoid over-engineering - only modularize major conceptual boundaries. Document your module structure proposal in module_proposal.md

"""


### Phase 5: Architecture and Structure


```
Based on the simplified concepts, and module proposal please propose the most suitable architecture for this project. Keep in mind that we'll be developing iteratively, evolving from a simple prototype to more complex versions over time. And our priority is solid foundation whcih can be expanded overtime and not immediate full scope solution. 

Please use the info from module_proposal.md intelligently (you may choose not to create a module if it is not neccesary or overengineered for the MVP logic ) and avoid tightly coupled architecture. 

Key considerations:
- Avoid over-engineering or excessive complexity or explicity at this stage
- The architecture will evolve as we progress, so maintain flexibility
- Focus on high-level concepts that can accommodate the project's core requirements
- Present a design that balances simplicity with extensibility
- Make sure to use proper design patterns in order to keep modularity of codebase(e.g., repository pattern for DB related operations)

```

### Phase 6: Fuzzy Module Documentation

```
For each module identified, create comprehensive documentation:

Create devdocs/modules/[module_name]/ containing:

1. what_is_this_for.md
   - Core purpose
   - Why it's a separate module
   - What breaks without it
   - Who depends on it

2. interfaces_and_endpoints.md
   - Public methods/functions
   - API endpoints
   - Event emissions
   - Data structures

3. integration_points.md
   - How to integrate this module
   - Multiple integration approaches if flexible
   - Best practices for usage

4. integration_requirements.md
   - Environment variables needed
   - Database schemas required
   - External services
   - Configuration files

5. limitations.md
   - Performance boundaries
   - Feature boundaries
   - Technical constraints
   - Security limitations

6. possible_use_cases.md
   - Common usage patterns
   - Anti-patterns to avoid
   - Performance tips

7. edge_cases_covered.md
   - Handled edge cases
   - Error scenarios
   - Recovery mechanisms

8. example_usage.md
   - Code examples
   - Setup instructions
   - Common operations
   - Testing approach

9. summary.md
   - Quick reference
   - Main interfaces
   - Critical limitations
   - Integration checklist
```

### Phase 7: Selecting One module and Preparing for implementation


One way to enforce AI to do the development is done in a moduler way is to implement one by one. 
Here we are lis
   
   """
 
   With the project information, architecture overview, and module structure defined, select the first module for implementation.
   Choose a module that:
  1. Encapsulates the most messy distractive existing code
  2. Is peripheral to the core system (minimal dependencies)
  3. Has stable requirements unlikely to change
  4. Can be implemented independently without requiring other modules to be fully defined first


  And then create [module_name]_module_implementation_proposal.md which explain in order 
  
  1.  what components this modules would have?
  2.  what the interface/endpoints this module would show
  3.  how it would be used with pseudo code
  4.  how it will be used by other/core modules (in a high level without definitive definition)
   """



### Phase 8: Module implementation

 """

 Please implement this module with required files. Based on our previous discussions and documentation, 
please provide:

- Complete file list with their respective directory paths
- Full implementation for each file
- All necessary code to make this module functional

 """



### Phase 9: Smoke test

Details are explained in chapter_7/smoke_tests_pattern.md

"""
Let's design comprehensive smoke tests to validate our implementation. 
Please create smoke_tests folder if it doesnt exists. and Please create a test plan with the following structure:

1. 5 test files, each containing 5 focused test cases
2. File naming convention: test_01_[test_focus_area].py, test_02_[next_focus_area].py, etc.
3. Make sure these tests 
      -  Individual functions/methods in isolation 
      -  Test how components work together
      -  Verify solidly defined requirements are met or not
      
4. For each test file, provide:
  - Clear description of what aspect it tests
  - Why this testing area is critical
  - Brief outline of each test case within the file
5. these tests shouldnt use any testing frameworks. Make the outputs verbose enough so you can see what exactly does not work. 
6. Start with initialization test file. 
7. Each test file's top comment should include how to run it manually. 
"""


### Phase 10: Running the smoke test and fix the errors

It is important to run smoke tests by ourself

"""

"""




### Phase 6: Development Support Documents

```
Create supporting documentation for development:

1. devdocs/decisions.md
   - Log architectural decisions as you make them
   - Format: Date, Decision, Reasoning, Trade-offs

5. Create devdocs/issues/ structure:
   - issues/solved/ - for resolved problems
   - issues/unsolved/ - for known issues
   - issues/relevant_to_future/ - for future considerations
```

### Phase 7: Human-in-the-Loop Review

```
STOP - Human Review Required

Before proceeding with implementation, review and modify:

1. Simplified concepts - Are they still too complex? Too simple?
2. Architecture - Does it match your vision? Any concerns?
3. Module boundaries - Do they make sense for your team?
4. Technology choices - Are they appropriate for your context?

Edit any generated documents to match your actual needs.
This is your chance to steer before implementation begins.

After review, create devdocs/hil_adjustments.md documenting:
- What you changed and why
- Concerns to watch for
- Decisions you're uncertain about
```

## For Existing Projects

### Archaeology Phase

```
Analyze this existing codebase and create DevDocs:

Phase 1 - Surface Scan:
1. Map directory structure
2. Identify technologies from package files
3. Find all existing documentation
4. Check recent git activity
5. Create devdocs/initial_observations.md

Phase 2 - Deep Dive:
1. Trace main entry points
2. Follow 3-5 critical user flows
3. Map data models and schemas
4. Document actual API endpoints
5. Update devdocs/project_description.md with reality
6. Create devdocs/discovered_architecture.md

Phase 3 - Pattern Recognition:
1. What patterns are actually used?
2. What conventions exist?
3. How are errors handled?
4. What's the testing approach?
5. Create devdocs/actual_patterns.md

Phase 4 - Technical Debt:
1. Find TODO/FIXME/HACK comments
2. Identify workarounds
3. Locate fragile code
4. Create devdocs/technical_debt.md
5. Create devdocs/fragile_areas.md

Phase 5 - Extract Concepts:
Read the implementation and extract what concepts are actually implemented.
Create the same concept documentation structure as new projects,
but based on what EXISTS, not what was planned.
```

### Migration Planning

```
With DevDocs established for the existing project:

1. Compare current state to desired state
2. Create devdocs/migration_plan.md with:
   - What needs to change
   - What order to change it
   - What risks exist
   - What can't change (constraints)

3. Create devdocs/refactoring_opportunities.md
4. Create devdocs/quick_wins.md for easy improvements
```

## Quick Start Checklist

For any project using DevDocs pattern:

```
Please set up DevDocs pattern:

- [ ] Create devdocs/ folder structure
- [ ] Write three foundation documents
- [ ] Extract concepts from requirements
- [ ] Create concept clarifications
- [ ] Simplify concepts for MVP
- [ ] Create simplified clarifications
- [ ] Design architecture
- [ ] Define modules
- [ ] Document each module
- [ ] Set up issues tracking
- [ ] Create support documents
- [ ] Human review checkpoint

Start with foundation documents and proceed systematically.
Each phase builds on the previous one.
```

## Continuous DevDocs Maintenance

```
As development proceeds, continuously update DevDocs:

After each work session:
1. Update relevant module docs if interfaces changed
2. Log any architectural decisions in decisions.md
3. Document any issues in issues/
4. Update limitations.md if new constraints discovered
5. Add to notes.md any observations

Weekly:
1. Review if simplified concepts need expansion
2. Check if new modules are needed
3. Update architecture.md with any evolution
4. Move relevant items from notes.md to proper docs

This maintains DevDocs as living documentation.
```

## The Complete DevDocs Prompt

For maximum effectiveness, combine all phases:

```
I need to establish comprehensive DevDocs pattern for this project.

[Include all phase prompts from above]

Proceed systematically through each phase, creating all specified documentation.
After each phase, pause for my review before continuing.
Maintain consistency across all documents.
Ensure documents reference each other appropriately.
Keep language clear and specific.

The goal is a complete knowledge base that allows any AI assistant
to understand and contribute to this project effectively.
```

---

This ready_prompt.md provides comprehensive, copy-paste ready prompts for establishing the full DevDocs pattern, incorporating all concepts from Chapter 6 including foundation documents, concepts, simplification, architecture, modules, issues tracking, and continuous maintenance.









### Phase 9: Interface Discussion for Selected Module 

"""
Task: Based on selected module, create a comprehensive interface design document (interface_discussion.md) that explores API requirements and
  possibilities.

  Required Analysis:

  1. List All known Interface Capabilities
    - What operations must the interface support?
    - What configuration options are needed?
    - What input/output formats are required?
    - What modes of operation should exist?
  2. Review Current Implementation
    - Analyze existing code structure
    - Identify limitations and gaps
    - Note what works well
  3. Explore Design Patterns
    - Present multiple interface approaches (builder, functional, config-based, etc.)
    - Show concrete code examples
    - Compare pros/cons of each
  4. Propose Recommended Interface
    - Design that balances simplicity and power
    - Usage examples from basic to advanced
    - Method signatures and chaining options
    - Error handling approach
  5. Document Open Questions
    - Key decisions needing resolution
    - Trade-offs to consider
    - Naming conventions
    - Default behaviors

  Goal: Produce a thorough discussion document that clarifies interface requirements and provides foundation for making implementation decisions. Focus on understanding what's possible and what makes sense for users.

  Format: Markdown document with code examples, structured sections, and clear reasoning for recommendations.

"""