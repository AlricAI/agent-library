# Speech

> ---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
draft: true
type: "upcoming" # or "past"
location: ""
description: ""
---

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
draft: true
type: "upcoming" # or "past"
location: ""
description: ""
---