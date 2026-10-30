<h1 align="center">汉字侠 · Hanzi Wanderer</h1>

<p align="center"><b>A runner game where every fight is a Chinese word.</b><br>
All 300 words of HSK 3, six regions of China, twenty-one creatures from Chinese folklore, and one very rude demon king.</p>

<p align="center"><img src="docs/regions.png" alt="The six regions of the campaign: Great Wall in autumn, Xi'an city wall at dusk, Dunhuang dunes, Chengdu bamboo forest, Guilin karst peaks, Shanghai Bund at night" width="860"></p>

---

## The story

很久很久以前，天下说同一种话。
*Long, long ago, all under heaven spoke one language.*

A merchant in Beijing could haggle with a fisherman in Guilin. A poet in Xi'an could be insulted by a critic in Shanghai and understand every word of it. Things were fine.

Then **混世魔王 Hùnshì Mówáng**, the Demon King of Chaos, got hold of the jade seal that held the language together, and broke it.

The country cracked into six pieces. The words scattered like spilled ink. Within a week, a man in Shanghai said 侬好, a woman in Guangzhou answered 雷猴, someone from Beijing tried 你好, and all three stared at each other in silence.

The Emperor sent for the only person still walking the roads: you, a wanderer in a straw hat. His request was short.

侠客，请你帮忙！
*Wanderer, help us.*

Three hundred words are missing. Each region hides fifty of them, guarded by the creatures that crawled out of the cracks: hopping corpses, fox spirits, water ghosts, terracotta soldiers who decided to go for a walk, and at the end of every road, a boss who plays dirty.

Win the words back, region by region, and the map heals. Lose, and you can always try again. The Demon King isn't going anywhere. (Well. He will. But he says he'll be back, and he mentions HSK 4.)

<p align="center"><img src="docs/story.png" alt="The six scenes of the opening story" width="760"></p>

---

## What it is actually for

Hanzi Wanderer is a vocabulary trainer for the **HSK 3** exam, dressed up as a game.

Your character runs on their own. When something blocks the road, a word appears and you pick its meaning out of four. Answer fast and you hit hard; answer wrong and you get hit. That's the whole loop, and it's deliberately small so you can play five minutes on a bus.

### Why it works better than a deck of flashcards

**It covers exactly what the exam covers.** All 300 HSK 3 words (HSK 2.0 list), split into six campaign stages of 50. Nothing extra to wade through, nothing missing.

**Speed matters, the way it does in a real conversation.** Answer within a quarter of the timer for triple damage, within half for double. Knowing a word "eventually" is not the same as knowing it, and the game makes you feel the difference.

**Wrong answers teach you four words, not one.** After every question, all four choices flip over and show their hanzi and pinyin. The distractors are real HSK 3 words too, so a miss still teaches you something.

**The questions are fair.** Every English meaning was rewritten so two answers can never both look right (老 is *old, in age*; 旧 is *old, not new*). Close pairs like 担心 / 着急 or 口 / 嘴 never appear in the same question.

**It remembers what you get wrong.** Missed words come back more often. The **错题本 Book of Shame** keeps a permanent record of every mistake: how often you missed a word, what you thought it meant ("You said *to be afraid* ×3"), and whether you've redeemed yourself since. A **雪耻 Redemption run** drills only those words until each one earns its 洗白 *Redeemed* stamp (three right in a row).

<p align="center"><img src="docs/book-of-shame.png" alt="The Book of Shame listing missed words with miss counts and stamps" width="640"></p>

**Bosses test different skills.** Each region's boss bends the rules, and the rules stack as you go:

| Trick | What it does | What it trains |
|---|---|---|
| 吼 Roar | Removes the pinyin | Reading the characters, not the romanization |
| 吞 Devour | Eats one answer, and sometimes it's the right one | Knowing a word well enough to pick the blank card |
| 火 Heat | 6-second timer | Instant recall |
| 缠 Coil | Answers swap places mid-question | Reading, not remembering positions |
| 镜 Mirror | English prompt, hanzi answers | Telling similar characters apart |
| 潮 Tide | A new combination every question | Everything at once |

<p align="center"><img src="docs/bosses.png" alt="Boss fights against the Taotie, the Ba serpent, the flood dragon and the Dragon King of the East Sea" width="760"></p>

**It sneaks in culture.** The 21 creatures in the **图鉴 bestiary** come from Chinese folklore and *Journey to the West*. Each one has its name broken down character by character (白骨精 = 白 white + 骨 bone + 精 spirit), a short story, and a "Hear it" button. You pick up words like 鬼, 龙 and 王 without trying.

<p align="center"><img src="docs/bestiary.png" alt="The bestiary with creatures grouped by region" width="680"></p>

