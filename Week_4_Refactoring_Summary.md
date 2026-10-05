# Week 4 Refactoring Summary

## Objective

Improve the readability, maintainability and efficiency of the Week 2 Library Book Inventory System.

## Major Refactoring

### 1. Single Responsibility

`InputValidator` now handles reusable input validation and ISBN normalization.

### 2. DRY

Repeated validation and ISBN normalization are centralized rather than copied into multiple CRUD methods.

### 3. Data Structure Optimization

The old ArrayList-based ISBN search required scanning records one by one.

The refactored implementation uses:

```java
Map<String, Book> booksByIsbn
```

Average ISBN lookup changes from O(n) to O(1).

### 4. Encapsulation

The manager does not expose its internal collection directly. `getAllBooks()` returns a snapshot wrapped as an unmodifiable list.

### 5. Regression Testing

JUnit 5 tests verify CRUD operations, validation, duplicate ISBN handling, case-insensitive ISBN lookup, update behavior, delete behavior and read-only collection behavior.

## Before and After

Before:

```java
for (Book book : books) {
    if (book.getIsbn().equalsIgnoreCase(isbn)) {
        return book;
    }
}
return null;
```

After:

```java
return booksByIsbn.get(normalizeIsbn(isbn));
```

The second implementation is shorter, easier to understand and has better average lookup performance.
