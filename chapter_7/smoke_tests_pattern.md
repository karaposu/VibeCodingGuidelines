# Smoke Tests Pattern

## What Are Smoke Tests?

In traditional development:
Quick tests to see if software "catches fire." They are mostly used to understand this should work but I should run it in minimal condition to see it really does or not. Traditional software test driven approach but when your app is releatively new and you are still trying to figure out certain things it would be unpractical to start writing code in official Test driven way.  Smoke tests are really useful filling this gap and you can just run the code and read the prints to see what is working and what is not. 


In vibe coding:  

Vibe coding is paradigm where verbosity matters. Usual test driven methods are about CI/CD but with vibe coding we want to see the logs want them verbose as much as possible. The point of smoke tests is notjust to know if code passes or not but read some real data in the output and confirm things are actually working. 

It is so easy for AI to start writing non verbose tests and when you read the output you wont see any data exposed and you have no idea how output data looks or if AI decided to use mocks and etc. So in vibe coding we explicitly request from AI to write these tests in a way that human can read and see the data flow and interpret as well.  



Smoke tests are 
     - Validation that AI understands your intent and you understand AI's intent. 
     - Shows AI indeed did what think it wanted to do
     - early warning system and prevent propagations of misunderstandings



## Why Smoke Tests Matter for AI

AI can generate perfectly valid code that solves the wrong problem. Smoke tests reveal this immediately.

Example:
```
Human: "Create user authentication"
AI: *builds biometric authentication system*
Smoke test file shows eye scanner codes
Human: "Wait, I meant just email/password"

```

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

Each file tests deeper understanding:

**test_01_initialization.py**
```python
"""
Basic sanity checks:
- Can we import the modules?
- Do classes instantiate?
- Are constants defined?
"""

def test_app_starts():
    """Application initializes without errors"""
    app = Application()
    assert app is not None

def test_database_connects():
    """Database connection works"""
    db = Database()
    assert db.is_connected()
```

**test_02_core_functionality.py**
```python
"""
Core features work in isolation:
- Can we create records?
- Can we read them back?
- Do calculations work?
"""

def test_create_expense():
    """Can create a basic expense"""
    expense = Expense(amount=50.0, category="food")
    assert expense.save()
    
def test_calculate_monthly_total():
    """Monthly totals calculate correctly"""
    # Not testing edge cases, just basic math
```

**test_03_user_workflows.py**
```python
"""
Complete user journeys:
- Real-world usage patterns
- Multi-step processes
- Expected user behavior
"""

def test_daily_expense_workflow():
    """User logs multiple expenses throughout the day"""
    user = User()
    
    # Morning coffee
    user.add_expense(5.50, "food", "Coffee")
    
    # Lunch
    user.add_expense(12.00, "food", "Lunch")
    
    # Transport
    user.add_expense(2.50, "transport", "Bus")
    
    assert user.get_today_total() == 20.00
```

## The Design-First Approach

### Write Tests Before Code

Share test design with AI:
```
"Here's my smoke test design: [paste tests]
These tests define what we're building.
Please implement code that makes these pass."
```

AI now understands:
- What you're building
- How it should work
- What matters most

### Tests as Specification

Your smoke tests become executable specifications:

```python
def test_privacy_requirement():
    """
    CRITICAL: All data must stay local.
    No network calls should ever be made.
    """
    with network_monitor() as monitor:
        app = Application()
        user = User()
        user.add_expense(100, "food")
        
    assert monitor.call_count == 0, "App made network calls!"
```

This test ensures AI doesn't add cloud features.

## Implementing with Smoke Tests

### The Loop

1. Design smoke tests
2. Share with AI
3. AI implements
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

### Name Tests Clearly

```python
# Bad
def test_1():
    pass

# Good  
def test_expense_entry_requires_only_amount_and_category():
    pass
```

### Document Intent

```python
def test_offline_first():
    """
    The app must work completely offline.
    This test ensures no features require internet.
    
    Why: Users should own their data and not depend on servers.
    """
```

### Test Concepts Not Code

```python
# Don't test implementation details
def test_uses_sqlite():  # Bad
    assert db.engine == "sqlite"

# Test the concept
def test_data_persists_between_sessions():  # Good
    app1 = Application()
    app1.add_expense(100)
    app1.close()
    
    app2 = Application()  
    assert app2.get_expenses()[0].amount == 100
```

### Keep Tests Readable

```python
def test_monthly_summary_shows_spending_by_category():
    # Arrange: Create diverse expenses
    create_expense(100, "food", "2024-01-05")
    create_expense(200, "food", "2024-01-15")
    create_expense(150, "transport", "2024-01-10")
    create_expense(300, "entertainment", "2024-01-20")
    
    # Act: Get summary
    summary = get_monthly_summary("2024-01")
    
    # Assert: Categories are grouped correctly
    assert summary["food"] == 300
    assert summary["transport"] == 150
    assert summary["entertainment"] == 300
    assert summary["total"] == 750
```

## Advanced Patterns

### The Sentinel Test

Add tests that guard against common AI mistakes:

```python
def test_no_external_dependencies():
    """SENTINEL: Prevent unnecessary dependencies"""
    with open("requirements.txt") as f:
        deps = f.read()
    
    blocked = ["requests", "boto3", "firebase"]
    for dep in blocked:
        assert dep not in deps, f"Unwanted dependency: {dep}"
```

### The Philosophy Test

Ensure code aligns with project philosophy:

```python
def test_philosophy_no_gamification():
    """Ensure no gamification features creep in"""
    codebase = scan_all_files()
    
    banned_terms = ["achievement", "badge", "streak", "points"]
    for term in banned_terms:
        assert term not in codebase.lower()
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

## The Meta-Test

Always include:

```python
def test_all_smoke_tests_have_descriptions():
    """Every test should explain what it's testing and why"""
    for test in get_all_tests():
        assert test.__doc__, f"{test.__name__} needs description"
```

## Quick Tips

1. **Write tests first** - Define before implement
2. **Test journeys** - Not individual functions
3. **Document why** - Intent matters more than how
4. **Keep simple** - Smoke tests aren't comprehensive
5. **Run often** - Catch drift early

Smoke tests are your contract with AI. Make them clear, make them run, make them matter.

Next: Fuzzy Architecture Pattern →