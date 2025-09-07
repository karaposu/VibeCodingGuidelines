# Smoke Tests Pattern


AI can generate perfectly valid code that solves the wrong problem. Smoke tests reveal this immediately.

## What Are Smoke Tests?

The name comes from if the code 'catches fire' when run.  Traditionally used for
 - discovering/understanding how particular module/API works 
 - early prototyping where TDD (Test-Driven Development) is overkill

So basically they let you quickly confirm that core functionality works under minimal conditions without the overhead of formal testing frameworks.

## Smoke Tests in Vibe Coding

Smoke tests Pattern provides  
    - Validation that AI understands your intent and you understand AI's intent. 
    - Shows AI indeed did what think it wanted to do
    - Early warning system and prevent propagations of misunderstandings
    - comprehensive summary of your project/module


Smoke tests serve not just to verify pass/fail status, but to expose actual data flow, data transformations and intermediate states and values, allowing AI& developers to understand exactly what's happening during execution. 


## How to Implement Smoke Tests pattern correctly


### 0. Verbose Over Clever

Make smoke tests verbose and show the data flow as well as key transformations (with raw samples and summaries).  Smoke tests are for both human dev and AI.  

### 1. Comprehensivity 

It is important for smoke tests to cover differnet scenarios. In traditional software development this is done by using different types of tests:

  - Unit tests - Test individual functions/methods in isolation
  - Integration tests - Test how components work together
  - End-to-end (E2E) tests - Test complete user workflows
  - Acceptance tests - Verify business requirements are met
  - Performance/Load tests - Test speed and scalability


And in vibe coding we adapt these tests into our Smoke Tests pattern. 



### 2. Progressive Complexity

The smoke tests shold start from isolated method checks and evolve into testing concepts while each file Each file testing deeper understanding 

test_login_returns_token >>>> ... >>>> test_basic_auth_flow_works 

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



### 3. Clear Intent 

Smoke tests should read like documentation so we can intervene. Also Naming the Tests Clearly and Readble is important 


### 4. Full implementation Coverage 


Smoke tests are a lot cheaper than wrong implementation, so create them as much as needed.

One basic rule is to ask AI to design 5 smoke test files with each file testing seperate logic. Each file having at least 5 individual tests. 

```
smoke_tests/
├── test_01_initialization.py
├── test_02_core_functionality.py  
├── test_03_user_workflows.py
├── test_04_edge_cases.py
└── test_05_integration.py
``` 

### 5. No mocking and Providing Real Data 

And you will see that AI-generated tests often default to minimal output or use mocks that obscure real behavior. Which if not checked might have result in Phantom success.  

It is your job to provide realistic data for smoke tests. If you are developing video engine or human voice detector
unless you provide a real data example, AI wont be able to mock these complex data and create phantom success via mock data. 

### 6. Always Rerun your smoke tests by yourself. 
 
Common pitfall is to trust AI's execution and interpretation of a smoke test. Sometimes AI can claim success when most tests pass and some fail. And this is not okay. 

Also reading smoke test output is a really quick way to have an idea about how AI implemented the features in terms of input output manupulations. 





