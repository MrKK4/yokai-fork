## 2024-05-19 - [LazyColumn Optimization]
**Learning:** In Jetpack Compose, using `list.forEach { item { ... } }` inside a `LazyColumn` forces Compose to treat each element as an individual unkeyed item, leading to unnecessary recompositions and node re-creations when the list updates. Replacing it with `items(items = list, key = { it.stableId }) { ... }` ensures efficient list item recycling.
**Action:** Always verify loops inside `LazyColumn` or `LazyRow` and replace them with `items()` or `itemsIndexed()` leveraging stable keys.
