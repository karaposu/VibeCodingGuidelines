# Managing AI Drift

## What Is AI Drift?

AI drift happens when AI gradually moves away from your original intent. Like a boat without anchor, small currents compound into major course changes. 

## Types of Drift

### 1. Complexity Drift
Starts simple, becomes enterprise.

```
Request 1: "Add user login"
AI: Simple email/password

Request 2: "Add password reset"
AI: Adds email service, queues, tokens

Request 3: "Add remember me"
AI: Adds Redis, session management, device tracking

Request 4: "Add social login"
AI: OAuth, SAML, OpenID, full identity provider
```

Suddenly you're building Auth0.

### 2. Style Drift
Inconsistent patterns across codebase.

```python
# Monday - functional style
def process_user(user_data):
    return transform(validate(user_data))

# Tuesday - OOP style
class UserProcessor:
    def process(self, user_data):
        self.validate()
        self.transform()

# Wednesday - procedural style
user_data = get_user()
validate_user(user_data)
transform_user(user_data)
```

### 3. Architecture Drift
Original design morphs unrecognizably.

```
Start: "Simple REST API"
Drift 1: Add GraphQL "for flexibility"
Drift 2: Add WebSockets "for real-time"
Drift 3: Add gRPC "for performance"
End: Four different API protocols
```

### 4. Scope Drift
Features multiply beyond intent.

```
Original: "Todo app"
+ "Add categories" 
+ "Add sharing"
+ "Add comments"
+ "Add notifications"
= Project management suite
```

### 5. Technology Drift
Stack grows unnecessarily.

```
Start: React + Node
+ Redux "for state"
+ MongoDB "for flexibility"  
+ Docker "for deployment"
+ Kubernetes "for scaling"
+ Kafka "for events"
= Overengineered todo app
```

## Why Drift Happens

Can be due to numerous reasons

### 1. AI Lacks Project Context
Each request seems isolated. AI doesn't see the big picture. Most common reason is due to bad context management. 

### 2. AI Optimizes Locally
Makes each piece "better" without considering whole.

### 3. Pattern Matching Gone Wild
AI applies patterns even when inappropriate.

### 4. No Persistent Memory
Can't remember "we decided to keep it simple."

## Drift Detection

### Early Warning Signs
- Imports growing rapidly
- New directories appearing
- Inconsistent naming
- Multiple ways to do same thing
- "Just one more feature"

### The Complexity Budget
Track complexity like technical debt:
```
Start: Complexity budget = 10
Add OAuth: -3 
Add Redis: -2
Add queue: -2
Remaining: 3
```

When budget hits 0, stop adding.

## Drift Prevention

### 1. The North Star Document
Create `VISION.md`:
```markdown
# Project Vision

This is a SIMPLE todo app for personal use.

NOT:
- Multi-user
- Enterprise
- Real-time
- Distributed

Core principle: If it takes > 1 hour to implement, we don't need it.
```

Reference constantly.

### 2. Explicit Constraints
Start requests with constraints:
```
"Add password reset. Keep it simple - no external services, 
no queues, just database tokens."
```

### 3. The Anchor Pattern
Regular reality checks:
```
"Before we continue, let's review:
- We're building X
- Current stack is Y
- We're avoiding Z
Still aligned?"
```

### 4. Incremental Boundaries
Set limits before each phase:
```
"For this session:
- No new dependencies
- No new patterns
- Just implement the feature"
```

### 5. The Simplicity Refactor
Periodically ask:
```
"This is getting complex. How can we simplify while keeping functionality?"
```

## Drift Recovery

### When You've Already Drifted

1. **Acknowledge the drift**
```
"We've drifted from simple to complex. 
Let's identify what we can remove."
```

2. **Document current state**
```
"List all technologies and patterns we're now using"
```

3. **Identify core requirements**
```
"What are the actual must-haves vs nice-to-haves?"
```

4. **Plan simplification**
```
"How can we meet core requirements with minimal stack?"
```

5. **Incremental rollback**
Don't rewrite. Gradually simplify.

## The Drift Dialogue

### Catching Early Drift
```
AI: "We should add caching for performance"
You: "Is performance actually a problem?"
AI: "Not yet, but..."
You: "Let's wait until it is"
```

### Redirecting Architecture Drift
```
AI: "This would be cleaner with microservices"
You: "We're keeping monolith for simplicity"
AI: "Understood, here's monolith version"
```

### Preventing Scope Drift
```
AI: "While we're at it, should we add..."
You: "No, let's finish current feature first"
```

## Positive Drift

Not all drift is bad. Sometimes AI suggests genuinely better approaches.

### Evaluating Positive Drift
Ask:
1. Does this simplify or complicate?
2. Does this align with project goals?
3. Is this solving real or imagined problems?
4. What's the maintenance cost?

### Accepting Good Ideas
```
AI: "Instead of custom auth, use NextAuth"
You: "That actually simplifies things. Let's do it."
```

## The Meta-Strategy

Best drift management is prevention:
- Clear vision from start
- Explicit constraints
- Regular reality checks
- Simplicity as core value

Remember: AI will always suggest more. Your job is knowing when to say no.

