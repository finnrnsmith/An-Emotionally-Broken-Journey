# Lorde & Jack Antonoff: An Emotionally Broken Journey
### Interactive Network Diagram

> "Lorde and Jack Antonoff 100% Were/Are Being Shady, Are Def Boning if Nothing Else, Lena Sucks Too But This is Bullshit and The People Deserve The Truth"

An interactive network visualization of the relationships, events, and songs documented in the *Believe in the Impossible* slideshow — built for exploring, clicking around, and adding your own thoughts.

---

## Using the Visualization

| Action | Result |
|---|---|
| Click a node or edge | Opens detail panel with description + Finn's Thoughts |
| Drag | Pan the graph |
| Scroll | Zoom in/out |
| `Songs ✓` button | Toggle song nodes on/off |
| `Events ✓` button | Toggle event nodes on/off |
| `Fit` | Fit everything in view |
| `Reset Layout` | Re-run the force layout (randomized) |
| `F` key | Fit view |
| `ESC` key | Close detail panel |

---

## Adding Finn's Thoughts

All annotations live in **`data/annotations.json`**. It's a flat key-value file — find the node or edge ID, add your text, save, redeploy.

### Example

```json
{
  "nodes": {
    "jack": {
      "finn_thoughts": "The audacity of this man. 13 years older. Living with his girlfriend. Producing an entire album. I cannot."
    },
    "writer_in_dark": {
      "finn_thoughts": "Written while lying next to him while Lena slept. Evil witch behavior. Iconic."
    }
  },
  "edges": {
    "lorde-jack-collab": {
      "finn_thoughts": "\"We were just obsessed with each other.\" Sure Jan."
    }
  }
}
```

### Node IDs (for reference)

**People:** `lorde` · `jack` · `lena` · `james` · `taylor` · `sonja` · `grimes`

**Albums:** `melodrama` · `pure_heroine` · `_1989`

**Songs:** `green_light` · `sober` · `the_louvre` · `liability` · `hard_feelings` · `writer_in_dark` · `sober_ii`

**Events:** `grammy_2014` · `coachella_2016` · `snl_2017`

**Band:** `bleachers`

---

## Deploying to GitHub Pages

### First-time setup

1. Create a new GitHub repository (e.g. `lorde-network`)
2. Push this folder:
   ```bash
   cd "lorde-network"
   git init
   git add .
   git commit -m "Initial commit"
   git remote add origin https://github.com/YOUR_USERNAME/lorde-network.git
   git push -u origin main
   ```
3. Go to **Settings → Pages → Source → Deploy from branch → main / root**
4. Your site will be live at: `https://YOUR_USERNAME.github.io/lorde-network/`

### Updating after editing annotations

```bash
git add data/annotations.json
git commit -m "Add Finn's thoughts"
git push
```

GitHub Pages redeploys automatically within ~60 seconds.

---

## Running Locally

Because `annotations.json` is loaded via `fetch()`, you need a local server (not `file://`):

```bash
# Option 1 — Python (easiest)
cd lorde-network
python3 -m http.server 8080
# then open http://localhost:8080

# Option 2 — Node
npx serve .
```

The visualization works offline too — the graph data is embedded directly in `index.html`. Only annotations require the server.

---

## Project Structure

```
lorde-network/
├── index.html              ← Full visualization (self-contained)
├── data/
│   ├── graph.json          ← All nodes & edges (reference / for editing)
│   └── annotations.json    ← Finn's Thoughts — edit this file
├── assets/                 ← Drop images/icons here for future use
└── README.md
```

---

## Extending the Graph

To add a new node or edge, edit **`data/graph.json`** and also update the embedded `GRAPH_DATA` constant inside `index.html` (search for `const GRAPH_DATA`). They should stay in sync.

To add a new annotation field, add it to `annotations.json` and update the `setFinnBox()` function in `index.html` to display it.

---

*Source material: "Believe in the Impossible: Lorde and Jack Antonoff – An Emotionally Broken Journey" · @buzzkillary*
