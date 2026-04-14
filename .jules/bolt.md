## 2025-04-13 - Optimize map+flatten to flatMap
**Learning:** Found several instances of `.map { ... }.flatten()` being used across various components in the Android application. In Kotlin, using `map` followed by `flatten` creates an unnecessary intermediate collection.
**Action:** Replaced these occurrences with `.flatMap { ... }` which is functionally equivalent but avoids allocating an intermediate collection, improving memory efficiency and saving processing cycles.
