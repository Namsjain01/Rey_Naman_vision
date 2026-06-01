# Rey Mindu — Interactive HTML Build Brief
### For Claude Code | Prepared for Naman Jain, Sarvahitey

---

## 0. How to use this file

Naman: drop this file into your project folder in VS Code, alongside an `assets/` folder
containing the images and video (see Section 4). Then open Claude Code in that folder and say:

> "Read REY_MINDU_BUILD_BRIEF.md and build the site exactly as specified. Look at every image
> in /assets before writing any code, so the layout fits the actual photos. Ask me before
> inventing any content that isn't in the brief."

Claude Code: this brief is the source of truth for **content**. Do not rewrite the philosophy,
invent new sections, or paraphrase the quoted passages — use the text as given. You have full
freedom over **craft**: layout, motion, typography execution, and polish.

---

## 1. What this is

A single-page interactive website that lets people **see** the vision for Rey Mindu rather than
read it in a document. Rey Mindu is a Lepcha village in East Sikkim being shaped into a mindful
living village — a mental well-being destination grounded in living Kagyu Buddhist and Lepcha
tradition, **not** a generic wellness resort.

**Primary audience:** the core project team and partners (people who already believe in the
project and need to see it expressed clearly), plus first-time viewers who need full context.
Build it so it works for someone encountering Rey Mindu for the first time.

**What it must do:** make the viewer feel the spirit of the place and understand how every
space connects to one common thread — mental well-being, witnessed through *thongdrol*
(liberation through seeing), *darshan* (reciprocal seeing), and *pang* (to witness).

---

## 2. Technical requirements

- **One self-contained `index.html`** with CSS and JS inline (or a tiny `/assets` folder for
  media only). Must open by double-clicking the file AND be hostable as-is (Netlify drop,
  GitHub Pages, etc.).
- **No build step, no frameworks required.** Vanilla HTML/CSS/JS, or a single CDN import if
  genuinely needed. Must work offline once assets are local.
- **Fully responsive** — looks right on a laptop and a phone. Most people will be shown this
  on a phone or in a screen-share.
- **No browser storage APIs** (localStorage/sessionStorage). Keep all state in memory.
- Smooth, performant. Lazy-load images. Compress the video reference if large.

---

## 3. Flow & interaction model

**A mix of scroll and click.** The site is divided into distinct chapters. The viewer **clicks
to move between chapters** (a fixed side or top nav, or large next/prev controls), and **scrolls
within** each chapter to move through its content. Think of each chapter as a "room" you enter,
then move through.

- A persistent, quiet navigation showing the chapters (see Section 5 for the list).
- **No loud opening animation.** The user explicitly does not want drama. Let the first image
  and one line of text do the work. Calm entry.
- Gentle scroll-reveal (fade/rise) is welcome. Nothing flashy.
- Each chapter should feel like a held space, not a slide in a pitch deck.

---

## 4. Assets — setup and mapping

The source files live in this folder (note the **trailing spaces** in the folder names — they
are real and must be kept exactly):

```
/Users/namsjain/Desktop/08_Ongoing_Projects/Ray Village /Videos and picture for HTML /
```

Claude Code: **do not ask Naman to rename anything.** Run the copy block below to pull each file
into a clean `/assets` folder inside the project with web-safe names, then build against the
clean names. (Spaces and special characters in the original filenames will break on the web,
which is why we copy-and-rename rather than reference them in place.)

### Copy block — run this first (macOS / zsh)

