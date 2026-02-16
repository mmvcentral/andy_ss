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

## Documentation Index

All related documentation is indexed in [docs/INDEX.md](docs/INDEX.md).

| Document | Description |
|----------|-------------|
| [docs/INDEX.md](docs/INDEX.md) | Full documentation index |
| [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md) | System architecture, fight modes, skills, animations |
| [docs/TRANSLATION.md](docs/TRANSLATION.md) | Japanese → English translation reference |
| [docs/log.md](docs/log.md) | Creator update history (changelog) |
| [docs/HISTORY.md](docs/HISTORY.md) | Alternate changelog format |

---

## File Structure

| File | Description |
|------|-------------|
| [andy_ss.def](andy_ss.def) | Character definition |
| [Andy.cns](Andy.cns) | Main states |
| [Andy-N.cns](Andy-N.cns) | Normal mode states |
| [Andy-S.cns](Andy-S.cns) | Shadow mode states |
| [Andy-H.cns](Andy-H.cns) | Super/Desperation moves |
| [Andy-EX.cns](Andy-EX.cns) | EX moves |
| [Andy-2.cns](Andy-2.cns) | Secondary/helper states |
| [!config.cns](!config.cns) | Global config |
| [Andy.cmd](Andy.cmd) | Command definitions |
| [Andy.air](Andy.air) | Animation definitions |
| [txt/readme.txt](txt/readme.txt) | Original readme (Shift-JIS) |
| [txt/更新履歴.txt](txt/更新履歴.txt) | Update history (Japanese) |
| [txt/技表・解説.txt](txt/技表・解説.txt) | Move list (Japanese) |
| [txt/Eng/Move List.txt](txt/Eng/Move List.txt) | English move list |
| [txt/Eng/User Policy.txt](txt/Eng/User Policy.txt) | Usage policy |

---

## System Architecture Summary

### Character Fight Modes

| Mode | var(15) | Description |
|------|---------|-------------|
| **Normal Mode** | 0 | Standard KOF-style moveset |
| **Classic Mode** | 1 | Alternate/retro moveset |
| **Shadow Mode** | 2 | Dark-themed variant |

For detailed architecture (skills, animations, counter parties), see [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md).

---

## Special Intros & Interactions

| Opponent | Condition |
|----------|-----------|
| Terry Bogard | Special intro (except Shadow) |
| Mai Shiranui | Special intro (except Shadow) |
| Tung Fu Rue | Special intro (except Shadow) |
| Geese Howard | Special intro |

### Taunt (気力充実) Compatibility

When using the creator's "気力充実" (Spirit Charge) system, taunting reduces opponent power by 1/2 bar against:

- Ryo Sakazaki, 2nd Mr. KARATE, Robert Garcia, EX Robert Garcia, Takuma Sakazaki, Mr. KARATE, Mr. BIG

### Potential Ability (潜在能力)

Special clash when both moves hit:

- **Terry Bogard:** Buster Wolf
- **Andy Bogard:** Cho Shinsoku Zan-ei Ken
- **Geese Howard:** Deadly Rave

---

## User Policy

- For M.U.G.E.N use only.
- Free to edit.
- Do not redistribute without edit.
- If edited and released, include this txt.

---

## Credits

- **SNK** – Original character
- **Elecbyte** – M.U.G.E.N engine
- **Soy Sauce (しょうゆ)** – Character creation
- **kong** – Sprite usage
- **Scal** – Sprite usage
- **アンディ** – Reference
- **てつや** – Graphics, sprites, system reference

---

## License

### Creative Circle License

This character is an **edition from the original author** (Soy Sauce) and is released under the **Creative Circle License**.

This MUGEN character is a fan-made adaptation of Andy Bogard from *Fatal Fury* and *The King of Fighters*. All original character designs, names, and related intellectual property belong to **SNK Corporation**.

- This work is distributed as a **Creative Circle** (同人サークル) work—a fan-made adaptation of the original game character.
- The original creator (Soy Sauce) retains rights to the MUGEN implementation.
- Use and distribution should respect the original author's terms and the MUGEN community guidelines.
- For commercial or extensive derivative use, please contact the original creator.
