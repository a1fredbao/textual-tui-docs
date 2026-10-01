---
name: textual-tui-docs
description: Use alongside textual-tui when a Textual task needs detailed local documentation for APIs, widgets, styles, events, screens, workers, testing, or runnable examples.
---

# Textual TUI Documentation

This skill is the detailed reference extension to `$textual-tui`. Use
`$textual-tui` for the project's baseline patterns and quick-start guidance.
Load this skill when exact API signatures, widget behavior, CSS property
semantics, event details, advanced patterns, or runnable examples matter.

The vendored official documentation lives in `references/docs/`. Treat it as
the primary local source before relying on memory or fetching the website.

## Workflow

1. Check the project's installed Textual version with its normal Python runner.
   For example, inspect `textual.__version__`. If the project pins a version,
   prefer behavior and signatures from that installed package.
2. Identify the narrow topic and open only the matching reference. Use the
   routing table below.
3. Search before reading a whole file:

   ```bash
   rg -n "DataTable.RowSelected|add_columns" references/docs
   rg --files references/docs | rg "data_table|worker|grid|text_area"
   ```

4. Read the relevant section, then inspect the linked example under
   `references/docs/examples/`. Examples are concrete and often answer more
   than the prose.
5. Verify exact signatures and runtime behavior against the installed package
   when the docs and local code disagree. Use `inspect.signature()`, `help()`,
   or a small Textual `run_test()` probe.

## Reference Map

| Task | Read |
| --- | --- |
| First app, installation, tutorial | `references/docs/getting_started.md`, `references/docs/tutorial.md`, `references/docs/examples/tutorial/` |
| App lifecycle, composition, mode, suspend | `references/docs/guide/app.md`, `references/docs/api/app.md`, `references/docs/api/compose.md` |
| Custom widgets and widget architecture | `references/docs/guide/widgets.md`, `references/docs/api/widget.md`, `references/docs/examples/guide/widgets/` |
| A specific built-in widget | `references/docs/widgets/<widget>.md`, matching `references/docs/examples/widgets/` file |
| Layout, containers, grid, docking, layers | `references/docs/guide/layout.md`, `references/docs/how-to/design-a-layout.md`, `references/docs/how-to/work-with-containers.md`, `references/docs/styles/grid/` |
| CSS selectors, pseudo-classes, nesting | `references/docs/guide/CSS.md`, `references/docs/examples/guide/css/` |
| Style units, box model, dimensions, colors | `references/docs/guide/styles.md`, `references/docs/css_types/`, `references/docs/examples/styles/` |
| A specific CSS property | `references/docs/styles/<property>.md`; use the grouped subdirectories for grid, links, and scrollbar colors |
| Events, input, focus, key bindings | `references/docs/guide/events.md`, `references/docs/guide/input.md`, `references/docs/guide/actions.md`, `references/docs/events/` |
| Reactive state and computed values | `references/docs/guide/reactivity.md`, `references/docs/api/reactive.md`, `references/docs/api/signal.md` |
| DOM queries and widget lookup | `references/docs/guide/queries.md`, `references/docs/api/query.md`, `references/docs/api/dom_node.md` |
| Screens, modal dialogs, navigation | `references/docs/guide/screens.md`, `references/docs/api/screen.md`, `references/docs/examples/guide/screens/` |
| Background work and async behavior | `references/docs/guide/workers.md`, `references/docs/api/worker.md`, `references/docs/api/work.md`, `references/docs/examples/guide/workers/` |
| Animation and transitions | `references/docs/guide/animation.md`, `references/docs/examples/guide/animator/` |
| Command palette and commands | `references/docs/guide/command_palette.md`, `references/docs/api/command.md` |
| Markup, content, and Rich renderables | `references/docs/guide/content.md`, `references/docs/api/content.md`, `references/docs/api/markup.md`, `references/docs/api/renderables.md` |
| Themes and design tokens | `references/docs/guide/design.md`, `references/docs/examples/themes/` |
| Testing and Pilot | `references/docs/guide/testing.md`, `references/docs/api/pilot.md`, `references/docs/examples/guide/testing/` |
| Timers and scheduled work | `references/docs/api/timer.md`, `references/docs/guide/workers.md` |
| Development console and hot reload | `references/docs/guide/devtools.md`, `references/docs/linux-console.md` |
| Packaging an app | `references/docs/how-to/package-with-hatch.md` |
| Exact module or class API | `references/docs/api/<module>.md` |
| Common errors or conceptual questions | `references/docs/FAQ.md`, `references/docs/help.md` |
| Complete widget gallery | `references/docs/widget_gallery.md`, `references/docs/widgets/index.md` |

## Documentation Conventions

- This is a snapshot of the upstream MkDocs source. Files may contain MkDocs
  directives such as `!!! note`, tabbed `=== "..."` blocks, and
  `--8<-- "docs/..."` includes.
- An include path beginning with `docs/` maps to
  `references/docs/`; for example, `docs/examples/events/custom01.py` is
  `references/docs/examples/events/custom01.py`.
- API pages are generated reference material. They are strongest for names,
  signatures, attributes, and methods; guides are better for choosing an
  approach.
- Example applications are under `references/docs/examples/`. Copy the
  relevant pattern rather than treating examples as a framework of their own.
- The snapshot excludes the upstream blog and site theme. If a topic is absent,
  use the installed package or the official online documentation as a fallback.

## Guardrails

- Do not infer current API behavior from an old example when the installed
  version exposes a different signature or deprecation.
- Do not load entire directories into context. Select one page, search it, and
  follow only the references needed for the task.
- Keep `$textual-tui` as the entry point for general implementation guidance;
  use this skill as the detailed lookup layer.
