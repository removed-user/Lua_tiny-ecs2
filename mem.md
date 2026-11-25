Memory traits:
Traits attatched to entities - such as:
Lifetime:
   - vault
   - cache
   - churn
Layout:
   - SoA
   - AoS
   - Pool
Mutability:
   - frozen
   - mutable

BackingStore: Compacted flat tables



1.
`mem.label(target, category, opts)`
Attaches a lightweight metadata tag to a table or module registry before compaction (leaving its runtime behavior unchanged until commit).
2.
`mem.commit()` — Runs the mini-ECS migration pass after libraries finish loading: flattens labeled structures into optimal layouts, swaps the original tables in-place into lightweight proxies, and triggers a full GC sweep to reclaim startup fragmentation.
3.
`mem.step(category)` / `mem.reset(category)` — Advances lifecycle systems (like flushing "churn" pools at the end of a frame or pruning "cache" buckets).
