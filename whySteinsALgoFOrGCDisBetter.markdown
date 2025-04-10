# LESSONSUMMARY: GCD Algorithms Deep Dive

## 1. Introduction to GCD Algorithms

### Euclidean Algorithm (Modulo method)
- Uses repeated modulo operation: `GCD(a, b) = GCD(b, a % b)`
- Portable and works well at higher-level languages.

### Stein's Algorithm (Binary GCD)
- Uses bit-shifting and subtraction.
- Replaces division with efficient bitwise operations:
  - If both numbers even: `GCD(x, y) = 2 * GCD(x/2, y/2)`
  - If one even, one odd: remove the factor of 2.
  - If both odd: `GCD(x, y) = GCD(|x - y| / 2, min(x, y))`

---

## 2. Why Stein's Algorithm is Better for Low-Level Systems

### Bitwise Operations
- Shifts (`>>`) are much faster than division.
- `x >> 1` is almost instantaneous, division is multi-cycle.

### Conditional Branching
- Euclidean algorithm uses modulo, which is high cost due to division.
- Branching is harder to predict with modulo; can cause pipeline stalls.
- Stein’s checks for even/odd using bitwise AND (`x & 1`), which is very fast.

### Pipeline Efficiency
- Modern CPUs prefer predictable instruction flows.
- Division interrupts smooth instruction flow and requires microcode assist on some CPUs.
- Shifts and logical operations complete in fewer cycles and keep the pipeline running.

---

## 3. Hardware-Level Analysis

### Power Efficiency
- Bitwise operations consume less power than arithmetic division.

### Instruction Set Utilization
- Modern instruction sets (x86, ARM) are optimized for bitwise operations.
- Embedded processors (ARM Cortex-M, RISC-V, etc.) benefit immensely.

### Embedded Processors
- Devices with no hardware divider or limited instruction sets use Stein’s Algorithm efficiently.

---

## 4. Performance Comparison (Theoretical)

- Division operation: ~20–40 CPU cycles.
- Bit-shift: ~1–3 CPU cycles (depending on architecture).
- In performance-critical code (cryptography, embedded systems), Stein’s gives noticeable speed-up.

**Example: Bitwise check (Fast)**
```c
if (x & 1) { /* x is odd */ }
else { /* x is even */ }
