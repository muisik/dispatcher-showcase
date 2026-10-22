I'll start by inspecting the relevant files.

All 5 acceptance tests pass.

## Summary

**Change made (only `src/pricing.py`):**

The original implementation added the percentage instead of subtracting it (`100 + percent`), and had no input validation. The fixed version:

```python
def apply_discount(price_cents, percent):
    if price_cents < 0:
        raise ValueError("price_cents must be non-negative")
    if percent < 0 or percent > 100:
        raise ValueError("percent must be between 0 and 100")
    return price_cents * (100 - percent) // 100
```

- **Discounts subtract:** `(100 - percent)` replaces `(100 + percent)`, so 20% off 1000 → 800.
- **Zero and 100 percent:** 0% preserves the price; 100% yields 0; a zero price stays 0.
- **Fractional cents round down:** integer floor division `// 100` truncates, so 199 at 10% → 179.
- **Validation:** negative prices and percentages outside 0..100 raise `ValueError`.

No tests, `.git`, or other files were touched; no dependencies installed and no network/env access used.

**Test result:** `Ran 5 tests in 0.000s — OK` (exit code 0), all REQ_001–REQ_005 passing.