# Karg & Thompson Algorithm — Closed Jobs Sequence Route Minimizer

**Author:** Pier Sergio Caltabiano  
**Date:** March 06, 2026

---

## About This Project

This is a personal project implementing the **Karg & Thompson heuristic insertion algorithm** to find a locally optimal sequence of jobs that minimizes the total travel time across a closed route — meaning the last job always returns to the first.

The idea for this project came from a university exam where I first encountered this algorithm. I always promised myself I would eventually automate the process, and this is that automation.

The program asks the user to input a list of jobs and the travel times between each pair, then builds an optimized sequence step by step using the insertion heuristic.

---

## How It Works

1. The user enters a list of jobs (between 2 and 10)
2. The user enters the travel time between every pair of jobs
3. The algorithm randomly selects 2 jobs as the starting sequence
4. Each remaining job is inserted into the position that minimizes the total route cost at that moment
5. The final sequence and its total travel time are displayed

---

## Limitations — Local Optimal vs Global Optimal

This algorithm finds a **locally optimal solution**, not necessarily the **globally optimal one**. This distinction is important and comes with several implications:

**Greedy decisions**  
At each step, the algorithm inserts a job in the position that looks best *at that moment*, without considering how that choice affects future insertions. A decision that looks good now may lead to a worse overall result later.

**Dependence on the starting pair**  
The two jobs chosen randomly at the start influence the entire sequence. A different starting pair can produce a completely different final route, with a different total cost.

**Some sequences can never be generated**  
Because the first job is always fixed, the structure of the algorithm prevents certain permutations from ever being considered. This means the true global optimum might be unreachable, even across many executions.

**How to interpret the result**  
The output should be read as a *good feasible solution* — a reasonable route that is efficient in practice — but not as a mathematical guarantee of the shortest possible sequence.

---

## How to Find the Global Optimum (and Why This Project Does Not)

The true global optimum can be found by evaluating all possible permutations (**brute force**). However, this becomes computationally impractical very quickly:

| Number of Jobs | Permutations to Evaluate |
|:--------------:|:------------------------:|
| 4              | 6                        |
| 6              | 120                      |
| 8              | 5,040                    |
| 10             | 362,880                  |

The heuristic approach trades **guaranteed optimality** for **speed and simplicity**, which is often an acceptable trade-off in real-world scheduling problems.
