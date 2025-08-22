# The DevDocs Pattern

This is most common vibe coding pattern. And the reason is it fills common pitfalls when it comes to vibe coding. And extremely helpful. 

If you have a specific vision on your mind it is not good idea to let ai go rogue for hours and create something different. It is really important to be on the same page of what is being created. But development is such process where most of the concepts will evolve over time and even though you have a good beginning documentation it is easy to get lost and introduce wrong concepts. 


And also without devdocs pattern. When we ask AI to do/implement something, it will include hidden task of planning
as well and due to context limitations memory state might be missing vital info and doing planning and implementation in one step will usuall introduce errors and hallucinations. 

Just like humans, it is easier for AI to focus on one task. This is why we will lighten it's task by enforcing a seperation between planning phase and implementation phase. 



1.  we shold know what AI thinks before we allow it to do the implemention, in every major step. 



2. AI should know what to implement before the implemention

- AI should know what to implement before the implemention
- Human in the loop 






This pattern has 3 concepts

- Devdocs helps us know what AI thinks before we let it implement something. 
- Let AI document what he should implement before it implements it. 
- Devdocs documentation is part of development 



devdocs enables you to be human in the loop. 





## Why Documentation as Source of Truth

Traditional development: Code is truth, docs are afterthought.
Vibe coding flips this: Documentation drives development.

In vibe coding, documentation isn't overhead or afterthought - it's the specification that AI uses to build and maintain the system correctly.

DevDocs pattern is one of the core design patterns for vibe coding. The idea is to use excessive documentation as a source of truth together with code. DevDocs matters because during development "why" can matter as much as "how" and to keep track of both context is really important.

Unlike traditional docs convention to store documentation in the root, devdocs lives inside the src because:
- DevDocs are integral to the build process (AI reads them)
- They're not optional metadata - they're required source material for further building and changes
- Keeping them with code emphasizes their active role
- They document intent while being necessary inputs for AI-driven development


Also one thing that is really important is to throughly reading the generated devdocs files and fixing them as soon as possible. 


Devdocs are 3 generic devdoc categories


generic project documentation which are the root documents
dev related documentatiion 
documentation about runing logic 




## The DevDocs Structure

```
project-root/
└── src/
    ├── devdocs/
    │   ├── project_description.md
    │   ├── philosophy.md
    │   ├── known_requirements.md
    │   ├── concepts.md
    │   ├── simplified_concepts.md
    │   ├── concept_clarifications/
    │   ├── simplified_concept_clarifications/
    │   ├── decisions.md
    │   ├── explorations.md
    │   ├── notes.md
        ├── user_stories.md
    │   └── modules/
    │       └── module_a/
    │           ├── what_is_this_for.md
    │           ├── interfaces_and_endpoints.md
    │           ├── integration_points.md
    │           ├── integration_requirements.md
    │           ├── limitations.md
    │           ├── possible_use_cases.md
    │           ├── edge_cases_covered.md
    │           └── example_usage.md
                └── summary.md
            
        issues/
            solved
                01_issue_tg_connection
                        explaination.md (includes when this issue occurs, and why it is problem in context of whole app) 
                        what_i_learned.md (explains what was done wrongly and why and what was the solition about this issue )
            unsolved
            future
    |
```



Lets explain each devdocs file. 

## The Three Foundation Documents

### 1. project_description.md

This document explains the project in general with all available details. It is basically structured version of messy project data.
  It should answer:
     What are we building?
     What problem are we solving
     What are the various scopes of this project?


This document anchors everything. AI reads this first.

### 2. philosophy.md

This document focuses of real world impacts/motivations/goals of the project. Holds important information and prevents  Complexity Drift as well as Scope Drift. 
Answers "what is the philosophy of this project?". Doesnt go into technical details but aims to capture the soft requirements and goals which are usually missed. 



### 3. known_requirements.md

Answer the question of 
What constraints exist for given project. 
And inspect the Requirements in 3 main categories:

 - Known Technical Requirements
 - Known Business Requirements
 - Known User Requirements

Requirements ground AI suggestions in reality.


## Concept Documentations
what is concepts.md

what is concept_clarifications/ folder for and what it includes

why do we need simplified_concepts.md and simplified_concept_clarifications/


## Context related documentation files

what is decisions.md
what is notes.md
what is user_stories.md
what is  explorations.md


## Module related documentation files






## Living Documentation Files

### decisions.md

Track architectural decisions as they happen. 
each entry explains 
    - what is current bottleneck/issue
    - what are our options
    - what is the best one, why
    - explain what needs to be changed in high level 

```markdown
# Architectural Decisions

## 2024-01-15: Use SQLite for local storage
- Considered: JSON files, SQLite, Realm
- Chose SQLite for: SQL queries, proven reliability, zero config
- Trade-off: Slightly larger app size

## 2024-01-20: Monolith over microservices
- Keeps deployment simple
- Single user app doesn't need service separation
- Can split later if needed
```

### explorations.md

Document what you tried and why you moved on:

