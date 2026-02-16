# Translation Reference

This document contains translations of all non-English comments found in CNS, CMD, DEF, and related text files. Original Japanese text (Shift-JIS/CP932) is preserved for reference.

---

## CNS / CMD Comment Translations

### Andy.cns — State Section Headers

| Original (Shift-JIS) | English |
|---------------------|---------|
| スタンド | Stand |
| しゃがみ開始 | Crouch start |
| しゃがみ | Crouch |
| 前歩き | Walk forward |
| AI用前進 | AI forward |
| ジャンプ | Jump |
| 速度 | Velocity |
| 死亡時 | On death |
| AI起動 | AI start |
| ターン向き | Turn facing |
| ステージ変更 | State change |
| 効果音 | Sound effect |
| アニメ | Animation |
| 相手喰らい | Opponent hit |
| 着地 | Landing |
| 追撃 | Follow-up |
| 無敵 | Invincible |
| 変数 | Variable |
| 攻撃判定 | Attack判定 |
| 攻撃判定発生前 | Before attack判定 |
| 相手判定 | Opponent判定 |
| 空中喰らい | Air hit |
| 吹っ飛び | Hitstun |
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

### Andy.cns — Jump States

| Original | English |
|----------|---------|
| ジャンプ開始 | Jump start |
| 終了 | End |
| 通常ジャンプ | Normal jump |
| 前ジャンプ | Forward jump |
| 後ジャンプ | Back jump |
| 前小ジャンプ | Forward small jump |
| 前中ジャンプ | Forward medium jump |
| 前大ジャンプ | Forward large jump |
| 後小ジャンプ | Back small jump |
| 後中ジャンプ | Back medium jump |
| 後大ジャンプ | Back large jump |
| 残像 | Afterimage |
| 重力 | Gravity |
| 座標 | Position |
| 結果 | Result |

### !config.cns — Config Section

