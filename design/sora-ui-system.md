# Sora — High-Fidelity UI System (Cyberpunk Glass)

## 1) Product Intent
**Sora** is a premium Otaku ecosystem that combines:
- Social feed behavior (Instagram/X style momentum).
- AI browser utility (anime/manga/novel discovery and fast actions).
- Community depth (friends flow, shelf tracking, watch-together, secure chat).

This system is designed for **mobile-first** usage with consistent interaction patterns and deep visual cohesion.

---

## 2) Visual Direction (inspired by uploaded references)
The uploaded UI references guide these decisions:
- Soft rounded mobile surfaces with high contrast foreground content.
- Blurred translucent containers over rich blue/purple gradients.
- Card-heavy layout with compact action clusters.
- Story/reel visual prominence and profile-centric community cues.

### Theme
- **Mode**: Premium Cyberpunk Dark (default).
- **Look**: Deep midnight gradients + neon highlights + glass layers.
- **Density**: Clean and uncluttered, with intentional negative space.

### Core Color Tokens
| Token | Hex | Usage |
|---|---|---|
| `bg.base.900` | `#070A14` | Main app background |
| `bg.base.800` | `#0C1020` | Elevated background |
| `bg.grad.start` | `#0A1233` | Gradient start |
| `bg.grad.end` | `#24164D` | Gradient end |
| `accent.cyan` | `#29E7FF` | Interactive accents |
| `accent.violet` | `#9C5CFF` | Secondary accents |
| `accent.pink` | `#FF4FD8` | Alert/state highlight |
| `text.primary` | `#F4F7FF` | Primary text |
| `text.secondary` | `#B8C1E0` | Supporting text |
| `stroke.glass` | `#FFFFFF2B` | Glass borders |
| `state.success` | `#40E8A0` | Verified/safe state |
| `state.warn` | `#FFBF4D` | Warning state |
| `state.error` | `#FF5F7A` | Error state |

### Typography
- **Primary Font**: Inter / SF Pro (fallback system sans).
- **Display Accent**: Space Grotesk for headings and badges.

Scale:
- `H1`: 28/34 semibold
- `H2`: 22/28 semibold
- `Title`: 18/24 medium
- `Body`: 15/22 regular
- `Caption`: 12/16 regular
- `Micro`: 11/14 medium

### Radii, Blur, and Shadow
- `radius.sm` 12, `md` 16, `lg` 22, `xl` 28, `pill` 999.
- Backdrop blur: `blur(24px)` for nav + modal, `blur(16px)` for cards.
- Shadows: low-spread outer glow using cyan/violet at 8–14% opacity.

---

## 3) Global Architecture
### Fixed Bottom Navigation (5 tabs)
1. Home
2. AI-Browser
3. Create/Upload (center emphasis)
4. Chat/E2EE
5. Profile

**Nav spec**
- Height: 74 (plus safe area).
- Glass container (`bg: #FFFFFF12`, blur 24).
- Active icon state: neon cyan ring + label.
- Create tab: floating circular action button with violet-cyan gradient.

### Shared Layout Grid
- Width: mobile 390 base artboard.
- Horizontal padding: 16.
- Content columns: 4-column flexible.
- Vertical rhythm: 8pt scale.

### Motion System
- Transition duration: 180–260ms.
- Easing: `cubic-bezier(0.2, 0.8, 0.2, 1)`.
- Shared element transitions: avatar, media cover, title.
- Use subtle parallax in feed/reel scroll.

---

## 4) Screen Wireframes (Structured)

## A. Home Feed (Moments + Reels + Watch)
**Top bar**
- Left: Sora logo glyph + app title.
- Center: segmented filter (`Moments | Reels | Watch`).
- Right: notifications + search.

**Content stack**
1. Story/Friends ribbon (horizontal avatars + live badges).
2. Moment cards (text/news style).
3. Reel block (9:16 autoplay panel with AI filter toggles: `Sub`, `Dub`, `Clip`, `AMV`).
4. Watch card (long-form video with progress and watch party CTA).

**Moment card fields**
- Avatar, username, timestamp, location/source.
- Text body (max 5 lines before expand).
- Optional media thumbnail.
- Actions: Like, Repost, Comment, Save.

## B. AI Browser Engine
**Header**
- `Ask AI` omnibar (prompt + voice + camera).
- Quick chips: `Anime`, `Manga`, `Novel`, `Character`, `Studio`.

**Results card structure**
- Cover thumbnail + title + year.
- Metadata row: genre tags, episodes/chapters, score.
- Official streams row: Crunchyroll/Netflix/Prime/etc. icons.
- CTAs:
  - `Add to My Shelf`
  - `Reader Mode` (for manga/LN)
  - `Why this result` (AI explainability)

**Reader Mode panel**
- Clean typography, dim distractions.
- Layout toggles: vertical scroll/page-flip.
- AI actions: summarize arc, explain references, translate phrase.

## C. Create/Upload (Centered Modal Flow)
**Entry point**
- Tap center nav action → modal sheet emerges from bottom to center.

**Modal content**
- Hero dropzone: `Add Art/Media`.
- Text field: “What’s your otaku moment?”
- `Tag People` tokenized input.
- `Who can see it` dropdown: Public/Friends/Private/Custom Circle.
- Optional fields: Location, Series tag, Spoiler toggle.
- Primary CTA: `Publish Post`.

## D. Chat / E2EE + Watch Together
**Inbox**
- Tabs: Inbox / Unread / Requests.
- Lock badge on top: `Verified Secure` + key fingerprint access.

**Conversation view**
- Message bubbles on glass strips.
- Pinned media row for anime clips.
- Composer tools: emoji, media, voice, spoiler mask.

**Group Call screen**
- Participant grid.
- Prominent `Watch Together` button.
- Sync status: latency meter + host controls.
- E2EE badge persistent throughout call.

## E. Profile + My Shelf
**Top area**
- Cover gradient + avatar + status badge.
- `Friends Flow` carousel (avatars/cards of active friends).

**My Shelf sections**
- Watching
- Completed
- Plan to Watch

Each item includes:
- Poster + title + format (anime/manga/novel).
- Progress bar (ep/ch count).
- 1–10 star/rating widget.
- Quick actions: update progress, mark complete, share.

---

## 5) Component Library
### Core Components
1. `GlassNavBar`
2. `GlassCard`
3. `NeonIconButton`
4. `SegmentedSwitch`
5. `AskAIBAR`
6. `MediaReelPlayer`
7. `WatchCardLongform`
8. `ShelfItemCard`
9. `Rating10Scale`
10. `SecureLockBadge`
11. `WatchTogetherButton`
12. `CreatePostModal`

### States
- Default / Hover / Pressed / Disabled.
- Loading skeletons for feed and search cards.
- Error/empty states with themed illustrations.

### Accessibility
- Minimum 4.5:1 text contrast for core text.
- 44x44 minimum tap targets.
- Reduce motion fallback.
- Captions always available for reels/watch.

---

## 6) Seamless Transition Rules
- Keep bottom nav persistent across all primary sections.
- Preserve contextual anchors (selected filter/tab) when returning.
- Use shared element transitions between feed cards and detail screens.
- Create modal should never fully detach user context; dismiss returns to same scroll position.
- Reader Mode can collapse back into AI result card without state loss.

---

## 7) Handoff Checklist
- Figma pages:
  1. Foundations (tokens)
  2. Components
  3. Home
  4. AI Browser
  5. Create
  6. Chat/E2EE
  7. Profile/My Shelf
  8. Prototypes (flow links)
- Export token JSON for dev handoff.
- Include interaction notes per component variant.

