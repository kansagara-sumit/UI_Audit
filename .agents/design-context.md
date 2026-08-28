# Design Context — DAR (Digital Analytics & Reporting)

Derived from the Figma file **Poster Dump** (`2f7sPporJBuFqsnyDtKd9P`), frames
`Elements` (1:1132), `The Greate one` (1:1610), and `New Projects` (1:248).

## Brand palette

| Token | Hex | Role |
|---|---|---|
| `--dar-red` | `#ED1B24` | Punctuation only. One or two marks per composition. Never a field. |
| `--dar-ink` | `#0A0A0A` | Primary text, negative panels |
| `--dar-cream` | `#FBF9F4` | Page ground |
| `--dar-sand` | `#F2EAD8` | Secondary ground, card fills |
| `--dar-yellow` | `#EDEBA9` | Light yellow — element/segment fill |
| `--dar-gold` | `#E6C877` | Gold — element/segment fill |
| `--dar-olive` | `#A8C48C` | Muted olive — element/segment fill |
| `--dar-taupe` | `#C9A1A9` | Rosy taupe — element/segment fill |
| `--dar-white` | `#FFFFFF` | Gaps, knockouts |

Greys from the Figma variables: text-primary `#000000`, text-tertiary `#666666`,
border `#C7C7C7`, surface `#FFFFFF`.

## Typography

Figma variables name the Coca-Cola corporate faces:

- `Display/S` — TCCC Unity Head Bold, 58 / 0.9 / -3
- `Heading/M` — TCCC Unity Head Medium, 25 / 1.2 / -1
- `Body/M` — TCCC Unity Regular, 16 / 1.5 / 0
- `Data/Label` — TCCC Unity Medium, 13 / 1.2 / 0

TCCC Unity is licensed and not present in this repo. Local substitution stack,
chosen to match the reference poster's contrast of heavy grotesk against
editorial serif italic:

- **Display / headings** — `Instrument Sans Bold` (grotesk, tight tracking)
- **Editorial accent** — `Instrument Serif Italic`, always in `--dar-red`
- **Body** — `Instrument Sans Regular`
- **Data labels / meta** — `Geist Mono`, uppercase, `letter-spacing: 0.08em`

## Element system

Ten elements drawn from the DAR wordmark letterforms plus the legacy arrow:
bracket, bar, shoulder, arrow, concave star, A-chevron, slash, star negative,
quad blocks, star mark. Master unit height **77px**.

Seven rules govern every band:

1. One scale — every element scaled by the same factor from the 77px master.
2. Rotation limited to 0°, 90°, 180°, −90°. No intermediate angles.
3. Scale uniformly. Corner radii are drawn, not parametric — never distort.
4. Colour from the brand palette only.
5. Red is punctuation. One or two reds per band.
6. Elements sit on one baseline, flush or on a single consistent gap.
7. Bands bleed off at least one artboard edge.

## Composition

Cream ground, a single red gesture, floating rotated cards with soft diffused
shadow, pill tags with a leading dot, generous macro-whitespace, and a DAR
element band bleeding off the bottom edge. Co-branding lockup: The Coca-Cola
Company + DAR, separated by a hairline rule.
