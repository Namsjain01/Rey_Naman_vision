# Rey Village — A Mindful Living Village

A single-page interactive site presenting the vision for Rey Village, a Lepcha village in East Sikkim being shaped into a mindful living and mental well-being destination grounded in living Kagyu Buddhist and Lepcha tradition.

**Project:** Sarvahitey / Naman Jain  
**Location:** Rey Village, East Sikkim, India  
**Year:** 2026

---

## About the Site

Ten chapters, navigated by click with scroll within each chapter. Built to be felt, not just read — the site lets people see the spirit of the place before encountering it in person.

### Chapters

1. The Place Before the Vision — incl. A Living Museum (QR audio walk)
2. The Common Thread — *Thongdrol, Darshan, Pang*
3. How Every Space Carries Two Roots
4. The Arc of Expression — Unbecoming, Making, Gathering
5. The Confluence — Sikkim art exchange
6. The Sacred & Still Layer
7. Sculpture Point & the Rooster Story
8. The Living Curriculum — incl. the Hot Stone Bath
9. Work, and Be Changed
10. The Two Registers / Closing

---

## Running Locally

No build step. Open `index.html` directly in a browser — double-click the file or drag it into Chrome/Safari.

All assets are in `/assets`. The site works fully offline once cloned.

---

## Deploying

Connected to Netlify via this GitHub repository. Every push to `main` auto-deploys within ~30 seconds.

To deploy an update:

```bash
git add -A
git commit -m "your message"
git push
```

---

## Technical

- Vanilla HTML / CSS / JS — no framework, no build step
- Fonts via Google Fonts (Spectral)
- All state in memory, no localStorage
- Videos: muted autoplay loop (unbecoming, paint-throw, pottery, sound-healing)
- Before/after slider: hall-now → hall-vision (drag anywhere)
- Scroll reveal via IntersectionObserver
- Responsive — mobile and desktop
