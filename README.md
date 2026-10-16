# Checkout Demo

A small checkout calculation library with **intentional bugs** for demonstrating
CommandOS reading a GitHub issue with Anchor Browser and testing a fix in a real
Daytona sandbox. This is a demo fixture, not a production storefront.

## Run the tests

Requires Node.js 20 or newer. There are no dependencies or installation steps.

```sh
npm test
```

The initial commit has **8 tests: 5 passing and 3 failing**. The failures describe
incorrect percentage discounts and a missing cent when splitting a payment.
The public issue documents the expected behavior. A successful repair should make
all 8 tests pass without weakening or deleting the assertions.

## Examples

- A $80 subtotal with a 25% discount should cost **$60**, not $55.
- A $80 cart with a 10% discount should cost **$72**, not $70.
- A $100 bill split three ways should be **$33.34, $33.33, $33.33**.

Fixed-amount discounts, zero-floor behavior, formatting, and ordinary cart totals
must continue to work.

## Files

- `src/money.js`: discounts, currency rounding, bill splitting, and formatting.
- `src/cart.js`: totals line items and applies a discount.
- `test/`: built-in Node.js tests covering both modules.

## Local demo copy

The prepared checkout on the demo Mac is `~/CommandOS-Demo/checkout-demo`.
CommandOS can stage that local directory into Daytona; it does not need GitHub
credentials in the sandbox. The cloud browser can read this public repository
and its issue without sharing the signed-in Chrome session.

Review the actual before/after test output and patch. Keep the Daytona sandbox
for inspection; publishing a fix or closing the issue is a separate action.
