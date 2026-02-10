# Recursion - Complete Interview Notes

## What is Recursion?

Recursion is a programming technique where a function calls itself to solve smaller instances of the same problem until a base case is reached.

### Key Components

- **Base Case** → stopping condition
- **Recursive Call** → function calls itself
- **Progress Toward Base Case** → input size must reduce

### Example:

```python
def factorial(n):
    if n == 0:
        return 1
    return n * factorial(n-1)
```

## Types of Recursion

1. **Direct Recursion** - Function calls itself directly.
   ```
   factorial(n) -> factorial(n-1)
   ```

2. **Indirect Recursion** - Function A calls B, and B calls A.

3. **Tail Recursion** - Recursive call is the last operation.

4. **Head Recursion** - Recursive call happens before processing.

5. **Tree / Binary Recursion** - Function makes multiple recursive calls (e.g., Fibonacci).

6. **Backtracking Recursion** - Explores all possible choices (subsets, permutations, N-Queens).

## Real World Applications / Use Cases

- File system traversal
- Tree and graph processing
- Parsing expressions / compilers
- Backtracking problems (Sudoku, N-Queens)
- Divide & Conquer algorithms (Merge Sort, Quick Sort)
- Dynamic Programming (memoized recursion)

## Pros and Cons of Recursion

### Pros

- Cleaner and readable code
- Natural fit for tree/graph problems
- Easier divide-and-conquer implementation

### Cons

- Higher memory usage (stack)
- Slower than iteration in some cases
- Risk of stack overflow

## Recursion vs Iteration

| Aspect | Recursion | Iteration |
|--------|-----------|----------|
| Readability | High | Moderate |
| Memory | Uses stack | Constant memory |
| Performance | Slightly slower | Faster |
| Use cases | Trees, backtracking | Loops, linear tasks |
## Head vs Tail Recursion (Storage / Memory)

| Aspect | Head Recursion | Tail Recursion |
|--------|---|---|
| Work position | After recursive call | Before recursive call |
| Stack usage | O(n) | O(1) with Tail Call Optimization |
| Python optimization | No TCO | No TCO |
| Convert to iteration | Harder | Easier |
## How to Calculate Time and Space Complexity

### Time Complexity

Count number of recursive calls using recursion tree.

**Examples:**
- Single recursion → O(n)
- Fibonacci → O(2^n)
- Merge sort → O(n log n)

### Space Complexity

Count maximum recursion depth (stack height).

**Examples:**
- Linear recursion depth n → O(n)
- Binary recursion depth log n → O(log n)

## Mental Model to Solve Recursion Problems

### Linear Recursion (Single Call)

1. Define function meaning
2. Write base case
3. Assume smaller problem solved
4. Combine result
5. Ensure size reduces

**Template:**

```python
def solve(n):
    if base_case:
        return answer
    smaller = solve(n-1)
    return combine(smaller)
```

### Binary / Multiple Recursion (Backtracking)

1. Identify choices
2. Try a choice
3. Explore recursively
4. Undo choice

## General Recursion Template

```python
def recursion(problem):
    if base_case:
        return result

    smaller_result = recursion(smaller_problem)

    return combine(smaller_result)
```

## Backtracking Template

```python
def backtrack(path, choices):
    if goal_reached:
        result.append(path.copy())
        return

    for choice in choices:
        path.append(choice)        # choose
        backtrack(path, new_choices)  # explore
        path.pop()                 # undo
```

## Common Interview Questions (Google / Amazon)

### Basic Recursion

- Factorial
- Fibonacci
- Reverse string / array
- Sum of array

### Intermediate

- Power(x,n)
- Climbing stairs
- Generate subsets
- Generate permutations
- Combination sum

### Advanced (Backtracking)

- N-Queens
- Sudoku solver
- Word search
- Rat in maze
- Palindrome partitioning

## Key Interview Insight

Most recursion interview questions fall into three patterns:

1. **Linear recursion** (reduce size)
2. **Binary recursion** (two calls)
3. **Backtracking** (generate all possibilities)

Mastering these templates solves 70–80% recursion interview problems.

## Recommended Practice Order

1. Factorial
2. Reverse string
3. Fibonacci
4. Subsets
5. Permutations
6. Combination Sum
7. N-Queens