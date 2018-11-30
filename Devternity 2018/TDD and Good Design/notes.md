# Does TDD really lead to good design?
>Sandro Mancuso

TDD could be seen as a set of workflows

Classicist and Outside In

### Classicist
Red Green Refactor

Design stage happened at the refactor stage. You already have a green test, but it is possibly a messy design. What does 'make it better' then mean at the refactor stage

As classes grow, we start to extract code out to other classes to support more complex functionality

### Outside in
Can start with a black box acceptance test, but often we want to ensure the correct thing happens further down

Use of mocks allows for a high level design of defining behaviour

Then you can test and implement the previously mocked functionality and so on, working into the system/domain

This can sometimes lead to a class with far to many mocked dependencies, driven as a result of a TDD designed system. So need to make sure you spend time refactoring these as well once the test is green

## Summary
Sometimes understanding of design patterns and the end goal are required, and without these, it's very unlikely TDD will guide you down the correct path. It should just be used as a tool to help with some finer details of an already established design