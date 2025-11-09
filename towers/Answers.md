#  MCON 264 — Recursion Assignment: Towers of Hanoi × 3


##  Overview

In this lab, you implemented three recursive versions of the Towers of Hanoi problem and (optionally) one iterative version.  
Each part reinforces a key concept of recursion — base case, recursive case, and growth pattern — and illustrates how recursion can be refactored or replaced by iteration.

---

## Part 1 — Classic Towers of Hanoi (`TowersOfHanoi.java`)

### 1. Base Case
_Describe the base condition that stops recursion (for example, what happens when `n == 0`?)._

> When there are 0 rings it takes no moves so that is the base case the method 
> returns without doing anything.

### 2. Recursive Case

> If there are more than 0 rings when the method is called it will
> call the method for one ring less and tell it to move from the from pile to the 
> aux pile. That ring will then move to the destination pile and then
> call the method for 1 less and tell it to move from the aux to the
> destination

### 3. Sample Trace (for n = 3)


|  Move #  | Ring | From | To |
|:--------:|:----:|:----:|:--:|
|    1     |  1   |  A   | C  | 
|    2     |  2   |  A   | B  |   
|    3     |  1   |  C   | B  |
|    4     |  3   |  A   | C  |
|    5     |  1   |  B   | A  |
|    6     |  2   |  B   | C  |
|    7     |  1   |  A   | C  |

_Total moves = 2ⁿ − 1 = 7 (for n = 3)_

---

## Part 2 — Counting Moves (`TowersExercise21.java`)

### 1. Approach
_How did you modify the standard recursion to count rather than print moves?_

>  The method calls remained the same the change is that instead of printing
> the move Ring x from A to B, I incremented the counter.

### 2. Verification of Formula
_Complete the table and verify that count = 2ⁿ − 1._

| n | Expected (2ⁿ − 1) | Program Output | Matches? (Y/N) |
|:--:|:--:|:--------------:|:--------------:|
| 1 | 1 |       1        |       Y        |
| 2 | 3 |       3        |       Y        |
| 3 | 7 |       7        |       Y        |
| 4 | 15 |       15       |       Y        |
| 5 | 31 |       31       |        Y       |

### 3. Reflection
_What changes when you replace printed moves with a counter? What are the pros and cons?_

> Just the action that is done in the method changes the calls remain the same. The downside is I
now know how many moves it will take but I don't know what the moves are.

---

## Part 3 — Hanoi Variation (`TowersVariations.java`)

### 1. New Rule
_Every move must pass through the middle peg. How does this alter the recursion?_

> Each time the method is called it calls itself recursively 3 times not just two
> The first call moves the tower from to the destination (when called it ensures each peg goes
> through the middle on its own). Then current peg moves to middle. Then we move n-1 to start point,
> current peg to goal, and n-1 back to destination.

### 2. Observed Move Counts

| n | Expected ≈ 3ⁿ − 1 | Program Output | Matches? (Y/N) |
|:--:|:--:|:--------------:|:--------------:|
| 1 | 2 |       2        |       Y        |
| 2 | 8 |       8        |       Y        |
| 3 | 26 |       26       |       Y        |
| 4 | 80 |       80       |       Y        |

### 3. Analysis
_Why does this variation grow faster than the standard version? How do additional move constraints affect complexity?_

> Each time the method is called it calls itself recursively 3 times not just two that is why
> it is 3ⁿ and not 2ⁿ.

---

## Comparative Analysis

### 1. Growth Patterns

| Version | Approx. Formula | Growth Type |
|:--|:--|:--|
| Standard | 2ⁿ − 1 | Exponential |
| Variation | 3ⁿ − 1 | Exponential (faster) |
| Iterative (Optional) | 2ⁿ − 1 | Same as recursive but loop based |

### 2. Stack Depth and Memory
_Estimate the maximum recursion depth before StackOverflowError and discuss how stack size (–Xss flag) affects this._

> ✎ Your answer here

---

## Part 4 — Beyond Recursion (Extra Credit)

### Iterative / Explicit-Stack Version (`TowersIterative.java`)

1. How does your iterative version simulate recursion?
2. How did you track pending calls or frames?
3. Which version (r vs iterative) is clearer? Why?

> ✎ Your answer here

---

## Discussion &amp; Reflection

1. What three questions can you use to verify a recursive solution works?
2. How do the base case and recursive case cooperate to guarantee termination?
3. What is the trade-off between elegance and efficiency in recursion?

> ✎ Your answers here

---

## References (APA or MLA format)

- Dale, N., Joyce, D., &amp; Weems, C. (2016). *Object-Oriented Data Structures Using Java* (Ch. 3 Recursion). Jones &amp; Bartlett.
- Additional videos or websites you consulted (YouTube CS50 Recursion, GeeksForGeeks Hanoi, etc.)

---

 **Submission Checklist**

- [ ] `TowersOfHanoi.java` — implemented and tested
- [ ] `TowersExercise21.java` — counts moves correctly
- [ ] `TowersVariations.java` — middle-peg constraint implemented
- [ ] (Extra Credit) `TowersIterative.java` — loop or explicit stack solution
- [ ] All JUnit tests pass (green on GitHub Actions)
- [ ] This `ANSWERS.md` file completed and committed to repo  
