# Contributing to flipperone-ui

This document explains how to contribute to the [flipperone-ui](https://github.com/flipperdevices/flipperone-ui) repository.

## What this repository is

`flipperone-ui` is a **design asset repository**, not a code repository. It contains everything needed to design and prototype the FlipCTL user interface for Flipper One:

- Figma design boards for the FlipCTL interface
- ProtoPie interactive prototypes
- Asset library with reusable UI components (icons, screens, widgets)
- Design specs for the Flipper One display

This repo does not contain firmware or application code. If you are looking to contribute code, see the main Flipper One firmware and application repositories instead.

---

## Display constraints

All design and asset work must conform to the Flipper One display specification:

| Property | Value |
|---|---|
| Physical resolution | 258x144 pixels |
| Usable resolution | **256x144 pixels** |
| Color space | **RGB666** (18-bit, 64 levels per channel) |
| Anti-aliasing | **Not permitted** on pixel-level assets |
| Minimum line weight | **2px** |

Design at 1:1 pixel scale. Do not design at 2x and scale down. The display renders every pixel literally - there is no subpixel rendering or anti-aliasing at the hardware level.

---

## Contribution paths

There are two ways to contribute to this repository.

### Path 1: Design contributions (Figma / ProtoPie)

Design contributions involve editing or extending the Figma boards or ProtoPie prototypes. This path requires access to the shared Figma workspace.

**Getting Figma access**

1. Open a GitHub issue in this repository.
2. Use the issue title format: `Figma access request: [your name or GitHub username]`
3. Apply the `figma-access` label to the issue.
4. A maintainer will invite you to the Flipper One Figma workspace within a few business days.

You do not need Figma access to browse the published design specs - those are linked from the repository README.

**Viewing the ProtoPie prototype**

1. Install [ProtoPie Player](https://www.protopie.io/player) on your device (desktop or mobile).
2. Open the prototype link listed in the repository README.
3. You can interact with the prototype without a ProtoPie account.

**Making design changes**

- Work in a named Figma branch (Figma's branching feature) rather than editing the main file directly.
- Follow the component library conventions already established in the file - reuse existing components where possible.
- Keep all frames at 256x144. Do not create frames at other sizes.
- Stay within the RGB666 color space. Avoid colors that cannot be represented in 18-bit color.
- When your changes are ready for review, open a GitHub issue or pull request (see "Submitting changes" below) and link your Figma branch.

---

### Path 2: Asset contributions (exported PNGs / SVGs)

Asset contributions involve adding or updating exported graphics files to the asset library. This path does not require Figma access - you can work in any design tool that can export clean pixel-accurate assets.

**Export specifications**

| Asset type | Format | Size | Notes |
|---|---|---|---|
| Screen bitmaps | PNG | 256x144 at 1x | No alpha channel |
| Icons and glyphs | SVG | Pixel-aligned paths | No effects, no gradients |
| Component previews | PNG | Native size at 1x | Transparent background allowed |

Export PNG files at exactly 1x (native pixel dimensions). Do not export at 2x or 3x.

For SVG files, clean up the export:
- Remove all Figma or Illustrator metadata attributes
- Flatten transforms where possible
- Use integer coordinates for paths
- No blur, shadow, or filter effects

**File naming convention**

```
component-name-state.png
component-name-state.svg
```

Examples:

```
battery-icon-full.svg
battery-icon-low.svg
battery-icon-charging.svg
menu-header-default.png
menu-header-active.png
status-bar-wifi-connected.svg
status-bar-wifi-disconnected.svg
```

Use lowercase, hyphens only (no underscores or spaces), and always include the state at the end. If the component has only one state, use `default`.

**Directory structure**

Place assets in the correct directory:

```
assets/
  icons/          -- SVG icons and glyphs
  screens/        -- Full 256x144 screen PNGs
  components/     -- Individual component PNGs
  prototypes/     -- ProtoPie files (.pie)
```

---

## Submitting changes

1. Fork the repository on GitHub.
2. Add your assets or make your changes in the correct directory.
3. Open a pull request against the `main` branch.
4. In the PR description, include:
   - A brief description of what changed and why
   - Screenshots or image previews of the new or modified assets
   - Reference to any related issue or Figma branch

Pull requests without screenshots will be asked to add them before review.

---

## Issue labels

| Label | Use |
|---|---|
| `design` | Design feedback, design questions, visual bugs |
| `figma-access` | Requests for Figma workspace access |
| `bug` | Incorrect assets, broken exports, naming errors |
| `enhancement` | New components, new screen designs, new icons |

---

## Discussion

For design discussion, feedback, and questions, join the Flipper community Discord and find the **#flipper-one-design** channel. This is the best place to propose larger design changes before opening a pull request.

Discord invite link: see the repository README.
