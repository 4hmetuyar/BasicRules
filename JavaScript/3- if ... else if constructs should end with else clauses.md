# "if ... else if" constructs should end with "else" clauses


- This rule applies whenever an if statement is followed by one or more else if statements; the final else if should be followed by an else statement.

- The requirement for a final else statement is defensive programming.

- The else statement should either take appropriate action or contain a suitable comment as to why no action is taken. This is consistent with the requirement to have a final default clause in a switch statement.

### Noncompliant Code Example (Uygunsuz Kod Örneği) :

```javascript
if (x == 0) {
  doSomething();
} else if (x == 1) {
  doSomethingElse();
}
```

### Compliant Solution (Uygun Kod Örneği) :

```javascript
if (x == 0) {
  doSomething();
} else if (x == 1) {
  doSomethingElse();
} else {
  throw "Unexpected value for x";
}
```

