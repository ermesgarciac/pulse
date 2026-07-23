# Pulse Design System

## Direction

Canonical visual language: Apple-inspired macOS/iOS/visionOS, with restrained glass, blur, depth, floating panels, precise typography, soft light, and native-feeling interaction.

This does not mean copying Apple interfaces. Pulse must establish its own recognizable music-workspace identity.

## Visual qualities

- Calm base surfaces with luminous blue/purple accent.
- Layered translucency only where it clarifies hierarchy.
- Dark-first professional music environment with a viable light theme later.
- Dense information presented with generous rhythm, not oversized empty cards.
- Subtle depth through material, border light, and shadow—not heavy gradients everywhere.
- Artwork and waveform color may enrich a local region without recoloring the entire shell.

## Token foundations

Tokens must exist for:

- Canvas, elevated, glass, hover, selected, and overlay surfaces.
- Primary, secondary, tertiary, disabled, and inverse text.
- Accent, success, warning, danger, info, review, offline, and sync states.
- Hairline and stronger separators.
- Corner radii by control, card, panel, and overlay.
- Spacing on a consistent base scale.
- Typography roles, not arbitrary font sizes.
- Shadow/elevation levels.
- Blur/material recipes.
- Motion duration and easing.
- Focus ring and keyboard-selection treatment.

Exact token values require a visual calibration milestone and screenshot review; do not invent “final” values in an architecture session.

## Layout rules

- Desktop shell prioritizes vertical working space.
- Sidebar is compact and collapsible.
- Top bar remains calm; avoid a crowded web-admin toolbar.
- The track table is a professional high-density surface.
- The Media Engine has stable placement and cannot feel bolted on.
- Overlays retain environmental context through depth and translucency.
- Minimum supported window dimensions must be declared and tested.

## Typography

- Use a system-native or carefully chosen variable sans family.
- Tabular numerals for BPM, time, key metrics, and progress.
- Strong distinction between track identity and supporting metadata.
- Avoid excessive all-caps.
- Truncation must preserve access to full values by tooltip/inspector.

## Iconography

- One coherent icon family with consistent optical weight.
- Symbols need text labels when meaning is not universal.
- Status cannot rely on color alone.
- Avoid decorative icons inside every label.

## Waveform

- Waveform is information, navigation, and editing—not decoration.
- Clear playhead, played/unplayed contrast, cue markers, structural sections, zoom, selection, and hover time.
- Markers remain legible over dynamic color.
- Reduced-motion mode avoids unnecessary animated glow.

## Components

Required reusable primitives include:

- App shell, top bar, Library switcher, sidebar group/item.
- Search/command trigger.
- Material panel and card.
- Toolbar, segmented control, filter chip, menu, popover.
- Data table, header, row, cell types, selection model.
- Status badge/indicator, confidence indicator, provenance label.
- Track identity, artwork, waveform, cue marker, Mini Player.
- Inspector, sheet, modal, toast, inline message.
- Empty, loading, offline, unavailable, error, and permission states.
- Form fields, rule builder, compare view, change preview.

## State design

Every interactive component documents:

- Default
- Hover
- Focus-visible
- Pressed
- Selected
- Disabled
- Loading
- Error

Every connected surface documents:

- No data
- Loading
- Partial data
- Stale cache
- Offline
- Unavailable/unsupported
- Permission denied
- Failure with retry

## Motion

- Motion explains origin, destination, hierarchy, and state change.
- Fast control feedback; slightly longer layered transitions.
- No continuous ambient animation competing with track work.
- Track Workspace expansion should feel spatially connected to the selected track.
- Respect reduced motion.

## Accessibility

- WCAG AA contrast for functional text and controls.
- Full keyboard navigation and visible focus.
- Semantic tables and accessible names.
- Scalable text without clipping critical actions.
- Status communicated through text/icon plus color.
- Waveform actions have keyboard alternatives.

## Visual verification

For every UI milestone:

1. Compare implementation with the canonical specification and approved references.
2. Capture default, loading, empty, error, selected, overlay, and narrow-window states.
3. Test at declared minimum and standard desktop sizes.
4. Verify typography, spacing, alignment, overflow, focus, and motion.
5. Record remaining deltas; “looks close” is not an acceptance criterion.

