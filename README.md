# UI_Audit

Working repo for the **COMPASS** (Marketing Finance Tool) UI audit and redesign.

The deliverables themselves live in Figma — this repo holds the agent skills used to
produce them, plus this record of what was done and where to find it.

---

## Figma file

**Marketing Finance Tool** — file key `skAYDS0exsP6cUWxUDAody`

| Page | Contents |
|---|---|
| `Campaign Creation` (original) | Source designs — **untouched**, plus an audit findings board and 18 numbered pins |
| `🎨 COMPASS Redesign — PowerApps v1` | Token sheet + 4 screens + 3 landing variants, Lato, built for PowerApps |
| `🧩 COMPASS × Untitled UI (free kit)` | Same screens rebuilt in Untitled UI grammar (Inter, gray-25→900, shadow-xs) |
| `🔬 Mobbin Lab — Analysis & Redesign v3` | Mobbin research board + shadcn/ui v3 screens + 3 landing variants |

All redesign pages are additive. The original designs were never modified.

---

## 1. Audit

Ran against three rule sets: `web-design-guidelines` (Vercel Web Interface Guidelines),
`ui-ux-pro-max` (priority-ordered checklist), and `redesign-existing-projects`.

Contrast was measured programmatically across **939 text nodes** in 8 representative
frames — **95 fail WCAG AA**.

**Critical**
- Status pills fail badly: "Submitted" `#F79900` on `#FDEBCC` = **1.89:1**; "Approved"
  `#3AB053` on `#E1F5E5` = **2.45:1** (4.5:1 required). Status is conveyed by colour alone.
- `#8C8C8C` grey used for both labels *and* real data values (3.36:1 on white, 2.95:1 on grey).
- Primary "Approval" button: white on `#829D68` = **3.01:1**.
- Treemap uses alarm-red for a neutral 26.2% brand share.

**High**
- Filter dropdowns 127×30 px with 10×10 px carets; row actions 20×20 px with delete beside edit.
- "Page 1 of 1000" navigable only by prev/next arrows.
- No loading, empty, or error states designed anywhere — only the happy path.

**Medium**
- Section colour bands read as state (pink "Basic Details" looks like an error before typing).
- Copy: "supervior" → supervisor; "reallocation's" → reallocations.
- Inconsistent number formatting (`265.248.4M`, `388715.77`).
- 8 leftover "Click here" placeholder components.
- Type drift: Inter + Open Sans across 10 weights and 21 sizes.

**Wins worth keeping** — persistent KPI band across report tabs; the Campaign Detail view's
card grouping; the confirm modal warning that editing an approved campaign re-triggers approval;
real content throughout (no lorem ipsum).

---

## 2. Design directions

Three parallel generations exist. They are alternatives, not a sequence.

**v1 — PowerApps (Lato)**
Every text pair ≥4.5:1, most ≥7:1. Single accent (`#E50201` for buttons — pure `#F40000`
is 4.3:1 with white and fails; `#F40000` is kept for the logo). Status pills pair an AA text
tone with a tinted background *and* a leading dot. 40 px inputs, 44 px buttons, 48 px rows,
8 px grid. Flat, hairline-bordered, auto-layout throughout — no gradients or blurs, so every
element maps to a PowerApps container, gallery, or modern control.

**v2 — Untitled UI (free kit)**
Same screens in Untitled UI's component grammar. Layers are named after their UUI counterparts
(`Button/primary`, `Badge`, `Metric item`, `Featured icon`, `Horizontal tabs`) so the real kit
can be swapped in later. Brand red mapped to `brand-600` the way UUI intends customisation.
Note: Inter is not a native PowerApps font — this page is the better reference if COMPASS ever
becomes a web app.

**v3 — shadcn/ui, Mobbin-informed**
Deep-mode Mobbin research across screens, flows, and sections surfaced eight structural gaps
shared by *all* previous versions:

1. Sidebar shell, not top-bar nav (Airtable, Quicken, Origin, Reddit Ads)
2. Selectable KPI cards with sparklines that drive the view below (Reddit, Pinterest)
3. Applied filters as removable tokens
4. Entity hierarchy exposed as tabs
5. Checkbox selection with a bulk-action bar
6. Pinned totals row
7. Create as a focused slide-over (~7 fields + disclosures), not a 21-field page
8. Data-freshness / FX-rate trust signals

v3 implements all eight, and adds the first time-series COMPASS has had (monthly BP vs RE09).

**Landing pages** — three treatments on each redesign page: flat editorial, gradient wash, and
a product collage built from native Figma vector tiles behind a directional scrim. The collage
is vector, not photographic: this environment blocks stock-photo and image-generation services.
Drop a licensed image onto the `bg/product collage` layer to make it real.

---

## 3. Skills

Installed via the [`skills`](https://skills.sh) CLI into `.agents/skills/`, symlinked into
`.claude/skills/` so Claude Code loads them as project skills.

| Skill | Source | Used for |
|---|---|---|
| `ui-ux-pro-max` | `nextlevelbuilder/ui-ux-pro-max-skill` | Priority-ordered audit checklist, design-system generation |
| `web-design-guidelines` | `vercel-labs/agent-skills` | Web Interface Guidelines compliance review |
| `frontend-design` | `anthropics/skills` | Distinctive, non-templated visual direction |
| `shadcn-ui` | `giuseppe-trisciuoglio/developer-kit` | Component patterns for v3 |
| `ui-animation` | `mblode/agent-skills` | Motion review (not applied — PowerApps can't build it) |
| taste-skill bundle | `Leonxlnx/taste-skill` | `high-end-visual-design`, `redesign-existing-projects`, `minimalist-ui`, and 9 others |

Reinstall with `npx skills add <source>`. `skills-lock.json` pins what is installed.

Caveat: several of these overlap heavily on "make UI less generic" and will compete to
auto-trigger. The core five are `ui-ux-pro-max`, `frontend-design`, `web-design-guidelines`,
`shadcn-ui`, and `ui-animation`.

---

## 4. Open items

- **Pick one direction to carry forward.** Recommended: v3's structure re-skinned in Lato and
  the brand palette — v3 fixes real usability gaps, but Inter/zinc isn't PowerApps-native.
- **Confirm PowerApps target** — canvas vs model-driven, modern vs classic controls.
- **Replace invented content** with the real field list, required-field rules, status taxonomy,
  approval roles, and FX rules.
- **Supply brand assets** — the real COMPASS/Coca-Cola lockup and DA&R logo as SVG (a
  placeholder "C" mark is in use).
- **Screens not yet designed** — Campaign Detail / approval view, the Phasing / Spend type /
  Variance / Ratio report tabs, Approvals queue, Dashboard, Admin panel.

---

## Notes

- `.claude/settings.local.json` is gitignored — it holds personal MCP tool permissions.
- Code-level rules from the Vercel guidelines (focus rings, `prefers-reduced-motion`,
  `autocomplete`, list virtualization, URL-reflected filter state) cannot be verified in a
  static design file and belong on the build checklist.
