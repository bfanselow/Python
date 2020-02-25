### Test-Driven-Development (TDD) using Python's "pytest"

### What exactly is TDD?
## Myth: TDD means creating all the tests for your application's functionality before writing any code. This myth creates the misconception that TDD practitioners don’t bother with good design and architecture phases.
## Reality: TDD does not mean you create all tests before writing any code.  TDD is simply a sequence by which you write code when you’re ready to start writing code. It an iterative process throughout the entire (iterative) development process.  Good TDD habits imply that when you begin to write actual code for a new piece of functionality, you start with a test that fails and then write the functionality such that the test eventually passes. TDD can be summarized as breaking your code into tiny pieces of functionality and then carefully defining “done” before you start the next incremental piece. Write a test that fails; now write the code that makes the test pass; When it passes, you’ll be done with the current bit you’re working on.

## Example: create a "BankAccount" class to model the opening an account, with methods for depositing and withdrawing funds from that account.

## TDD steps:
1) create a project dir ./pytest_tdd to host a BankAccount class
2) Optional virtualenv:  cd pytest_tdd; virtualenv [-p python3.x] <ve_name>; source <ve_name>bin/activate; pip install -U pytest
3) Create a "tests" dir to host all pytest test files.
4) In the tests dir, create a test file: "test_bank_account.py" and write some simple functionality tests (which will fail).
5) run the tests: python3 -m pytest -v
   (If we want to run only certain tests we can specify test-names by regex:  python3 -m pytest -k <regex> -v)
6) Create the BankAccount.py class to pass the simple tests. 
7) Iterative repetition of steps 4-6: consider additional functionality; write more tests; add additional functionality to pass tests. 

/pytest_tdd
├── BankAccount.py
├── conftest.py
└── tests
    │  
    └── test_bank_account.py

## Optimizing for many tests
* conftest.py file: Primary use is for "@pytest.fixture" definitions. These allows us to defined commonly used variables, methods, etc. used throughout the tests - minimizing "boilerplate" code.
* parametrizing: @pytest.mark.parametrize() before a test functions allows us to run the test against multiple sets of inputs and an expected output.


## NOTES:
* It is tempting to write tests that fail as a way of ensuring that the functionality fails in an expected way. Do NOT write tests that purposely fail. ALL tests should pass!  If you need to ensure that a method handles failure conditions, write the test such that the failure condition is properly handled such that the test PASSES! For example, write a test that verifies that an exception gets raised on failure and then write the code that raises the exception.
* Do not make "test coverage" the goal of testing. If you make a certain level of coverage a target, people will try to attain it. The trouble is that high coverage numbers are too easy to reach with low quality testing. You're likely to get lots of tests looking for things that rarely go wrong and distracting you from testing the things that really matter.