```markdown
# Explorations

## Attempted: Real-time sync across devices
- Built prototype with CloudKit
- Realized it violated our privacy-first philosophy
- Learned: Local-first means truly local
- Abandoned in favor of manual export/import

## Attempted: AI-powered categorization
- Too complex for MVP
- Privacy concerns with cloud AI
- Saved for future local ML exploration
```

### notes.md

Informal thoughts that might become formal later:

```markdown
# Development Notes

- Currency conversion might need offline rates
- Consider widget for quick expense entry
- Dark mode is probably essential
- Export format might need receipts attachment later
```

## Concepts Documentation
 
### concepts.md & concept_clarifications

Extract key technical concepts from requirements

"""
Using these project_description.md, philosophy.md,  known_requirements.md
 create me 
   - `concepts_to_implement.md`  by extracting the key
technical concepts (needed ones only and core ones. )

and then for each concept in concepts_to_implement.md create me a clarification markdown file
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

Put 1_ 2_ 3_ like prefix of each file to order them and make sure priotize the core concepts when you are ordering them. and do this in devdocs/concept_clarifications/
"""

### simplified_concepts.md & simplified_concept_clarifications/


The concept_clarifications dir contains many concepts. And implementing each of them with their full scope is not a good idea.  And there is a high chance when you read all 
these full scope concepts you felt overwhelmed and it will be same for ai too. Our job as a human in the loop is to 
make AI do the work in a modular gradual increments.  

So at first we want to create a working prototpye and then expand this prototype to MVP over time. 
This is why first we will ask AI to create simplified_concepts_to_implement.md file. 

But when it is simplifiying these features it must not oversimplify the concept that in the end when we are going to expand the features we would need full rewrite of databases and submodules. 

This is a step where you get to be human in the loop and actually do some real work. It is vital for the rest of the development that you edit the these simplified concept files. Make sure you read them and clarify anything which doesnt make sense. 


"""
I want you to create simplified_concepts_to_implement.md using concepts_to_implement.md and the goal is to trim the features but the core ones for each concept so we can still have these concepts but they are more about prototype. 

And make sure you follow these rules during simplification
        - do not oversimplify the concept to the point underlying architecture is oversimplified and does not support the original concept
        - if a concept has a support for multi subconcept, do not binarize it but diminish the number of supported subconcepts by priotizing the most important ones. 

And then for each concept in simplified_concepts_to_implement.md create me a clarification markdown file
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

"""


## Module-Level Documentation

Since we are building the our project in a decoupled way., We are gonna have multiple submodules. 
And these modules should be able to integrate with each other.  

Requirement change of one module will surely have some effect on interface and maybe deeper level on another submodule. 
This is why we are gonna keep up-to-date documentation for each. 
You might think code is the documentation and this is an overkill, however code itself does not exlain "why"  and during integration development of multiple modules why matters as much as code itself. Multi module Development is a parallel process where each change in either module might propagate backwards and forward and might break the requirement. 



## The Human-in-the-Loop Moment

This is a step where you get to be human in the loop and actually do some real work. It is vital for the rest of the development that you edit these simplified concept files. Make sure you read them and clarify anything which doesn't make sense.

Review and adjust:
- Is simplification too aggressive?
- Will this create technical debt?
- Does it still solve core problem?
- Can we build on this foundation?

## Using DevDocs with AI

### Starting a Session
```
"Please read all files in src/devdocs/ to understand the project context.
Pay special attention to philosophy.md for our core principles."
```

### Working on a Module
```
"I need to work on authentication. Please read:
1. src/devdocs/modules/auth/*.md for module context
2. src/devdocs/simplified_concepts.md for current scope"
```

### Preventing Drift
```
"This suggestion seems complex. Let's check if it aligns with 
our philosophy.md and the limitations.md for this module."
```

## The Living Documentation Principle

DevDocs aren't static:
- Update decisions.md after architectural choices
- Add to explorations.md when trying new approaches
- Expand module docs as understanding deepens
- Mark completed concepts in concepts.md

## Benefits of DevDocs Pattern

1. **AI Alignment**: Every session starts with shared context
2. **Decision History**: Why we built it this way
3. **Scope Control**: Clear boundaries prevent creep
4. **Module Clarity**: Each part knows its role
5. **Evolution Tracking**: See how project developed

## Common Pitfalls

### Over-Documentation
Don't document every function. Document concepts, boundaries, and decisions.

### Under-Documentation
"I'll remember why" - You won't. AI definitely won't.

### Stale Documentation
Update as you build. Outdated docs are worse than no docs.

### Skipping Module Docs
Each module needs its own context. Don't assume it's obvious.

## Quick Start Checklist

- [ ] Create src/devdocs/ structure
- [ ] Write three foundation documents
- [ ] Add decisions.md, explorations.md, notes.md
- [ ] Extract concepts from requirements
- [ ] Create detailed clarifications
- [ ] Simplify for prototype
- [ ] Create module folders as you build
- [ ] Document each module's purpose and boundaries

DevDocs pattern transforms AI from code generator to thoughtful collaborator who understands not just what to build, but why and how it fits together.













