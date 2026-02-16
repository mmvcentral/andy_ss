# Andy Bogard (アンディ・ボガード)

## Character Introduction

**Andy Bogard** is a character from SNK's *Fatal Fury* (餓狼伝説) and *The King of Fighters* series. He is the younger brother of Terry Bogard and a practitioner of the Shiranui-ryuu Ninjutsu (不知火流忍術) martial art style. Andy is known for his calm, disciplined personality and his rivalry with his brother Terry. He trained under the legendary ninja master Hanzo Shiranui and later became engaged to Mai Shiranui, Hanzo's granddaughter.

### Original Creator

- **MUGEN Creator:** Soy Sauce (しょうゆ)
- **Contact:** soysaucemugen1@gmail.com
- **Twitter:** https://twitter.com/soysaucemugen1

### Character Storyline (Fatal Fury / KOF)

Andy Bogard is the younger brother of Terry Bogard. After their father Jeff Bogard was killed by Geese Howard, Andy left South Town to train in Japan under the Shiranui-ryuu Ninjutsu master Hanzo Shiranui. Unlike Terry's street-fighting style, Andy uses a refined ninjutsu-based martial art combining strikes, throws, and ki-based projectiles. He has appeared in every King of Fighters tournament, often teaming with his brother and Joe Higashi as the "Fatal Fury Team."

---

## File Structure & Related Documentation

> **Documentation index:** See [docs/INDEX.md](docs/INDEX.md) for a full index of all related files.  
> **Changelog:** See [docs/HISTORY.md](docs/HISTORY.md) for the original creator's update history.

| File | Description |
|------|-------------|
| [docs/INDEX.md](docs/INDEX.md) | Full documentation index |
| [docs/HISTORY.md](docs/HISTORY.md) | Changelog (original creator) |
| [txt/readme.txt](txt/readme.txt) | Original Japanese readme (Shift-JIS) |
| [txt/更新履歴.txt](txt/更新履歴.txt) | Update history / Changelog (Japanese) |
| [txt/技表・解説.txt](txt/技表・解説.txt) | Move list & skill explanations (Japanese) |
| [txt/技表・解説(クラシック).txt](txt/技表・解説(クラシック).txt) | Classic mode move list |
| [txt/技表・解説(シャドウ).txt](txt/技表・解説(シャドウ).txt) | Shadow mode move list |
| [txt/変数表.txt](txt/変数表.txt) | Variable reference table |
| [txt/Eng/Move List.txt](txt/Eng/Move List.txt) | English move list |
| [txt/Eng/User Policy.txt](txt/Eng/User Policy.txt) | Usage policy |
| [txt/Eng/Injected Moves.txt](txt/Eng/Injected Moves.txt) | Config-injectable moves |

---

## System Architecture Analysis

### Character Fight Modes

The character supports **three modes** (configurable via `!config.cns`):

| Mode | var(15) | Description |
|------|---------|-------------|
| **Normal Mode** | 0 | Standard KOF-style moveset |
| **Classic Mode** | 1 | Alternate/retro moveset |
| **Shadow Mode** | 2 | Dark-themed variant |

### CNS File Architecture

| File | Purpose | Key Statedefs |
|------|----------|---------------|
| `!config.cns` | Global config, parent vars, helper 9999 | 10000 |
| `Andy.cns` | Main states | 0–995, 5000–7210, 9999, 10100, 20000+ |
| `Andy-N.cns` | Normal mode states | 200, 1000+ |
| `Andy-S.cns` | Shadow mode states | — |
| `Andy-H.cns` | Super/Desperation moves | 3000+ |
| `Andy-EX.cns` | EX moves | 1050–1065, 1150–1171, 2050–2070, 2150–2160 |
| `Andy-2.cns` | Secondary/alternate states | -2, -3 |

### State Machine Overview

#### Core States (Andy.cns)

| State | Type | Description |
|-------|------|-------------|
| 0, 1 | Stand | Idle, AI turn |
| 10, 11 | Crouch | Crouch start, crouch |
| 20 | Walk | Forward walk |
| 30 | AI walk | AI-controlled forward |
| 40–52 | Jump | Jump variants (neutral, forward, back, etc.) |
| 100–106 | Crouch attacks | Crouch light/heavy |
| 120–192 | Standing attacks | Standing normals |
| 500–540 | Hit states | Ground hit, knockdown |
| 700–750 | Throws | Throw states |
| 900–995 | Hit reactions | Ground/air hit, knockdown |
| 5050–5150 | KO/Death | Death states |
| 5600–5715 | Special moves | Zan-ei Ken, Hisho Ken, etc. |
| 5900 | — | Misc |
| 6080–6081 | — | Misc |
| 7000–7210 | Super helpers | Super move helpers |
| 9999 | Helper | Main config helper |
| 10100 | — | Misc |
| 20000 | Tag | Tag team |
| 200100, 200110 | — | Tag/climax |

#### Special Move States (Statedef → Skill)

