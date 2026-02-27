# 🐍 Python `None` Type -- Complete Tutorial

------------------------------------------------------------------------

## 1. Introduction

In Python, `None` is a special constant that represents the **absence of
a value** or a **null value**.

-   It is **not 0**
-   It is **not an empty string**
-   It is **not False**
-   It is its own data type: `NoneType`

``` python
x = None
print(x)
print(type(x))
```

Output:

    None
    <class 'NoneType'>

There is only **one** `None` object in a Python program.

------------------------------------------------------------------------

## 2. Memory Model

### 🔹 Is `None` a Singleton?

Yes. `None` is a **singleton object**.

This means: - Only one instance of `None` exists in memory. - Every
variable assigned to `None` points to the same object.

``` python
a = None
b = None

print(a is b)  # True
```

### 🔹 Identity vs Equality

Always use `is` to compare with `None`.

``` python
x = None

print(x is None)   # ✅ Recommended
print(x == None)   # ⚠️ Not recommended
```

Why? - `is` checks identity (same object in memory) - `==` checks value
equality

Since `None` is a singleton, identity comparison is correct and faster.

------------------------------------------------------------------------

## 3. Internal Architecture / Working

### 🔹 CPython Implementation

Internally in CPython:

-   `None` is implemented as a global object called `Py_None`
-   Its type is `NoneType`
-   Defined in C source as:

``` c
PyObject *Py_None;
```

Python ensures: - It cannot be instantiated manually - You cannot
subclass `NoneType` - It is immutable

### 🔹 NoneType Characteristics

``` python
print(type(None))              # <class 'NoneType'>
print(isinstance(None, type(None)))  # True
```

You cannot do this:

``` python
None = 10  # ❌ SyntaxError
```

You also cannot create another None:

``` python
new_none = type(None)()  # ❌ TypeError
```

------------------------------------------------------------------------

## 4. Use Cases

### 4.1 Default Function Return

If a function does not return anything explicitly, it returns `None`.

``` python
def greet():
    print("Hello")

result = greet()
print(result)  # None
```

------------------------------------------------------------------------

### 4.2 Default Parameter Values

``` python
def process(data=None):
    if data is None:
        data = []
    return data
```

Why? - Avoids mutable default argument problems.

------------------------------------------------------------------------

### 4.3 Placeholder Value

``` python
user = None

if user is None:
    print("User not assigned yet")
```

------------------------------------------------------------------------

### 4.4 Represent Missing Data

``` python
data = {
    "name": "Pankaj",
    "middle_name": None
}
```

------------------------------------------------------------------------

### 4.5 Sentinel Value

Used to detect whether argument was passed:

``` python
_sentinel = object()

def func(value=_sentinel):
    if value is _sentinel:
        print("No value provided")
```

------------------------------------------------------------------------

## 5. Pros and Cons

### ✅ Pros

-   Clear representation of "no value"
-   Singleton → memory efficient
-   Prevents accidental object creation
-   Improves API clarity

### ❌ Cons

-   Can cause `NoneType` errors if unchecked
-   Confused with False/0/"" by beginners
-   Improper comparisons (`==`) may cause logical bugs

Example of common error:

``` python
x = None
print(x.upper())  # AttributeError
```

------------------------------------------------------------------------

## 6. Best Practices

### ✔ Always Use `is None`

``` python
if value is None:
    ...
```

------------------------------------------------------------------------

### ✔ Avoid Mutable Defaults

Wrong:

``` python
def func(items=[]):  # ❌
    pass
```

Correct:

``` python
def func(items=None):  # ✅
    if items is None:
        items = []
```

------------------------------------------------------------------------

### ✔ Use Type Hints

``` python
from typing import Optional

def find_user(user_id: int) -> Optional[str]:
    return None
```

------------------------------------------------------------------------

### ✔ Guard Against None

``` python
if value is not None:
    print(value.upper())
```

------------------------------------------------------------------------

## 7. Interview Tips

### 🔥 Common Questions

1.  Is `None` same as `0`? → No.

2.  Is `None` same as False? → No, but `bool(None)` is False.

``` python
print(bool(None))  # False
```

3.  Why use `is` instead of `==`? → Because `None` is a singleton.

4.  What is the type of None? → `NoneType`

5.  What does a function return if no return statement? → `None`

------------------------------------------------------------------------

### 💡 Senior-Level Insight

-   `None` is part of Python's object model.
-   It behaves similarly to `null` in other languages but is a proper
    object.
-   Proper handling of `None` prevents production-level bugs.

------------------------------------------------------------------------

# 🎯 Summary

`None` is:

-   A singleton object
-   Instance of `NoneType`
-   Used to represent absence of value
-   Returned implicitly by functions
-   Best compared using `is`

Mastering `None` helps you write cleaner, safer, and more Pythonic code.
