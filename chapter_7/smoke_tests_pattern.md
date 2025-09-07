# Smoke Tests Pattern

Smoke tests Pattern provides  
     - Validation that AI understands your intent and you understand AI's intent. 
     - Shows AI indeed did what think it wanted to do
     - Early warning system and prevent propagations of misunderstandings

## What Are Smoke Tests?

The name comes from if the code 'catches fire' when run.  Traditionally used for
 - discovering/understanding how particular module/API works 
 - early prototyping where TDD (Test-Driven Development) is overkill

So basically they let you quickly confirm that core functionality works under minimal conditions without the overhead of formal testing frameworks.

## Smoke Tests in Vibe Coding

In vibe coding they verbosity is essential. Unlike traditional TDD focused on CI/CD automation, vibe coding emphasizes comprehensive logging and data visibility. Smoke tests serve not just to verify pass/fail status, but to expose actual data flow, data transformations and intermediate states and values, allowing AI& developers to understand exactly what's happening during execution. 

And you will see that AI-generated tests often default to minimal output or use mocks that obscure real behavior. Which if not checked might have result in Phantom success.  


We ask AI to create smoke tests which covers 

  - Unit tests - Test individual functions/methods in isolation
  - Integration tests - Test how components work together
  - End-to-end (E2E) tests - Test complete user workflows
  - Acceptance tests - Verify business requirements are met
  - Performance/Load tests - Test speed and scalability





Rules regarding smoke tests:


- The smoke tests shold start from isolated method checks and evolve into testing concepts while each file Each file testing deeper understanding ( test_login_returns_token >>>> ... >>>> test_basic_auth_flow_works )
- Smoke tests should read like documentation so we can intervene 
- Smoke tests are a lot cheaper than wrong implementation, so create them as much as needed. 
- AI  works well with Smoke Test loop   Run test> Fix failures >Run again > Run next Test
- Name the Tests Clearly and Readble. 
- Tests act as comprehensive summary of your project/module. 

 



## Why Smoke Tests Matter for AI

AI can generate perfectly valid code that solves the wrong problem. Smoke tests reveal this immediately.

Example:
```
Human: "Create user authentication"
AI: *builds biometric authentication system*
Smoke test file shows eye scanner codes
Human: "Wait, I meant just email/password"

```


The smoke tests shold start from isolated method checks and evolve into testing concepts while each file Each file testing deeper understanding ( test_login_returns_token >>>> ... >>>> test_basic_auth_flow_works )


Smoke tests should read like documentation so we can intervene 

Smoke tests are a lot cheaper than wrong implementation, so create them as much as needed. 

AI  works well with Smoke Test loop   Run test> Fix failures >Run again > Run next Test

Name the Tests Clearly and Readble. 

Tests as comprehensive summary  


Design 5 test files before implementing anything


## The Smoke Test Philosophy

### Test Understanding, Not Implementation

Traditional tests verify correctness.
Smoke tests verify comprehension.

```python
# Traditional test
def test_login_returns_token():
    assert login(user, pass).startswith("jwt")

# Smoke test  
def test_basic_auth_flow_works():
    """Can a user sign up, log in, and access protected resource?"""
    # Tests the entire concept, not details
```

### Verbose Over Clever

Smoke tests should read like documentation:

```python
def test_expense_entry_complete_flow():
    """
    Test that a user can:
    1. Open the expense entry form
    2. Enter an amount
    3. Select a category
    4. Save the expense
    5. See it in their expense list
    
    This is the core user journey that must work.
    """
```

AI uses these descriptions to understand intent.

## Designing Smoke Tests

### The 5-File Pattern

Design 5 test files before implementing anything:

```
smoke_tests/
├── test_01_initialization.py
├── test_02_core_functionality.py  
├── test_03_user_workflows.py
├── test_04_edge_cases.py
└── test_05_integration.py
```

### Progressive Complexity

Each file tests deeper understanding. 
It is common to have first file as 

test_01_initialization.py
- Can we import the modules?
- Do classes instantiate?
- Are constants defined?

and second file as: 

test_02_connectivity.py
  - Can we connect to the database?
  - Do API endpoints respond?
  - Are external services reachable?
  - Do authentication mechanisms work?
  - Can we read/write to external resources?

but each app is different and have different requirements. So we can have as many smoke tests we want. 



## Implementing with Smoke Tests

### The Loop

1. AI Designs smoke tests based on codebase
3. AI implements smoke tests
4. Run tests
5. Fix failures 
6. Repeat

### Catching Misunderstandings Early

When test fails:
```
FAILED: test_no_user_accounts_needed
AI added user registration flow
```

Immediate correction:
```
"Our philosophy is no user accounts.
Please remove registration and make it work locally only."
```



## Smoke Test Best Practices

### Name Tests Clearly and Readble

```python
# Bad
def test_1():
    pass

# Good  
def test_expense_entry_requires_only_amount_and_category():
    pass
```


## Smoke Tests Evolution

### Prototype Phase
- Basic functionality
- Happy paths only
- Minimal edge cases

### MVP Phase  
- Add integration tests
- Include error scenarios
- Test performance basics

### Production Phase
- Comprehensive coverage
- Security tests
- Load testing

Smoke tests are your contract with AI. Make them clear, make them run, make them matter.

Next: Fuzzy Architecture Pattern →



### Tests as comprehensive summary  
