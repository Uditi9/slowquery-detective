# slowquery-detective 🕵️

Point it at a PostgreSQL log (with `log_min_duration_statement` set) and it groups queries by fingerprint, ranks them by total time, and suggests starter indexes. Zero dependencies.

```bash
pip install -e .
slowquery postgres.log
```
```
 #  calls   total ms    avg ms    max ms  query
 1      2     2000.5    1000.2    1200.5  SELECT * FROM orders WHERE user_id = ? AND status = ?
    hint: CREATE INDEX ON orders (user_id, status);
```

Hints are heuristics. Always confirm with `EXPLAIN ANALYZE`.

Test: `python -m unittest discover -s tests` (set `PYTHONPATH=src`).
