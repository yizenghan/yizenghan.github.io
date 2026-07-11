# Add 2026 Recent Works Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Add Agent-as-a-Router, K-Forcing, and Towards 3D-Aware Video Diffusion Models to the homepage Recent Works and News sections with accurate metadata, official links, and consistent visuals.

**Architecture:** Keep the existing single-file static-site architecture. Add three image assets under `figures/`, prepend three paper cards to `#recent-works`, and prepend three dated items to `.news-list`; do not change the Representative tab, CSS, JavaScript, or page structure.

**Tech Stack:** Static HTML/CSS/JavaScript, local PNG/JPG assets, GitHub Pages.

---

## Agreed scope and ordering

Add the three works in reverse publication-date order at the top of Recent Works:

1. Agent-as-a-Router — submitted 2026-06-22.
2. K-Forcing — submitted 2026-06-09.
3. Towards 3D-Aware Video Diffusion Models — submitted 2026-06-01.
4. Keep DyDiT++ and all existing cards after them.

Add three News entries at the top, all dated `06/2026`, in the same order. Do not add any of the three to Representative Publications in this iteration.

## Confirmed metadata and links

### Agent-as-a-Router

- Title: `Agent-as-a-Router: Agentic Model Routing for Coding Tasks`
- Authors: `Pengfei Zhou, Zhiwei Tang, Yixing Ma, Jiasheng Tang, Yizeng Han, Zhenglin Wan, Fanqing Meng, Wei Wang, Bohan Zhuang, Wangbo Zhao, Yang You`
- Venue label: `Arxiv Preprint, 2026.`
- PDF: `https://arxiv.org/abs/2606.22902`
- Code: `https://github.com/LanceZPF/agent-as-a-router`
- Proposed description: `We formulate model routing as an agentic Context-Action-Feedback loop and introduce ACRouter and CodeRouterBench for efficient routing across frontier LLMs on coding tasks.`
- Proposed asset: `figures/agent_router.png`

### K-Forcing

- Title: `K-Forcing: Joint Next-K-Token Decoding via Push-Forward Language Modeling`
- Authors in the current arXiv metadata: `Zhiwei Tang, Yuanyu He, Yizheng Han, Wangbo Zhao, Jiasheng Tang, Fan Wang, Bohan Zhuang`
- Homepage display name: use the correct spelling `<b>Yizeng Han</b>`; the current arXiv and GitHub citation spell it `Yizheng Han`.
- Venue label: `Arxiv Preprint, 2026.`
- PDF: `https://arxiv.org/abs/2606.10820`
- Code: `https://github.com/alibaba-damo-academy/K-Forcing`
- Proposed description: `K-Forcing learns a push-forward language model for joint next-k-token decoding, achieving about 2.4-3.5x batch-serving speedup while reusing the autoregressive backbone.`
- Proposed asset: `figures/k_forcing.png`

### Towards 3D-Aware Video Diffusion Models

- Title: `Towards 3D-Aware Video Diffusion Models: Render-Free Human Motion Control with Mesh Tokenization`
- Authors: `Jingyun Liang, Min Wei, Shikai Li, Yizeng Han, Hangjie Yuan, Lei Sun, Weihua Chen, Fan Wang`
- Venue label: `Arxiv Preprint, 2026.`
- PDF: `https://arxiv.org/abs/2606.02000`
- Project: `https://jingyunliang.github.io/MeshToken/`
- Proposed description: `We condition video diffusion models directly on compressed 3D human mesh tokens for render-free motion control with improved 3D structure and viewpoint awareness.`
- Proposed asset: `figures/mesh_token.png`

## Task 1: Resolve the only metadata ambiguity (resolved)

**Files:**
- No files modified.

**Step 1: Confirm the K-Forcing author spelling**

The homepage will show `Yizeng Han` even though arXiv v2 and the official GitHub citation currently show `Yizheng Han`.

**Step 2: Record the decision**

Use the confirmed spelling in both the paper card and any future CV/bibliographic updates. Do not silently guess.

## Task 2: Prepare three publication images

**Files:**
- Create: `figures/agent_router.png`
- Create: `figures/k_forcing.png`
- Create: `figures/mesh_token.png`

**Step 1: Select authoritative source visuals**

- Agent-as-a-Router: use the framework/ACRouter overview from the official repository or paper.
- K-Forcing: use the AR vs speculative decoding vs K-Forcing overview from the official repository.
- MeshToken: use the method overview from the official project page.

Do not reuse `figures/agent.png`; it belongs to Agent Attention.

**Step 2: Save and normalize assets**

Crop surrounding whitespace, preserve labels, and export as RGB PNG. Target approximately 2:1 to 3:2 landscape composition, at least 800 px wide, and preferably below 800 KB per image.

