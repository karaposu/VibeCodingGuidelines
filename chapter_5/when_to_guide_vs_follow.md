# When to Guide vs When to Follow

## The Fundamental Question

Every AI interaction presents a choice: Do I lead or do I follow? Wrong choice = wasted time.

## When to Guide (You Lead)

### 1. Business Requirements
AI doesn't know your users, market, or constraints.

```
GUIDE: "Users need to export data for tax purposes in specific format"
NOT: "How should users export data?"
```

### 2. Architecture Decisions
AI suggests patterns. You choose based on reality.

```
GUIDE: "We're using microservices because we have separate teams"
NOT: "Should we use microservices?"
```

### 3. Performance Constraints
AI doesn't know your scale or bottlenecks.

```
GUIDE: "This needs to handle 10k requests/second"
NOT: "Make it fast"
```

### 4. Security Requirements
AI knows general security. You know your threat model.

```
GUIDE: "We need SOC2 compliance with audit logging"
NOT: "Make it secure"
```

### 5. Integration Points
AI doesn't know your existing systems.

```
GUIDE: "This must integrate with our legacy SOAP API"
NOT: "How should this communicate with other services?"
```

## When to Follow (AI Leads)

### 1. Implementation Details
Once direction is set, let AI handle specifics.

```
FOLLOW: "What's the best way to implement JWT refresh tokens?"
GUIDE: "Users need to stay logged in for 30 days"
```

### 2. Best Practices
AI knows current standards better than most developers.

```
FOLLOW: "How should I structure this React component?"
GUIDE: "It needs to display user profiles"
```

### 3. Error Handling
AI excels at comprehensive error cases.

```
FOLLOW: "What errors should this API endpoint handle?"
GUIDE: "It processes payment webhooks"
```

### 4. Refactoring Suggestions
AI sees patterns you might miss.

```
FOLLOW: "This code feels complex. Suggest improvements."
GUIDE: "It must remain backwards compatible"
```

### 5. Technology Selection
For well-understood problems, AI knows tool tradeoffs.

```
FOLLOW: "What caching solution for session data?"
GUIDE: "We're on AWS with Redis experience"
```

## The Grey Zone

Some decisions need negotiation:

### API Design
```
Human: "I need user management endpoints"
AI: "Here's a RESTful design..."
Human: "Actually, we prefer GraphQL"
AI: "Here's the GraphQL schema..."
```

Start by following, then guide corrections.

### Database Schema
```
AI: "Suggests normalized schema"
Human: "We optimize for reads, denormalize"
AI: "Here's denormalized version"
```

Let AI propose, you dispose.

### Testing Strategy
```
Human: "We need tests"
AI: "Unit, integration, and E2E tests..."
Human: "We only do integration tests"
AI: "Focused integration test suite..."
```

## Pattern Recognition

### Guide When:
- Domain-specific knowledge required
- Business logic involved
- External constraints exist
- Past decisions affect current
- User experience matters

### Follow When:
- Technical implementation unclear
- Multiple valid approaches exist
- Best practices needed
- Common patterns apply
- You're learning something new

## The Evolution Pattern

Projects typically flow:
1. **Early**: Heavy guiding (requirements, constraints)
2. **Middle**: Balanced (negotiating approaches)
3. **Late**: Heavy following (implementation details)

## Communication Strategies

### When Guiding
Be specific and constraining:
```
"Build auth with these requirements:
- Email/password only
- 2FA via SMS
- Session length 24 hours
- PostgreSQL storage"
```

### When Following  
Be open and exploratory:
```
"I need authentication. What approach would you recommend given modern security practices?"
```

### The Hybrid Approach
Most effective:
```
"I need auth for a B2B SaaS (context).
What's the current best practice (follow)?
Must integrate with Okta (guide)."
```

## Anti-Patterns

### Over-Guiding
```
"Create a function named X that takes Y parameters 
and implements using Z algorithm with..."
```
You're using AI as a typist.

### Over-Following
```
"Build me an app"
"What kind?"
"You decide"
```
You'll get generic solutions.

### Guide/Follow Confusion
```
"Implement auth however you think is best 
but it must work exactly like our old system"
```
Mixed signals create bad results.

## The Trust Ladder

As you work with AI more:
1. **Start**: Guide everything
2. **Learning**: Follow for exploration
3. **Comfort**: Balance naturally
4. **Mastery**: Intuitive switching

## Quick Decision Framework

Ask yourself:
1. Does this require domain knowledge? → Guide
2. Is this a solved problem? → Follow
3. Are there external constraints? → Guide
4. Am I learning? → Follow
5. Is there one right answer? → Guide

## The Meta Rule

When unsure whether to guide or follow:
```
"Given [context], should I specify [decision] 
or would you recommend an approach?"
```

Let AI help you decide when to lead.

Next: Managing AI Drift →