| Statedef | Skill | Animation |
|----------|-------|-----------|
| 1000–1010 | Zan-ei Ken (斬影拳) | Projectile |
| 1050–1065 | EX Zan-ei Ken (EX斬影拳) | Projectile |
| 1150–1171 | Gen-ei Shiranui (幻影不知火) | Air special |
| 2050–2070 | Gen-ei Shiranui Hiei (幻影不知火・飛影) | Air special |
| 2150–2160 | Gen-ei Shiranui Bakushin (幻影不知火・爆震) | EX air |
| 3000+ | Cho Reppa Dan (超裂破弾) | DM |

### Skill System & Animation Mapping

#### Special Moves (必殺技)

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

#### EX Special Moves (EX必殺技)

| Skill | Japanese | Command | Statedef |
|-------|----------|---------|----------|
| Zan-ei Ken Ugachi | 斬影拳・穿 | DB,F + X+Y | 1050 |
| Zatsu Hisho Ken | 絶・飛翔拳 | D,DB,B + X+Y | 1050 |
| Bakushin | 爆震 | D,DF,F + A+B (air) | 2150 |
| Yami Abisegeri Kai | 闇・浴びせ蹴り・改 | F,D,DF + A+B | — |

#### Desperation Moves (超必殺技)

| Skill | Japanese | Command | Statedef |
|-------|----------|---------|----------|
| Cho Reppa Dan | 超裂破弾 | D,DB,B,DB,D,DF,F + A/B | 3000 |
| Bakuretsu Tensho Ken | 爆裂天翔拳 | D,DB,B,DB,D,DF,F + X/Y | — |
| Dan Da Dan | 男打弾 | D,DF,F,D,DF,F + X/Y (mash) | — |

#### MAX / CLIMAX

| Skill | Japanese | Command |
|-------|----------|---------|
| Zetsu Reppa Dan | 絶・裂破弾 | D,DB,B,DB,D,DF,F + A+B |
| Zan-ei Reppa | 斬影裂破 | D,DB,B,DB,D,DF,F + X+Y |
| Cho Shinsoku Zan-ei Ken | 超・神・速・斬影拳 | D,DB,B,DB,D,DF,F + Y+B |

### Animation Counter Parties

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

### Variable Reference (var/fvar)

| var | Japanese | English |
|-----|----------|---------|
| var(0) | 追撃判定 | Follow-up判定 |
| var(1) | コマンド判定 | Command判定 |
| var(2) | 相手判別 | Opponent ID |
| var(3) | カウンター判定 | Counter判定 |
| var(10) | キャンセル特殊技 | Cancel special |
| var(11) | キャンセル必殺技 | Cancel special move |
| var(12) | スーパーキャンセル可能 | Super cancel possible |
| var(13) | スーパーキャンセル | Super cancel |
| var(14) | ヒット判定 | Hit判定 |
| var(15) | モード | Mode |
| var(32) | 先行入力受付時間 必殺技 | Precede input time (special) |
| var(33) | 先行入力受付時間 超必殺技 | Precede input time (super) |
| var(34) | 地上技空中ガード可能 | Ground air guard |
| var(35) | 空中技・飛び道具空中ガード可能 | Air/proj air guard |
| var(36) | 自分空中ガード可能 | Self air guard |
| var(37) | 画面フラッシュ | Screen flash |

---

## Japanese Translation Table

### CNS / CMD Comment Translations

| Japanese | English |
|----------|---------|
| スタンド | Stand |
| しゃがみ | Crouch |
| 速度 | Velocity |
| 死亡時 | On death |
| AI起動 | AI start |
| ターン向き | Turn facing |
| ダッシュ | Dash |
| 前歩き | Walk forward |
| AI用前進 | AI forward |
| ジャンプ | Jump |
| 通常ジャンプ | Normal jump |
| 前ジャンプ | Forward jump |
| 後ジャンプ | Back jump |
| 変数 | Variable |
| 効果音 | Sound effect |
| 速度 | Velocity |
| 無敵 | Invincible |
| ステート変更 | State change |
| 座標 | Position |
| アニメ | Animation |
| 攻撃判定 | Attack判定 |
| 攻撃判定発生前 | Before attack判定 |
| 相手判定 | Opponent判定 |
| 相手喰らい | Opponent hit |
| 空中喰らい | Air hit |
| 吹っ飛び | Hitstun |
| 着地 | Landing |
| 追撃 | Follow-up |
| 必殺技 | Special move |
| 超必殺技 | Desperation move |
| スーパーキャンセル | Super cancel |
| キャンセル可能 | Cancelable |
| 飛び道具 | Projectile |
| 連続技 | Combo |
| コンボ補正 | Combo scaling |
| 没技 | Cut/injected moves |
| 先行入力 | Precede input |
| 受付時間 | Reception time |
| 没技解放 | Injected moves unlock |
| 没技オフ | Injected off |
| 没技オン | Injected on |

### Skill Names (Japanese → English)

