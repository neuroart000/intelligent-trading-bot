# Test

**Time:** ~30 minutes  
**Goal:** Apply the changes below. You don’t need to run the full pipeline or the server; fixing the code and running the tests is enough.

---

## Task 1: Fix shutdown bug in the server (≈5 min)

In **`service/server.py`**, in the `finally` block at the end of `start_server`:

- One condition uses the wrong reference for the Binance venue. Fix it so the comparison uses the `Venue` enum (same style as the MT5 check on the next line).

**File:** `service/server.py` (around line 285)

---

## Task 2: Use the returned health-check function (≈5 min)

In **`service/server.py`**, the code gets `health_check_fn` from `get_collector_functions(venue)` but never uses it.

- In **`main_collector_task`**: replace the call that runs the “data provider” health check with a call to the function returned by `get_collector_functions` (so the correct venue’s health check runs).
- In **`start_server`** (initial health check before the scheduler): use that same returned function instead of the current call.

**Files:** `service/server.py` (around lines 96 and 199)

---

## Task 3: Fix venue comparisons in inputs (≈5 min)

In **`inputs/__init__.py`**, the comparisons use `venue.BINANCE` and `venue.MT5` (attribute on the variable). Use the `Venue` enum so it’s clear and consistent (e.g. `Venue.BINANCE`, `Venue.MT5`).

**File:** `inputs/__init__.py`

---

## Task 4: Sync dependencies and add one sentence to README (≈10 min)

- Ensure **`requirements.txt`** and **`pyproject.toml`** list the same core packages and version ranges (no new optional packages required; just align what’s already there).
- In the main **`README.md`**, add one sentence that tells readers where to find dependency/version notes (point to **`docs/dependency-updates.md`**).

---

## Task 5: Add a short CHANGELOG entry (≈2 min)

In **`CHANGELOG.md`**, under the current version (e.g. `v0.8.dev`), add a line describing the fixes from Tasks 1–3 (e.g. “Fix server shutdown venue check; use venue-specific health check; fix Venue enum usage in inputs”).

---

## Done

- Run **`pytest tests/`** and make sure all tests pass.
- You’re not required to install or run Binance/MT5/Telegram; passing tests are sufficient.
