# zz-items

Administrative/debug/catharsis item set for Enhanced Edition Infinity Engine cleanup.

Intentionally unbalanced. Not for proper playthroughs.

## Scope

This is a single WeiDU mod with game-specific item/spell templates.

Supported variants currently intended:

* BG2EE
* IWDEE

Each game installs its own `.ITM` and `.SPL` resources from a separate directory:

```text
zz-items/
  lang/
    english.tra
  bg2/
    *.ITM
    *.SPL
  iwd/
    *.ITM
    *.SPL
```

The installed resource names are shared, but the templates are not required to be identical.

## Why game-specific templates?

Enhanced Edition games share an engine family, but not identical resources, strings, animations, encounter assumptions, or threat profiles.

BG2EE may justify broader protection from no-save/no-MR nonsense.

IWDEE generally needs less paranoia; most hostile effects are expected to be handled by extreme saves, magic resistance, or recovery tools.

This package is not currently a fully pruned opcode-minimal design. It is a working fossil/archive.

## Items

### `ZZSTICK` — The Bonker

A.k.a. The Murderstick.

Quarterstaff/admin weapon.

* main mode: 40-ft melee reach, 100 blunt damage, dispel rider, and no-save/no-MR slay rider
* alternate mode: proper ranged weapon mode with beholder-ray projectile, 10 magic damage, and dispel rider
* APR set to 5; with Improved Haste applied, it becomes 10

Special abilities:

* instant visibility / illusion revocation: `ZZSTICKO.SPL`
* instant visible-area enemy summon cleanup and dispel magic without level check
* instant visible-area enemy slay, no save, no magic resistance

### `ZZHEAD` — Halo of Certainty

Admin headgear for improvement of active abilities.

* constant Improved Alacrity while worn
* -10 casting speed improvement
* +100% wild surge bonus
* +6 to all spell slots, arcane or divine where applicable
* all thieving skill bonuses +100, stealth +200
* viewing distance set to 23, near the engine's practical maximum
* luck, infravision, Non-Detection

Special abilities include instant wish-grade rest, map reveal, invisibility, and Knock. Knock is not instant.

### `ZZBODY` — Garment of Immunity

Admin armor/body slot item.

* AC set to engine minimum of -20, with additional -20 AC modifiers for each damage type
* saving throws get -20 bonus
* magic resistance +200%, capped by the engine to 127%
* all other resistances set to 100%
* minimum hit point / ability score safety
* immunity to fatigue
* immunity to normal and magical weapons
* immunity to Time Stop
* high movement bonuses
* protection from known no-save/no-MR nonsense; this can vary between games
* aim was to protect the wearer from all non-scripted disabling or reload-forcing effects
* instant cleanse: Heal, Greater Restoration, and self-dispel reset

Exact protection details may differ between BG2EE and IWDEE templates.

## Installation

Install with WeiDU.

The mod chooses the correct resource directory based on the target game.

There is no in-game quest, store, drop, or balanced placement. Use console as any proper admin should do.

## Console injection

After installation, add the items manually by console:

```baf
C:CreateItem("ZZSTICK")
C:CreateItem("ZZHEAD")
C:CreateItem("ZZBODY")
```

## Warnings

These tools can break scripted encounters.

Do not use lethal or area-processing abilities before required dialogue, transformations, surrender states, phase changes, journal updates, death scripts, or quest variables have completed.

Keep pre-area saves.

Known risks:

* killing bosses too quickly;
* skipping trigger regions;
* preventing death-watch scripts from arming;
* interrupting encounter state transitions;
* processing a quest actor before the script clerk has stamped the papers.

If a fight matters for progression, let the encounter initialize before administrative cleanup.

## Status

Private/personal alpha archive.

BG2EE is the primary/refined variant.

IWDEE was useful for private cleanup but may contain redundant or imperfect effects.

This is not a polished public balance package, nor will ever be.
