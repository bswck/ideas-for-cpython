# ideas-for-cpython
Tracking my ideas &amp; rationales for contributions to CPython

## [contextvars](https://docs.python.org/3/library/contextvars.html)
- [x] Create and reuse one context for the entire asyncio REPL session (python/cpython#124595)
  **Rationale:** It's a bug and doesn't let asyncio REPL users present contextvars correctly.
  **Cost/Benefit**: Low cost, easy fix. A significant benefit—correct, intuitive behavior.
- [ ] Correct documentation for [HAMT](https://github.com/python/cpython/blob/8fbf10d6cfd9c69ffcc1f80fa0c5f33785197af7/Python/hamt.c) members of `contextvars.Context` (`.keys()`, `.values()`, `.items()`)
  **Rationale:** The documentation is misleading as is.
  **Cost/Benefit**: Low cost, easy fix. A little but enough benefit—better documentation
  - [ ] **TODO:** Check if python/cpython#124773 doesn't fix this
  - [ ] To correct: those members don't return lists, they return immutable sequences over keys/items/values
- [ ] Make HAMT support set-like operations like dict views (`&`, `|` etc.)
  **Rationale:** Being able to validate PEP 567 contexts against a known set of required context variables. 
  **Cost/Benefit**: High cost and an uneasy fix (remember we can just do `set(context.keys()) & ...`). Low benefit—there are other, working ways.
  - [ ] **TODO:** Read the HAMT implementation and see if it's feasible and theoretically correct

## New REPL
- [ ] Fix `python -I -i -m asyncio` behavior
  **Rationale:** It's buggy!
  **Cost/Benefit**: High cost and an uneasy fix (remember we can just do `set(context.keys()) & ...`). High benefit—correct behavior and a supported way of testing the asyncio REPL.
