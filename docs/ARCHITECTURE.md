# System Architecture Analysis

Detailed analysis of the Andy Bogard (andy_ss) character's fight mode, skills, animations, and counter-party systems for MUGEN.

---

## 1. Character Fight Modes

The character supports **three modes** configurable via `!config.cns` (Statedef 10000, helper 9999):

| Mode | var(15) | Description |
|------|---------|-------------|
| **Normal Mode** | 0 | Standard KOF-style moveset |
| **Classic Mode** | 1 | Alternate/retro moveset |
| **Shadow Mode** | 2 | Dark-themed variant |

Mode selection affects:
- Special intros (Shadow mode excludes Terry, Mai, Tung Fu Rue intros)
- Victory poses
- Palette/FX (Fire vs. normal coloring)
- Some move availability

---

## 2. CNS File Architecture

| File | Purpose | Key Statedefs |
|------|---------|---------------|
| `!config.cns` | Global config, parent vars, helper 9999 | 10000 |
| `Andy.cns` | Main states (stand, crouch, walk, jump, normals, hits, throws) | 0–995, 5000–7210, 9999, 10100, 20000+ |
| `Andy-N.cns` | Normal mode states (normals, specials) | 200, 1000+ |
| `Andy-S.cns` | Shadow mode states | — |
| `Andy-H.cns` | Super/Desperation moves | 3000+ |
| `Andy-EX.cns` | EX moves | 1050–1065, 1150–1171, 2050–2070, 2150–2160 |
| `Andy-2.cns` | Secondary/helper states, debug, tag logic | -2, -3 |

### Config Helper (Statedef 10000)

- **var(15)**: Mode (0=Normal, 1=Classic, 2=Shadow)
- **var(32)**: Precede input time (special) — default 6F
- **var(33)**: Precede input time (super) — default 12F
- **var(34–36)**: Air guard flags (ground, air/proj, self)
- **var(37)**: Screen flash (0=off, 1=on)
- **var(49)**: Injected skills (0=off, 1=on)
- **var(50)**: AI startup (0=off)
- **var(51–53, 59)**: AI combo/guard/level/frequency

---

## 3. State Machine Overview

### Core States (Andy.cns)

| State | Type | Description |
|-------|------|-------------|
| 0, 1 | Stand | Idle, AI turn |
| 10, 11 | Crouch | Crouch start, crouch |
| 20 | Walk | Forward walk |
| 30 | AI walk | AI-controlled forward |
| 40–52 | Jump | Jump variants (neutral, forward, back, small/medium/large) |
| 100–106 | Crouch attacks | Crouch light/heavy |
| 120–192 | Standing attacks | Standing normals |
| 500–540 | Hit states | Ground hit, knockdown |
| 700–750 | Throws | Throw states |
| 900–995 | Hit reactions | Ground/air hit, knockdown |
| 5050–5150 | KO/Death | Death states |
| 5600–5715 | Special moves | Zan-ei Ken, Hisho Ken, etc. |
| 7000–7210 | Super helpers | Super move helpers |
| 9999 | Helper | Main config helper |
| 10100 | Misc | — |
| 20000 | Tag | Tag team |
| 200100, 200110 | Tag/Climax | — |

### Special Move States (Statedef → Skill)

| Statedef | Skill | Animation |
|----------|-------|-----------|
| 1000–1010 | Zan-ei Ken (斬影拳) | Projectile |
| 1050–1065 | EX Zan-ei Ken (EX斬影拳) | Projectile |
| 1150–1171 | Gen-ei Shiranui (幻影不知火) | Air special |
| 2050–2070 | Gen-ei Shiranui Hiei (幻影不知火・飛影) | Air special |
| 2150–2160 | Gen-ei Shiranui Bakushin (幻影不知火・爆震) | EX air |
| 3000+ | Cho Reppa Dan (超裂破弾) | DM |

---

## 4. Skill System & Animation Mapping

### Special Moves (必殺技)

