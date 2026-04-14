## 2025-04-13 - Optimize map+flatten to flatMap
**Learning:** Found several instances of `.map { ... }.flatten()` being used across various components in the Android application. In Kotlin, using `map` followed by `flatten` creates an unnecessary intermediate collection.
**Action:** Replaced these occurrences with `.flatMap { ... }` which is functionally equivalent but avoids allocating an intermediate collection, improving memory efficiency and saving processing cycles.

## 2024-05-24 - Avoid `forEach { item { ... } }` in LazyColumn
**Learning:** In Jetpack Compose, using `forEach { item { ... } }` inside a `LazyColumn` instead of the `items()` extension creates a separate `item` declaration for every element. This prevents Compose from treating the items as a single list of dynamically recycled elements, leading to increased memory usage and degraded scrolling performance. Furthermore, it prevents the use of `key`s for efficient recomposition when the list changes.
**Action:** Always use `items(myList)` (or `itemsIndexed`) instead of iterating over a list to manually create individual `item` blocks, and provide a stable `key` parameter whenever possible.
