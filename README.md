---
title: "Templating"
description: "Creation-time templates and render-time body templating with Handlebars"
id: "diaryx.templating"
version: "0.1.0"
author: "Diaryx Team"
license: "PolyForm Shield 1.0.0"
repository: "https://github.com/diaryx-org/plugin-templating"
categories: ["productivity", "editor"]
tags: ["templates", "handlebars", "workflow"]
capabilities: ["workspace_events", "custom_commands"]
artifact:
  url: ""
  sha256: ""
  size: 0
  published_at: ""
ui:
  - slot: SettingsTab
    id: templating-settings
    label: "Templates"
  - slot: EditorExtension
    id: templateVariable
  - slot: EditorExtension
    id: conditionalBlock
  - slot: BlockPickerItem
    id: templating-if-else
    label: "If / Else"
  - slot: BlockPickerItem
    id: templating-for-audience
    label: "For Audience"
---

# diaryx_templating_extism

Extism WASM guest plugin that provides all templating functionality for Diaryx.

## Overview

This plugin owns creation-time and render-time templating end-to-end:

- list, get, save, and delete workspace templates
- render body templates (Handlebars engine) for `{{#if}}`, `{{#for-audience}}`, etc.
- fast-path `HasTemplates` check for body content
- render creation-time templates with `{{variable}}` substitution
- editor extensions via `Builtin` manifest type for TemplateVariable and ConditionalBlock

## Commands

- `ListTemplates` — list workspace and built-in templates
- `GetTemplate` — get template content by name
- `SaveTemplate` — save template to workspace `_templates/` folder
- `DeleteTemplate` — delete a workspace template
- `RenderBody` — render body templates with Handlebars for a given body + frontmatter
- `HasTemplates` — fast-path check for `{{` in body
- `RenderCreationTemplate` — render a creation-time template with variable substitution

## Exports

- `manifest`
- `init`
- `shutdown`
- `handle_command`
- `get_config`
- `set_config`
- `on_event`

## Build

```bash
cargo build -p diaryx_templating_extism --target wasm32-unknown-unknown --release
```
