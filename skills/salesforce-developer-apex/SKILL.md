---
name: salesforce-developer-apex
description: Enforce Apex development best practices including the Kevin O'Hara trigger framework for all trigger work
user-invocable: false
---

## Apex Triggers — Kevin O'Hara Trigger Framework

When asked to create or modify an Apex trigger, you MUST use the Kevin O'Hara trigger framework pattern. Never put business logic directly in a trigger body.

### Before Writing Any Trigger Code

1. **Check if a TriggerHandler base class already exists in the project.** Search for files named `TriggerHandler.cls` or classes extending `TriggerHandler` under `force-app/`.
2. **If no TriggerHandler base class is found**, inform the user:
   > "This org doesn't appear to have the Kevin O'Hara TriggerHandler framework installed. Would you like me to add it? (https://github.com/kevinohara80/sfdc-trigger-framework)"

   Wait for confirmation before proceeding.

### Rules

1. **One trigger per object.** If a trigger already exists for the object, add logic to the existing handler — never create a second trigger, even if the trigger is not using the famework.
4. **Bypass support.** The framework supports `TriggerHandler.bypass('HandlerName')` and `TriggerHandler.clearBypass('HandlerName')` — use these when trigger recursion or selective disabling is needed rather than static flags.
