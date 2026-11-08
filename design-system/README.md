# TapBack Design System

The TapBack design system for the **POS app** (tablet, 960 × 600) and the shared brand rules used by the dashboard.

**Source:** Figma "Tapback Dashboard — Trezo" → page "TapBack identity — 02" (boards: UX rules, Tokens · Colour, Tokens · Type & space, Components · Icons / Buttons & chips / Content / Shell).

```
design-system/
├── boards/      7 board images (UX rules, colour, type & space, icons, buttons & chips, content, shell)
├── icons/       49 line icons (24 × 24, stroke 1.8, currentColor)
├── fonts/       Poppins (Latin) + IBM Plex Sans Arabic (Arabic) · 400 / 500 / 600 / 700
└── tokens/      tapback-ds.css (colour, type, spacing, radius, touch, layout + component reference)
```

> The **dashboard** (web) uses Inter and the metric colours from `/tokens`. The **POS app** uses Poppins + IBM Plex Sans Arabic and the tokens in this folder. Both share the TapBack brand colours (navy `#054156`, lime `#D0FE17`).

## Colour

| Token | Hex | Use |
|---|---|---|
| Navy · primary | `#054156` | Primary actions, selected background |
| Lime · selected / current | `#D0FE17` | Selected ✓, current item |
| Ink · text | `#181818` | Text |
| Gray · secondary text | `#5F6E74` | Secondary text |
| Line · borders | `#E2E8EA` | Borders, dividers |
| Surface · page | `#F4F7F8` | Page background |
| Light · info / editing | `#DAEFF6` | Info, editing state, quick keys |
| Scrim | `#071E26` | Overlays |
| Success / bg | `#17803A` / `#DCFCE7` | Done, paid |
| Warning / bg | `#B45309` / `#FEF3C7` | Warning, offline |
| Error / bg | `#C8341F` / `#FDECEA` | Error |

Status colours always come with an icon and a word.

## Type

Poppins for Latin, IBM Plex Sans Arabic for Arabic. 4 px grid.

| Style | Size · weight |
|---|---|
| Display | 24 Bold |
| Title | 20 Bold |
| Heading | 16 SemiBold |
| Body strong | 14 SemiBold |
| Body | 14 Regular |
| Caption | 12 Regular / Medium |
| Meta | 11 Regular (time stamps only) |

**Spacing:** 4 · 8 · 12 · 16 · 24 · 32
**Radius:** 10 small controls · 12 inputs & rows · 14 buttons · 16 small cards · 20 cards · 24 dialogs
**Layout (tablet 960 × 600):** status 24 · top bar 56 · rail 72 · content · order panel 320 · gesture 16. Touch ≥ 48, primary 56.

## Components

| Group | Components (variants) |
|---|---|
| Buttons & chips | Button (Primary / Secondary / Ghost / Danger · L / M / S) · Icon button · Chip (Default / Selected / Disabled) · Status pill (Success / Warning / Error / Neutral / Info) |
| Content | Field · Stepper · Keypad key · Tab · Product tile · Option card · Cart line · Toast · Choice tile · Due card · Payment row · Brand tile |
| Shell | Top bar (Online / Offline) · Rail · Ordering bar · Order action · App menu (Manager / Employee) · Manager approval |

Sizes and colours for each component: comment block at the end of `tokens/tapback-ds.css`, and the board images in `boards/`.

## UX rules (every screen is checked against these 16 rules)

1. **Speed**: a routine sale takes ≤ 3 taps per item. No typing for routine work; use keypads, chips and steppers.
2. **Touch**: targets ≥ 44 × 44 px (48 for main controls), primary actions 56 px high, ≥ 8 px between targets.
3. **One primary**: one primary (navy) action per screen or dialog, at the end of the reading path.
4. **Colour meaning**: Selected = navy + lime ✓ · Done / paid = green · Warning / offline = amber · Error = red. Never colour alone; always icon + text.
5. **Say why**: a disabled action shows its reason next to it (e.g. "Choose 2 appetizers · 1/2").
6. **No dead ends**: every error says what happened, why, and the next step, with a button for it.
7. **Prevent, then confirm**: block invalid input where it happens (min / max, no drawer) instead of failing later at Pay.
8. **Undo over "Are you sure?"**: reversible actions get Undo. Confirmation only for irreversible ones (End of day, void after kitchen).
9. **Sensitive = reason**: open drawer, cash out, void, refund, discount need a reason; above a limit, manager approval.
10. **Visible status**: online / offline, sync queue, printer, drawer and shift are always visible in the top bar.
11. **Money as spoken**: typing 500 means 500.00. Quick amounts, live change / remaining, currency always shown.
12. **Full names**: item names wrap to 2 lines, never cut mid-word. Arabic and English both supported.
13. **Consistency**: same component, same place, same words. Terms follow Cashin: Check, Drawer, Tender, Business day.
14. **Recognition over recall**: the order always shows brand, type, table and customer. Best-sellers first.
15. **Offline-first**: selling never waits for the network. Queued items are labelled and synced later.
16. **Readable**: text ≥ 12 px (11 only for meta), contrast ≥ 4.5 : 1, layouts ready for RTL.

## Icons

49 line icons, 24 × 24, stroke 1.8, round caps, `currentColor`:

`check` `plus` `minus` `x` `back` `chev` `down` `alert` `lock` `search` `bell` `print` `sync` `user` `sale` `orders` `table` `shift` `chart` `box` `gear` `kitchen` `bag` `scooter` `dine` `staff` `send` `pause` `split` `note` `wifi` `trash` `swap` `cash` `card` `wallet` `percent` `gift` `qr` `phone` `chat` `noreceipt` `nfc` `home` `drawer` `more` `menu` `group` `idcard`

## Licences

Poppins and IBM Plex Sans Arabic: SIL Open Font License 1.1 (see `fonts/*/OFL.txt`). TapBack brand assets: property of TapBack.
