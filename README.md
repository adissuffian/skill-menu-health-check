# Menu Health Check Skill

A GitHub Copilot skill for checking whether Domino's staging menus are up or down across supported markets.

## What It Does

This skill guides Copilot through the staging order flow for one or more Domino's markets and reports whether the menu is available.

Supported markets include:
- AU
- NZ
- JP
- FR
- BE
- DE
- NL
- LU
- SG
- MY
- TW

## Repo Structure

```text
menu-health-check/
  SKILL.md
  references/
    market-test-data.md
```

## Install

Copy the `menu-health-check` folder into one of the supported Copilot skill locations.

Project-scoped locations:
- `.github/skills/menu-health-check/`
- `.agents/skills/menu-health-check/`
- `.claude/skills/menu-health-check/`

User-scoped locations:
- `~/.copilot/skills/menu-health-check/`
- `~/.agents/skills/menu-health-check/`
- `~/.claude/skills/menu-health-check/`

The final layout must keep the folder name and skill name aligned:

```text
.github/skills/menu-health-check/SKILL.md
```

## Requirements

- VS Code with GitHub Copilot Chat
- Browser automation support available to the agent
- Access to Domino's staging environments
- VPN or internal network access if required by the stage URLs

## How To Run

In Copilot Chat, invoke the skill directly:

```text
/menu-health-check AU
/menu-health-check AU NZ
/menu-health-check all
```

You can also use natural language if your setup allows automatic skill discovery, for example:

```text
Check menu health for AU and NZ in staging.
Check all Domino's staging markets and report which menus are down.
```

## What The Skill Checks

For each requested market, the skill:
1. Opens the market's stage homepage
2. Selects Pick Up or Delivery
3. Enters test location data
4. Selects a store
5. Selects an order time
6. Verifies whether the menu loads successfully

## Output

The skill returns a summary like this:

```text
| Market | Status | Notes |
|--------|--------|-------|
| AU     | UP     |       |
| NZ     | DOWN   | Timeout loading store list |
```

## Notes

- Market-specific test data is in `menu-health-check/references/market-test-data.md`
- The skill uses staging URLs only
- Some markets may have localized UI labels and layouts
