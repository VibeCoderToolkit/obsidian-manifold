# Manifold

A typewritten document theme for Obsidian. Cold war era paperwork: continuous
form manifold paper, carbon copy ink, stencil section labels and a rubber stamp
on every document.

![Manifold, the cream manifold sheet](./images/screenshot.png)

![Cyanotype, the blueprint sheet](./images/screenshot-dark.png)

Two sheets:

- **Light, MANIFOLD.** Aged cream manifold paper, black typewriter ribbon,
  carbon copy blue for links and accents, red stamp. Fan-fold green-bar banding
  on tables and code.
- **Dark, CYANOTYPE.** The same document reproduced as an engineering blueprint.
  Prussian blue sheet, weak cyan draughtsman's grid, chalk white type, chart cyan
  accents, red stamp.

## Install

From Obsidian: open Settings, Appearance, Themes, select Manage, search for
Manifold, then Install and use.

By hand: copy the `Manifold` folder into `<vault>/.obsidian/themes/`, then
choose it in Settings, Appearance, Themes. A restart is not required.

The four Courier Prime faces and one Special Elite face ship inside `fonts/`, so
nothing is fetched from the network and the theme works offline.

## What is in it

Paper and ink

- Tractor-feed perforations down both edges of the sheet, with the margin rule a
  continuous form printer leaves behind.
- Paper grain in light mode, a 32 px draughtsman's grid in dark mode.
- Ink bleed: a fraction of a pixel of offset on body text so the ribbon reads as
  pressed onto paper rather than rendered by a screen.

Typography

- Courier Prime everywhere, including the interface, so the whole machine reads
  as one typewriter.
- Special Elite for headings and labels. H1 and H2 are separated by rules, not by
  size alone. H4 through H6 are small boxed labels, the sort printed on a
  government form.

Document furniture

- A rubber stamp printed beside the note title. Text and visibility are both
  configurable.
- Selecting text lays a redaction bar over it and knocks the glyphs out, so the
  passage is unreadable while the selection is held. Releasing the selection
  restores it. Nothing on disk is touched.
- A passage can also be redacted for good, so the bar stays after the selection
  is gone. That needs the companion plugin, see below.
- The properties block is styled as a document control form, headed FORM 1049-A.
- A dashed cut line for horizontal rules and a closing line at the end of every
  document in reading view.

Structure

- Green-bar banding on alternating table rows and, one band per line, inside code
  blocks.
- Checkboxes are square form boxes with a typewritten X, not a rounded tick.
- Callouts are stamped dockets: square, outlined in the signal colour, title set
  in the stencil face with a rule under it. Callout icons are removed.
- Tags are uppercase bordered reference labels.
- Every radius in the application is 0. Menus, modals, tabs, toggles, scrollbars
  and buttons are square and hairline ruled.
- Period callout palette only: cobalt, teal, olive, amber, signal red, graphite.

## Redacting a passage for good

The theme draws a permanent bar for any passage marked as
`<mark class="redacted">words</mark>`. Typing that by hand works, but the
companion plugin does it for you:

- Right-click a selection and choose **Redact selection**.
- Or select and press Ctrl+Shift+R. On a Mac it is Cmd+Shift+R.
- Run it again on the same passage to lift the bar. Select the whole thing, or
  just put the cursor inside it, and run it once more.

The plugin lives in `.obsidian/plugins/manifold-redact/`. It is already switched
on and the hotkey is already bound, written into `.obsidian/community-plugins.json`
and `.obsidian/hotkeys.json`. Press Ctrl+R in Obsidian, or restart it, to load
the plugin. If the hotkey does not take, set it by hand in Settings, Hotkeys,
under "Manifold Redaction: Toggle redaction on the selection".

In the editor the line you are working on lifts its overlay so the passage can be
read and edited, and the bar closes again when you move the cursor away. In
reading view and in print the bar stays shut.

Honest limitation: this is a document marking, not encryption. The words stay in
the file as plain text, so search, sync, export and anyone who opens the note
will still see them. If a passage genuinely must not be read, delete it.

## Tuning

The theme exposes its knobs as CSS variables on `body`. Set them in a CSS
snippet (Settings, Appearance, CSS snippets) inside a `body { }` rule, or install
the community plugin **Style Settings** and use the Manifold panel, which is
already declared in the theme.

| Variable | Default | Meaning |
| --- | --- | --- |
| `--manifold-choice-paper` | `#f1ecdc` | Sheet colour for light mode |
| `--manifold-choice-ink` | `#2b2a24` | Ribbon colour |
| `--manifold-choice-accent` | `#27467f` | Accent (carbon blue in light, cyan in dark) |
| `--manifold-choice-perforation` | `#b0a483` | Tractor-feed hole ink |
| `--manifold-choice-stamp-text` | `"CONFIDENTIAL"` | Stamp wording, quotes included |
| `--manifold-choice-stamp-display` | `block` | `none` hides the stamp |
| `--manifold-choice-footer-text` | `"END OF DOCUMENT"` line | Closing line, quotes included |
| `--manifold-choice-redaction` | `#000000` | Bar laid over selected text. Black on the cream sheet, the ink colour on the blueprint. |
| `--manifold-choice-greenbar-alpha` | `0.3` | Green-bar strength, 0 disables |
| `--manifold-choice-ink-bleed` | `0.25` | Ink weight on the paper, 0 for a new ribbon |

The Style Settings values are read through a fallback, so an override applies in
both light and dark mode. If you want light and dark to differ, set
`--manifold-paper` and `--manifold-ink` directly inside a
`.theme-light { }` and `.theme-dark { }` snippet instead.

To start from a different stock entirely, copy the theme folder and edit the
"TUNABLE" block at the top of `.theme-light` in `theme.css`.

## Files

```
Manifold/
  manifest.json
  theme.css            the whole theme
  fonts/               Courier Prime ×4, Special Elite ×1
  _preview/            a standalone HTML harness, useful for design changes
```

`_preview/preview.html` renders the same markup Obsidian produces for a reading
view, so a change to `theme.css` can be judged in a browser without switching
themes. Delete the folder if you do not want it.

The companion redaction plugin is not part of the theme folder and has its own
repository, https://github.com/VibeCoderToolkit/obsidian-manifold-redact. Copy
the `manifold-redact` folder from there into `<vault>/.obsidian/plugins/` and
enable it. Existing redactions keep rendering without it, because the bar is
theme CSS.

## Licence

Courier Prime is (c) Quote-Unquote Apps, SIL Open Font License 1.1.
Special Elite is (c) Astigmatic / Brian J. Bonislawsky, Apache License 2.0.
The theme CSS is yours to do with as you like.
