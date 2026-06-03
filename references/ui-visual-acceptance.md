# UI Visual Acceptance

Use this reference whenever a game task touches UI, game screens, table layouts, card display, bottom action areas, overlays, settings pages, stats pages, or UI changes after audio/art asset integration.

## Mandatory Rule

Real-resolution visual acceptance is required before a UI-related task can be marked `Done`.

Do not treat these as substitutes:

- Headless smoke tests.
- Scene-load success.
- Button existence checks.
- Logic/unit tests.
- Console output indicating no script errors.

Those checks are useful for loading and logic validation, but they do not prove that a game UI is visible, clickable, or readable.

## Before Development

Inspect and record enough layout facts to avoid building into an impossible screen:

- Default project window size.
- Stretch/scale configuration.
- Root layout and primary containers.
- Fixed control sizes.
- Minimum heights and widths.
- Top status/header height.
- Bottom player interaction area height.
- Sidebars, capture areas, overlays, and margins.
- Whether vertical space is sufficient for the main interaction area at `1280x720`.

If the vertical space estimate already suggests that the bottom hand, action buttons, status hints, or decision buttons will be clipped, treat that as a design blocker before implementation.

## Required Resolutions

After development, verify the actual running game or screenshots at:

- Default window size.
- `1280x720`.
- `1366x768`.
- `1600x900`.
- `1920x1080`.

Use the actual game scene or rendered screenshots. A headless command alone is not a visual check.

## Per-Resolution Checklist

For every required resolution, confirm:

- Top status bar is fully visible.
- Central primary content is fully visible.
- Bottom player hand or primary interaction area is fully visible.
- Bottom main action buttons are visible and clickable.
- Status hints and decision buttons are not clipped.
- Capture areas and sidebars do not push bottom content out of the viewport.
- Overlay buttons are fully visible and clickable.
- Text has no clipping, overlap, or overflow.
- The player's main interaction area is visible on the first screen without scrolling unless the design explicitly requires scrolling.

## Blocking UI Problems

Treat any of these as blocking:

- Bottom hand is clipped.
- Main action buttons are clipped or cannot be clicked.
- Status hints are clipped.
- Decision buttons are clipped.
- Overlay primary/confirm/cancel buttons are clipped or cannot be clicked.
- Sidebars or capture areas push the bottom interaction area out of the viewport.
- Text overlaps, is cut off, or escapes its container.
- The main player interaction area is not visible in the first viewport.

## Reporting Requirements

When visual acceptance passes, report the checked resolutions and the observed result.

When the environment cannot perform actual visual inspection, report exactly:

```text
未完成分辨率视觉验收
```

Then state why, for example:

- No runnable game executable.
- No browser or screenshot tool.
- No display/screenshot environment.
- Scene cannot be launched.

In that case:

- Do not mark the UI task as `Done`.
- Do not claim UI acceptance passed.
- You may report headless tests separately as logic/loading validation only.
