## Common Pitfalls

### Overloading the Root File
One common mistake is adding too many rules to the root `claude.md` file. Since this file is loaded by default in every session, keeping it lean is crucial to avoid unnecessary token usage. Instead, point to other resource files only when the situation calls for it.

### Misclassification
Another pitfall is misclassifying transactions or tasks. For example, categorizing Canva as freelancer instead of software can lead to inaccurate spending trackers. Correcting these misclassifications ensures accurate future classifications.

### Repeating Rules
Avoid repeating the same rule in multiple files. For example, if your root `voice_principles.md` file includes rules like 'no corporate jargon,' do not restate those rules in workstation-specific `claude.md` files. Instead, focus on task-specific preferences.

### Ignoring Session Audits
Failing to regularly audit sessions can result in unsaved principles and preferences. Use the `{forward slash} session audit` prompt to scan the conversation and capture any unsaved information.