```bash
mkdir -p assets
SRC="/Users/namsjain/Desktop/08_Ongoing_Projects/Ray Village /Videos and picture for HTML "

cp "$SRC/Screenshot 2026-06-01 at 4.07.30 PM.png"  assets/monastery-far.png      # monastery, far / hero
cp "$SRC/Screenshot 2026-06-01 at 4.08.09 PM.png"  assets/monastery-near.png     # monastery, outer near
cp "$SRC/Screenshot 2026-06-01 at 4.08.01 PM.png"  assets/monastery-inside.png   # monastery, inside
cp "$SRC/Screenshot 2026-06-01 at 4.08.17 PM.png"  assets/monk-bell.png          # monk ringing a bell
cp "$SRC/Screenshot 2026-06-01 at 4.08.28 PM.png"  assets/meditation-room.png    # meditation room by monastery
cp "$SRC/Screenshot 2026-06-01 at 4.08.38 PM.png"  assets/wds-room.png           # WDS room
cp "$SRC/Screenshot 2026-06-01 at 4.09.14 PM.png"  assets/hall-now.png           # 12-room hall, current
cp "$SRC/Screenshot 2026-06-01 at 4.19.15 PM.png"  assets/hall-vision.png        # 12-room hall, what it becomes
cp "$SRC/Screenshot 2026-06-01 at 4.13.43 PM.png"  assets/paint-room.png         # paint-throwing room
cp "$SRC/Screenshot 2026-06-01 at 4.16.12 PM.png"  assets/pottery.png            # pottery section
cp "$SRC/Screenshot 2026-06-01 at 4.08.51 PM.png"  assets/fishing-1.png          # fishing spot
cp "$SRC/Screenshot 2026-06-01 at 4.09.02 PM.png"  assets/fishing-2.png          # fishing spot
cp "$SRC/VIDEO-2026-04-16-11-06-18.mp4"            assets/unbecoming.mp4         # breaking video

# Village map (note: different sub-folder — "For mapping ", with a trailing space)
MAP="/Users/namsjain/Desktop/08_Ongoing_Projects/Ray Village /For mapping "
cp "$MAP/Rey Village Map.jpg"                      assets/village-map.jpg        # hand-drawn village map
```

If any `cp` fails, the folder name or a filename has changed — check the exact path with
`ls -la "/Users/namsjain/Desktop/08_Ongoing_Projects/Ray Village /Videos and picture for HTML /"`
before continuing.

### Mapping — clean name → where it's used

| Clean name in /assets | Source description | Used in |
|---|---|---|
| `monastery-far.png` | Monastery from far out (the beautiful shot) | Opening / Chapter 1 hero + Chapter 8 closing |
| `monastery-near.png` | Monastery outer, from near | Chapter 1 (the monastery) |
| `monastery-inside.png` | Monastery from inside | Chapter 1 / sacred layer |
| `monk-bell.png` | Monk ringing a bell | Chapter 1 / sound & sacred |
| `meditation-room.png` | Meditation room beside the monastery | Chapter 5 (sacred layer) |
| `wds-room.png` | WDS room | Chapter 4b (Making Space) |
| `hall-now.png` | 12-room building hall, current state | Chapter 4c (before) |
| `hall-vision.png` | 12-room hall, what we can make it into | Chapter 4c (after) |
| `paint-room.png` | Paint-throwing room | Chapter 4b (Making Space) |
| `pottery.png` | Pottery section | Chapter 4b (Making Space) |
| `fishing-1.png` | Fishing spot | Chapter 7 (nature) |
| `fishing-2.png` | Fishing spot | Chapter 7 (nature) |
| `unbecoming.mp4` | Video of breaking stuff | Chapter 4a (Unbecoming Space) |
| `village-map.jpg` | Hand-drawn map of Rey Village | Chapter 1 (orientation) + Chapter 8 (closing) |

**For `hall-now.png` + `hall-vision.png`:** present these as a "now → what it becomes" pair —
a before/after slider or two side-by-side framed images. This is one of the most powerful
moments in the site.

**The video (`unbecoming.mp4`):** muted, looping, contained within the Unbecoming Space chapter.
It should feel like evidence, not spectacle — let it play quietly behind or beside the text.

### Additional media to ADD later (leave clean placeholder slots)

Build labelled, styled empty slots so Naman can drop these in without touching layout:
- Lepcha weaving / textile patterns (for texture and the craft theme)
- Lepcha traditional instruments (Tungbuk lute, Pumtong Pulit flute)
- The li house (Kaa Den-Mo-Lee) — heritage structure
- The river / orange orchard
- A reference video or two for sound healing / drum circle / artist residency mood

Do not search the web inside the build unless Naman asks. Use placeholders with clear captions
like *"[ photo slot: Lepcha weaving — to be added ]"* styled to match the design.

---

## 5. Chapters & content

Use this content as written. Lepcha/Tibetan terms in italics, kept as-is. Tone: calm, precise,
warm, unhurried. Short lines. Lots of breathing room.

