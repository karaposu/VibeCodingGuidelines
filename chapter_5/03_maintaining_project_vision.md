# Maintaining Project Vision

## Vision vs Features

Every project starts with vision. Features are just the implementation. But features tend to overshadow vision over time.

Vision: "Help people track daily habits"
Features creep: Social sharing, gamification, AI coaching, premium subscriptions...
Result: Another bloated app nobody uses

## The Vision Document

### Create PROJECT_VISION.md

```markdown
# Project Vision

## What We're Building
Simple habit tracker for personal use

## Why We're Building It  
Existing apps are too complex and distracting

## Core Principles
1. One screen to see all habits
2. No social features
3. No gamification
4. Works offline
5. Data stays local

## What Success Looks Like
User opens app, marks habits, closes app. 10 seconds total.

## What We're NOT Building
- Social network
- Analytics platform  
- Productivity suite
- AI assistant
```

This becomes your constitution.

## Vision Drift Patterns

### The Expert Trap
```
Week 1: "Simple habit tracker"
Week 2: "Add habit categories"
Week 3: "Add habit analytics"
Week 4: "Add habit recommendations"
Week 5: Complex productivity suite
```

Each addition seems logical. Together they kill the vision.

### The Technology Trap
```
Vision: "Simple and fast"
Reality: React + Redux + GraphQL + Microservices + Kubernetes
```

Tech excitement overrides user needs.

### The Competitor Trap
```
"App X has this feature..."
"Users might expect..."
"We should probably add..."
```

Copying others loses your unique vision.

## Protecting Vision During Development

### 1. The Vision Check Ritual

Before each session:
```
"Let's revisit our vision: [paste vision]
Today's work should support this."
```

After each feature:
```
"Does this align with our vision of simplicity?"
```

### 2. The User Story Filter

Every feature must trace to original vision:
```
Feature: "Add social sharing"
Question: "How does this help 'track daily habits simply'?"
Answer: "It doesn't"
Decision: "Reject"
```

### 3. The Complexity Tax

Each deviation from vision has cost:
- More code to maintain
- More bugs to fix
- More docs to write
- More cognitive load
- Less focus on core

### 4. The "No" List

Document what you're NOT doing:
```markdown
# NOT Doing
- User accounts (local only)
- Social features (personal tool)
- Notifications (reduces addiction)
- Analytics (privacy first)
- Integrations (standalone)
```

Reference when AI suggests these.

## Vision Communication with AI

### Setting Context
```
"We're building a habit tracker with these constraints:
- Local only
- No accounts
- Maximum simplicity
Please keep suggestions within these bounds."
```

### Redirecting Suggestions
```
AI: "We could add achievement badges"
You: "That violates our 'no gamification' principle"
AI: "Understood, keeping it simple"
```

### Vision-First Prompting
```
"Given our vision of [X], how should we implement [Y]?"
```

Not just "implement Y".

## The Evolution vs Revolution Problem

### Evolution (Good)
Vision remains, implementation improves:
```
V1: Text list of habits
V2: Visual checkboxes
V3: Better mobile layout
Core vision: ✓ Still simple tracker
```

### Revolution (Bad)
Vision replaced by feature creep:
```
V1: Simple tracker
V2: Add social
V3: Add marketplace
Core vision: ✗ Now social platform
```

## Stakeholder Pressure

### Internal Pressure
Your own "wouldn't it be cool if..."

Defense: Write it down, wait a week. Still excited? Maybe. Probably not.

### External Pressure  
"Users are asking for..."

Defense: Do they want THIS app to do that, or do they want ANY app to do that?

### AI Pressure
"Best practices suggest..."

Defense: Best for whom? Your vision is unique.

## The Vision Keeper Role

In team settings, designate a Vision Keeper:
- Reviews all major decisions
- Has veto power on vision violations  
- Updates vision doc as needed
- Protects simplicity

With AI, YOU are the Vision Keeper.

## Signs Vision is Maintained

✓ New users understand app in seconds
✓ Features feel cohesive
✓ Codebase remains manageable
✓ Original users still happy
✓ You can explain app in one sentence

## Signs Vision is Lost

✗ Need tutorial for basic use
✗ Features feel bolted on
✗ Codebase becoming unwieldy
✗ Original users leaving
✗ Elevator pitch takes whole elevator ride

## The Refocus Strategy

When vision gets fuzzy:

1. **Return to Origin**
   "Why did we start this?"

2. **Survey Damage**
   "What have we added that doesn't serve vision?"

3. **Plan Removal**
   "What can we cut?"

4. **Recommit**
   Update vision doc, share with AI

## The Success Paradox

Success brings feature requests. Features kill what made you successful.

```
Simple app → Users love it → Request features → Complex app → Users leave
```

Vision protection breaks this cycle.

## Quick Vision Test

Before any major decision:
1. Does this serve our core users?
2. Does this align with our principles?
3. Would we build this if starting today?
4. What would we lose by saying no?

If unclear, default to no.

## The Long Game

Projects with maintained vision:
- Stay maintainable
- Keep users happy
- Remain enjoyable to work on
- Actually get finished

Projects that lose vision:
- Become maintenance nightmares
- Lose user focus
- Burn out developers
- Often abandoned

Your vision is your project's soul. Protect it.

Next: Part III - Vibe Coding Patterns →