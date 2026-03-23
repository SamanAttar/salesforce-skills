---
name: salesforce-devops
description: Automatically maintain package.xml and enforce deployment best practices whenever Salesforce metadata files are created, modified, or deleted
user-invocable: false
---

Whenever you create, rename, or delete any Salesforce metadata file in this project, you MUST update the `manifest/package.xml` to stay in sync. This is a **blocking requirement** — never leave package.xml stale.

## Metadata-Type Mapping

When a file is created or deleted under `force-app/`, determine its metadata type from the path and add/remove the corresponding `<members>` entry in `package.xml`:

## Rules

1. **Always read `manifest/package.xml` before editing it** — never assume its current contents.
2. **Keep `<members>` entries sorted alphabetically** within each `<types>` block.
3. **Keep `<types>` blocks sorted alphabetically** by their `<name>` element.
4. **When adding a new metadata type**, create a new `<types>` block in the correct sorted position.
5. **When removing the last member of a type**, remove the entire `<types>` block.
6. **Never duplicate entries** — check before adding.
7. **The `<version>` element** must always match the project's `sourceApiVersion` in `sfdx-project.json`.
8. **On file deletion**, remove the corresponding member. If the `<types>` block becomes empty, remove it entirely.

## Validation

After updating `package.xml`, verify:
- Every metadata file under `force-app/main/default/` has a corresponding entry
- No entries reference files that don't exist
- XML is well-formed with proper indentation (4 spaces)
