---
name: salesforce-admin
description: Enforce Salesforce admin best practices when creating or modifying custom fields, objects, or metadata
user-invocable: false
---

When creating or modifying Salesforce custom fields or objects, always follow these steps:

## Before Creating a Field
- Confirm the field type is appropriate for the data being stored
- Ask if the field should be required

## Field-Type-Specific Questions

### Master-Detail
- Ask for the Child Relationship Name
- Ask about the Sharing Setting: minimum access level on the Master record to create/edit/delete Detail records (Read Only or Read/Write)
- Ask if Allow Reparenting should be enabled (allowing child records to be moved to other parent records)
- Ask if there are any lookup filters

### Lookup
- Ask what to do if the lookup record is deleted:
  - Clear the value of this field (not available if the field is required)
  - Don't allow deletion of the lookup record
- Ask if there are any lookup filters

## Permissions
- Ask which profiles and/or permission sets should have Read or Edit access to the new field
- Add field-level security (FLS) entries for the appropriate profiles/permission sets

## Page Layouts
- Ask which page layout(s) the field should be added to
- Confirm placement/section on the layout
- Layout must contain an item for required layout fields

## Checklist Before Done
2. Field-level security is set for relevant profiles/permission sets
3. Field is added to the correct page layout(s) in the right section
4. If a picklist — values are confirmed
5. If a lookup/master-detail — relationship and sharing implications are considered