**There's a reason to come back.** Coins (铜钱) from fights buy new characters: a panda, Zhu Bajie, Sun Wukong (whose staff grows all the way to the enemy) and the Laughing Buddha.

<p align="center"><img src="docs/shop.png" alt="The shop with five playable characters" width="680"></p>

### What it doesn't do (yet)

To be clear, the game trains **recognition**, which is the easiest part of knowing a word. It doesn't train writing, tones, listening without text, or sentences. HSK 3 also has a lot of grammar words (把, 被, 越…越…) that are best learned in context. Those are the next things on the list.

---

## Playing it

There's nothing to install.

- **On a computer:** download `index.html` and open it in any modern browser.
- **On a phone:** put the file on any static host (GitHub Pages, Netlify Drop, etc.) and open the link. Opening the raw file from a phone's file manager often won't run it.

Controls: tap or click an answer, or press **1–4**. **P** or **Esc** pauses.

Your progress (coins, characters, bestiary, mistakes) is saved in your browser. It stays between sessions, but it's per browser and per copy of the game. Clearing site data or using a private window wipes it.

The voice uses your device's built-in speech engine, so you need a Chinese voice installed. Most phones and Macs have one already.

---

## How it's built

The whole game is **one HTML file**, about 170 KB and 2,600 lines. No framework, no build step, no image files. If you can open a text editor, you can mod it.

### Under the hood

- **Everything you see is drawn in code.** The characters, creatures, six regional backdrops and story scenes are all drawn with the Canvas 2D API. Every creature is one function that takes a scale and a time value and paints itself, so the same code draws it in battle, in the bestiary portrait and in the cutscenes.
- **Backgrounds scroll in layers.** Each region is a stack of layers (sky, far mountains, landmarks, near ground) that move at different speeds. Mountains, dunes and bamboo come from simple sine curves and a seeded hash, so the road looks endless without storing anything.
- **Only the essentials come from outside.** The fonts load from Google Fonts (Ma Shan Zheng, Noto Serif SC, Barlow Semi Condensed), and the game falls back to system fonts offline. Speech uses the browser's Web Speech API, and the sound effects are synthesized with the Web Audio API.
- **Saving uses localStorage.** Everything is one JSON object under a single key, wrapped in try/catch so the game still runs where storage is blocked.

### Map of the code

Everything lives inside one `<script>`:

| Section | What's there |
|---|---|
| `WORDS` | The 300 words as `hanzi\|pinyin\|meaning` lines |
| `CONFUSE` | Near-synonym pairs that must never share a question |
| `REGIONS` | The six campaign stops: map position, theme, boss, flavour text |
| `FOES` | The 21 creatures: stats, rarity, region, lore, character breakdown, boss tricks, draw function |
| `SKINS` | Playable characters and their draw functions |
| `STORY` | Intro and ending scenes: text, pinyin, and a draw function per scene |
| Game loop | `requestAnimationFrame` drives `update(dt)` and `draw()`; delays go through a small timer queue so pausing freezes everything |
| Question engine | Weighted word picking (misses count more), distractor selection, boss tricks |
| Scenes | One function per region (`sceneBeijing`, `sceneXian`, …), plus shared helpers for layers, ground and weather |

### Adding things

- **A creature:** write a `drawSomething(s, t, moving)` function that draws it facing left with its feet at `(0,0)`, then add an entry to `FOES` with its region (`where`), stats and lore. It appears in battles and in the bestiary automatically.
- **A character:** write a `skinSomething(...)` function facing right and add it to `SKINS` with a price.
- **A region:** add a scene function, an entry in `REGIONS` and a boss.

### Testing

During development, the game was checked with Playwright in headless Chromium. Scripts took screenshots at desktop and phone sizes, and a bot that always answers correctly played full stages, boss fights and the ending, to catch broken flows and script errors.

---

## Credits

- **Vocabulary:** the HSK 3 list (HSK 2.0) as published on [hsk.academy](https://hsk.academy/en/hsk-3-vocabulary-list). The English meanings were rewritten for this game.
- **Folklore:** *Journey to the West*, the *Classic of Mountains and Seas*, and Chinese folk tradition. All creature and character artwork is original and drawn in code.
- **Fonts:** Ma Shan Zheng, Noto Serif SC and Barlow Semi Condensed, all under the SIL Open Font License, served by Google Fonts.

## License

*To be decided.* The current proposal is:

- **Code:** MIT License
- **Story, lore texts and artwork:** [Creative Commons Attribution-ShareAlike 4.0](https://creativecommons.org/licenses/by-sa/4.0/)

Creative Commons licenses are written for creative works, not software, so the code gets a software license and everything else gets CC.
