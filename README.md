# Salesforce Skills for AI Coding Agents

A collection of reusable AI agent skills that enforce Salesforce best practices across admin configuration, Apex development, and DevOps workflows.

## Philosophy

These skills are intentionally concise. They are not meant to be an exhaustive reference for everything an AI agent should know about Salesforce — the models already have that knowledge. Instead, these skills are a curated set of guardrails for the things agents commonly forget, skip, or get wrong. Think of them as corrections and reminders, not tutorials.

## Compatible Tools

These skills work with any AI coding agent that supports skill/instruction files:

- **Claude Code** (Anthropic)
- **Windsurf** (Codeium)
- **Cursor**
- **GitHub Copilot**
- **Agentforce** (Salesforce)
- **Cline**
- **Aider**
- **Amazon Q Developer**
- **Tabnine**
- **JetBrains AI Assistant**
- **Sourcegraph Cody**

## Skills Included

### Salesforce Admin (`salesforce-admin`)
Enforces best practices when creating or modifying custom fields, objects, and metadata — including field-level security, page layout placement, and relationship configuration.

### Salesforce Apex Developer (`salesforce-developer-apex`)
Enforces Apex development best practices including the [Kevin O'Hara trigger framework](https://github.com/kevinohara80/sfdc-trigger-framework). Prevents business logic in trigger bodies and ensures one-trigger-per-object.

### Salesforce DevOps (`salesforce-devops`)
Automatically maintains `package.xml` in sync with metadata changes. Enforces sorted entries, correct metadata-type mapping, and validates consistency on every file create, rename, or delete.

## Installation (Claude Code)

Copy the skill folders into your Claude skills directory:

```bash
cp -r skills/* ~/.claude/skills/
```

## Installation (Other Tools)

Copy the relevant `SKILL.md` content into your tool's instruction/rules file (e.g., `.cursorrules`, `.windsurfrules`, `.github/copilot-instructions.md`, or equivalent).

## License

MIT
