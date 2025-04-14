# Array Reversal: Recursion vs Iteration - Deep Technical Analysis

## 1) Recursive Approach (Two Pointers)
-----------------------------------
- Uses two pointers: start (`arr`) and end.
- Base condition: `if (arr >= end) return;`
- Swaps values and recurses inward.
- **Time Complexity:** O(N)
- **Space Complexity:** O(N/2) recursive calls (stack space)
- **Performance:** Clear logic, good for education, less ideal for production.

## 2) Recursive Approach (Single Pointer + Size)
--------------------------------------------
- Uses one pointer (`arr`) and size parameter.
- Derives end pointer internally each time.
- Base condition: `if (arr >= end) return;`
- Swaps values and recurses inward.
- **Time Complexity:** O(N)
- **Space Complexity:** O(N/2) recursive calls.
- **Practical Note:** Cleaner interface, solves the minimalist recursion puzzle!

## 3) Iterative Approach (Recommended)
-----------------------------------
- Uses a `while` loop with two pointers (start, end).
- Swaps values until `start >= end`.
- **Time Complexity:** O(N)
- **Space Complexity:** O(1) - No recursion!
- **Performance:** Best choice for production and systems-level programming.

## Scientific Memory-Level Insights:
- Recursive versions have extra stack usage (O(N/2)).
- Iterative is cache-friendly and avoids function call overhead.
- Recursive solutions are good for learning recursion depth and pointer manipulation.
- Iterative preferred for embedded, OS kernels, and performance-critical systems.

## Final Note:
- You successfully understood the nuances of recursive depth, pointer arithmetic,
  and iterative optimization.
- Excellent exercise for strengthening systems programming mindset!
