## 2024-10-24 - Moko Resources vs Android Resources for A11y
**Learning:** When adding `contentDescription`s for screen reader accessibility in Compose, this app uses Moko Resources (`dev.icerock.moko.resources.compose.stringResource` with `yokai.i18n.MR`) for app-specific strings, which conflicts with Android's native `androidx.compose.ui.res.stringResource` (used for `android.R` strings like 'OK'/'Cancel').
**Action:** If using both in the same file, explicitly use fully qualified imports (e.g., `androidx.compose.ui.res.stringResource`) for Android resources to prevent compilation errors.
