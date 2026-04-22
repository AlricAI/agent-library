# SPONSORSHIP TOUR

> This document provides detailed documentation for sponsorship and tour management tools.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Sponsorship & Tour Management Toolsets

This document provides detailed documentation for sponsorship and tour management tools.

## Sponsorship Manager Tools

| Tool Name             | Description                                  | Status |
| --------------------- | -------------------------------------------- | ------ |
| `sponsor_research`    | Research and identify potential sponsors     | Active |
| `create_sponsor_read` | Generate personalized sponsor advertisements | Active |
| `track_performance`   | Monitor sponsor campaign performance         | Active |
| `generate_report`     | Create performance reports for sponsors      | Active |

---

## sponsor_research

Researches and identifies potential sponsors based on target demographics and budget.

### Parameters

| Parameter             | Type   | Required | Description                  |
| --------------------- | ------ | -------- | ---------------------------- |
| `target_demographics` | array  | Yes      | Target audience demographics |
| `budget_range`        | object | Yes      | Budget constraints           |
| `excluded_categories` | array  | No       | Categories to exclude        |

### Example Usage

```json
{
  "target_demographics": ["18-34", "comedy fans", "urban"],
  "budget_range": { "min": 5000, "max": 50000 },
  "excluded_categories": ["alcohol", "gambling"]
}
```

---

## create_sponsor_read

Generates personalized sponsor advertisements based on sponsor information.

### Parameters

| Parameter           | Type   | Required | Description                      |
| ------------------- | ------ | -------- | -------------------------------- |
| `sponsor_info`      | object | Yes      | Sponsor details and requirements |
| `integration_style` | enum   | Yes      | Style of sponsor integration     |
| `duration`          | number | Yes      | Target duration in seconds       |

### Integration Styles

- `host_read` - Host reads ad naturally during episode
- `produced_ad` - Pre-produced advertis

*[truncated — see source for full prompt]*