Okay, I will go through the provided OCR text and extract formulas and theorems. This will be a comprehensive list.

**Chapter 1: Introduction**

*   **Page 16 (Integers):**
    *   `x mod m`: remainder when x is divided by m.
    *   Example: `17 mod 5 = 2`
*   **Page 17 (Modular Arithmetic):**
    *   `(a+ b) mod m = (a mod m+ b mod m) mod m`
    *   `(a− b) mod m = (a mod m− b mod m) mod m`
    *   `(a· b) mod m = (a mod m· b mod m) mod m`
*   **Page 17 (Floating Point Numbers):**
    *   Comparison: `abs(a-b) < ε` (where ε is a small number like 10⁻⁹)
*   **Page 20 (Sum Formulas):**
    *   General sum: `Σ_{x=1 to n} x^k = 1^k + 2^k + 3^k + ... + n^k`
    *   Sum of first n integers: `Σ_{x=1 to n} x = 1+2+3+...+n = n(n+1)/2`
    *   Sum of first n squares: `Σ_{x=1 to n} x^2 = 1^2+2^2+3^2+...+n^2 = n(n+1)(2n+1)/6`
    *   (Mention of Faulhaber's formula)
*   **Page 21 (Sum Formulas continued):**
    *   Arithmetic progression sum: `(sum of n numbers from a to b) = n(a+b)/2`
    *   Geometric progression sum: `a + ak + ak² + ... + b = (bk - a) / (k - 1)`
    *   Special geometric sum: `1 + 2 + 4 + 8 + ... + 2^(n-1) = 2^n - 1`
    *   Harmonic sum upper bound: `Σ_{x=1 to n} (1/x) ≤ log₂(n) + 1`
*   **Page 22 (Set Theory):**
    *   Number of subsets of a set S: `2^|S|`
    *   Set builder notation: `{f(n) : n ∈ S}`
*   **Page 23 (Logic & Functions):**
    *   Floor function: `⌊x⌋`
    *   Ceiling function: `⌈x⌉`
*   **Page 24 (Functions & Logarithms):**
    *   Factorial definition: `n! = Π_{x=1 to n} x = 1·2·3·...·n`
    *   Factorial recursion: `0! = 1`, `n! = n·(n-1)!`
    *   Fibonacci numbers recursion: `f(0) = 0`, `f(1) = 1`, `f(n) = f(n-1) + f(n-2)`
    *   Binet's formula: `f(n) = ((1+√5)^n - (1-√5)^n) / (2^n √5)`
    *   Logarithm definition: `log_k(x) = a` if and only if `k^a = x`
    *   Logarithm of a product: `log_k(ab) = log_k(a) + log_k(b)`
    *   Logarithm of a power: `log_k(x^n) = n·log_k(x)`
    *   Logarithm of a quotient: `log_k(a/b) = log_k(a) - log_k(b)`
    *   Change of base formula: `log_u(x) = log_k(x) / log_k(u)`
    *   Number of digits of integer x in base b: `⌊log_b(x)⌋ + 1`

**Chapter 2: Time Complexity**

*   (No specific mathematical formulas/theorems, mostly O-notation concepts)

**Chapter 3: Sorting**

*   **Page 37 (Inversions):**
    *   Max number of inversions in an array of n elements: `n(n-1)/2`
*   **Page 38 (Sorting Lower Bound):**
    *   Comparison sort lower bound: `Ω(n log n)` (derived from `log₂(n!) ≥ (n/2)·log₂(n/2)`)

**Chapter 5: Complete Search**

*   **Page 64 (Meet in the Middle):**
    *   Complexity reduction: `O(2^n)` to `O(2^(n/2))` (since `2^(n/2) = √2^n`)

**Chapter 7: Dynamic Programming**

*   **Page 76 (Coin Problem - Recursive Formulation):**
    *   `solve(x) = min(solve(x-c₁) + 1, solve(x-c₂) + 1, ...)`
    *   General recursive function for min coins:
        `solve(x) = ∞` if `x < 0`
        `solve(x) = 0` if `x = 0`
        `solve(x) = min_{c∈coins} (solve(x-c) + 1)` if `x > 0`
*   **Page 79 (Coin Problem - Counting Solutions):**
    *   General recursive function for counting ways:
        `solve(x) = 0` if `x < 0`
        `solve(x) = 1` if `x = 0`
        `solve(x) = Σ_{c∈coins} solve(x-c)` if `x > 0`
*   **Page 81 (Paths in a Grid):**
    *   `sum(y,x) = max(sum(y,x-1), sum(y-1,x)) + value[y][x]`
*   **Page 82 (Knapsack Problems):**
    *   `possible(x,k) = possible(x-w_k, k-1) ∨ possible(x, k-1)`
*   **Page 84 (Edit Distance):**
    *   `distance(a,b) = min(distance(a,b-1)+1, distance(a-1,b)+1, distance(a-1,b-1)+cost(a,b))`
    *   where `cost(a,b) = 0` if `x[a]=y[b]`, else `cost(a,b)=1`.
*   **Page 86 (Counting Tilings):**
    *   Formula for number of tilings of n x m grid: `Π_{a=1 to ⌊n/2⌋} Π_{b=1 to ⌊m/2⌋} 4·(cos²(πa/(n+1)) + cos²(πb/(m+1)))`

**Chapter 9: Range Queries**

*   **Page 94 (Sum Queries):**
    *   `sum_q(a,b) = sum_q(0,b) - sum_q(0,a-1)` (using prefix sums)
*   **Page 95 (Minimum Queries - Sparse Table):**
    *   Preprocessing recursion: `min_q(a,b) = min(min_q(a, a+w-1), min_q(a+w, b))` where `w = (b-a+1)/2`
    *   Query: `min_q(a,b) = min(min_q(a, a+k-1), min_q(b-k+1, b))` where k is largest power of 2 not exceeding `b-a+1`.
*   **Page 96 (Binary Indexed Tree):**
    *   `tree[k] = sum_q(k - p(k) + 1, k)`
*   **Page 98 (Binary Indexed Tree Implementation):**
    *   `p(k) = k & -k` (largest power of two that divides k)

**Chapter 10: Bit Manipulation**

*   **Page 105 (Bit Representation):**
    *   Conversion from binary `b_k...b_0` to decimal: `b_k 2^k + ... + b_1 2^1 + b_0 2^0`
*   **Page 107 (Bit Operations):**
    *   `~x = -x-1` (for not operation)
    *   `x << k` corresponds to multiplying `x` by `2^k`
    *   `x >> k` corresponds to dividing `x` by `2^k` (integer division)
    *   `x & (1 << k)` (checks if kth bit is set)
    *   `x | (1 << k)` (sets kth bit)
    *   `x & ~(1 << k)` (clears kth bit)
    *   `x ^ (1 << k)` (inverts kth bit)
    *   `x & (x-1)` (clears the last set bit)
    *   `x & -x` (isolates the last set bit / gets the value of the smallest power of 2 that is a factor of x)
    *   `x | (x-1)` (inverts all bits after the last set bit)
    *   `x & (x-1) == 0` (checks if x is a power of two, for positive x)
*   **Page 112 (Optimal Selection - DP with Bitmask):**
    *   `total(S,d) = min(total(S,d-1), min_{x∈S} (total(S \ {x}, d-1) + price[x][d]))`
*   **Page 115 (Counting Subsets - DP with Bitmask / "SOS DP"):**
    *   `sum(S) = Σ_{A⊂S} value[A]`
    *   Recursive definition for `partial(S,k)`:
        `partial(S,k) = value[S]` if `k = -1`
        `partial(S,k) = partial(S,k-1)` if `k ∉ S`
        `partial(S,k) = partial(S,k-1) + partial(S \ {k}, k-1)` if `k ∈ S`

**Chapter 16: Directed Graphs**

*   **Page 154 (Successor Paths - Preprocessing for k-th successor):**
    *   `succ(x,k) = succ(x)` if `k=1`
    *   `succ(x,k) = succ(succ(x, k/2), k/2)` if `k > 1` (and k is power of two for base, general k by sum of powers of two)

**Chapter 18: Tree Queries**

*   **Page 179 (Distances of Nodes using LCA):**
    *   `distance(a,b) = depth(a) + depth(b) - 2 * depth(c)` where c is LCA of a and b.

**Chapter 19: Paths and Circuits**

*   **Page 184 (Eulerian Path/Circuit Existence - Undirected):**
    *   Eulerian Path: Connected graph AND (all nodes even degree OR exactly two nodes odd degree).
    *   Eulerian Circuit: Connected graph AND all nodes even degree.
*   **Page 185 (Eulerian Path/Circuit Existence - Directed):**
    *   Eulerian Path: Strongly connected (for edges on path) AND (for all nodes, indegree=outdegree OR one node indegree=outdegree-1, one node outdegree=indegree-1, others indegree=outdegree).
    *   Eulerian Circuit: Strongly connected AND for all nodes, indegree=outdegree.
*   **Page 187 (Hamiltonian Paths - Existence Theorems):**
    *   **Dirac's Theorem:** If deg(v) ≥ n/2 for all v, graph has Hamiltonian path (actually circuit).
    *   **Ore's Theorem:** If deg(u) + deg(v) ≥ n for every pair of non-adjacent u,v, graph has Hamiltonian path (actually circuit).
*   **Page 188 (De Bruijn Sequences):**
    *   Length of De Bruijn sequence (alphabet k, substring length n): `k^n + n - 1`

**Chapter 20: Flows and Cuts**

*   (Implicitly) **Max-Flow Min-Cut Theorem:** The maximum flow from a source to a sink is equal to the minimum capacity of an s-t cut.
*   **Page 199 (Hall's Theorem):**
    *   A bipartite graph has a matching that covers all nodes in a set X (e.g., left nodes) if and only if for every subset A ⊆ X, `|A| ≤ |N(A)|` (where N(A) is the set of neighbors of nodes in A).
*   **Page 199 (Kőnig's Theorem):**
    *   In any bipartite graph, the number of edges in a maximum matching equals the minimum number of vertices in a vertex cover.
*   **Page 201 (Node-Disjoint Path Cover):**
    *   Size of minimum node-disjoint path cover = `n - c` (where n is num nodes, c is size of max matching in corresponding bipartite graph).
*   **Page 203 (Dilworth's Theorem):**
    *   In any finite partially ordered set (or DAG), the size of a minimum path cover equals the size of a maximum antichain.

**Chapter 21: Number Theory**

*   **Page 207 (Prime Factorization):**
    *   Unique Prime Factorization: `n = p₁^α₁ p₂^α₂ ... p_k^α_k`
*   **Page 208 (Properties from Prime Factorization):**
    *   Number of factors (τ(n)): `τ(n) = Π_{i=1 to k} (α_i + 1)`
    *   Sum of factors (σ(n)): `σ(n) = Π_{i=1 to k} (1 + p_i + ... + p_i^α_i) = Π_{i=1 to k} (p_i^(α_i+1) - 1) / (p_i - 1)`
    *   Product of factors (μ(n)): `μ(n) = n^(τ(n)/2)`
    *   Perfect number: `n = σ(n) - n`
    *   Density of primes (Prime Number Theorem approximation): `π(n) ≈ n / ln(n)`
*   **Page 209 (Conjectures):**
    *   **Goldbach's Conjecture:** Every even integer n > 2 is `a+b` where a,b are primes.
    *   **Twin Prime Conjecture:** Infinite pairs `{p, p+2}` where p, p+2 are primes.
    *   **Legendre's Conjecture:** Always a prime between `n²` and `(n+1)²`.
*   **Page 210 (GCD and LCM):**
    *   `lcm(a,b) = (a*b) / gcd(a,b)`
*   **Page 211 (Euclid's Algorithm):**
    *   `gcd(a,b) = a` if `b=0`
    *   `gcd(a,b) = gcd(b, a mod b)` if `b ≠ 0`
*   **Page 211 (Euler's Totient Function):**
    *   `φ(n) = Π_{i=1 to k} p_i^(α_i-1) (p_i - 1)`
    *   `φ(n) = n - 1` if n is prime.
*   **Page 211 (Modular Arithmetic Properties - repeated):**
    *   `(x+y) mod m = (x mod m + y mod m) mod m`
    *   `(x-y) mod m = (x mod m - y mod m) mod m`
    *   `(x·y) mod m = (x mod m · y mod m) mod m`
    *   `x^n mod m = (x mod m)^n mod m`
*   **Page 212 (Modular Exponentiation):**
    *   `x^n = 1` if `n=0`
    *   `x^n = (x^(n/2)) * (x^(n/2))` if `n` is even
    *   `x^n = x^(n-1) * x` if `n` is odd
*   **Page 212 (Fermat's Little Theorem & Euler's Theorem):**
    *   **Fermat's Little Theorem:** `x^(m-1) ≡ 1 (mod m)` (if m is prime, x and m coprime).
    *   Consequence: `x^k ≡ x^(k mod (m-1)) (mod m)`.
    *   **Euler's Totient Theorem:** `x^φ(m) ≡ 1 (mod m)` (if x and m coprime).
*   **Page 212 (Modular Inverse):**
    *   `x x⁻¹ ≡ 1 (mod m)`
    *   `x⁻¹ ≡ x^(φ(m)-1) (mod m)` (if x, m coprime)
    *   `x⁻¹ ≡ x^(m-2) (mod m)` (if m is prime, x, m coprime)
*   **Page 214 (Diophantine Equations):**
    *   `ax + by = c`
    *   `ax + by = gcd(a,b)` (solvable by extended Euclidean algorithm)
    *   General solution from particular solution (x₀, y₀): `(x₀ + k * b/gcd(a,b), y₀ - k * a/gcd(a,b))`
*   **Page 215 (Chinese Remainder Theorem):**
    *   System: `x ≡ a_i (mod m_i)` for `i=1...n` (m_i coprime)
    *   Solution: `x = Σ_{k=1 to n} a_k X_k (X_k⁻¹ mod m_k)` where `X_k = (Π m_i) / m_k`
*   **Page 215 (Lagrange's Four-Square Theorem):**
    *   Every positive integer can be represented as a sum of four squares.
*   **Page 216 (Zeckendorf's Theorem):**
    *   Every positive integer has a unique representation as a sum of non-consecutive Fibonacci numbers.
*   **Page 216 (Euclid's Formula for Primitive Pythagorean Triples):**
    *   `(n² - m², 2nm, n² + m²)`
*   **Page 216 (Wilson's Theorem):**
    *   `(n-1)! ≡ n-1 (mod n)` if and only if n is prime. (Note: often stated as `(n-1)! ≡ -1 (mod n)`)

**Chapter 22: Combinatorics**

*   **Page 217 (Integer Partitions - specific case):**
    *   Number of ways to represent n as sum of positive integers: `f(n) = 2^(n-1)`
    *   Recursive: `f(0)=1`, `f(n) = Σ_{i=0 to n-1} f(i)` for `n>0`.
*   **Page 218 (Binomial Coefficients):**
    *   Recursive: `(n k) = (n-1 k-1) + (n-1 k)`
    *   Formula: `(n k) = n! / (k!(n-k)!)`
    *   Symmetry: `(n k) = (n n-k)`
    *   Sum: `Σ_{k=0 to n} (n k) = 2^n`
*   **Page 219 (Binomial Theorem):**
    *   `(a+b)^n = Σ_{k=0 to n} (n k) a^(n-k) b^k`
*   **Page 220 (Stars and Bars / Balls and Boxes):**
    *   Scenario 1 (at most one ball per box): `(n k)`
    *   Scenario 2 (multiple balls per box): `(k+n-1 k)`
    *   Scenario 3 (at most one, no adjacent): `(n-k+1 k)` (This is `(n-k+1 choose (n-k+1) - (k)) = (n-k+1 choose k)`)
*   **Page 220 (Multinomial Coefficients):**
    *   `(n k₁, k₂, ..., k_m) = n! / (k₁! k₂! ... k_m!)` where `Σ k_i = n`
*   **Page 221 (Catalan Numbers):**
    *   Recursive: `C_n = Σ_{i=0 to n-1} C_i C_{n-i-1}` (with `C_0 = 1`)
    *   Binomial coefficient form: `C_n = (1/(n+1)) * (2n n)`
*   **Page 222 (Inclusion-Exclusion Principle):**
    *   Two sets: `|A ∪ B| = |A| + |B| - |A ∩ B|`
*   **Page 223 (Inclusion-Exclusion Principle):**
    *   Three sets: `|A∪B∪C| = |A|+|B|+|C| - |A∩B|-|A∩C|-|B∩C| + |A∩B∩C|`
*   **Page 224 (Derangements - Recursive):**
    *   `f(1)=0`, `f(2)=1`, `f(n) = (n-1)(f(n-2) + f(n-1))` for `n > 2`
*   **Page 224 (Burnside's Lemma):**
    *   Number of distinct configurations = `(1/|G|) * Σ_{g∈G} |X^g|` (where G is group of symmetries, X^g is set of fixed points under g).
    *   Simplified for rotations of n items: `(1/n) * Σ_{k=1 to n} c(k)` (as in text)
    *   Necklaces (n pearls, m colors): `(1/n) * Σ_{i=0 to n-1} m^(gcd(i,n))`
*   **Page 225 (Cayley's Formula):**
    *   Number of labeled trees on n nodes: `n^(n-2)`

**Chapter 23: Matrices**

*   **Page 228 (Matrix Multiplication):**
    *   `AB[i,j] = Σ_{k=1 to n} A[i,k] · B[k,j]`
*   **Page 229 (Matrix Power):**
    *   `A^k = A · A · ... · A` (k times)
    *   `A^0 = I` (Identity matrix)
*   **Page 229 (Determinant):**
    *   `det(A) = Σ_{j=1 to n} A[1,j] C[1,j]` (expansion by first row)
    *   Cofactor: `C[i,j] = (-1)^(i+j) det(M[i,j])`
*   **Page 230 (Inverse Matrix):**
    *   `A⁻¹[i,j] = C[j,i] / det(A)` (Note: uses transpose of cofactor matrix)
*   **Page 230 (Linear Recurrences):**
    *   `f(n) = c₁f(n-1) + c₂f(n-2) + ... + c_k f(n-k)`
*   **Page 231 (Matrix form for Linear Recurrences):**
    *   For Fibonacci: `[f(i+1); f(i+2)] = [0 1; 1 1] * [f(i); f(i+1)]`
    *   `[f(n); f(n+1)] = [0 1; 1 1]^n * [f(0); f(1)]`
*   **Page 233 (Graphs and Matrices - Shortest Paths modification):**
    *   Modified matrix multiplication for shortest paths with exactly k edges: `AB[i,j] = min_k (A[i,k] + B[k,j])`

**Chapter 24: Probability**

*   **Page 235 (Basic Probability):**
    *   `P(event) = (number of desired outcomes) / (total number of outcomes)`
*   **Page 236 (Probability of an Event A):**
    *   `P(A) = Σ_{x∈A} p(x)`
*   **Page 237 (Complement):**
    *   `P(Ā) = 1 - P(A)`
*   **Page 237 (Union):**
    *   `P(A ∪ B) = P(A) + P(B) - P(A ∩ B)`
    *   If A, B disjoint: `P(A ∪ B) = P(A) + P(B)`
*   **Page 237 (Conditional Probability):**
    *   `P(A|B) = P(A ∩ B) / P(B)`
*   **Page 238 (Intersection):**
    *   `P(A ∩ B) = P(A) * P(B|A)`
    *   If A, B independent: `P(A ∩ B) = P(A) * P(B)`
*   **Page 239 (Expected Value):**
    *   `E[X] = Σ_x P(X=x) * x`
    *   **Linearity of Expectation:** `E[X₁ + X₂ + ... + X_n] = E[X₁] + E[X₂] + ... + E[X_n]`
*   **Page 240 (Distributions):**
    *   Uniform Distribution `E[X] = (a+b)/2`
    *   Binomial Distribution `P(X=x) = p^x (1-p)^(n-x) * (n x)`, `E[X] = pn`
    *   Geometric Distribution `P(X=x) = (1-p)^(x-1) p`, `E[X] = 1/p`

**Chapter 25: Game Theory**

*   **Page 247 (Nim Game Analysis):**
    *   Nim sum: `s = x₁ ⊕ x₂ ⊕ ... ⊕ x_n` (Losing state if s=0, winning if s≠0)
*   **Page 248 (Sprague-Grundy Theorem):**
    *   Grundy number (g-number) of a game state `S`: `g(S) = mex({g(S') | S' is reachable from S})`
    *   `mex(Set)` = Minimum Excluded value (smallest non-negative integer not in Set).
*   **Page 250 (Subgames):**
    *   Grundy number of a sum of impartial games = Nim sum of their Grundy numbers.
*   **Page 251 (Grundy's Game):**
    *   Move: divide heap into two non-empty heaps of different sizes.
    *   `f(n) = mex({f(i) ⊕ f(n-i) | 1 ≤ i < n/2})` (with appropriate base cases like f(1)=f(2)=0)

**Chapter 26: String Algorithms**

*   **Page 255 (Polynomial Hashing):**
    *   `hash(s) = (s[0]A^(n-1) + s[1]A^(n-2) + ... + s[n-1]A^0) mod B`
*   **Page 256 (Substring Hash):**
    *   `hash(s[a...b]) = (h[b] - h[a-1]p[b-a+1]) mod B` (where h is prefix hashes, p is powers of A)

**Chapter 27: Square Root Algorithms**

*   **Page 264 (Integer Partitions Observation):**
    *   Sum of `1, 2, ..., k` is `k(k+1)/2`. If this is `n`, then `k = O(√n)`.

**Chapter 28: Segment Trees Revisited**

*   **Page 270 (Polynomial Updates - sum in range [x,y] with lazy polynomial):**
    *   `sum = s + Σ_{u=0 to y-x} (z_k u^k + z_{k-1} u^{k-1} + ... + z_0)`

**Chapter 29: Geometry**

*   **Page 275 (Heron's Formula for triangle area):**
    *   `Area = √[s(s-a)(s-b)(s-c)]` where `s = (a+b+c)/2`
*   **Page 278 (Cross Product of vectors a=(x₁,y₁), b=(x₂,y₂)):**
    *   `a × b = x₁y₂ - x₂y₁`
*   **Page 279 (Area of triangle with vertices a,b,c using cross product):**
    *   `Area = |(a-c) × (b-c)| / 2`
*   **Page 280 (Distance from point p to line s₁s₂):**
    *   `d = |(s₁-p) × (s₂-p)| / |s₂-s₁|`
*   **Page 281 (Shoelace Formula for polygon area):**
    *   `Area = (1/2) |Σ_{i=1 to n-1} (x_i y_{i+1} - x_{i+1} y_i)|` (assuming p₁=p_n)
    *   Alternative form: `Area = (1/2) |Σ_{i=1 to n-1} (x_{i+1} - x_i)(y_i + y_{i+1})|`
*   **Page 282 (Pick's Theorem for polygon area):**
    *   `Area = a + b/2 - 1` (a=interior integer points, b=boundary integer points)
*   **Page 282 (Distance Functions):**
    *   Euclidean distance: `√[(x₂-x₁)² + (y₂-y₁)²]`
    *   Manhattan distance: `|x₁-x₂| + |y₁-y₂|`
*   **Page 284 (Manhattan Distance with Rotated Coordinates):**
    *   If `p'_i = (x_i+y_i, y_i-x_i)`, then
        `|x₁-x₂| + |y₁-y₂| = max(|x'₁-x'₂|, |y'₁-y'₂|)`

This list should cover the significant formulas and named theorems mentioned in the OCR text. Some are definitions or properties rather than standalone theorems, but are fundamental to the concepts discussed.
