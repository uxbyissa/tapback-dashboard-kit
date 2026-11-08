# Handoff notes — TapBack Dashboard (Meed · Today)

Design source: Figma file **"Tapback Dashboard — Trezo"**, page **"TapBack identity — 02"**.

| Frame | What it is |
|---|---|
| Style 3 — Trezo · Glass + Apple UX · TapBack colours · Meed real data | Main dashboard (approved design) |
| Variant B — vivid colours + TapBack lime accent | Same dashboard with lime accents on key items |
| Style 3 · TapBack — Concept detail · Meed | Concept detail page (opens from a concept row) |
| Hover cards column | 10 hover cards (popovers / tooltips) |
| Floating elements column | Toasts, Quick Look, context menu, Inspector |
| Flow — the CEO opens Meed · Today | 18 frames, one per moment of the interaction flow |

## 1. Identity rule

- **TapBack identity only in the top bar and the side menu**: navy `#054156` top bar, lime `#D0FE17` logo and active side-menu icon, navy side-menu text.
- Primary buttons (Today segment, Export, primary toast buttons) use the navy gradient `#0B5B77 → #054156`.
- Everything inside the content area uses the metric colours below.

## 2. Colour rule — one colour per metric, everywhere

| Metric | Colour | Subtle background | Used for |
|---|---|---|---|
| Net sales | `#2E64C6` | `#EEF3FB` | Net sales KPI, store share bars, trend lines, today bar, leaderboard bars |
| Orders | `#2DB6F5` (text `#0EA5E9`) | `#E8F7FE` | Orders KPI, orders hover card |
| Avg. ticket | `#8B5CF6` | `#F3EEFF` | Avg. ticket KPI and its hover card |
| Gross profit | `#25B003` | `#EEFFE5` | Profit KPI, profit segment, profit column |
| Stores | `#EC4899` (text `#DB2777`) | `#FDEEF6` | Stores KPI, **every** store badge |

- Parts of net sales use the blue tints `#2E64C6 → #5C8AD6 → #7FA2E0 → #8AABE3 → #B9CDEF → #D6E2F6` (payments, order mode, yesterday / last week, cost).
- Deductions: Tax `#94A3B8`, Discounts `#475569`, Unreconciled `#DDE1E8`.
- Status only for alerts and limits: success `#25B003`, warning `#F5A524`, danger / void `#FD5812`.
- Users are neutral (`#94A3B8`). Concept Meed badge `#8E1B2E`.

## 3. Trezo build map (every element = stock Trezo / Bootstrap 5)

| Element | Trezo / Bootstrap component |
|---|---|
| KPI row | Trezo stats card (`.card`) + ApexCharts sparkline (`type: area`, `sparkline.enabled`) |
| Pills, chips, Live | `.badge.rounded-pill` (`bg-*-subtle`) |
| Where today's gross sales went | stacked `.progress` (6 `.progress-bar`) + legend list + `.badge` for Refund |
| Needs attention | `.list-group` + status `.badge` + `.btn-sm` actions |
| Stores table | Trezo `.table.table-hover` + inline `.progress` for share + ApexCharts sparkline for trend; column picker = `.dropdown` with checkboxes |
| Today vs yesterday | ApexCharts bar (horizontal, goals marker) |
| Store leaderboard / Sales mix | `.list-group` + `.progress` |
| Loss & control | ApexCharts heatmap with colour ranges (within / near / over limit) |
| Period tabs · Export | `.btn-group` · `.btn-primary` + `.dropdown` |
| Toast · Quick Look · Context menu · Inspector | `.toast` · `.popover` · `.dropdown-menu` · `.offcanvas-end` |

## 4. Interactions

- **Hover cards**: Trezo popover, `data-bs-trigger="hover focus"`, delay 150 ms show / 100 ms hide. Click pins it, Esc closes. Chart-segment tooltips use an ApexCharts custom tooltip with the same card markup.
- **Hover ring**: the hovered element gets a 2 px ring in its metric colour.
- **Live chip**: data streams in; "updated Xs ago" refreshes; numbers count up in 300 ms.
- **Toast** (bottom-right, fixed): only for breached limits (voids 2.6% > 2%). Actions: Review voids · Set limit · Remind me in 1h.
- **Quick Look**: hover a store row 400 ms or press Space. Click a row → Inspector (offcanvas from the right). Right-click → context menu.
- **Export**: runs in the background with a progress toast. Reversible actions show **Undo** instead of "Are you sure?".
- **Pop out**: Document Picture-in-Picture live mini-window (Chrome / Edge); in-page floating card as fallback.
- **Big numbers**: full value in tables and KPIs; compact K / M in charts with the full value on hover. Long names truncate with a tooltip.
- **"—"** = not in the data source yet. Cells fill automatically when the API provides them.

## 5. Hover cards (content)

| # | Trigger | Card |
|---|---|---|
| 1 | Net Sales KPI | How net was made: gross − tax − void − discounts = net; refunds tracked separately |
| 2 | Orders KPI | Orders by channel (estimated from sales share) |
| 3 | Avg. Ticket KPI | Inside one ticket: net 18.44 · tax 2.68 · void 0.56 · discounts 0.05 |
| 4 | Gross Profit KPI | What-if slider: void rate → profit and margin |
| 5 | Stores Open KPI | Top 10 vs other stores share |
| 6 | Void segment | Void vs limit + Review / Set alert |
| 7 | Today vs yesterday | Gap to match yesterday |
| 8 | User row | Orders, estimated sales, gap to #2 |
| 9 | Payment bar | Tender amount, share, all cards %, cash, delivery apps |
| 10 | Heatmap cell | Voided amount, over-limit amount + Review / Remind |

Images: `previews/components/`.

## 6. Estimated values (shown with ≈ / est.)

Replace with real fields when the API exposes them.

- Net per order = 517,265.91 ÷ 28,053 = **18.44**
- Orders yesterday ≈ yesterday net ÷ 18.44
- Store orders ≈ store net ÷ 18.44 · Store profit ≈ store net × 15.97% margin
- Stores open **78+** = lower bound: top 10 stores = 81,702.77; the other 435,563.14 comes from stores each below #10 (6,423.27) → at least 68 more
- Profit what-if assumes voided items carry no cost