### Chapter 1 — The Place Before the Vision
*Hero: `monastery-far.png` (the beautiful distant monastery shot), one line over or beneath it.*

Opening line (large, quiet):
> Rey Mindu is already a mindful village. We are not building one.

Body:
> A Lepcha village in East Sikkim, between Rumtek and Lingdum monasteries. A *bongthing* in his
> seventies still chants here. A monastery, rebuilt three times over a century, stands where an
> old clay stupa once was. 108 white flags multiply mantra in the wind for the dead. A buckwheat
> roll is served with millet beer to a guest who has walked up from the ridge.
>
> These are not raw materials for a project. They are the project, complete in themselves.

Pull-quote (set apart):
> What the village needs is not a vision imposed from outside — but a protective architecture
> that lets what is already here continue, while finding the right channels for it to be expressed.

*Use `monastery-near.png`, `monastery-inside.png`, `monk-bell.png` through this chapter as the
viewer scrolls.*

*End Chapter 1 with `village-map.jpg` as an orientation moment — once the viewer has felt the
place, the map shows them its deliberate geography. Caption it simply, e.g. "The village holds
two zones — the Village Core, and the Riverside Area about 1.3 km away." Present the map large
and clear (it's hand-drawn — let it feel like a hand-drawn map, framed, not cropped). It can be
tappable to zoom on mobile. The same map can return small at the start of Chapter 8 as a "here
is the whole of it" beat.*

---

### Chapter 2 — The Common Thread
*Texture-forward chapter. Minimal images, strong typography. Deep colour field.*

> Combine seven pillars into one offering, with a single thread running through all of it:
> mental well-being, Vajrayana Buddhism, Lepcha culture, art, music and sound, local
> sensitivities, and local experiences. Not heavy. Not clinical. A place that restores you.

> The thread is mental well-being. But Rey Mindu already owns the words for it.

Three terms, presented as three cards or a slow reveal:
- **Thongdrol** — *liberation through seeing.* The one who looks and the thing looked at are not two.
- **Darshan** — *reciprocal seeing.* The viewer is also seen; blessing passes through the exchange.
- **Pang** — the Lepcha word in *Pang Lhabsol*: *to witness.*

Closing line:
> Spectatorship is one-way, and it consumes. *Darshan*, *thongdrol*, and *pang* are two-way, and
> they transmit. A guest who arrives with these is a witness — not a tourist. That is the whole
> difference.

---

### Chapter 3 — How Every Space Carries Two Roots
*The conceptual heart. Explain the design principle simply, then the rest of the site demonstrates it.*

> Every space here means two things at once.

- **The surface root** — what anyone feels instantly, with no explanation.
- **The deep root** — what the village's living traditions already say about the same thing.

> The two hold together. And the deep root is never lectured to a guest — it is *arranged*, so
> the village teaches it through how it is lived. The orchard's one rule teaches the Lepcha
> relationship with land without a word. Sitting at the cremation ground teaches impermanence
> without a dharma talk.

Pull-quote:
> Any wellness resort can build a breaking room. Only Rey Mindu can build one where the reason
> *why* you break things already lives in the monastery 200 metres away.

---

### Chapter 4 — The Arc of Expression
*Three spaces, presented in sequence: release → making → gathering. Each gets its own scroll section.*

Intro:
> The active spaces form an arc — from the most physical release to the most communal gathering.
> A guest can move through all three in a day. They stand in counterpoint to the still, sacred
> spaces. Holding both poles at once is the non-dual architecture, made into a village.

#### 4a — The Unbecoming Space
*Use `unbecoming.mp4` here, muted and looping. A separate, semi-outdoor structure at the village edge.*

- **Surface:** You are carrying something heavy — anger, grief, jealousy, shame. These are real.
  This space gives them a form to meet. *Name what you are carrying. Bring it here. Leave it.*
- **Deep:** The five Vajrayana poisons — ignorance, attachment, aversion, pride, jealousy — are
  not foreign invaders to be suppressed. They are the raw material of awakening: the poison is
  also the medicine, recognised and transformed. The *bongthing*'s work with *Mung* spirits
  follows the same logic — the difficult is not destroyed, but appeased and transformed.
- The non-dual view of human experience: **anger and peace are not two.**

#### 4b — The Making Space (WDS Building)
*Use `wds-room.png`, `paint-room.png`, `pottery.png`.*

- **Surface:** Work with your hands. Throw paint, shape clay, weave. The thinking mind quiets.
  You become the making. A space to become a child again.
- **Deep:** Dōgen's cook found awakening in the kitchen, not the meditation hall. Marpa built his
  tower stone by stone — the labour was the transmission. The Lepcha weaver chants mantras for
  the named owner while weaving the *Sumok-thyaktuk* hat. Making and practice are not two.

#### 4c — The Gathering Hall (12-Room Building)
*Use the `hall-now.png` → `hall-vision.png` before/after pairing here. This is a key moment.*

- **Surface:** Come together. Listen, play, speak, be witnessed. The open mic where you finally
  sing the thing you've carried. The drum circle where you stop thinking and start feeling.
- **Deep:** Ritual music at the monastery is *chöpa* — offering, not entertainment. *Cham* is
  moving meditation. Performer and witness are not two. So the hall has **no fixed stage** — the
  architecture refuses the idea of one person performing at others.
- **A space in three modes:** *Creation* (an artist in residence working alone) → *Exchange*
  (their work meeting the village's own musicians and weavers) → *Gathering* (open mic, concert,
  dialogue, dinner).
- **The one condition of the residency:** the work must leave something behind. A song learned by
  a local musician, a technique exchanged, a conversation that shifts how a villager sees their
  own tradition. Not a retreat that uses the village as backdrop — a relationship where something
  flows both ways. This is the Lepcha principle of reciprocity, applied to culture: you do not
  take from the orchard without asking.

---

### Chapter 5 — The Sacred & Still Layer
*Quieter visual register. More white/dark space, slower pacing. Use `meditation-room.png`,
`monastery-inside.png`.*

> These spaces are protected, not programmed. They make plain what kind of place this is.

- **The Monastery & Meditation Room** — visitors attend as witnesses, in *thongdrol* mode. The
  monks' practice always takes precedence over any documentation. Supervised sitting happens in
  the meditation room, with the resident Lama's blessing. The Tantric practices are sensitive and
  secret — surface engagement only, never claiming deep access.
- **The Cremation Ground** — the most direct expression of non-dual practice the village has,
  where body and mountain, samsara and nirvana, are recognised as not two. Visitors may sit and
  contemplate when no ceremony is happening, and do nothing else. Never photographed as scenery.
  *Most mindful travel avoids death. Rey Mindu cannot, and should not — it is the most honest
  thing the village offers.*
- **Kaa Den-Mo-Lee (the li house)** — a 130+ year old traditional Lepcha house, to be restored
  with the Culture Department as conservation, not renovation. Not a vernacular style but a
  cosmological form. *[photo slot: the li house — to be added]*

---

### Chapter 6 — Sculpture Point & the Rooster Story
*The village's own founding myth. Give this its own chapter — it is the visual identity anchor.*

> Near the VLW office, with views toward Gangtok and Rumtek, three sculptures are planned: the
> Rooster, the Lepcha King, and Guru Rinpoche. This is where the village's own story stands.

The story (present beautifully — this is folklore, handle it with care):
> When evil spirits built a bridge by night, crossing the stream to carry away the people of Rey,
> the village prayed. Guru Rinpoche, seeing the bridge near completion, released a rooster from
> Munomkung. Mistaking its crow for the arrival of dawn, the spirits abandoned their work and
> fled — leaving the bridge forever unfinished. The stones were scattered across the land, and
> the footprints of that struggle remain on the rocks to this day. From then on, the villagers
> lived in peace.

Reflection line:
> It is not a story about power. It is a story about timing, and witnessing, and the natural order
> reasserting itself — a single crow, at exactly the right moment. That is how Rey Mindu itself works.

---

### Chapter 7 — The Living Curriculum (Nature)
*Use `fishing-1.png`, `fishing-2.png`. Open, airy, green.*

> The river, the orchard, the forest, the flowers — not amenities. The Lepcha worldview, made
> walkable. The landscape is the teacher.

- **Surface:** Walk beside the river. Sit in the orchard. Fishing as patience and stillness, not
  sport. The trek from monastery into the sanctuary as the longest exhale. The village needs
  more flowers.
- **Deep:** In Lepcha cosmology the river is inhabited by *lu* — water spirits. The forest asks
  for a ceremony honouring the bamboo's spirit before cutting. When a guest is told they may not
  pluck from the orchard without asking, they are not given a rule — they are given a teaching:
  **the land is a relationship, not a resource.**
- The riverside and fishing area will be cleared and declared sacred — protected by meaning, not
  only by rules.

---

### Chapter 8 — The Two Registers / Closing
*Bring it home. Short. Calm. A single closing image — `monastery-far.png` again, full-bleed.*

> The whole village rests on one contrast it must learn to hold:

- **The expressive** — the Unbecoming Space, the Making Space, the Gathering Hall. Sound, colour,
  release. Placed so the noise moves into the landscape, never into the quiet.
- **The still** — the monastery, the meditation room, the cremation ground, the orchard, the
  riverside, and small silence spaces scattered through the village, where people sit together
  without speaking.

Final line (large, quiet):
> A guest moves between the two across a day. The movement itself is the practice.

---

## 6. Design language

**Mood:** rich and textured, reflecting Buddhist and Lepcha visual culture. Deep, saturated,
warm — never sterile, never "spa minimalism." It should feel like the inside of a monastery and
the warmth of a Lepcha home, not a tech landing page.

**Colour palette (use as a starting point, refine against the actual photos):**
- Deep monastery green `#1D6E56` and a darker forest `#0F3D2E`
- Warm ochre / butter-lamp gold `#C8922A`
- Vermilion / Tibetan red accent `#9E2B25` (use sparingly — for emphasis, the rooster, the sacred)
- Warm off-black ink `#211C18` for text
- Aged-paper / raw-clay background `#F2EBDD` for light sections
- Let dark and light chapters alternate to create rhythm (sacred = darker, nature = lighter)

**Texture:** subtle. A faint paper or raw-plaster grain on backgrounds. Thin rule-lines in gold
or green. Avoid drop shadows that look like generic web cards — prefer framed images, like
photographs mounted on a wall.

**Typography:**
- A characterful serif for headings (something with warmth and history — e.g. a Garamond,
  Spectral, or similar). Avoid Times.
- A clean, readable serif or humanist sans for body.
- Generous line-height. Short measure (max ~65 characters). Let text breathe.
- Lepcha/Tibetan terms always in italics.

**Motion:** restrained. Slow fades on scroll, gentle parallax on hero images at most. The
before/after hall slider is the one "interactive toy." Nothing bounces.

**Lepcha motif:** if a decorative element is wanted, draw on Lepcha weaving geometry (clean
woven-pattern borders/dividers) rather than generic mandalas. Keep it minimal and authentic.

---

## 7. Attribution

Footer of the final chapter, quiet and small:

> Naman Jain  |  Sarvahitey  |  Rey Mindu  |  2026

---

## 8. Guardrails (important — do not violate)

- **Never** use the phrase "Nomad Sikkim" anywhere.
- The Tantric/Vajrayana practices are secret and sensitive — surface engagement only. Never
  imply guests get access to deep practices.
- The *bongthing* is real and must be protected — no photos of him, no naming, do not present
  him as an attraction. Reference the tradition, not the person.
- This is a vision/working document, not a booking site. **No prices, no "Book Now," no fake
  testimonials, no invented statistics.** If a number isn't in this brief, don't put it in.
- The li house age is "130+ years" (oral testimony says older) — don't state a single exact
  larger figure as fact.
- Folklore (the rooster story) is presented with respect, as the village's own story.

---

## 9. Build order (suggested for Claude Code)

1. View every image in `/assets` first. Note orientation and what each shows.
2. Set up the page shell, nav, chapter scaffold, and design tokens.
3. Build chapter by chapter, content first, then style.
4. Wire the chapter navigation (click between) and scroll-reveal (within).
5. Build the hall before/after slider and embed the video (muted/loop).
6. Add placeholder slots for the to-be-added media.
7. Responsive pass (phone + laptop), then a performance/lazy-load pass.
8. Confirm it opens by double-click AND is ready to host.
