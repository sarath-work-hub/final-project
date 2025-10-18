# SHA-256 Implementation in C++  
### Computing the SHA-256 Hash of the Book of Mark (RSV)

This repository contains a **pure C++ implementation** of the SHA-256 cryptographic hash algorithm, following the official pseudocode from the [SHA-2 specification](https://en.wikipedia.org/wiki/SHA-2).

The project demonstrates how to:
- Implement SHA-256 from scratch using 32-bit operations.
- Read a full text file (in this case, the *Book of Mark* from the Revised Standard Version).
- Compute and output its exact SHA-256 hash.

---

##  Project Overview

**File:** `sha256_mark.cpp`  
**Input file:** `mark_rsv.txt` (contains the full Book of Mark text)  
**Output:** SHA-256 hash (64-character hexadecimal string)

---

## How It Works

SHA-256 (Secure Hash Algorithm 256-bit) is part of the SHA-2 family designed by the NSA and standardized by NIST (FIPS PUB 180-4).  
It works by:

1. **Padding** the input to a multiple of 512 bits.
2. **Parsing** the message into 512-bit blocks.
3. **Initializing** eight 32-bit hash values.
4. **Processing** each block through 64 rounds of bitwise operations.
5. **Combining** results into a 256-bit (32-byte) hash value.

This implementation uses:
- Bitwise rotations (`rotr`)
- Message schedule array `W[64]`
- Compression function with constants `K[64]`
- Final output concatenation of eight 32-bit state variables.

---

## Code Structure

| Function | Description |
|-----------|--------------|
| `rotr(x, n)` | Performs right rotation on a 32-bit word. |
| `transform()` | Core compression function applied on each 512-bit block. |
| `update()` | Accepts data in chunks and buffers until full blocks are processed. |
| `final()` | Pads the message, appends length, and finalizes the hash. |
| `sha256()` | Helper to compute hash in one step. |
| `main()` | Reads `mark_rsv.txt`, runs SHA-256, and prints the resulting hash. |

---

## 🧾 How to Build and Run

### 1️ Prerequisites
You need a C++17-compatible compiler (e.g., GCC, Clang, or MSVC).

###  Clone or Download
```bash
git clone https://github.com/<your-username>/sha256-mark.git
cd sha256-mark