**Step 3: Verify assets**

Run:

```bash
file figures/agent_router.png figures/k_forcing.png figures/mesh_token.png
du -h figures/agent_router.png figures/k_forcing.png figures/mesh_token.png
```

Expected: all three files are valid PNG images; none is unexpectedly multi-megabyte.

**Step 4: Commit assets**

```bash
git add figures/agent_router.png figures/k_forcing.png figures/mesh_token.png
git commit -m "Add visuals for 2026 recent works"
```

## Task 3: Add three News entries

**Files:**
- Modify: `index.html`, immediately after `<ul class="news-list">` near the current first `01/2026` item.

**Step 1: Prepend the entries**

Insert:

```html
<li class="news-item"><span class="news-date">06/2026</span> <span class="news-text">We release <a href="https://arxiv.org/abs/2606.22902">Agent-as-a-Router</a>, an agentic model-routing framework for coding tasks, together with <a href="https://github.com/LanceZPF/agent-as-a-router">code and CodeRouterBench</a>.</span></li>
<li class="news-item"><span class="news-date">06/2026</span> <span class="news-text">We release <a href="https://arxiv.org/abs/2606.10820">K-Forcing</a> for joint next-k-token decoding via push-forward language modeling.</span></li>
<li class="news-item"><span class="news-date">06/2026</span> <span class="news-text">We release <a href="https://arxiv.org/abs/2606.02000">Towards 3D-Aware Video Diffusion Models</a> for render-free human motion control with mesh tokenization.</span></li>
```

**Step 2: Check ordering**

Run:

```bash
sed -n '985,1010p' index.html
```

Expected: the three `06/2026` entries appear before the existing `01/2026` entries.

## Task 4: Add the three Recent Works cards

**Files:**
- Modify: `index.html`, immediately after `<div id="recent-works" class="subsection-content active">` and before the DyDiT++ card.

**Step 1: Add Agent-as-a-Router card**

Use the existing `.paper-item` structure with:

- Image `figures/agent_router.png`, alt text `Agent-as-a-Router`.
- User name wrapped in `<b>`.
- Venue `Arxiv Preprint, 2026.`.
- Description and official PDF/Code links from the confirmed metadata above.

**Step 2: Add K-Forcing card**

Use image `figures/k_forcing.png`, the confirmed spelling from Task 1, venue `Arxiv Preprint, 2026.`, the proposed description, and PDF/Code links.

**Step 3: Add MeshToken card**

Use image `figures/mesh_token.png`, alt text `MeshToken`, venue `Arxiv Preprint, 2026.`, the proposed description, and PDF/Project links.

**Step 4: Verify paper count and ordering**

Run:

```bash
rg -c 'class="paper-item"' index.html
sed -n '1025,1145p' index.html | rg 'paper-title|paper-venue'
```

Expected: total paper-card count increases from 22 to 25; the first four Recent Works titles are Agent-as-a-Router, K-Forcing, Towards 3D-Aware Video Diffusion Models, and DyDiT++.

**Step 5: Commit content**

```bash
git add index.html
git commit -m "Add three 2026 works to homepage"
```

## Task 5: Validate the static page

**Files:**
- Verify: `index.html`
- Verify: `figures/agent_router.png`
- Verify: `figures/k_forcing.png`
- Verify: `figures/mesh_token.png`

**Step 1: Run structural checks**

```bash
rg -c '<html' index.html
rg -c '</html>' index.html
rg -c '<body' index.html
rg -c '</body>' index.html
rg -n '2606\.22902|2606\.10820|2606\.02000' index.html
```

Expected: each structural count is 1; each arXiv ID occurs in both News and Recent Works.

**Step 2: Start a local server**

```bash
python3 -m http.server 8000
```

Open `http://127.0.0.1:8000/` and check desktop and mobile widths.

**Step 3: Perform visual QA**

Verify:

- all three images load and remain readable;
- long titles and author lists wrap without horizontal overflow;
- cards remain ordered correctly;
- the News list starts with the three June 2026 entries;
- Recent/Representative tab switching still works;
- PDF, Code, and Project links open the intended official pages;
- existing cards and mobile layout are unchanged.

**Step 4: Check the final diff**

```bash
git diff HEAD~2 --stat
git status --short
```

Expected: only `index.html` and the three new images are part of the feature; the plan document may be committed separately if desired.

## Task 6: Publish after approval

**Step 1: Push only after the user approves the rendered result**

```bash
git push origin main
```

**Step 2: Verify GitHub Pages**

After deployment, check `https://yizenghan.top/` in a private/incognito context and verify the three cards, News entries, and external links.
