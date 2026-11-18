# linux-kernel-contributions

A collection of kernel patches submitted by me for the Linux kernel mainline driver tree.

---

### 1. `drivers/mfd/dln2.c` — Clean up dln2_unregister_event_cb() loop logic
* **Status:** Applied ([Lore Thread](https://lore.kernel.org/mfd/179381522079.1916138.4679305340156782083.b4-ty@b4/T/#u))
* **Detection Tool:** Coccinelle (`scripts/coccinelle/iterators/use_after_iter.cocci`)
* **Category:** Iterator Scope
* **Summary:** Refactored `dln2_unregister_event_cb()` to eliminate post-loop usage of the list iterator variable `i`. Introduced an `entry` pointer to capture the entry inside the lock scope prior to freeing, preventing potential use-after-free conditions and removing redundant state booleans.

---

### 2. `drivers/staging/vme.c` — avoid iterator variable access outside list loop
* **Status:** Currently in [mainline](https://github.com/torvalds/linux/commit/ac086c03d031832ea3f1cf6c306812b50355c770)
* **Detection Tool:** Coccinelle (`scripts/coccinelle/iterators/use_after_iter.cocci`)
* **Category:** Iterator Scope
* **Summary:** Independently identified and drafted a [fix](https://lore.kernel.org/linux-staging/20261012034020.100737-1-oliva.scorza@gmail.com/). Audit confirmed it was discovered a [week prior](https://lore.kernel.org/linux-staging/20261005042911.64922-1-marinela.selseth@firmwaredesign.org/), validating the analysis methodology and finding.