| Japanese | Romaji | English |
|----------|--------|---------|
| 斬影拳 | Zan-ei Ken | Slash Shadow Fist |
| 飛翔拳 | Hisho Ken | Flying Strike |
| 激・飛翔拳 | Geki Hisho Ken | Fierce Flying Strike |
| 昇龍弾 | Shoryu Dan | Rising Dragon |
| 空破弾 | Kuha Dan | Air Break |
| 幻影不知火 | Gen-ei Shiranui | Phantom Shiranui |
| 幻影不知火・飛影 | Gen-ei Shiranui Hiei | Phantom Shiranui Hiei |
| 幻影不知火・爆震 | Gen-ei Shiranui Bakushin | Phantom Shiranui Explosion |
| 闇・浴びせ蹴り | Yami Abisegeri | Dark Shower Kick |
| 超裂破弾 | Cho Reppa Dan | Super Raging Wave |
| 爆裂天翔拳 | Bakuretsu Tensho Ken | Explosive Heaven Strike |
| 男打弾 | Dan Da Dan | Male Strike |
| 絶・裂破弾 | Zetsu Reppa Dan | Absolute Raging Wave |
| 斬影裂破 | Zan-ei Reppa | Slash Shadow Raging Wave |
| 超・神・速・斬影拳 | Cho Shinsoku Zan-ei Ken | Super God-Speed Slash Shadow |

### Command / Config Terms

| Japanese | English |
|----------|---------|
| 上げ面 | Agemen (Upper face) |
| 上顎 | Uwa Agito (Upper jaw) |
| 下顎 | Shimo Agito (Lower jaw) |
| 剛臨・改 | Gourin Kai |
| 抱え込み投げ | Kakaekomi Nage |
| 緊急回避 | Emergency evasion |
| 吹っ飛ばし攻撃 | Blow off |
| ガードキャンセル | Guard cancel |
| スーパーキャンセル | Super cancel |
| 挑発 | Taunt |
| 受け身 | Recovery |
| パワー | Power |
| ゲージ | Gauge |
| 先行入力 | Precede input |
| 受付時間 | Reception time |

---

## Update History (Changelog)

Translated from original `txt/更新履歴.txt`:

| Date | Changes |
|------|---------|
| 2020/03/08 | Initial release |
| 2020/03/09 | Fixed WinMugen effect positions; EX Gekiheki Haisui Sho usable when injected off; fixed crouch light kick hitbox |
| 2020/03/10 | Zan-ei Ken voice change; M3 Tremo-man EX Zan-ei hit fix; EX Shoryu Dan / Hisho Ken voice; Zatsu Hisho Ken damage tweaks; Cho Shinsoku Zan-ei Ken invincibility; Yami Abisegeri / Cho Shinsoku command notation |
| 2020/03/11 | IKEMEN jump fix; air guard config fix; GC blow-off invincibility; P throw follow-up fix; Geki Hisho Ken air hit fix; Kuha Dan tweaks; Gen-ei Hiei corner fix; Cho Reppa Dan sprite; Dan Da Dan effect; victory pose fix; AI added |
| 2020/03/23 | P throw KO fix; Agemen damage; Zan-ei Ken / Hisho Ken distance; Geki Hisho Ken tweaks; EX Hisho Ken persistence; Gen-ei Hiei corner; Gen-ei auto-turn; Bakushin KO fix; Yami Abisegeri SC disabled; MAX Cho Reppa / Zetsu Reppa sprites; Zan-ei Reppa / Bakuretsu Tensho Ken hitbox; Zan-ei Reppa weak → Hisho Reppa; Shadow intro fix; victory pose fix |
| 2020/04/13 | Back step special move fix; projectile hit gauge fix; Guile config |
| 2020/05/10 | Ryu config; special intro fix |
| 2020/07/09 | Ken config |
| 2020/08/22 | Vega config |
| 2020/09/12 | Brainwashed Ken config; special victory pose fix |
| 2020/11/29 | Krauser config; down smoke effect |
| 2021/04/05 | Iori config |
| 2021/11/03 | Jump auto-turn fix |
| 2023/09/02 | Kyo renewal config; KO camera fix |
| 2023/09/03 | WinMugen compatibility fix |

---

## Special Intros & Interactions

| Opponent | Condition |
|----------|-----------|
| Terry Bogard | Special intro (except Shadow) |
| Mai Shiranui | Special intro (except Shadow) |
| Tung Fu Rue | Special intro (except Shadow) |
| Geese Howard | Special intro |

## Taunt (気力充実) Compatibility

When using the creator's "気力充実" (Spirit Charge) system, taunting reduces opponent power by 1/2 bar against:

- Ryo Sakazaki, 2nd Mr. KARATE, Robert Garcia, EX Robert Garcia, Takuma Sakazaki, Mr. KARATE, Mr. BIG

## Potential Ability (潜在能力)

Special clash when both moves hit:

- **Terry Bogard:** Buster Wolf
- **Andy Bogard:** Cho Shinsoku Zan-ei Ken
- **Geese Howard:** Deadly Rave

## User Policy

- For M.U.G.E.N use only.
- Free to edit.
- Do not redistribute without edit.
- If edited and released, include this txt.

## Credits

- **SNK** – Original character
- **Elecbyte** – M.U.G.E.N engine
- **Soy Sauce (しょうゆ)** – Character creation
- **kong** – Sprite usage
- **Scal** – Sprite usage
- **アンディ** – Reference
- **てつや** – Graphics, sprites, system reference
