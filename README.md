# ideas-for-cpython
Tracking my ideas &amp; rationales for contributions to CPython

## [contextvars](https://docs.python.org/3/library/contextvars.html)
- [x] Create and reuse one context for the entire asyncio REPL session (python/cpython#124595)
- [ ] Correct documentation for [HAMT](https://github.com/python/cpython/blob/8fbf10d6cfd9c69ffcc1f80fa0c5f33785197af7/Python/hamt.c) members of `contextvars.Context` (`.keys()`, `.values()`, `.items()`)
  - [ ] **TODO:** Check if python/cpython#124773 doesn't fix this)
  - [ ] To correct: those members don't return lists, they return immutable sequences over keys/items/values
- [ ] Make HAMT support set-like operations like dict views (`&`, `|` etc.)
  - [ ] **TODO:** Read the HAMT implementation and see if it's feasible and theoretically correct