| Skill | Japanese | Command | Statedef | Counter/Notes |
|-------|----------|---------|----------|---------------|
| Zan-ei Ken | 斬影拳 | DB,F + X/Y | 1000, 1010 | SC possible |
| Hisho Ken | 飛翔拳 | D,DB,B + X | 1000 | Projectile |
| Geki Hisho Ken | 激・飛翔拳 | D,DB,B + Y | 1000 | Projectile |
| Shoryu Dan | 昇龍弾 | F,D,DF + X/Y | 1050–1065 (EX) | SC |
| Kuha Dan | 空破弾 | B,DB,D,DF,F + A/B | — | Brake: X+A |
| Gen-ei Shiranui | 幻影不知火 | D,DF,F + A/B (air) | 1150–1171 | Uwa/Shimo follow-ups |
| Gen-ei Shiranui Hiei | 幻影不知火・飛影 | D,DB,B + A/B | 2050–2070 | Uwa/Shimo follow-ups |
| Yami Abisegeri | 闇・浴びせ蹴り | F,D,DF + A/B | — | — |

### EX Special Moves (EX必殺技)

| Skill | Japanese | Command | Statedef |
|-------|----------|---------|----------|
| Zan-ei Ken Ugachi | 斬影拳・穿 | DB,F + X+Y | 1050 |
| Zatsu Hisho Ken | 絶・飛翔拳 | D,DB,B + X+Y | 1050 |
| Bakushin | 爆震 | D,DF,F + A+B (air) | 2150 |
| Yami Abisegeri Kai | 闇・浴びせ蹴り・改 | F,D,DF + A+B | — |

### Desperation Moves (超必殺技)

| Skill | Japanese | Command | Statedef |
|-------|----------|---------|----------|
| Cho Reppa Dan | 超裂破弾 | D,DB,B,DB,D,DF,F + A/B | 3000 |
| Bakuretsu Tensho Ken | 爆裂天翔拳 | D,DB,B,DB,D,DF,F + X/Y | — |
| Dan Da Dan | 男打弾 | D,DF,F,D,DF,F + X/Y (mash) | — |

### MAX / CLIMAX

| Skill | Japanese | Command |
|-------|----------|---------|
| Zetsu Reppa Dan | 絶・裂破弾 | D,DB,B,DB,D,DF,F + A+B |
| Zan-ei Reppa | 斬影裂破 | D,DB,B,DB,D,DF,F + X+Y |
| Cho Shinsoku Zan-ei Ken | 超・神・速・斬影拳 | D,DB,B,DB,D,DF,F + Y+B |

---

## 5. Animation Counter Parties

| Animation | Related States | Counter Parties |
|-----------|----------------|-----------------|
| Stand (0–6) | 0, 1, 11 | Turn, facing |
| Crouch (10–12) | 10, 11 | Crouch attacks |
| Walk (20–21) | 20 | Run |
| Jump (40–47) | 40–52 | Jump attacks |
| Zan-ei Ken (1000–1010) | 1000, 1010 | Projectile helper |
| EX Zan-ei (1050–1065) | 1050, 1060 | Projectile, hit override |
| Gen-ei Shiranui (1150–1171) | 1150–1171 | Uwa/Shimo follow-ups |
| Gen-ei Hiei (2050–2070) | 2050–2070 | Uwa/Shimo follow-ups |
| Cho Reppa Dan (3000) | 3000 | Super helper 7000 |

### Counter-Party Logic

- **Chain Cancel**: Normal → Special → Super chain possible
- **Super Cancel (SC)**: Special moves can cancel into super when SC flag set
- **Guard Cancel**: X+A during guard (1 power) for blow-off; Y+B for super cancel
- **Power MAX**: 1 power to enable SC; 2 for MAX super; 3 for CLIMAX
- **Combo scaling**: Each hit reduces damage; max reduction 20% (normal), 40% (super), 50% (CLIMAX)

---

## 6. Special Intros & Interactions

| Opponent | Condition |
|----------|-----------|
| Terry Bogard | Special intro (except Shadow) |
| Mai Shiranui | Special intro (except Shadow) |
| Tung Fu Rue | Special intro (except Shadow) |
| Geese Howard | Special intro |

### Potential Ability (潜在能力) — Special Clash

When both moves hit:
- **Terry Bogard**: Buster Wolf
- **Andy Bogard**: Cho Shinsoku Zan-ei Ken
- **Geese Howard**: Deadly Rave

---

## 7. Variable Reference (var/fvar)

See [TRANSLATION.md](TRANSLATION.md) for full variable table. Key vars:

| var | Purpose |
|-----|---------|
| var(0) | Follow-up判定 |
| var(1) | Command判定 |
| var(2) | Opponent ID (for special intros) |
| var(10–13) | Cancel flags |
| var(15) | Mode |
| var(32–33) | Precede input times |
| var(34–37) | Air guard, flash |
| var(50–59) | AI |