| Original | English |
|----------|---------|
| コンフィグ | Config |
| 無モード | No mode |
| 0で通常モード | 0 = Normal mode |
| 1でクラシックモード | 1 = Classic mode |
| 2でシャドウモード | 2 = Shadow mode |
| 先行入力受付時間 必殺技 | Precede input time (special) |
| 先行入力受付時間 超必殺技 | Precede input time (super) |
| 地上技・超必殺技空中ガード | Ground/super air guard |
| 空中技・飛び道具空中ガード | Air/projectile air guard |
| 自分空中ガード | Self air guard |
| 画面フラッシュ | Screen flash |
| パワー倍率 | Power magnification |
| 計算解放 | Injected skills |
| AI起動時 | AI start |
| AIコンボレベル | Combo level |
| AIガードレベル | Guard level |
| AI通常レベル | AI level |
| 行動頻度 | Frequency level |
| 相手変身時Pal | Opponent transform Pal |
| 設定方法 | Config method |
| 炎(強) | Fire (strong) |
| 炎 | Fire |
| 赤緑 | Red/Green |
| パワー[MAXゲージ x座標 | Power MAX gauge X |
| パワー[MAXゲージ y座標 | Power MAX gauge Y |
| パートナーが選択時 | When partner selected |

### Andy-H.cns — Super Moves

| Original | English |
|----------|---------|
| 超裂破弾 | Cho Reppa Dan (Super Raging Wave) |
| 超必殺技演出 | Super move effect |
| スーパーキャンセル | Super cancel |

### Andy-EX.cns — EX Moves

| Original | English |
|----------|---------|
| EX飛翔拳 | EX Hisho Ken |
| EX必殺技演出 | EX special move effect |
| 座標 | Position |
| 飛び道具 | Projectile |
| 攻撃判定発生前 | Before attack判定 |
| 終了 | End |
| 速度 | Velocity |
| 通常補正 | Normal scaling |
| アニメ判定 | Animation判定 |

### Andy-2.cns — Helper / Debug

| Original | English |
|----------|---------|
| 起動時デバッグ | Startup debug |
| クリップボード | Clipboard |
| 喰らい判定 | Hit判定 |
| タグ用変数 | Tag variables |
| ヒット判定 | Hit判定 |
| ヒット判定発生前 | Before hit判定 |

### Andy-N.cns — Normal Mode

| Original | English |
|----------|---------|
| 通常時上段パンチ | Normal upper punch |
| 攻撃判定 | Attack判定 |
| 攻撃判定発生前 | Before attack判定 |

---

## Andy.cmd — Command Name Translations

### Command Section Headers

| Original | English |
|----------|---------|
| キャラクター設定 | Character config |
| デフォルト設定 | Default config |
| AIコマンド | AI command |
| 個別起動用 | Individual startup |
| AI専用用 | AI专用 |
| タグチーム | Tag team |
| CLIMAX超必殺技 | CLIMAX super |
| MAX超必殺技 | MAX super |
| 超必殺技 | Desperation move |
| EX必殺技 | EX special move |
| 必殺技 | Special move |
| 連続入力受付 | Combo input |
| 受け身 | Recovery |
| 通常ループ技 | Normal loop |

### Skill Names (Command → English)

| Original | Romaji | English |
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
| 飛翔拳 上 | Hisho Ken (upper) | — |
| 飛翔拳 強 | Hisho Ken (strong) | — |
| 空破弾 上 | Kuha Dan (upper) | — |
| 空破弾 強 | Kuha Dan (strong) | — |
| 斬影拳・穿 | Zan-ei Ken Ugachi | — |
| 絶・飛翔拳 | Zatsu Hisho Ken | — |
| 爆震 | Bakushin | — |
| 闇・浴びせ蹴り・改 | Yami Abisegeri Kai | — |
| 剛臨・改 | Gourin Kai | — |
| 抱え込み投げ | Kakaekomi Nage | — |
| 緊急回避 | Emergency evasion |
| 吹っ飛ばし攻撃 | Blow off |
| ガードキャンセル | Guard cancel |
| 挑発 | Taunt |
| 受け身 | Recovery |
| パワー | Power |
| ゲージ | Gauge |
| 交換 | Tag |
| アタック | Attack |
| フルパワーコンボ | Full Power Combo |

### Command / Config Terms

| Original | English |
|----------|---------|
| 上げ面 | Agemen (Upper face) |
| 上顎 | Uwa Agito (Upper jaw) |
| 下顎 | Shimo Agito (Lower jaw) |

---

## Variable Reference (変数表.txt)

### var() — Integer Variables

| var | Original | English |
|-----|----------|---------|
| var(0) | 追撃判定 | Follow-up判定 |
| var(1) | コマンド判定 | Command判定 |
| var(2) | 相手判別 | Opponent ID |
| var(3) | カウンター判定 | Counter判定 |
| var(4) | 全必殺技ヒット時パターン | All special hit pattern |
| var(5) | ヒットパターン x座標 | Hit pattern X |
| var(6) | ヒットパターン y座標 | Hit pattern Y |
| var(7) | ヒットタイプ | Hit type |
| var(8) | ヒットタイプ | Hit type |
| var(9) | ヒットフレーム | Hit frame |
| var(10) | キャンセル特殊技 | Cancel special |
| var(11) | キャンセル必殺技 | Cancel special move |
| var(12) | スーパーキャンセル可能 | Super cancel possible |
| var(13) | スーパーキャンセル | Super cancel |
| var(14) | ヒット判定 | Hit判定 |
| var(15) | モード | Mode |
| var(16) | パワーMAX判定 | Power MAX判定 |
| var(17) | パートナー数 | Partner count |
| var(18) | パートナー起動数 | Partner startup count |
| var(19) | パートナー終了数 | Partner end count |
| var(20) | 必殺全必殺技発動可能判定 | Special all-special possible |
| var(21) | 超必全必殺技発動可能判定 | Super all-special possible |
| var(22) | 相手判定 | Opponent判定 |
| var(25) | 相手キャンセル可能判定 | Opponent cancel possible |
| var(26) | 相手PalFX赤 | Opponent PalFX R |
| var(27) | 相手PalFX緑 | Opponent PalFX G |
| var(28) | 相手PalFX青 | Opponent PalFX B |
| var(30) | パワー[MAXゲージ x座標 | Power MAX gauge X |
| var(31) | パワー[MAXゲージ y座標 | Power MAX gauge Y |
| var(32) | 先行入力受付時間 必殺技 | Precede input time (special) |
| var(33) | 先行入力受付時間 超必殺技 | Precede input time (super) |
| var(34) | 地上技空中ガード可能 | Ground air guard |
| var(35) | 空中技・飛び道具空中ガード可能 | Air/proj air guard |
| var(36) | 自分空中ガード可能 | Self air guard |
| var(37) | 画面フラッシュ | Screen flash |
| var(40) | 一回使用変数@ | One-time use var |
| var(41) | 一回使用変数A | One-time use var |
| var(50) | AI起動時発動 | AI startup |
| var(51) | AIコンボレベル | AI combo level |
| var(52) | AIガードレベル | AI guard level |
| var(53) | AI通常レベル | AI level |
| var(55) | AIコンボ指定 | AI combo指定 |
| var(56) | AI行動指定 | AI action指定 |
| var(57) | AI行動判定 | AI action判定 |
| var(58) | AI用ステート | AI state |
| var(59) | AI行動頻度 | AI frequency |

### fvar() — Float Variables

| fvar | Original | English |
|------|----------|---------|
| fvar(0) | コンボ補正 | Combo scaling |
| fvar(1) | コンボ補正係数 | Combo scaling factor |
| fvar(2) | パワー[MAX効果音時間 | Power MAX sound time |
| fvar(3) | パワー[MAX攻撃力倍率 | Power MAX attack rate |
| fvar(4) | パワー倍率 | Power magnification |
| fvar(5) | 係数補正 | Coefficient correction |
| fvar(6) | 立って挑発時 | Stand taunt |

---

## txt/readme.txt (Japanese — Shift-JIS)

Full content translated. See [txt/readme.txt](../txt/readme.txt) for original. Key sections:

- **Character**: Andy Bogard (アンディ・ボガード)
- **Modes**: Normal, Classic, Shadow (configurable)
- **Special Intros**: Terry, Mai, Tung Fu Rue, Geese
- **Taunt (気力充実)**: Reduces opponent power vs. Art of Fighting team
- **Potential Ability (潜在能力)**: Special clash moves
- **User Policy**: MUGEN use only, free to edit, do not redistribute without edit

---

## txt/技表・解説.txt (Move List — Japanese)

- **通常技**: Normal moves
- **特殊技**: Special moves
- **必殺技**: Special moves (Zan-ei Ken, Hisho Ken, etc.)
- **EX必殺技**: EX special moves
- **超必殺技**: Desperation moves
- **MAX超必殺技**: MAX desperation
- **CLIMAX超必殺技**: CLIMAX super

---

## txt/更新履歴.txt (Update History)

See [log.md](log.md) for full translated changelog.
