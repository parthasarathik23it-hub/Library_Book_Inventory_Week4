# Library Book Inventory System - Week 4

## Code Refactoring and Optimization

This project is the refactored version of the Week 2/Week 3 Java Library Book Inventory System.

### Main improvements

- Applied DRY principle.
- Separated validation into `InputValidator`.
- Used `BookManager` as the single class responsible for inventory operations.
- Replaced repeated linear ISBN searches with a `LinkedHashMap`.
- ISBN lookup is O(1) on average.
- Preserved insertion order for predictable display.
- Added defensive/read-only access to inventory data.
- Improved exception messages.
- Added JUnit 5 regression tests.
- Added comments explaining important refactoring decisions.

## Project structure

```text
src/
├── main/java/com/partha/library/
│   ├── Main.java
│   ├── model/Book.java
│   ├── service/BookManager.java
│   └── util/InputValidator.java
└── test/java/com/partha/library/service/
    └── BookManagerTest.java
```

## Run tests

```bash
mvn test
```

## Compile

```bash
mvn clean compile
```

## Run

From an IDE, run:

```text
com.partha.library.Main
```

## Complexity improvement

Previous design:
- ISBN search with ArrayList: O(n)
- Duplicate check: O(n)
- Delete by ISBN: O(n)

Refactored design:
- ISBN lookup with Map: O(1) average
- Duplicate check: O(1) average
- Delete by ISBN: O(1) average

The map uses ISBN as the unique business key while `LinkedHashMap` keeps insertion order.
